# Introduction to PySpark

## Table of Contents

- [Introduction to PySpark](#introduction-to-pyspark)
  - [Table of Contents](#table-of-contents)
  - [**Getting to know PySpark**](#getting-to-know-pyspark)
    - [Using Spark in Python](#using-spark-in-python)
    - [Using DataFrames](#using-dataframes)
  - [**Manipulating data**](#manipulating-data)
    - [SQL in a nutshell](#sql-in-a-nutshell)
    - [Joining](#joining)

## **Getting to know PySpark**

### Using Spark in Python
- Examining The SparkContext
```python
from pyspark import SparkContext
sc = SparkContext("local", "First App")

# Verify SparkContext
print(sc)

# Print Spark version
print(sc.version)
```

**[⬆ back to top](#table-of-contents)**

### Using DataFrames
- Creating a SparkSession
```python
# Import SparkSession from pyspark.sql
from pyspark.sql import SparkSession

# Create spark
spark = SparkSession.builder.getOrCreate()

# Print spark
print(spark)
```

- Viewing tables
```python
# Print the tables in the catalog
print(spark.catalog.listTables())
```

- Are you query-ious?
```python
# Don't change this query
query = "FROM flights SELECT * LIMIT 10"

# Get the first 10 rows of flights
flights10 = spark.sql(query)

# Show the results
flights10.show()
```

- Pandafy a Spark DataFrame
```python
# Don't change this query
query = "SELECT origin, dest, COUNT(*) as N FROM flights GROUP BY origin, dest"

# Run the query
flight_counts = spark.sql(query)

# Convert the results to a pandas DataFrame
pd_counts = flight_counts.toPandas()

# Print the head of pd_counts
print(pd_counts.head())
```

- Put some Spark in your data
```python
# Create pd_temp
pd_temp = pd.DataFrame(np.random.random(10))

# Create spark_temp from pd_temp
spark_temp = spark.createDataFrame(pd_temp)
spark_temp.show()

# Examine the tables in the catalog
print(spark.catalog.listTables())

# Add spark_temp to the catalog
spark_temp.createOrReplaceTempView('temp')

# Examine the tables in the catalog again
print(spark.catalog.listTables())
```

- Dropping the middle man
```python
# Don't change this file path
file_path = "/usr/local/share/datasets/airports.csv"

# Read in the airports data
airports = spark.read.csv(file_path, header=True)

# Show the data
airports.show()
```

**[⬆ back to top](#table-of-contents)**

## **Manipulating data**

- Creating columns
```python
# Create the DataFrame flights
flights = spark.table("flights")

# Show the head
flights.show()

# Add duration_hrs
flights = flights.withColumn("duration_hrs", flights.air_time / 60)
```

### SQL in a nutshell
- Filtering Data
```python
# Filter flights by passing a string
long_flights1 = flights.filter("distance > 1000")

# Filter flights by passing a column of boolean values
long_flights2 = flights.filter(flights.distance > 1000)

# Print the data to check they're equal
print(long_flights1.show())
print(long_flights2.show())
```

- Selecting II
```python
# Define avg_speed
avg_speed = (flights.distance/(flights.air_time/60)).alias("avg_speed")

# Select the correct columns
speed1 = flights.select("origin", "dest", "tailnum", avg_speed)
speed1.show()

# Create the same table using a SQL expression
speed2 = flights.selectExpr("origin", "dest", "tailnum", "distance/(air_time/60) as avg_speed")
speed2.show()
```

- Aggregating
```python
# Find the shortest flight from PDX in terms of distance
flights.filter(flights.origin == "PDX").groupBy().min("distance").show()

# Find the longest flight from SEA in terms of air time
flights.filter(flights.origin == "SEA").groupBy().max("air_time").show()
```

- Aggregating II
```python
# Average duration of Delta flights
flights.filter(flights.carrier == "DL").filter(flights.origin == "SEA").groupBy().avg("air_time").show()

# Total hours in the air
flights.withColumn("duration_hrs", flights.air_time/60).groupBy().sum("duration_hrs").show()
```

- Grouping and Aggregating I
```python
# Group by tailnum
by_plane = flights.groupBy("tailnum")

# Number of flights each plane made
by_plane.count().show()

# Group by origin
by_origin = flights.groupBy("origin")

# Average duration of flights from PDX and SEA
by_origin.avg("air_time").show()
```

- Grouping and Aggregating II
```python
# Import pyspark.sql.functions as F
import pyspark.sql.functions as F
flights.show()

# Group by month and dest
by_month_dest = flights.groupBy("month", "dest")

# Average departure delay by month and destination
by_month_dest.avg("dep_delay").show()

# Standard deviation of departure delay
by_month_dest.agg(F.stddev("dep_delay")).show()
```

**[⬆ back to top](#table-of-contents)**

### Joining
- Joining II
```python
# Examine the data
print(airports.show())

# Rename the faa column
airports = airports.withColumnRenamed("faa", "dest")

# Join the DataFrames
flights_with_airports = flights.join(airports, on="dest", how="leftouter")

# Examine the new DataFrame
print(flights_with_airports.show())
```

**[⬆ back to top](#table-of-contents)**
