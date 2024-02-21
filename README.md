# OslofjordKG
Knowledge graph for the Climatebarometer for the Oslofjord


## Queries:

The "ast:morhua" variable needs to be dynamic so that I can use this query for multiple different species of fish.

```
PREFIX ast: <http://www.smolang.org/oslofjordDT#>
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>

SELECT
    ?name
    ?maxSpawnTemp
    ?minSpawnTemp
    ?maxTemp
    ?minTemp
    ?prefMaxSpawnTemp
    ?prefMinSpawnTemp
WHERE {
    ast:morhua rdfs:subClassOf
        ?o1, ?o2, ?o3, ?o4, ?o5, ?o6, ?o7 .
    ?o7 owl:hasValue ?name ;
        owl:onProperty ast:Name .
    ?o1 owl:hasValue ?maxSpawnTemp ;
        owl:onProperty ast:maxSpawningTemperature .
    ?o2 owl:hasValue ?minSpawnTemp ;
        owl:onProperty ast:minSpawningTemperature .
    ?o3 owl:hasValue ?maxTemp ;
        owl:onProperty ast:maxTemperature .
    ?o4 owl:hasValue ?minTemp ;
        owl:onProperty ast:minTemperature .
    ?o5 owl:hasValue ?prefMaxSpawnTemp ;
        owl:onProperty ast:preferredMaxSpawningTemperature .
    ?o6 owl:hasValue ?prefMinSpawnTemp ;
        owl:onProperty ast:preferredMinSpawningTemperature .
}
```


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
       FILTER(?minTemp > xsd:double(temperature) && ?maxTemp < xsd:double(temperature) && ?name = xsd:string("name")) .
}

```

## Questions you want to ask the knowledgegraph: 

It would be great to be able to query the knowledge graph to retrieve if a specific species can be found with data within the ranges of

- Temperature
- Salinity
- Turbidity
