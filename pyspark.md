# PySpark Basics Cheat Sheet

## Setup

```python
from pyspark.sql import SparkSession

spark = SparkSession.builder \
    .appName("MyApp") \
    .getOrCreate()
````

## Creating DataFrames

### From a list of tuples

```python
data = [("Alice", 25), ("Bob", 30)]
columns = ["Name", "Age"]
df = spark.createDataFrame(data, columns)
```

### From CSV

```python
df = spark.read.csv("file.csv", header=True, inferSchema=True)
```

### From JSON

```python
df = spark.read.json("file.json")
```

## Viewing Data

```python
df.show()           # Display rows
df.printSchema()    # Print schema
df.columns          # List column names
df.describe().show()# Summary statistics
```

## Selecting & Filtering

```python
df.select("Name").show()
df.select("Name", "Age").show()

df.filter(df["Age"] > 25).show()
df.where(df["Age"] == 30).show()
```

## Column Operations

```python
from pyspark.sql.functions import col, expr

df.withColumn("AgePlusOne", col("Age") + 1).show()
df.withColumnRenamed("Age", "Years").show()
```

## Aggregations

```python
df.groupBy("Name").count().show()
df.groupBy("Name").agg({"Age": "avg"}).show()

from pyspark.sql.functions import avg, max, min

df.groupBy("Name").agg(
    avg("Age").alias("AvgAge"),
    max("Age").alias("MaxAge")
).show()
```

## Sorting & Dropping

```python
df.orderBy("Age").show()
df.orderBy(col("Age").desc()).show()

df.drop("Age").show()
```

## Joins

```python
df1.join(df2, on="id", how="inner").show()
df1.join(df2, on="id", how="left").show()
df1.join(df2, on="id", how="outer").show()
```

## Working with Nulls

```python
df.na.drop().show()
df.na.fill({"Age": 0}).show()
df.filter(df["Age"].isNull()).show()
```

## Saving Data

```python
df.write.csv("output.csv", header=True)
df.write.json("output.json")
df.write.parquet("output.parquet")
```

## SQL Queries

```python
df.createOrReplaceTempView("people")
spark.sql("SELECT * FROM people WHERE Age > 25").show()
```

---

Reference: [PySpark API Docs](https://spark.apache.org/docs/latest/api/python/)
