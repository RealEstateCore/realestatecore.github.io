---
title: DTDL2MD -- The DTDL to Markdown documentation generator
---

* **GitHub Repository:** [RealEstateCore/DTDL2MD](https://github.com/RealEstateCore/DTDL2MD)
* **Author:** [Karl Hammar](https://karlhammar.com)

This tool parses a DTDL ontology and generates a set of markdown files describing the content of that ontology.

It accepts either a single JSON file or a directory as input -- in the latter case, it traverses the directory recursively and parses all JSON files within it and its children.

It emits a set of Markdown files structured in accordance with the inheritance hierarchy of the parsed DTDL Interface models, and an index file listing all those interfaces.

For an example of how this might look, see the [RealEstateCore documentation](https://github.com/RealEstateCore/rec/tree/main/Doc).

## Usage

```
dotnet run -i C:\path-to-ontology -o C:\output-directory
```

## Options

```
  -i, --inputPath     Required. The path to the ontology root directory or file to translate.

  -o, --outputPath    Required. The path at which to put the generated Markdown files.

  --help              Display this help screen.

  --version           Display version information.
```