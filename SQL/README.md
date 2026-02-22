
# Opioid Mortality Insights: A PySpark & SparkSQL Big Data Study
This project demonstrates high-level Big Data analysis using Apache Spark (PySpark) and SparkSQL. By processing a large-scale dataset on US Opioid Overdose Deaths (1999–2014), I utilized SQL-on-DataFrame operations to extract critical public health insights, such as state-by-state mortality trends and prescription-to-population correlations.

## 🛠️ Technical SQL Implementation
The core of this project focuses on leveraging the SparkSQL engine to perform relational queries on distributed datasets.

1. Relational Data Modeling
- Schema Enforcement: Defined and registered DataFrames as temporary SQL views (train_table) to enable standard SQL syntax on unstructured CSV data.
- Feature Engineering: Used withColumn and SQL expressions to calculate new metrics, such as the Prescription-per-Population ratio, to normalize data across states with varying sizes.

2. Advanced Querying & Analytics
- Complex Aggregations: Developed subqueries and Common Table Expressions (CTEs) to identify the state with the highest "Crude Rate" of mortality for every year in the dataset.
- Data Sanitization: Implemented SQL filtering to exclude "Unreliable" or "Suppressed" data points, ensuring the integrity of the statistical results.
- Window Functions: Utilized ROW_NUMBER() and partitioning logic to isolate top-tier records across time-series horizons.


<details>
<summary><b>View SQL Query: Which state has the highest Crude Rate per year?</b></summary>

```sql
SELECT Year, State, Max_Crude_Rate
    FROM (
        SELECT *, ROW_NUMBER() OVER(PARTITION BY Year ORDER BY Max_Crude_Rate DESC) AS rn
        FROM (
            SELECT Year, State, MAX(`Crude Rate`) AS Max_Crude_Rate 
            FROM train_table 
            WHERE `Crude Rate` != "Unreliable" AND `Crude Rate` != "Suppressed"
            GROUP BY Year, State
        ) max_crude_rate_per_year_and_state
    ) 
    WHERE rn = 1
    ORDER BY Year DESC

## 📈 Key Insights & Results
### Mortality Trends
- Successfully isolated the highest mortality rates per state, identifying regional spikes in states like Colorado (2014) and Washington (2013).
- Prescription Correlation: Integrated prescription data to visualize the 200% increase in opioid-related overdoses alongside retail pharmacy trends.
- Distributed Efficiency: Demonstrated the ability to handle millions of records using Spark’s local[*] configuration for optimized parallel processing.


## 🛠️ Tech Stack
- Engine: Apache Spark (PySpark)
- Query Language: SparkSQL / Standard SQL
- Environment: Jupyter Notebook / SQLContext
- Techniques: Window Functions, CTEs, Schema Inference, Temporary Views
