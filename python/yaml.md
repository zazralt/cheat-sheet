## Installing a YAML Library

```bash
pip install pyyaml
```

---

## Importing YAML

```python
import yaml
```

---

## Convert YAML to Dict (Deserialization)

```python
# Load dict from YAML string
yaml_str = """
name: Alice
age: 30
skills:
  - Python
  - YAML
"""
data = yaml.load(yaml_str)
```

```python
# Load dict from YAML file
with open("data.yml", "r") as f:
    data = yaml.safe_load(f)
```

---

## Convert Dict to YAML (Serialization)

```python
# Convert dict to YAML string
data = {"name": "Alice", "age": 30, "skills": ["Python", "YAML"]}
yaml_str = yaml.dump(data)
```

```python
# Save dict to YAML file
with open("data.yml", "w") as f:
    yaml.dump(data, f)
```

---

## Pretty-Printing YAML

```python
yaml_str = yaml.dump(
    data,
    sort_keys=False,       # Preserve key order
    indent=4,              # Indentation spaces
    default_flow_style=False  # Use block style
)
print(yaml_str)
```

---

## Loading Multiple Documents

```python
yaml_text = """
---
name: Alice
---
name: Bob
"""
docs = list(yaml.safe_load_all(yaml_text))
```
---
