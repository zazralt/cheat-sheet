# Python Basics Cheat Sheet

## Variables and Data Types

```python
x = 10               # Integer
pi = 3.14            # Float
name = "Alice"       # String
is_valid = True      # Boolean
````

## Data Structures

```python
# List
fruits = ["apple", "banana", "cherry"]
fruits[0]           # Access

# Tuple
point = (1, 2)

# Set
unique_nums = {1, 2, 3}

# Dictionary
person = {"name": "Alice", "age": 30}
person["name"]      # Access value
```

## Control Flow

```python
# If-else
if x > 0:
    print("Positive")
elif x == 0:
    print("Zero")
else:
    print("Negative")

# For loop
for fruit in fruits:
    print(fruit)

# While loop
while x > 0:
    x -= 1
```

## Functions

```python
def greet(name):
    return f"Hello, {name}"

greet("Alice")
```

## Classes and Objects

```python
class Person:
    def __init__(self, name):
        self.name = name

    def greet(self):
        return f"Hi, I'm {self.name}"

p = Person("Alice")
p.greet()
```

## Common Built-ins

```python
len(fruits)           # Length
range(5)              # Range object
type(name)            # Type of variable
int("10")             # Convert string to int
str(10)               # Convert int to string
```

## File I/O

```python
# Writing
with open("file.txt", "w") as f:
    f.write("Hello world")

# Reading
with open("file.txt", "r") as f:
    content = f.read()
```

## Exceptions

```python
try:
    1 / 0
except ZeroDivisionError:
    print("Cannot divide by zero")
finally:
    print("Done")
```

## Importing Modules

```python
import math
from datetime import datetime
```

## Virtual Environments (CLI)

```bash
python -m venv venv
source venv/bin/activate      # Linux/macOS
venv\Scripts\activate         # Windows
```

---

Reference: [Python Docs](https://docs.python.org/3/)


# Python Dictionary Cheat Sheet

## Creating a Dictionary

```python
person = {"name": "Alice", "age": 30}
empty_dict = {}
````

## Accessing Values

```python
person["name"]          # 'Alice'
person.get("age")       # 30
person.get("gender", "N/A")  # 'N/A' if key doesn't exist
```

## Modifying Entries

```python
person["age"] = 31
person["city"] = "London"   # Add new key
```

## Removing Entries

```python
del person["age"]
person.pop("city")
person.clear()              # Remove all items
```

## Dictionary Methods

| Method           | Description                          |
| ---------------- | ------------------------------------ |
| `.keys()`        | Returns a view of keys               |
| `.values()`      | Returns a view of values             |
| `.items()`       | Returns view of key-value pairs      |
| `.update(dict2)` | Merges `dict2` into current dict     |
| `.pop(key)`      | Removes and returns the value of key |
| `.get(key)`      | Returns value or `None` (or default) |

## Looping Through a Dictionary

```python
for key in person:
    print(key, person[key])

for key, value in person.items():
    print(key, value)
```

## Dictionary Comprehensions

```python
squares = {x: x*x for x in range(5)}  # {0: 0, 1: 1, ..., 4: 16}
```

## Nesting

```python
people = {
    "alice": {"age": 30, "city": "NY"},
    "bob": {"age": 25, "city": "LA"}
}
```

---

Reference: [Python dict Docs](https://docs.python.org/3/library/stdtypes.html#dict)
