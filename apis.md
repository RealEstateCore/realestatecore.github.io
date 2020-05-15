---
layout: page
title: API:s
permalink: /apis/
---

We have learned that a shared ontology is only part of the interoperability puzzle; in order for smart building interoperability to really take off, we also need shared API:s that allow exchange of data expressed using those shared ontologies. To that end we have standardized API:s for RealEstateCore-compliant systems. This page describes first how  RealEstateCore objects can be serialized to be transmitted over the wire; and thereafter, describes underlying transport mechanisms for such messages (our REST-based and streaming data-based API:s).

## Message Schemas

RealEstateCore provides two message serializations, suited to different uses; standard JSON-LD and our custom REC Edge Message syntax.

### JSON-LD Messages

RealEstateCore objects are RDF graph entities, so they can be expressed using the [JSON-LD](https://json-ld.org) serialization of RDF. JSON-LD is very similar to the JSON syntax web developers typically use, and it has quickly become a de facto standard for RDF transmission on the web. JSON-LD messages can be loaded and examined in a variety of tools, e.g., the [JSON-LD Playground](https://json-ld.org/playground/), for easy debugging. The REC REST API described below uses JSON-LD messaging. An example REC object (an entrance hallway with two sensors) in JSON-LD is displayed below:

```
{
  "@context": {
    "@base": "https://example.com/myDataSet#",
    "label": "http://www.w3.org/2000/01/rdf-schema#label",
    "core": "https://w3id.org/rec/core/",
    "device": "https://w3id.org/rec/device/"
  },
  "@id": "EBuildingEntranceHallway",
  "@type": "core:Room",
  "label": "JTH E-Building Entrance Hallway",
  "core:isPartOfBuilding": {
    "@id": "EBuilding",
    "@type": "core:Building"
  },
  "core:containsMountedDevice": [
    {
      "@id": "Thermometer1",
      "@type": "device:Sensor"
    },
    {
      "@id": "LuxMeter1",
      "@type": "device:Sensor"
    }
  ]
}
```

A downside to JSON-LD representation is that since it is a generic representation, it is as you can see comparatively wordy; for situations where bandwidth is limited we recommend the REC Edge Message syntax (below) instead.

### REC Edge Messages

RealEstateCore Edge Messages are compact, legible JSON messages intended for edge-to-cloud or cloud-to-edge messaging using REC semantics, regardless of underlying transport mechanism. The edge message specification is expressed using [JSON Schema](https://json-schema.org/). The schema is intended to support limited-bandwidth devices with possibly sporadic connectivity; thus it supports packing multiple REC entities per message, each with their own timestamps. An example is provided below:

```
{
  "format": "rec3.1.1",
  "deviceId": "https://recref.com/device/64b65a99-a53c-47f5-b959-1c7a641d82d8",
  "observations": [
    {
      "observationTime": "2019-05-27T20:07:44Z",
      "value": 16.1,
      "valueString": "Open",
      "valueBoolean": false,
      "quantityKind": "https://w3id.org/rec/core/Temperature",
      "sensorId" : "https://recref.com/sensor/e0d5120b-90f1-48d6-a47f-f8ccd7727b04"
    }
  ],
  "actuationCommands":[
    {
      "actuationCommandTime": "2019-05-27T20:07:48Z",
      "actuationId": "https://recref.com/actuator/a49feda7-2bc3-4793-b87f-8ec0c3909f9b/actuation/267b6a9b-e3fd-4809-b526-2/",
      "actuatorId": "https://recref.com/actuator/a49feda7-2bc3-4793-b87f-8ec0c3909f9b/",
      "value": 16.1,
      "valueString": "Open",
      "valueBoolean": false
    }
  ]
}
```

Note that the REC Edge Message specification only supports entities of the following types:

* [device:Observation](https://w3id.org/rec/device/Observation)
* [actuation:actuationCommand](https://w3id.org/rec/actuation/ActuationCommand)
* [actuation:actuationCommandResponse](https://w3id.org/rec/actuation/ActuationCommandResponse)
* [device:Exception](https://w3id.org/rec/device/Exception)

For a more extensive documentation, see the [README](https://github.com/RealEstateCore/rec/blob/master/api/edge_messages/README.md) and [schema definition](https://github.com/RealEstateCore/rec/blob/master/api/edge_messages/edge_message.schema.json) files in the `api/edge_messages` subdirectory of the REC ontology repository. 

## REST API

* Short text about how the API is defined and developed.
  * OWL2OAS
* Link to API principles document
* Link to OAS specificaiton
* Link to current generated Swagger docs

## Streaming API:s

Lorem ipsum.

### Idun ProptechOS IoTHub/Edge API

Lorem ipsum.

### MQTT

Should we write something about this being in development? Queues: rec/%entityType%, messages contain single JSON-LD entity of that type.

### Apache Kafka

Should we write something about this being in development? 

