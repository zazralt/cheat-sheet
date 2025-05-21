# SPARQL Basics Cheat Sheet
SPARQL (SPARQL Protocol and RDF Query Language) is used to query RDF (Resource Description Framework) data.

```sparql
## Basic Query Structure
SELECT ?subject ?predicate ?object
WHERE {
  ?subject ?predicate ?object .
}
````

## SELECT Clause

Used to specify which variables to return:

```sparql
SELECT ?name ?email
WHERE {
  ?person foaf:name ?name ;
          foaf:mbox ?email .
}
```

## PREFIX

Defines namespaces to shorten URIs:

```sparql
PREFIX foaf: <http://xmlns.com/foaf/0.1/>

SELECT ?name
WHERE {
  ?person foaf:name ?name .
}
```

## FILTER

Used to restrict results:

```sparql
FILTER (?age > 18)
FILTER regex(?name, "^A")
```

## OPTIONAL

Returns optional data if available:

```sparql
SELECT ?name ?email
WHERE {
  ?person foaf:name ?name .
  OPTIONAL { ?person foaf:mbox ?email . }
}
```

## LIMIT and OFFSET

Used for pagination:

```sparql
LIMIT 10
OFFSET 20
```

## ORDER BY

Sorts the results:

```sparql
ORDER BY ASC(?name)
ORDER BY DESC(?age)
```

## DISTINCT

Avoids duplicate results:

```sparql
SELECT DISTINCT ?name
WHERE {
  ?person foaf:name ?name .
}
```

## ASK

Returns true/false if the pattern exists:

```sparql
ASK WHERE {
  ?person foaf:name "Alice" .
}
```

## CONSTRUCT

Returns RDF triples:

```sparql
CONSTRUCT {
  ?person foaf:fullName ?name .
}
WHERE {
  ?person foaf:name ?name .
}
```

## DESCRIBE

Returns RDF data about a resource:

```sparql
DESCRIBE <http://example.org/person/Alice>
```

---

Reference: [W3C SPARQL 1.1 Specification](https://www.w3.org/TR/sparql11-query/)
