# OslofjordKG
Knowledge graph for the Climatebarometer for the Oslofjord


## Queries:

```
ASK WHERE{
       ?fish rdfs:subClassOf ?b1 .
       ?b1 owl:onProperty ast:Name .
       ?b1 owl:hasValue ?name .
       ?fish rdfs:subClassOf ?b .
       ?fish rdfs:subClassOf ?b2 .
       ?b owl:hasValue ?minTemp .
       ?b owl:onProperty ast:minTemperature .
       ?b2 owl:hasValue ?maxTemp .
       ?b2 owl:onProperty ast:maxTemperature .
       FILTER(?minTemp <= xsd:double(5) && ?maxTemp >= xsd:double(5) && ?name = xsd:string("Atlantic Cod")) .
}
```

## Questions you want to ask the knowledgegraph: 

It would be great to be able to query the knowledge graph to retrieve if a specific species can be found with data within the ranges of

- Temperature
- Salinity
- Turbidity
