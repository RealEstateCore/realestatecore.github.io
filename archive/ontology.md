---
title: Ontology
permalink: /archive/ontology/
---

## The Building Knowledge Graph

RealEstateCore (REC) is an ontology, which can most easily be thought of as a standard and interoperable schema for building knowledge graphs; it defines the types (*classes*) of nodes you can have in your graph, the types of relations (*object properties*) these nodes have with one another, and the types of data values (*data properties*) associated with them. By using REC, you get two distinct advantages:

1. You do not need to spend a lot of time and resources on designing your own data model; we've already done it for you.
2. Your data is automatically compatible with that of other REC users (e.g., your suppliers or your customers), greatly simplifying data and process integration (doubly so if you also utilize the REC APIs to exchange data).

RealEstateCore is used with RDF-based knowledge graphs. There is a wealth of information about RDF available on the net, which we will not duplicate here; suffice to say that in RDF, a knowledge graph is made up of a (potentially very large) set of statements, each of which consist of three components: the *subject* of the statement, the *predicate* that captures *what* the statement intends to say about the subject , and the *object* that carries the value of that assertion. E.g., a graph might include the statement `WhiteHouse ownedBy USGovernment`, or `IBM hasNumberOfEmployees 345900`. Due to their structure, a statement is often known as a *triple*.

In the below we introduce some key REC classes and exemplify their use with RDF triples.

## Modularity

RealEstateCore consists of a set of individual ontology modules, tied together by a shared core. The intent is that users be able to utilize only those modules that their particular use case requires. 

The REC module nanespaces are organized using the following pattern `https://w3id.org/rec/{MODULE}/`, with entities being minted using slashes as module-entity delimiter, e.g., `https://w3id.org/rec/building/Balcony`. To differentiate beteween versions we utilize version IRIs; a specific version of a specific module can be resolved as `https://w3id.org/rec/{MODULE}/{VERSION}/`.

We also provide a composed ontology consisting of all modules (RealEstateCore Full), as we've found many users prefer to include everything by default. REC Full is available at `https://w3id.org/rec/full/`.

