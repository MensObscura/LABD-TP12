# LABD-TP12


Exercice 1
__________

Question 1
__________

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
__________


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
