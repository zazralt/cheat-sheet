# rdflib Basics Cheat Sheet (Python)

## What is rdflib?
`rdflib` is a Python library for working with RDF (Resource Description Framework), including parsing, creating triples, querying with SPARQL, and serializing RDF graphs.

---

## Installation

```bash
pip install rdflib
````

---

## Core Components

```python
from rdflib import Graph, Literal, RDF, URIRef, Namespace
```

---

## Creating a Graph

```python
g = Graph()
```

---

## Adding Triples

```python
ex = Namespace("http://example.org/")
g.add((ex.Alice, RDF.type, ex.Person))
g.add((ex.Alice, ex.name, Literal("Alice")))
```

---

## Parsing RDF Data

```python
g.parse("data.rdf")                         # Format auto-detected
g.parse("data.ttl", format="turtle")
g.parse("data.jsonld", format="json-ld")
```

---

## Serializing Graphs

```python
g.serialize("output.ttl", format="turtle")
print(g.serialize(format="nt").decode("utf-8"))
```

---

## Querying with SPARQL

```python
qres = g.query("""
    PREFIX ex: <http://example.org/>
    SELECT ?name
    WHERE {
        ?person a ex:Person ;
                ex:name ?name .
    }
""")

for row in qres:
    print(row.name)
```

---

## Checking & Iterating

```python
(ex.Alice, RDF.type, ex.Person) in g  # Membership test

for subj, pred, obj in g:
    print(subj, pred, obj)
```

---

## Namespaces

```python
g.bind("ex", ex)

from rdflib.namespace import FOAF, RDFS
g.add((ex.Bob, FOAF.knows, ex.Alice))
```

---

## Common Formats

| Format    | Description |
| --------- | ----------- |
| `xml`     | RDF/XML     |
| `turtle`  | Turtle      |
| `nt`      | N-Triples   |
| `json-ld` | JSON-LD     |
| `n3`      | Notation3   |

---

Reference: [rdflib Documentation](https://rdflib.readthedocs.io/)

