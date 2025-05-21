# SPARQL Basics Cheat Sheet
SPARQL (SPARQL Protocol and RDF Query Language) is used to query RDF (Resource Description Framework) data.

## Basic Query Structure

```sparql
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


# Advanced SPARQL Cheat Sheet

## BIND
Assigns the result of an expression to a new variable.

```sparql
SELECT ?name ?upperName
WHERE {
  ?person foaf:name ?name .
  BIND(UCASE(?name) AS ?upperName)
}
````

## UNION

Combines results from multiple patterns (logical OR).

```sparql
SELECT ?person ?info
WHERE {
  {
    ?person foaf:name ?info .
  } UNION {
    ?person foaf:mbox ?info .
  }
}
```

## Federated Queries (SERVICE)

Queries remote SPARQL endpoints.

```sparql
SELECT ?name
WHERE {
  SERVICE <http://dbpedia.org/sparql> {
    ?person foaf:name ?name .
    ?person dbo:birthPlace dbr:Berlin .
  }
}
```

> ⚠ Note: The remote endpoint must support SPARQL 1.1 and allow federated queries.

## Additional Advanced Constructs

### VALUES

Inline data binding (like a local table of values):

```sparql
SELECT ?person ?name
WHERE {
  VALUES ?person { ex:Alice ex:Bob }
  ?person foaf:name ?name .
}
```

### MINUS

Excludes results matching a pattern:

```sparql
SELECT ?person
WHERE {
  ?person a foaf:Person .
  MINUS { ?person foaf:mbox ?email . }
}
```

### Subqueries

Nested queries for advanced filtering:

```sparql
SELECT ?person ?age
WHERE {
  {
    SELECT ?person (MAX(?age) AS ?age)
    WHERE {
      ?person ex:hasAge ?age .
    }
    GROUP BY ?person
  }
}
```

