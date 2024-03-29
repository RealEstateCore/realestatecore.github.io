---
title: Tenant modelling
---

## Scenario

This guide continues building on our previous [Spatial](../spatial/) modelling guide; to get the most out of it, please skim it first.

The owner of the *Costello Heights* building, *Costello Real Estate* now wishes to add to their knowledge graph information about their tenants, what part of the property those tenants are leasing, the duration of their lease contract, etc. While such modelling in itself may not provide many business benefits over some existing tenant database system, integrating it into the smart building knowledge graph will allow the property owner to easily query for, e.g., *Which tenants will be affected by maintenance work on the lower AHU*, or *What’s the reported occupancy rate of conference rooms leased by Initech*.

## Types used

In addition to the types from the previous guide, this modelling task will include:

* [Agent](/ontology/Agent/Agent)
    * [Person](/ontology/Agent/Person)
    * [Organization](/ontology/Agent/Organization/Organization) > [Company](/ontology/Agent/Organization/Company.md)
* [Event](/ontology/Event/Event)
    * [Lease](/ontology/Event/Lease)
* [Collection](/ontology/Collection/Collection)
    * [Apartment](/ontology/Collection/Apartment)

Conceptually, we think of Leases as events in that they have a start and end timestamp. They add to these attributes certain relationships (see below) that indicate what is being leased, by whom, to whom.

## Relationships and Properties used

### Relationships

* [Architecture](/ontology/Space/Architecture/Architecture).ownedBy -- Relates a piece of architecture to its legal owner.
* [Apartment](/ontology/Collection/Apartment).includes -- Indicates which rooms that make up a given apartment.
* [Lease](/ontology/Event/Lease).leasor -- The owner Agent that is leasing out something; in this case, the *Costello Real Estate* corporation.
* [Lease](/ontology/Event/Lease).leasee -- The Agent that is leasing (i.e., making use of) the leased object.
* [Lease](/ontology/Event/Lease).leaseOf -- What is being leased; in this case, a Space or an Apartment (a Collection of spaces), but might as well be a desk, or a piece of equipment such as a coffee machine, projector, etc.


### Properties

* [Event](/ontology/Event/Event).start
* [Event](/ontology/Event/Event).end

## Graphical representation

![Graphical representation of spatial modelling solution](tenant.png)

## RDF triples representation (SHACL models)

[Download TTL file](tenant.ttl)

```
# Namespaces
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
@prefix rec: <https://w3id.org/rec#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .
@prefix : <https://example.com#> .

# Type declarations. 
# Spaces
:CostelloHeights    rdf:type        rec:Building        .
:LowerFloor         rdf:type        rec:Level           .
:UpperFloor         rdf:type        rec:Level           .
:AtticFloor         rdf:type        rec:Level           .
:120                rdf:type        rec:Room            .
:121                rdf:type        rec:Room            .
:122                rdf:type        rec:Room            .
:123                rdf:type        rec:Room            .
:124                rdf:type        rec:Room            .

# Apartments and leases
:Apartment1         rdf:type        rec:Apartment       .
:Apartment2         rdf:type        rec:Apartment       .
:Lease1             rdf:type        rec:Lease           .
:Lease2             rdf:type        rec:Lease           .
:UpperFloorLease    rdf:type        rec:Lease           .
:AtticLease         rdf:type        rec:Lease           .

# Agents
:CostelloRealEstate rdf:type        rec:Company         .
:Initech            rdf:type        rec:Company         .
:LumberghInc        rdf:type        rec:Company         .
:JohnDoe            rdf:type        rec:Person          .
:JaneDoe            rdf:type        rec:Person          .

# Spatial topology & apartment inclusion
:CostelloHeights    rec:hasPart     :LowerFloor     .
:CostelloHeights    rec:hasPart     :UpperFloor     .
:CostelloHeights    rec:hasPart     :AtticFloor     .
:LowerFloor         rec:hasPart     :120            .
:LowerFloor         rec:hasPart     :121            .
:LowerFloor         rec:hasPart     :122            .
:LowerFloor         rec:hasPart     :123            .
:LowerFloor         rec:hasPart     :124            .
:Apartment1         rec:includes    :120            .
:Apartment1         rec:includes    :121            .
:Apartment2         rec:includes    :122            .
:Apartment2         rec:includes    :123            .
:Apartment2         rec:includes    :124            .

# Lease relations
:Lease1             rec:leasor      :CostelloRealEstate     .
:Lease1             rec:leasee      :JohnDoe                .
:Lease1             rec:leaseOf     :Apartment1             .
:Lease2             rec:leasor      :CostelloRealEstate     .
:Lease2             rec:leasee      :JaneDoe                .
:Lease2             rec:leaseOf     :Apartment2             .
:UpperFloorLease    rec:leasor      :CostelloRealEstate     .
:UpperFloorLease    rec:leasee      :Initech                .
:UpperFloorLease    rec:leaseOf     :UpperFloor             .
:AtticLease         rec:leasor      :CostelloRealEstate     .
:AtticLease         rec:leasee      :LumberghInc            .
:AtticLease         rec:leaseOf     :AtticFloor             .

# Lease durations
:Lease2             rec:start       "2022-01-01T08:00:00Z"^^xsd:dateTime        .
:AtticLease         rec:start       "2015-07-01T08:00:00Z"^^xsd:dateTime        .
:AtticLease         rec:end         "2022-12-31T23:59:59Z"^^xsd:dateTime        .
```

