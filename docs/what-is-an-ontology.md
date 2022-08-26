---
title: What is an ontology?
---

RealEstateCore (REC) is an ontology, which can most easily be thought of as a standard and interoperable schema for building knowledge graphs; it defines the types of nodes you can have in your graph, the types of relations these nodes have with one another, and the types of data values associated with them. By using REC, you get two distinct advantages:

1. You do not need to spend a lot of time and resources on designing your own data model; we’ve already done it for you.
2. Your data is automatically compatible with that of other REC users (e.g., your suppliers or your customers), greatly simplifying data and process integration (doubly so if you also utilize the REC APIs to exchange data).

RealEstateCore was originally designed to be used with RDF-based knowledge graphs, and this is still the intended use of our SHACL version. There is a wealth of information about RDF available on the net, which we will not duplicate here; suffice to say that in RDF, a knowledge graph is made up of a (potentially very large) set of statements, each of which consist of three components: the *subject* of the statement, the *predicate* that captures what the statement intends to say about the subject, and the *object* that carries the value of that assertion. E.g., a graph might include the statement `WhiteHouse ownedBy USGovernment`, or `IBM hasNumberOfEmployees 345900`. Due to their structure, a statement is often known as a *triple*. On this documentation site, we often exemplify partial graphs using triple-like notation. 

Note that RDF is only one data model for knowledge graphs, and the same structures could equally well be described using one of the many property graph models available on the market, e.g., Neo4J, Apache TinkerPop, etc. In fact, the DTDL version of REC specifically supports the Azure Digital Twins platform, which does not use an RDF data representation. We find that translating between different graph formalisms is generally not a complex or time-consuming problem, as long as one has a well-described schema such as what RealEstateCore provides.

## Identity in ontologies

To enable data exchange and data integration using ontologies, it is important that data types and field identifiers are uniquely identifiable; that is to say, short and common identifiers such as *Person* are inappropriate, as they are likely to be reused in different contexts with different meanings. In ontologies we often use URIs as identifiers; so for example, a RealEstateCore building is defined as *https://w3id.org/rec#Building* (SHACL version) or *dtmi:org:w3id:rec:Building* (DTDL version), and the *architectedBy* relationship has the identifier *https://w3id.org/rec#architectedBy* (SHACL).

## Alignments

In the best of all worlds, there would be only one unambiguous ontology per problem domain, which would cover all the needs of that field. In the real world, however, because problems are multifaceted and evolving, because people have different interpretations and biases, and because projects evolve over time in disjoint settings, we find an ecosystem of multiple well-adopted ontologies, many of which have partial feature overlaps. A crucial part of ontology-based data exchange is thus to figure out *alignments* between different ontologies, enabling automated machine translation of data from one model to another. For instance, one such alignment might be that an instance of RealEstateCore *Space* is equivalent to an instance of *Zone* from BOT (the Building Topology Ontology). In RealEstateCore we work actively to reduce overlaps with other leading ontologies in the field, and to develop such alignments when necessary.