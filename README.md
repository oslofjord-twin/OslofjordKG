# OslofjordKG
Knowledge graph for the Climatebarometer for the Oslofjord


## Queries:

Query used by runtime monitor. Gets different temperature values connected to atlantic cod (morhua). Would also like to get similar values for other species of fish.

```
SELECT
    ?maxSpawnTemp
    ?minSpawnTemp
    ?maxTemp
    ?minTemp
    ?prefMaxSpawnTemp
    ?prefMinSpawnTemp
WHERE {
    ex:Morhua rdfs:subClassOf
        ?o1, ?o2, ?o3, ?o4, ?o5, ?o6 .
    ?o1 owl:hasValue ?maxSpawnTemp ;
        owl:onProperty ex:maxSpawningTemperature .
    ?o2 owl:hasValue ?minSpawnTemp ;
        owl:onProperty ex:minSpawningTemperature .
    ?o3 owl:hasValue ?maxTemp ;
        owl:onProperty ex:maxTemperature .
    ?o4 owl:hasValue ?minTemp ;
        owl:onProperty ex:minTemperature .
    ?o5 owl:hasValue ?prefMaxSpawnTemp ;
        owl:onProperty ex:preferredMaxSpawningTemperature .
    ?o6 owl:hasValue ?prefMinSpawnTemp ;
        owl:onProperty ex:preferredMinSpawningTemperature .
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
