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

# SPARQL Functions Cheat Sheet

| Function Type       | Function Name                         | Description |
|---------------------|----------------------------------------|-------------|
| **String Functions** | `STR()`                               | Get the string representation of an RDF term |
|                     | `CONCAT(str1, str2, ...)`              | Concatenate strings |
|                     | `STRLEN(str)`                          | Length of a string |
|                     | `UCASE(str)`                           | Convert to uppercase |
|                     | `LCASE(str)`                           | Convert to lowercase |
|                     | `SUBSTR(str, start, [length])`         | Extract substring |
|                     | `REPLACE(str, pattern, replacement)`   | Replace substring using regex |
|                     | `STRSTARTS(str, prefix)`               | True if str starts with prefix |
|                     | `STRENDS(str, suffix)`                 | True if str ends with suffix |
|                     | `CONTAINS(str, substr)`                | True if str contains substr |
|                     | `ENCODE_FOR_URI(str)`                  | Encode for URI |
|                     | `STRUUID()` / `UUID()`                 | Generate random UUID |
| **Numeric Functions** | `ABS(x)`                             | Absolute value |
|                     | `ROUND(x)`                             | Round to nearest integer |
|                     | `CEIL(x)`                              | Smallest integer ≥ x |
|                     | `FLOOR(x)`                             | Largest integer ≤ x |
|                     | `RAND()`                               | Random float between 0 and 1 |
| **Date/Time Functions** | `NOW()`                            | Current date and time |
|                        | `YEAR(dateTime)`                   | Extract year |
|                        | `MONTH(dateTime)`                  | Extract month |
|                        | `DAY(dateTime)`                    | Extract day |
|                        | `HOURS(dateTime)`                  | Extract hour |
|                        | `MINUTES(dateTime)`                | Extract minutes |
|                        | `SECONDS(dateTime)`                | Extract seconds |
|                        | `TIMEZONE(dateTime)`               | Timezone info |
|                        | `TZ(dateTime)`                     | Timezone as string |
| **Boolean Functions** | `BOUND(?var)`                        | True if variable is bound |
|                      | `ISIRI(term)` / `ISURI(term)`        | True if term is an IRI |
|                      | `ISBLANK(term)`                      | True if term is a blank node |
|                      | `ISLITERAL(term)`                    | True if term is a literal |
|                      | `REGEX(str, pattern [, flags])`      | True if string matches regex |
| **Type Conversion**   | `STR()`                               | Convert to string |
|                      | `xsd:datatype()`                      | Cast to datatype, e.g. `xsd:integer("123")` |
| **Hash Functions**    | `MD5(str)`                            | MD5 hash of string |
|                      | `SHA1(str)` / `SHA256(str)` etc.      | SHA hash of string |
| **Aggregate Functions** | `COUNT(*)`                         | Count of results |
|                        | `SUM(expr)`                         | Sum of values |
|                        | `AVG(expr)`                         | Average value |
|                        | `MIN(expr)` / `MAX(expr)`           | Minimum or maximum value |
|                        | `GROUP_CONCAT(expr; separator)`     | Concatenate values in group |
|                        | `SAMPLE(expr)`                      | Random value from group |

---

Reference: [W3C SPARQL Functions](https://www.w3.org/TR/sparql11-query/#funcs)

