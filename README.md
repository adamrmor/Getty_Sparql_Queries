# Getty_Sparql_Queries
A repository of queries for extracting data from the Getty Vocabs.

### Extract all places within the Oceania place Hierarchy 
````
select * where {
  ?x gvp:parentString ?l
      filter regex(?l, "oceania","i")
 ?x  gvp:placeTypePreferred [gvp:prefLabelGVP [xl:literalForm ?type]].
 optional { ?x  xl:prefLabel [xl:literalForm ?lab; dct:language gvp_lang:en]}.
 optional { ?x gvp:prefLabelGVP/xl:literalForm ?labGVP }
 optional { ?x skos:scopeNote/rdf:value ?scopenotes.}
 ?x foaf:focus/wgs:lat ?lat.
 ?x foaf:focus/wgs:long ?long.
 optional {  ?x gvp:placeTypePreferred/skos:scopeNote ?typenote.
 ?typenote  dcterms:language aat:300388277.}
}
````
