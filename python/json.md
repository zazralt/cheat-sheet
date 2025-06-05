Here's a clean **JSON Cheat Sheet for Python** without emojis:

---

## Importing the JSON Module

```python
import json
```

---

## Convert Python to JSON (Serialization)

```python
# Convert dict to JSON string
data = {"name": "Alice", "age": 30}
json_str = json.dumps(data)

# Save to file
with open("data.json", "w") as f:
    json.dump(data, f)
```

---

## Convert JSON to Python (Deserialization)

```python
# Convert JSON string to dict
json_str = '{"name": "Alice", "age": 30}'
data = json.loads(json_str)

# Load from file
with open("data.json", "r") as f:
    data = json.load(f)
```

---

## Pretty-Printing JSON

```python
pretty = json.dumps(data, indent=4)
print(pretty)
```

---

## Common Options for `json.dumps()`

| Option                   | Description                        |
| ------------------------ | ---------------------------------- |
| `indent=4`               | Pretty-print with indentation      |
| `sort_keys=True`         | Sort keys alphabetically           |
| `separators=(',', ': ')` | Compact formatting                 |
| `ensure_ascii=False`     | Allow Unicode characters in output |

---

## Handling Complex Objects

```python
# Custom encoding for unsupported types
import datetime

def encode_custom(obj):
    if isinstance(obj, datetime.datetime):
        return obj.isoformat()
    raise TypeError("Type not serializable")

json_str = json.dumps({"now": datetime.datetime.now()}, default=encode_custom)
```

---

## Parsing Nested JSON

```python
nested_json = '{"person": {"name": "Alice", "age": 30}}'
data = json.loads(nested_json)
print(data['person']['name'])  # Alice
```

---

## Common Errors

* `JSONDecodeError`: Malformed JSON string
* `TypeError`: Trying to serialize unsupported Python type