Note that we use HTTP content negotation to automatically return an appropriate representation of the above URIs in accordance with what the client requests. E.g., if you are using a web browser to access those links, you will get the HTML-based ontology documentation; but if you load them in a tool that requests RDF (e.g., Protégé or TopBraid Composer, you will get that ontology representation instead.

## Key Classes

<img src="/images/OntologyDiagram.jpg" alt="RealEstateCore ontology overview" style="width: 75%;" />

The figure above (borrowed from the [DTDL port](https://github.com/Azure/opendigitaltwins-building) of REC) illustrates a subset of the key classes in RealEstateCore, which are described in greater detail below. 

RealEstateCore employs a set of design principles shared across these classes:

* Parthood is described using the `core:hasPart` and `core:isPartOf` object properties. Restrictions are defined on top-level classes such that instances of these classes can only have other instances of the same class as parts; e.g., assets can only have assets as parts, spaces can only have spaces, and so forth. This provides a simple a consistent way for developers to navigate the building topology. To jump across these topologies (e.g., to indicate that an asset has a spatial location, other specific properties are used, see below.)
* Spatial location is described using `core:hasLocation` and `core:isLocationOf` object properties together with some `core:Space` instance. 
* *Administrative parthood*, i.e., membership in a `core:Collection`, is described using the object properties `core:includedIn` and `core:includes`.
* To indicate that a capability *or* asset has a coverage or impact area (e.g., a camera covering a lobby, an HVAC unit covering an apartment), or other functional relation to some REC entity, we utilize the `core:serves` and `core:servedBy` object properties. These properties are at present comparatively ambiguous. 

For exhaustive documentation, see the [PyLODE docs](https://doc.realestatecore.io/).

### Spaces

A `core:Space` is contiguous part of the physical world that has a 3D spatial extent and that contains or can contain sub-spaces. For example a *Region* can contain many pieces of *Land*, which in turn can contain many *Buildings*, which in turn can contain *Levels* and *Rooms*. This concept is comparable to a [Zone](https://w3id.org/bot#Zone) in the [BOT ontology](http://w3id.org/bot).

    :JU-E-Building      rdf:type        core:Building
    :JU-E-Building-L1   rdf:type        core:Level
    :E2412              rdf:type        core:Room
    :E2412              core:isPartOf   :JU-E-Building-L1
    :JU-E-Building-L1   core:isPartOf   :JU-E-Building

![Space example as a graph](/images/SpaceExample.png)

### Building components

A `core:BuildingComponent`is a part that constitutes a piece of a building's structural makeup, for example Facade, Wall, Slab, RoofInner, etc.

### Assets

A `core:Asset` is an object which is placed inside of a building, but is not an integral part of that building's structure. We provide a substantial hierarchy of assests, for example architectural, furniture, equipment, systems, etc.

    :AHU1               rdf:type        asset:AirHandlingUnit
    :MaintenanceRoom1   rdf:type        core:Room
    :MainLobby          rdf:type        core:Room
    :AHU1               core:locatedIn  :MaintenanceRoom1
    :AHU1               core:serves     :MainLobby

![Asset example as a graph](/images/AssetExample.png)

### Logical device

`core:LogicalDevice`: A physical or logical object defined as an electronic equipment or software that communicates and interacts with a digital twin platform. A logical device could be an integrated circuit inside of a smart HVAC unit, or a virtual server running on a Kubernetes cluster. Logical devices can have Capability instances (through hasCapability) that describe their input/output capabilities. If Logical Devices are embedded within Asset entities (through the hostedBy property) such capabilities typically denote the capabilities of the asset.

### Capabilities, sensing and actuating

A `core:Capability` indicates the capacity of a entity, be it a Space, an Asset, or a LogicalDevice, to produce or ingest data. This is equivalent to the term "point" in Brick Schema and generic Building Management System. Specific subclasses specialize this behavior: `core:Sensor` entities harvest data from the real world, `core:Actuator` entities accept commands from a digital twin platform, and `core:Parameter` entities configure some capability or system. Capabilities are connected to spaces or assets using the `core:isCapabilityOf`and `core:hasCapability` object properties.

The `core:Event` class includes subclasses that can be utilized to represent individual observations or actuations in a REC-based system, e.g., `core:Observation` or `actuation:ActuationRequest`. For a further discussion on RealEstateCore-based actuation, see our [tutorial on the subject](/tutorials/actuation).

    :TemperatureSensor1     rdf:type                        device:TemperatureSensor
    :E2414                  rdf:type                        core:Room
    :TemperatureSensor1     core:isCapabilityOf             :E2414
    :TemperatureSensor1     qudt:hasQuantityKind            quantitykind:Temperature
    :TemperatureSensor1     qudt:unit                       unit:DEG_C
    :Obs9442234442          rdf:type                        core:Observation
    :Obs9442234442          core:observationGeneratedBy     :TemperatureSensor1
    :Obs9442234442          core:value                      "19.8"

![Capability example as a graph](/images/CapabilityExample.png)

### Collections

`core:Collection` covers administrative groupings of entities that are adressed and treated as a unit for some purpose. These entities may have some spatial arrangement (e.g., an apartment is typically contiguous) but that is not a requirement (see, e.g., a distributed campus consisting of spatially disjoint plots or buildings).

### Agents, persons, and organizations

`core:Agent` describes any basic types of stakeholder that can have roles or perform activities, and is subclassed into, e.g., people, companies, departments. This bears some resemblance to FOAF, which it was originally inspired by, but has since diverged due to requirements shift.

## Measurement units and data values

We heavily reuse [QUDT.org](http://qudt.org/) for observable property quantity kinds ( *Temperature*, *Pressure*, *Angle*, etc.) and for measurement units. In order to reduce complexity and dependency on remote IRIs we have opted to clone their design into REC as-is, maintaining the original namespaces.

## Ontology Documentation

For every REC release, we auto-generate documentation directly from the ontology and its annotations; see the documentation site, where each version is listed, at [https://doc.realestatecore.io](https://doc.realestatecore.io).

For an overview of RealEstateCore (or other ontologies) we recommend the use of [WebVOWL](http://www.visualdataweb.de/webvowl/). A version of WebVOWL is embedded in the autogenerated documentation.