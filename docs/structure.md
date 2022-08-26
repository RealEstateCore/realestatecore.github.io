---
title: RealEstateCore Structure
---

**TODO: FIX AN IMAGE**

The figure above illustrates the overall REC structure and key design points, which are described in greater detail below. The [browsable reference documentation](/ontology/) contains a list of all types and all of their properties. 

RealEstateCore employs a set of design principles:

* Parthood is described using the `hasPart` and `isPartOf` relationships. Instances of a type can only have other instances of the same type as parts; e.g., assets can only have assets as parts, spaces can only have spaces, and so forth. This provides a simple a consistent way for developers to navigate the building topology. To jump across these topologies (e.g., to indicate that an asset has a spatial location), other specific properties are used, see below.
* Spatial location is described using `hasLocation` and `isLocationOf` relationships together with some `Space` instance.
* Administrative parthood, i.e., membership in a `Collection`, is described using the relationships `includedIn` and `includes`.

## Spaces

A `Space` is contiguous part of the physical world that has a 3D spatial extent and that contains or can contain sub-spaces. For example a *Region* can contain many *Sites*, which in turn can contain many *Buildings*, which in turn can contain *Levels* and *Rooms*. This concept is comparable to a [Zone](https://w3id.org/bot#Zone) in the [BOT ontology](http://w3id.org/bot). Note that we differentiate between spaces that are designed/architected (subtypes of `Architecture`) and spaces that are not; the former have a number of properties specific to constructed spaces.

    :JU-E-Building      rdf:type        rec:Building
    :JU-E-Building-L1   rdf:type        rec:Level
    :E2412              rdf:type        rec:Room
    :E2412              rec:isPartOf   :JU-E-Building-L1
    :JU-E-Building-L1   rec:isPartOf   :JU-E-Building

![Space example as a graph](/images/SpaceExample.png)

## Building elements

A `BuildingElement` is a part that constitutes a piece of a building's structural makeup, for example Facade, Wall, Slab, RoofInner, etc.

## Assets

An `Asset` is an object which is placed inside of a building, but is not an integral part of that building's structure. We provide a hierarchy of assests, for example architectural, furniture, etc. Our Equipment asset hierarchy is sourced from our collaboration with [Brick Schema](https://brickschema.org).

    :AHU1               rdf:type        brick:AHU
    :MaintenanceRoom1   rdf:type        rec:Room
    :MainLobby          rdf:type        rec:Room
    :AHU1               rec:locatedIn   :MaintenanceRoom1
    :AHU1               brick:feeds     :MainLobby

**TODO: FIX BELOW IMAGE**

![Asset example as a graph](/images/AssetExample.png)

## Points, sensing and actuating

A `Point` indicates the capacity of an entity, be it an Architecture, an Asset, to produce or ingest data. The Point hierarchy is sourced from our collaboration with [Brick Schema](https://brickschema.org).  Specific subclasses specialize this behavior: `Sensor` entities harvest data from the real world, `Command` entities accept commands from a digital twin platform, and `Setpoint` entities configure some capability or system, etc. Points are connected to spaces or assets using the `hasPoint` and `isPointOf` relations.

The `Event` class includes subclasses that can be utilized to represent individual observations or command actuations in a REC-based system, e.g., `ObservationEvent` or `ActuationEvent`. 

    :TemperatureSensor1     rdf:type                        brick:Temperature_Sensor
    :E2414                  rdf:type                        rec:Room
    :TemperatureSensor1     core:isPointOf                  :E2414
    :TemperatureSensor1     brick:hasQuantity               :Temperature
    :TemperatureSensor1     brick:hasUnit                   unit:DEG_C
    :Obs9442234442          rdf:type                        rec:ObservationEvent
    :Obs9442234442          rec:sourcePoint                 :TemperatureSensor1
    :Obs9442234442          rec:payload                     "19.8"

**TODO: FIX BELOW IMAGE**
![Capability example as a graph](/images/CapabilityExample.png)

## Collections

`Collection` covers administrative groupings of entities that are adressed and treated as a unit for some purpose. These entities may have some spatial arrangement (e.g., an apartment is typically contiguous) but that is not a requirement (see, e.g., a distributed campus consisting of spatially disjoint plots or buildings).

## Agents, persons, and organizations

`Agent` describes any basic types of stakeholder that can have roles or perform activities, and is subclassed into, e.g., people, companies, departments. This bears some resemblance to FOAF, which it was originally inspired by, but has since diverged due to requirements shift.