# Python Dictionary (`dict`) Cheat Sheet

Links: [Wiki](https://en.wikipedia.org/wiki/Dictionary_%28data_structure%29) | [W3Schools](https://www.w3schools.com/python/python_dictionaries.asp)

```python
# Creating a dictionary
my_dict = {"name": "Alice", "age": 25, "city": "New York"}
```

---

## Creating Dictionaries

```python
# Empty dictionary
d = {}

# With values
d = {"a": 1, "b": 2}

# Using dict() constructor
d = dict(a=1, b=2)

# From list of tuples
d = dict([("a", 1), ("b", 2)])
```

---

## Accessing Data

```python
d["a"]           # 1 (raises KeyError if missing)
d.get("a")       # 1
d.get("z", 0)    # default value if key not found
```

---

## Adding & Updating

```python
d["c"] = 3                   # Add new key
d["a"] = 100                 # Update value
d.update({"b": 200, "d": 4}) # Update multiple
```

---

## Removing Keys

```python
d.pop("a")        # Removes and returns value
del d["b"]        # Removes key
d.popitem()       # Removes and returns last (key, value)
d.clear()         # Empties dictionary
```

---

## Iterating

```python
for k in d: print(k)                # Keys
for v in d.values(): print(v)       # Values
for k, v in d.items(): print(k, v)  # Key-Value pairs
```

---

## Dictionary Methods

```python
d.keys()       # dict_keys(['a', 'b', 'c'])
d.values()     # dict_values([1, 2, 3])
d.items()      # dict_items([('a', 1), ('b', 2), ('c', 3)])
```

---

## Checking Existence

```python
"a" in d        # True
"z" not in d    # True
```

---

## Dictionary Comprehension

```python
squares = {x: x**2 for x in range(5)}
# {0:0, 1:1, 2:4, 3:9, 4:16}
```

---

## Nested Dictionaries

```python
nested = {
    "person1": {"name": "Alice", "age": 25},
    "person2": {"name": "Bob", "age": 30}
}

nested["person1"]["age"]  # 25
```

---

## Copying

```python
d2 = d.copy()         # Shallow copy
import copy
d3 = copy.deepcopy(d) # Deep copy (for nested dicts)
```

---

## Merging

```python
d1 = {"a": 1, "b": 2}
d2 = {"b": 3, "c": 4}

merged = {**d1, **d2}   # {'a': 1, 'b': 3, 'c': 4}
```

---

## DefaultDict (from collections)

```python
from collections import defaultdict

dd = defaultdict(int)
dd["x"] += 1   # No KeyError, default 0
```

---

## Counter (Special Dict)

```python
from collections import Counter

cnt = Counter("banana")
# Counter({'a': 3, 'n': 2, 'b': 1})
```

---

## Useful Tricks

```python
# Swap keys and values
inv = {v: k for k, v in d.items()}

# Initialize with same value
d = dict.fromkeys(["a", "b", "c"], 0)
```
---

## Looping Through Dictionaries

### Loop Over Keys

```python
for key in d:
    print(key, d[key])
```

Equivalent to:

```python
for key in d.keys():
    print(key, d[key])
```

---

### Loop Over Values

```python
for value in d.values():
    print(value)
```

---

### Loop Over Key–Value Pairs

```python
for key, value in d.items():
    print(f"{key} => {value}")
```

---

### Loop with Index (Enumerate)

```python
for i, (key, value) in enumerate(d.items()):
    print(i, key, value)
```

---

### Nested Dictionaries

```python
nested = {
    "person1": {"name": "Alice", "age": 25},
    "person2": {"name": "Bob", "age": 30}
}

for person, info in nested.items():
    for k, v in info.items():
        print(person, k, v)
```

---

### Dictionary Comprehensions (Loop + Build New Dict)

```python
# Square values
d = {"a": 1, "b": 2, "c": 3}
squares = {k: v**2 for k, v in d.items()}
# {'a': 1, 'b': 4, 'c': 9}
```
