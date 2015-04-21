# LABD-TP12


Exercice 1
----------

Question 1
-----------

```
SELECT ?x  WHERE
{
?x a rdfs:Class 
}
```
```
<?xml version="1.0" ?>
<sparql xmlns='http://www.w3.org/2005/sparql-results#'>
<head>
<variable name='x'/>
</head>
<results>
<result>
<binding name='x'><uri>http://www.inria.fr/2007/09/11/humans.rdfs#Animal</uri></binding>
</result>
<result>
<binding name='x'><uri>http://www.inria.fr/2007/09/11/humans.rdfs#Female</uri></binding>
</result>
<result>
<binding name='x'><uri>http://www.inria.fr/2007/09/11/humans.rdfs#Lecturer</uri></binding>
</result>
<result>
<binding name='x'><uri>http://www.inria.fr/2007/09/11/humans.rdfs#Male</uri></binding>
</result>
<result>
<binding name='x'><uri>http://www.inria.fr/2007/09/11/humans.rdfs#Man</uri></binding>
</result>
<result>
<binding name='x'><uri>http://www.inria.fr/2007/09/11/humans.rdfs#Person</uri></binding>
</result>
<result>
<binding name='x'><uri>http://www.inria.fr/2007/09/11/humans.rdfs#Researcher</uri></binding>
</result>
<result>
<binding name='x'><uri>http://www.inria.fr/2007/09/11/humans.rdfs#Woman</uri></binding>
</result>
<result>
<binding name='x'><uri>http://www.labd.org/2015/sport/schema#Ballon</uri></binding>
</result>
<result>
<binding name='x'><uri>http://www.labd.org/2015/sport/schema#MaterielSportif</uri></binding>
</result>
<result>
<binding name='x'><uri>http://www.labd.org/2015/sport/schema#Raquette</uri></binding>
</result>
<result>
<binding name='x'><uri>http://www.labd.org/2015/sport/schema#Sport</uri></binding>
</result>
<result>
<binding name='x'><uri>http://www.labd.org/2015/sport/schema#SportBallon</uri></binding>
</result>
<result>
<binding name='x'><uri>http://www.labd.org/2015/sport/schema#SportCollectif</uri></binding>
</result>
<result>
<binding name='x'><uri>http://www.labd.org/2015/sport/schema#SportEquipe</uri></binding>
</result>
<result>
<binding name='x'><uri>http://www.labd.org/2015/sport/schema#SportIndividuel</uri></binding>
</result>
<result>
<binding name='x'><uri>http://www.labd.org/2015/sport/schema#SportRaquette</uri></binding>
</result>
<result>
<binding name='x'><uri>http://www.labd.org/2015/sport/schema#TerrainDeSport</uri></binding>
</result>
<result>
<binding name='x'><uri>http://www.labd.org/2015/sport/schema#Velo</uri></binding>
</result>
</results>
</sparql>
```

Question 2
----------

```
SELECT *  WHERE
{
?x a rdf:Property 
?x rdfs:domain ?domain  
BIND (URI("http://www.labd.org/2015/sport/schema#Sport") AS ?u)
FILTER (?u = ?domain)
}
```
```
<?xml version="1.0" ?>
<sparql xmlns='http://www.w3.org/2005/sparql-results#'>
<head>
<variable name='x'/>
<variable name='domain'/>
<variable name='u'/>
</head>
<results>
<result>
<binding name='x'><uri>http://www.labd.org/2015/sport/schema#sePratiqueSur</uri></binding>
<binding name='domain'><uri>http://www.labd.org/2015/sport/schema#Sport</uri></binding>
<binding name='u'><uri>http://www.labd.org/2015/sport/schema#Sport</uri></binding>
</result>
<result>
<binding name='x'><uri>http://www.labd.org/2015/sport/schema#utiliseMateriel</uri></binding>
<binding name='domain'><uri>http://www.labd.org/2015/sport/schema#Sport</uri></binding>
<binding name='u'><uri>http://www.labd.org/2015/sport/schema#Sport</uri></binding>
</result>
</results>
</sparql>
```

