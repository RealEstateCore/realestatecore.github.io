---
title: DTDL2OAS -- The DTDL to OpenAPI Specification converter
---

* **GitHub Repository:** [RealEstateCore/DTDL2OAS](https://github.com/RealEstateCore/DTDL2OAS)
* **Author:** [Karl Hammar](https://karlhammar.com)

This is a converter for translating [DTDL ontologies](https://www.w3.org/TR/shacl/) into
[OpenAPI Specification](https://swagger.io/specification/) documents. DTDL (Digital Twin Definition Language) is a JSON-LD-based
language for modelling digital twins, their relations and properties, telemetry capabilities, command capabilities, etc. 
OpenAPI Specification is a standard for describing REST endpoints and operations.
This tool generates REST endpoints for the DTDL Interfaces (i.e., types) declared in an ontology, and generates [JSON-LD](https://json-ld.org)
schemas for those types based on their Relations (to other types) and Properties (data fields).

## Usage

```
dotnet run -i C:\path-to-DTDL-ontology -a C:\path-to-annotations.txt -m C:\mappings.csv -n C:\namespace-abbreviations.txt -o C:\output-file.yaml
```

## Options

```
  -s, --server                        (Default: http://localhost:8080/) The server URL (where presumably an API
                                      implementation is running).

  -i, --inputPath                     Required. The path to the ontology root directory or file to translate.

  -a, --annotationsPath               Required. Path to ontology annotations file detaililing, e.g., version, license,
                                      etc.

  -m, --mappingsPath                  Required. Path to mappings CSV file matching endpoint names to DTDL Interfaces.

  -n, --namespaceAbbreviationsPath    Path to file mapping ontology namespace prefixes to abbreviations.

  -o, --outputPath                    Required. The path at which to put the generated OAS file.

  --help                              Display this help screen.

  --version                           Display version information.
```

## Annotations, mappings, and namespace abbreviation files

For examples of these files, see the [RealEstateCore API directory](https://github.com/RealEstateCore/rec/tree/main/API/REST)