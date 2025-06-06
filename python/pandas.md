# Pandas Basics Cheat Sheet
Links: [Wiki](https://en.wikipedia.org/wiki/Pandas_(software)) | [W3C Schools](https://www.w3schools.com/python/pandas/default.asp)

````python
import pandas as pd
````

## Creating DataFrames

```python
# From dictionary
data = {'Name': ['Alice', 'Bob'], 'Age': [25, 30]}
df = pd.DataFrame(data)

# From CSV
df = pd.read_csv('file.csv')

# From Excel
df = pd.read_excel('file.xlsx')
```

## Viewing Data

```python
df.head()        # First 5 rows
df.tail()        # Last 5 rows
df.info()        # Summary
df.describe()    # Stats summary
df.shape         # (rows, columns)
df.columns       # Column names
```

## Selecting Data

```python
df['Name']             # Single column
df[['Name', 'Age']]    # Multiple columns
df.iloc[0]             # First row (by index)
df.loc[0]              # First row (by label)
df.loc[0, 'Name']      # Specific value
```

## Filtering Rows

```python
df[df['Age'] > 25]         
df[(df['Age'] > 20) & (df['Age'] < 30)]
```

## Modifying Data

```python
df['Age'] = df['Age'] + 1       
df['NewCol'] = df['Age'] * 2    
df['Name'] = df['Name'].replace({'AI': 'Artificial Intelligence'})
df.rename(columns={'Age': 'Years'}, inplace=True)
df.drop('NewCol', axis=1, inplace=True)
```

## Grouping & Aggregation

```python
df.groupby('Name').mean()
df.groupby('Name')['Age'].sum()
```

## Sorting

```python
df.sort_values(by='Age')
df.sort_values(by='Age', ascending=False)
```

## Handling Missing Data

```python
df.isnull()            
df.dropna()            
df.fillna(0)           
```

## Saving Data

```python
df.to_csv('output.csv', index=False)
df.to_excel('output.xlsx', index=False)
```

---

Reference: [Pandas Documentation](https://pandas.pydata.org/docs/)

# JSON Normalization in Pandas Cheat Sheet

## What is JSON Normalization?
JSON normalization is the process of **flattening nested JSON** data into a flat table (DataFrame), making it easier to analyze and manipulate.

---

## Basic Setup

```python
import pandas as pd
from pandas import json_normalize
import json
````

---

## Example JSON

```python
data = [
    {
        "id": 1,
        "name": "Alice",
        "info": {
            "age": 25,
            "city": "New York"
        }
    },
    {
        "id": 2,
        "name": "Bob",
        "info": {
            "age": 30,
            "city": "London"
        }
    }
]
```

---

## Basic Normalization

```python
df = json_normalize(data)
```

**Result:**

| id | name  | info.age | info.city |
| -- | ----- | -------- | --------- |
| 1  | Alice | 25       | New York  |
| 2  | Bob   | 30       | London    |

---

## Flattening with `record_path`

```python
nested_json = {
    "school": "XYZ High",
    "students": [
        {"name": "Alice", "score": 90},
        {"name": "Bob", "score": 85}
    ]
}

df = json_normalize(nested_json, record_path="students", meta="school")
```

---

## Flatten Deeply Nested JSON

Use `sep` to control the column name format:

```python
df = json_normalize(data, sep="_")
```

Now columns look like: `info_age`, `info_city`

---

## Handling Lists in Fields

```python
data = [
    {"id": 1, "tags": ["python", "pandas"]},
    {"id": 2, "tags": ["json"]}
]

df = json_normalize(data)
```

You may need `explode()` if you want to separate list values:

```python
df = df.explode("tags")
```

---

## From JSON String or File

```python
with open("data.json") as f:
    data = json.load(f)

df = json_normalize(data)
```

---

## Summary of Parameters

| Parameter     | Description                                      |
| ------------- | ------------------------------------------------ |
| `data`        | Raw JSON or list of dicts                        |
| `record_path` | Path to nested list (for flattening arrays)      |
| `meta`        | Fields to retain from parent structure           |
| `sep`         | Separator for nested keys (default is `.`)       |
| `errors`      | Error handling for missing paths (`ignore`, etc) |

---

Reference: [pandas.json\_normalize() Docs](https://pandas.pydata.org/docs/reference/api/pandas.json_normalize.html)
