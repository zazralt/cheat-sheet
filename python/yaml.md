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

## Convert YAML to Python (Deserialization)

```python
# Load from YAML string
yaml_str = """
name: Alice
age: 30
skills:
  - Python
  - YAML
"""
data = yaml.safe_load(yaml_str)

# Load from YAML file
with open("data.yml", "r") as f:
    data = yaml.safe_load(f)
```

---

## Convert Python to YAML (Serialization)

```python
# Python dict to YAML string
data = {"name": "Alice", "age": 30, "skills": ["Python", "YAML"]}
yaml_str = yaml.safe_dump(data)

# Save to YAML file
with open("data.yml", "w") as f:
    yaml.safe_dump(data, f)
```

---

## Pretty-Printing YAML

```python
yaml_str = yaml.safe_dump(
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

## Common Options for `yaml.safe_dump()`

| Option                    | Description                    |
| ------------------------- | ------------------------------ |
| `sort_keys=False`         | Keep dictionary key order      |
| `indent=4`                | Indentation spaces             |
| `default_flow_style=True` | Use inline style (`{}` / `[]`) |
| `allow_unicode=True`      | Preserve Unicode characters    |
| `explicit_start=True`     | Add `---` at start of output   |

---

## Preserving Formatting & Comments (ruamel.yaml)

```bash
pip install ruamel.yaml    # Preserve formatting & comments
```

```python
from ruamel.yaml import YAML

yaml_rt = YAML()
yaml_rt.preserve_quotes = True

with open("config.yml", "r") as f:
    data = yaml_rt.load(f)

with open("config.yml", "w") as f:
    yaml_rt.dump(data, f)
```

---

## Common Errors

* `yaml.YAMLError`: General parse or syntax error
* Indentation errors: YAML requires spaces, not tabs
* Ambiguous values: Quote strings like `yes`, `no`, `on`, `off` to avoid them being parsed as booleans
