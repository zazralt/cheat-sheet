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

