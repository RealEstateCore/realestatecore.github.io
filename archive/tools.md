---
title: Tools
permalink: /archive/tools/
---

In addition to the ontology itself, the RealEstateCore Consortium also hosts the development of several software tools, configuration files, and documents that support the adoption and utilization of REC and other ontologies.

## Software

* [OWL2OAS](/OWL2OAS/) -- This is a converter for translating 
OWL ontologies into OpenAPI Specification documents. 
OpenAPI Specification is a standard for describing 
REST endpoints and operations. This tool generates 
REST endpoints for the classes (i.e., concepts) 
declared in an ontology, and generates JSON-LD 
schemas for those classes based on the object and 
data properties that they are linked to in the 
ontology (either via rdfs:domain/rdfs:range, or 
via property restrictions). OWL2OAS is used to 
generate the official RealEstateCore REST API.
* [OWL2DTDL](https://github.com/Azure/opendigitaltwins-tools) -- A converter for translating 
OWL ontologies into DTDL (Digital Twin Definition Language) interface definitions, for use, e.g., 
with Microsoft Azure Digital Twins. This tool is used to generate the [official DTDL version of RealEstateCore](https://github.com/Azure/opendigitaltwins-building).
* [ExcelRDF](/ExcelRDF/) -- An Excel plugin that provides light-weight 
translation from OWL ontology to XLS skeleton, and 
from a filled-out version of that XLS skeleton to RDF -- 
enabling linked data generation from existing Excel-based 
tools and workflows. This tool can be used for onboarding 
buildings onto RealEstateCore systems by translating 
existing taglists or other relational data structures.

## Configurations

* [Home Assistant Configurations](https://github.com/RealEstateCore/HomeAssistantConfigs) --
This repository hosts configuration files for the popular [Home Assistant](https://www.home-assistant.io)
open source home automation platform, enabling Home Assistant to emit RealEstateCore-formatted 
messages.

## Documents

* [Procurement documents](https://github.com/RealEstateCore/ProcurementDocuments) -- 
This repository contains documentation that supports real estate holder 
procurement of new buildings that speak RealEstateCore from the outset. 
Presently this documentation is only availabile in Swedish, but we are 
working to translate it to English.