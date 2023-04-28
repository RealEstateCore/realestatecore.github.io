---
title: Resources
permalink: /resources/
---

## REC Ontology

The RealEstateCore ontology is released in the both [DTDL (Digital Twin Definition Language)](https://github.com/Azure/opendigitaltwins-dtdl)  and [SHACL (Shapes Constraint Language)](https://www.w3.org/TR/shacl/) languages, for broadest availability across technology stacks. For a discussion on the differences and tradeoffs between these versions, see the documentation page [DTDL or SHACL](/docs/DTDL-or-SHACL).

* [DTDLv2](https://github.com/RealEstateCore/rec/tree/main/Source/DTDLv2)
* [SHACL](https://github.com/RealEstateCore/REC4/tree/main/Source/SHACL)

## API Definitions

* [OpenAPI (Swagger) specification](https://raw.githubusercontent.com/RealEstateCore/rec/main/API/REST/RealEstateCore.Ontology.DTDLv2.yaml) -- [Documentation](/docs/API/REST) -- This RESTful API specifices how clients and other systems can create, read, update, and delete entities in a RealEstateCore-based smart building platform.
* [Edge message specification](https://raw.githubusercontent.com/RealEstateCore/rec/main/API/Edge/edge_message.schema.json) -- [Documentation](/docs/API/Edge) -- Our southbound format, enabling battery- or bandwidth-constrained edge devices to communicate sensor readings, commands, alerts, etc. upward into a RealEstateCore-based platform. 

## Software

* [SHACL2DTDL](https://github.com/RealEstateCore/SHACL2DTDL) -- [Documentation](/docs/tools/SHACL2DTDL) -- Translates SHACL shapes to DTDL interfaces.
* [DTDL2OAS](https://github.com/RealEstateCore/DTDL2OAS) -- [Documentation](/docs/tools/DTDL2OAS) -- Generates OpenAPI (Swagger) specifications corresponding with a DTDL ontology.
* [DTDL2MD](https://github.com/RealEstateCore/DTDL2MD) -- [Documentation](/docs/tools/DTDL2MD) -- Generates Markdown documentation for a DTDL ontology.

## Configurations

* [Home Assistant Configurations](https://github.com/RealEstateCore/HomeAssistantConfigs) –- This repository hosts configuration files for the popular Home Assistant open source home automation platform, enabling [Home Assistant](https://www.home-assistant.io/) to emit RealEstateCore-formatted messages.

## Documents

* [Procurement](https://github.com/RealEstateCore/procurement) -- This repository contains documentation that supports real estate holder procurement of new buildings that speak RealEstateCore from the outset. Presently this documentation is availabile in Swedish, English, Dutch, and French.
