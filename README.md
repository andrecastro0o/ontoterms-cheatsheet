# ontoterms-cheatsheet
A compilation of essential terms from high-level ontologies


## [SKOS](https://www.w3.org/TR/2009/NOTE-skos-primer-20090818/)
Namespace: http://www.w3.org/2004/02/skos/core#

RDF: http://www.w3.org/TR/skos-reference/skos.rdf

### Classes:

[skos:Concept](https://www.w3.org/TR/skos-reference/#Concept) - an idea or notion 
```ttl
skos:Concept  rdfs:label  "Concept"@en ;
        rdfs:isDefinedBy  <http://www.w3.org/2004/02/skos/core> ;
        skos:definition   "An idea or notion; a unit of thought."@en ;
        rdf:type          owl:Class .
```

[skos:ConceptScheme](https://www.w3.org/TR/skos-reference/#ConceptScheme)  an aggregation of one or more SKOS concepts. The namespace of the ontology can constitute the ConceptScheme

```ttl
skos:ConceptScheme  rdfs:label  "Concept Scheme"@en ;
        rdfs:isDefinedBy  <http://www.w3.org/2004/02/skos/core> ;
        skos:definition   "A set of concepts, optionally including statements about semantic relationships between those concepts."@en ;
        skos:scopeNote    "A concept scheme may be defined to include concepts from different sources."@en ;
        skos:example      "Thesauri, classification schemes, subject heading lists, taxonomies, 'folksonomies', and other types of controlled vocabulary are all examples of concept schemes. Concept schemes are a
lso embedded in glossaries and terminologies."@en ;
        rdf:type          owl:Class ;
        owl:disjointWith  skos:Concept .
```

### Object Properties:

[skos:hasTopConcept](https://www.w3.org/TR/skos-reference/#hasTopConcept) - Relates a concept scheme to a topmost concept for that scheme.
```
skos:hasTopConcept  rdfs:label  "has top concept"@en ;
        rdfs:isDefinedBy  <http://www.w3.org/2004/02/skos/core> ;
        skos:definition   "Relates, by convention, a concept scheme to a concept which is topmost in the broader/narrower concept hierarchies for that scheme, providing an entry point to these hierarchies."@en ;
        rdf:type          owl:ObjectProperty ;
        rdfs:domain       skos:ConceptScheme ;
        rdfs:range        skos:Concept ;
        owl:inverseOf     skos:topConceptOf ;
        rdf:type          rdf:Property .
``` 

Example:
```ttl
myonto:    a                   skos:ConceptScheme ;
           dct:title           "My Ontot"@en ;
           skos:hasTopConcept  myonto:1 , myonto:111 , myonto:11 .        
```  

[skos:inScheme](https://www.w3.org/TR/skos-reference/#inScheme) - Relates a resource (for example a concept) to a concept scheme

```ttl
skos:ConceptScheme  rdfs:label  "Concept Scheme"@en ;
        rdfs:isDefinedBy  <http://www.w3.org/2004/02/skos/core> ;
        skos:definition   "A set of concepts, optionally including statements about semantic relationships between those concepts."@en ;
        skos:scopeNote    "A concept scheme may be defined to include concepts from different sources."@en ;
        skos:example      "Thesauri, classification schemes, subject heading lists, taxonomies, 'folksonomies', and other types of controlled vocabulary are all examples of concept schemes. Concept schemes are a
lso embedded in glossaries and terminologies."@en ;
        rdf:type          owl:Class ;
        owl:disjointWith  skos:Concept .
```

[skos:broader](https://www.w3.org/TR/skos-reference/#broader)

```ttl
skos:broader  rdfs:label    "has broader"@en ;
        rdfs:isDefinedBy    <http://www.w3.org/2004/02/skos/core> ;
        skos:definition     "Relates a concept to a concept that is more general in meaning."@en ;
        rdfs:comment        "Broader concepts are typically rendered as parents in a concept hierarchy (tree)."@en ;
        skos:scopeNote      "By convention, skos:broader is only used to assert an immediate (i.e. direct) hierarchical link between two conceptual resources."@en ;
        rdf:type            owl:ObjectProperty ;
        rdfs:subPropertyOf  skos:broaderTransitive ;
        owl:inverseOf       skos:narrower ;
        rdf:type            rdf:Property .
``` 


[skos:narrower](https://www.w3.org/TR/skos-reference/#narrower)

```ttl
skos:narrower  rdfs:label   "has narrower"@en ;
        rdfs:isDefinedBy    <http://www.w3.org/2004/02/skos/core> ;
        skos:definition     "Relates a concept to a concept that is more specific in meaning."@en ;
        skos:scopeNote      "By convention, skos:broader is only used to assert an immediate (i.e. direct) hierarchical link between two conceptual resources."@en ;
        rdfs:comment        "Narrower concepts are typically rendered as children in a concept hierarchy (tree)."@en ;
        rdf:type            owl:ObjectProperty ;
        rdfs:subPropertyOf  skos:narrowerTransitive ;
        owl:inverseOf       skos:broader ;
        rdf:type            rdf:Property .
```


### Annotation Properties
* [skos:prefLabel](https://www.w3.org/TR/skos-reference/#prefLabel) - The preferred lexical label for a resource
* [skos:altLabel](https://www.w3.org/TR/skos-reference/#altLabel) - An alternative lexical label for a resource
* [skos:hiddenLabel](https://www.w3.org/TR/skos-reference/#hiddenLabel) - A lexical label for a resource that should be hidden when generating visual displays of the resource, but should still be accessible to free text search operations


## SKOSXML
