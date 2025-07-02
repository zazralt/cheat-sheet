# **Turtle Syntax Cheat Sheet**

Turtle (Terse RDF Triple Language) is a textual syntax for RDF that allows data to be expressed in triples: **subject predicate object**.

---

## **1. Basic Structure**

```turtle
@prefix ex: <http://example.org/> .

ex:John ex:hasName "John Smith" .
```

Each line is a triple:
**Subject** → **Predicate** → **Object**

---

## **2. Prefixes**

Define namespaces to avoid repetition:

```turtle
@prefix foaf: <http://xmlns.com/foaf/0.1/> .
@prefix ex:   <http://example.org/> .
```

Use `@base` to set default base IRI:

```turtle
@base <http://example.org/> .
```

---

## **3. Literals**

### String

```turtle
"Some text"
"Multilingual string"@en
```

### Datatype

```turtle
"42"^^<http://www.w3.org/2001/XMLSchema#integer>
"2025-07-02"^^xsd:date
```

### Escaping

```turtle
"He said: \"Hello\""
```

---

## **4. Abbreviations**

### a → rdf\:type

```turtle
ex:John a foaf:Person .
```

### ;

Reuse subject:

```turtle
ex:John
  a foaf:Person ;
  foaf:name "John" ;
  foaf:age 42 .
```

### ,

Reuse subject and predicate:

```turtle
ex:John foaf:knows ex:Alice, ex:Bob .
```

---

## **5. Collections and Containers**

### List (rdf\:List)

```turtle
ex:ListExample ex:hasList ( "one" "two" "three" ) .
```

### Blank Nodes

```turtle
_:bnode a foaf:Person ;
       foaf:name "Unnamed Person" .
```

Or inline:

```turtle
ex:Jane foaf:knows [ foaf:name "Unnamed" ] .
```

---

## **6. Comments**

Use `#` for comments:

```turtle
# This is a comment
```

---

## **7. IRIs**

* Full: `<http://example.org/resource>`
* Prefixed: `ex:resource` (with `@prefix`)
* Relative: if `@base` is defined

---

## **8. Example**

```turtle
@prefix ex: <http://example.org/> .
@prefix foaf: <http://xmlns.com/foaf/0.1/> .

ex:Alice
  a foaf:Person ;
  foaf:name "Alice" ;
  foaf:mbox <mailto:alice@example.org> ;
  foaf:knows [
    a foaf:Person ;
    foaf:name "Bob"
  ] .
```
