---
title: REC Edge Messages
---

**Please note:** This material is for RealEstateCore 3.3. The REST and Edge API formats are being updated to support RealEstateCore 4, but this work is not expected to be complete until REC4 is released in non-preview version, in the fall of 2022. 

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