Question 3
-----------

```
PREFIX sports: <http://www.labd.org/2015/sport/schema#> 

SELECT *
WHERE {
  ?x  a sports:Sport
}
```

Question 4
----------

```
SELECT *
WHERE {
  ?x rdfs:comment ?c
  filter(regex(?c,"sport","s"))
}
```


Question 5
----------
```
PREFIX sports: <http://www.labd.org/2015/sport/schema#>
SELECT *
WHERE {
  ?x a sports:Sport 
  FILTER NOT EXISTS {?x sports:utiliseMateriel ?y}

}
```

Question 6
----------

```
PREFIX sports: <http://www.labd.org/2015/sport/schema#> 
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs> 
SELECT DISTINCT ?h (COUNT(?s1) AS ?s)
WHERE {

  ?h sports:pratique ?s1
  
}
GROUP BY ?h
HAVING  (?s >1)
```

```
PREFIX sports: <http://www.labd.org/2015/sport/schema#> 
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs> 
SELECT *
WHERE {
  ?h sports:pratique ?s1
  ?h sports:pratique ?s2
FILTER(?s1 != ?s2)
}
```
Question 7
-----------

```
PREFIX sports: <http://www.labd.org/2015/sport/schema#> 
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs> 
SELECT DISTINCT ?h (COUNT(?s1) AS ?s)
WHERE {

  ?h sports:pratique ?s1
  
}
GROUP BY ?h
HAVING  (?s =1)

```

```
PREFIX sports: <http://www.labd.org/2015/sport/schema#> 
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs> 
SELECT DISTINCT ?h
WHERE {

?h sports:pratique ?s1

 MINUS { SELECT DISTINCT ?h
	WHERE {   ?h sports:pratique ?s1
  		?h sports:pratique ?s2
		FILTER(?s1 != ?s2)
}
}
}
```

Question 8
----------
```
PREFIX sports: <http://www.labd.org/2015/sport/schema#> 
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs> 
SELECT DISTINCT ?h (COUNT(?s1) AS ?s)
WHERE {

  ?h sports:pratique ?s1
  
}
GROUP BY ?h
```

Question 9
----------

```
PREFIX sports: <http://www.labd.org/2015/sport/schema#> 
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs> 
SELECT DISTINCT ?o
WHERE {


    ?s sports:match/rdfs:label ?m
    ?s sports:match/sports:duree ?d
    ?d rdfs:member ?o
    FILTER (xsd:string(?m)= "Match de Basket")

}


```


Question 10
-----------

```````````
PREFIX sports: <http://www.labd.org/2015/sport/schema#> 
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs> 
SELECT DISTINCT ?o
WHERE {


    ?s sports:match/rdfs:label ?m
    ?s sports:match/sports:duree ?d
    ?d rdfs:member ?o
    FILTER (contains(xsd:string(?o), "NBA"))
    FILTER (xsd:string(?m)= "Match de Basket")
    

}
```

Question 11
-----------

```
PREFIX sports: <http://www.labd.org/2015/sport/schema#> 
select distinct ?sp ?d
where {
  {
  ?s a sports:SportCollectif
  ?sp sports:match/sports:duree ?d 
  FILTER NOT EXISTS {?d rdfs:member ?f}
  }
UNION
  {
  ?s a sports:SportCollectif
  ?s sports:match/sports:duree/rdfs:member ?d
  } 
}
```


Exercice 2
----------

Question 1
-----------

```
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX jb: <http://bond007.org/RDF/mes_donnees.rdf#>
SELECT ?n ?r WHERE
{
 jb:me foaf:knows ?f
 ?f foaf:name ?n
 OPTIONAL {?f foaf:homepage ?r}
}
```