## Azure Digital Twins JSON representation (DTDL models)

[Download JSON file](tenant.json)

```
{
    "digitalTwinsFileInfo": {
        "fileVersion": "1.0.0"
    },
    "digitalTwinsGraph": {
        "digitalTwins": [
            {
                "$dtId": "CostelloHeights",
                "$etag": "W/\"ee7f9ac5-cde8-482e-9f3f-de4b3da170f8\"",
                "geometry": "[[14.16, 57.77], ... , [14.16, 57.77]]",
                "$metadata": {
                    "$model": "dtmi:org:w3id:rec:Building;1"
                }
            },
            {
                "$dtId": "UpperFloor",
                "$etag": "W/\"3d904969-d842-4bf0-b1f6-7ff6b687460c\"",
                "levelNumber": 2,
                "$metadata": {
                    "$model": "dtmi:org:w3id:rec:Level;1"
                }
            },
            {
                "$dtId": "LowerFloor",
                "$etag": "W/\"459c63ee-04d7-4031-91fb-e50e64a5d8b4\"",
                "levelNumber": 1,
                "geometry": "[[0.5, 0.5], ... , [15.5, 15.5]]",
                "$metadata": {
                    "$model": "dtmi:org:w3id:rec:Level;1"
                }
            },
            {
                "$dtId": "AtticFloor",
                "$etag": "W/\"ea99986e-30a3-4ac8-ba9e-54d4fe163e55\"",
                "$metadata": {
                    "$model": "dtmi:org:w3id:rec:Level;1"
                }
            },
            {
                "$dtId": "CostelloRealEstate",
                "$etag": "W/\"400fb626-1ded-49bc-8d20-6ac6123fe6c4\"",
                "$metadata": {
                    "$model": "dtmi:org:w3id:rec:Company;1"
                }
            },
            {
                "$dtId": "Initech",
                "$etag": "W/\"db553c47-a3da-4f01-b0c6-d4f85bc9a236\"",
                "$metadata": {
                    "$model": "dtmi:org:w3id:rec:Company;1"
                }
            },
            {
                "$dtId": "LumberghInc",
                "$etag": "W/\"cc518ea3-90a0-4264-9a49-80f6155792da\"",
                "$metadata": {
                    "$model": "dtmi:org:w3id:rec:Company;1"
                }
            },
            {
                "$dtId": "120",
                "$etag": "W/\"d1db10f1-a098-4c5d-8e2f-092e8c11f418\"",
                "geometry": "[[4.0, 2.5], ... , [4.0, 2.5]]",
                "$metadata": {
                    "$model": "dtmi:org:w3id:rec:Room;1"
                }
            },
            {
                "$dtId": "121",
                "$etag": "W/\"de627e80-7ec8-438f-a06b-6eed138a53f6\"",
                "$metadata": {
                    "$model": "dtmi:org:w3id:rec:Room;1"
                }
            },
            {
                "$dtId": "122",
                "$etag": "W/\"6684da81-1756-4cc5-9301-cd8aa60638ab\"",
                "$metadata": {
                    "$model": "dtmi:org:w3id:rec:Room;1"
                }
            },
            {
                "$dtId": "123",
                "$etag": "W/\"ba40792d-7a5d-4828-86cb-82e5f5b0d169\"",
                "$metadata": {
                    "$model": "dtmi:org:w3id:rec:Room;1"
                }
            },
            {
                "$dtId": "124",
                "$etag": "W/\"9a17f209-d862-4857-ae31-be650c4c68d5\"",
                "$metadata": {
                    "$model": "dtmi:org:w3id:rec:Room;1"
                }
            },
            {
                "$dtId": "JohnDoe",
                "$etag": "W/\"0b86cc72-9c8d-420d-a65c-da1253a50c27\"",
                "$metadata": {
                    "$model": "dtmi:org:w3id:rec:Person;1"
                }
            },
            {
                "$dtId": "JaneDoe",
                "$etag": "W/\"ff575ee8-10e5-4b8d-a3f2-c95a1a1db4c8\"",
                "$metadata": {
                    "$model": "dtmi:org:w3id:rec:Person;1"
                }
            },
            {
                "$dtId": "Apartment1",
                "$etag": "W/\"b3fde95a-add6-4f10-8d8e-fdd94d9bdff1\"",
                "$metadata": {
                    "$model": "dtmi:org:w3id:rec:Apartment;1"
                }
            },
            {
                "$dtId": "Apartment2",
                "$etag": "W/\"5bac6a1a-fef9-428d-84cf-5ff9a1b472bf\"",
                "$metadata": {
                    "$model": "dtmi:org:w3id:rec:Apartment;1"
                }
            },
            {
                "$dtId": "Lease1",
                "$etag": "W/\"016a73c9-3eb2-46ac-8021-1e8ffa02c7f1\"",
                "$metadata": {
                    "$model": "dtmi:org:w3id:rec:Lease;1"
                }
            },
            {
                "$dtId": "Lease2",
                "$etag": "W/\"1afe7baf-a8be-43c7-8aea-f8cd58fa4ae0\"",
                "start": "2022-01-01T08:00:00Z",
                "$metadata": {
                    "$model": "dtmi:org:w3id:rec:Lease;1"
                }
            },
            {
                "$dtId": "UpperFloorLease",
                "$etag": "W/\"1bb4cc46-1f66-4265-b13d-e83c3dcea198\"",
                "$metadata": {
                    "$model": "dtmi:org:w3id:rec:Lease;1"
                }
            },
            {
                "$dtId": "AtticLease",
                "$etag": "W/\"2f19f0f0-8e81-456b-815c-000791a03670\"",
                "end": "2022-12-31T23:59:59Z",
                "start": "2015-07-01T08:00:00Z",
                "$metadata": {
                    "$model": "dtmi:org:w3id:rec:Lease;1"
                }
            }
        ],
        "relationships": [
            {
                "$relationshipId": "6fea7ce8-1827-4d6f-8773-dc42ffd124b5",
                "$sourceId": "CostelloHeights",
                "$targetId": "UpperFloor",
                "$relationshipName": "hasPart",
                "$etag": "W/\"fbbb0925-b5a2-4221-ad4e-4eb45e6311ef\""
            },
            {
                "$relationshipId": "5451cb07-4a2c-4b0e-b2f8-a81f777e85c6",
                "$sourceId": "CostelloHeights",
                "$targetId": "LowerFloor",
                "$relationshipName": "hasPart",
                "$etag": "W/\"99b9f7b6-a150-4923-952f-f08f14bf08be\""
            },
            {
                "$relationshipId": "52a97c6b-3f2e-4c8b-b93c-de854836e4c4",
                "$sourceId": "CostelloHeights",
                "$targetId": "CostelloRealEstate",
                "$relationshipName": "ownedBy",
                "$etag": "W/\"c0edc873-c1ef-441f-9cd0-36425f5fda47\""
            },
            {
                "$relationshipId": "1c9beca2-4a8c-45e9-b674-a0c5af9095cf",
                "$sourceId": "CostelloHeights",
                "$targetId": "AtticFloor",
                "$relationshipName": "hasPart",
                "$etag": "W/\"0ccbefbe-1558-4353-95ee-a74bf4864e03\""
            },
            {
                "$relationshipId": "ecd6ee86-9a5a-4622-b49b-c7f1152fd9b2",
                "$sourceId": "LowerFloor",
                "$targetId": "120",
                "$relationshipName": "hasPart",
                "$etag": "W/\"c40a3d21-422a-4266-adef-d227e91a5b86\""
            },
            {
                "$relationshipId": "68ced7c1-331c-445f-bf0b-a6210e712711",
                "$sourceId": "LowerFloor",
                "$targetId": "121",
                "$relationshipName": "hasPart",
                "$etag": "W/\"f00d1bf6-a19c-41ba-b252-03e991ee6686\""
            },
            {
                "$relationshipId": "4355b6e6-594d-4822-b998-10f458416a67",
                "$sourceId": "LowerFloor",
                "$targetId": "122",
                "$relationshipName": "hasPart",
                "$etag": "W/\"ffb8efd0-d4ff-4ab3-822f-20033428b831\""
            },
            {
                "$relationshipId": "10be59cf-d2c4-44f6-af5d-fdacaa17bcff",
                "$sourceId": "LowerFloor",
                "$targetId": "123",
                "$relationshipName": "hasPart",
                "$etag": "W/\"4dd04bc8-4597-4f34-bd44-786badbf352b\""
            },
            {
                "$relationshipId": "dc5b29bc-3d05-413e-8ab2-7aff6e65db32",
                "$sourceId": "LowerFloor",
                "$targetId": "124",
                "$relationshipName": "hasPart",
                "$etag": "W/\"193d754d-bbd8-4c00-b64f-00b1fce90ded\""
            },
            {
                "$relationshipId": "da803177-4322-49aa-8935-afa3a184b79a",
                "$sourceId": "Lease1",
                "$targetId": "Apartment1",
                "$relationshipName": "leaseOf",
                "$etag": "W/\"279614fe-1899-4239-a989-cc5426288407\""
            },
            {
                "$relationshipId": "52df1cd8-32ae-4032-8811-e3a12d29b8e4",
                "$sourceId": "Lease1",
                "$targetId": "JohnDoe",
                "$relationshipName": "leasee",
                "$etag": "W/\"8a0a6e04-369f-4199-9bae-535138debd7c\""
            },
            {
                "$relationshipId": "e94e8378-c54a-40f8-9e4e-a6d63438bb9b",
                "$sourceId": "Lease1",
                "$targetId": "CostelloRealEstate",
                "$relationshipName": "leasor",
                "$etag": "W/\"a756eff8-55f9-418b-a704-f0ba88ebe812\""
            },
            {
                "$relationshipId": "5bbb7b2d-4e7a-4b1c-870c-2a94554a973c",
                "$sourceId": "Lease2",
                "$targetId": "CostelloRealEstate",
                "$relationshipName": "leasor",
                "$etag": "W/\"d3a1db30-f152-46fb-a164-4521506e6ca4\""
            },
            {
                "$relationshipId": "1e8c2968-c301-4dfa-912a-8d06e61da650",
                "$sourceId": "Lease2",
                "$targetId": "JaneDoe",
                "$relationshipName": "leasee",
                "$etag": "W/\"24b30c8d-23ea-4302-a5de-376afdb0fe99\""
            },
            {
                "$relationshipId": "03a89721-f08e-4fde-b704-0ed28d6de99e",
                "$sourceId": "Lease2",
                "$targetId": "Apartment2",
                "$relationshipName": "leaseOf",
                "$etag": "W/\"e31f06b9-4ec0-46a3-a763-c31a45c0db7e\""
            },
            {
                "$relationshipId": "72422cb2-b93e-4500-aedc-2957d9a64814",
                "$sourceId": "Apartment1",
                "$targetId": "120",
                "$relationshipName": "includes",
                "$etag": "W/\"09e7f42f-246e-4646-a02f-e62253234655\""
            },
            {
                "$relationshipId": "82884024-788e-4069-b1f5-16f04aa33be5",
                "$sourceId": "Apartment1",
                "$targetId": "121",
                "$relationshipName": "includes",
                "$etag": "W/\"46e9396b-fea1-4434-96c0-0bd0284ea3cc\""
            },
            {
                "$relationshipId": "69c44a6c-52b7-47a5-9fcf-c07663f637e8",
                "$sourceId": "Apartment2",
                "$targetId": "122",
                "$relationshipName": "includes",
                "$etag": "W/\"9c1e120e-11c0-459a-a3a5-35af9d9b84f9\""
            },
            {
                "$relationshipId": "6d945479-ca06-44db-a151-6ba6c44e78fa",
                "$sourceId": "Apartment2",
                "$targetId": "123",
                "$relationshipName": "includes",
                "$etag": "W/\"5aaec31c-b645-41ca-b698-8b0dde28dc90\""
            },
            {
                "$relationshipId": "7e3d1b50-cec9-4e59-96e3-5bb576aa32f3",
                "$sourceId": "Apartment2",
                "$targetId": "124",
                "$relationshipName": "includes",
                "$etag": "W/\"a42bff68-bea1-4546-9e4d-d32e8556f7c4\""
            },
            {
                "$relationshipId": "667f3a8b-baaf-46b3-a6e6-bae6f907ad60",
                "$sourceId": "UpperFloorLease",
                "$targetId": "UpperFloor",
                "$relationshipName": "leaseOf",
                "$etag": "W/\"8be3936e-c1e9-4894-bdd5-f1452f40dfcf\""
            },
            {
                "$relationshipId": "23368da3-ea7a-45c6-89d6-9bde8486b308",
                "$sourceId": "UpperFloorLease",
                "$targetId": "Initech",
                "$relationshipName": "leasee",
                "$etag": "W/\"196ba74b-a984-4330-b9a0-d973ac1c2978\""
            },
            {
                "$relationshipId": "68720ba2-85fa-4ee7-a05c-2622c33324d0",
                "$sourceId": "UpperFloorLease",
                "$targetId": "CostelloRealEstate",
                "$relationshipName": "leasor",
                "$etag": "W/\"da5f3c2d-7209-4fee-bb38-ca2d40ebe4f9\""
            },
            {
                "$relationshipId": "1907c610-eb41-4b29-820f-b765e55d94d1",
                "$sourceId": "AtticLease",
                "$targetId": "AtticFloor",
                "$relationshipName": "leaseOf",
                "$etag": "W/\"4a0c7ee0-c0c5-4dc3-9976-0c93fec973e0\""
            },
            {
                "$relationshipId": "3c5af3ec-5c3d-443a-9cfb-a3361eafcf11",
                "$sourceId": "AtticLease",
                "$targetId": "LumberghInc",
                "$relationshipName": "leasee",
                "$etag": "W/\"54ca5a82-d22d-4241-8ec2-d09bbb119bb6\""
            },
            {
                "$relationshipId": "69edf208-6575-453c-8462-5ab6c3f42091",
                "$sourceId": "AtticLease",
                "$targetId": "CostelloRealEstate",
                "$relationshipName": "leasor",
                "$etag": "W/\"b1777032-f1e0-4b2e-a687-32cf3c9fa4f7\""
            }
        ]
    }
}
```
