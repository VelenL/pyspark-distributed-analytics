# Distributed Analytics with PySpark

Two academic case studies using PySpark's distributed APIs: unstructured tweet analysis with RDD transformations and structured real-estate analysis with DataFrames and Spark SQL.

> The goal is to demonstrate how the same Spark ecosystem supports both text processing and schema-based business analysis. This is a cleaned portfolio version of a team course project.

## Case study 1 — Tweet analysis with RDDs

The first notebook analyses approximately **58,000 tweet records** with PySpark RDD operations.

### Pipeline

1. Tokenise and normalise text with regular expressions.
2. Use `flatMap`, `filter`, `map`, `reduceByKey` and `sortBy` to calculate frequencies.
3. Extract the most frequent mentions and hashtags.
4. Join tweet tokens with positive and negative word lexicons.
5. Remove stop words, mentions, hashtags and noisy terms with successive `subtract` transformations.
6. Visualise the top sentiment and contextual words with Pandas, Matplotlib and Seaborn.

![Positive and negative word counts](assets/sentiment-words.png)

![Contextual word counts](assets/contextual-words.png)

The sentiment step is **lexicon-based frequency analysis**, not a machine-learning sentiment classifier.

## Case study 2 — Real-estate analysis with DataFrames and Spark SQL

The second notebook analyses approximately **80,000 real-estate transaction rows**.

### Pipeline

- Define an explicit schema with `StructType` and `StructField`.
- Read a semicolon-delimited CSV into a Spark DataFrame.
- Register a temporary SQL view.
- Use Spark SQL to compare transaction volumes by city, property type and sale type.
- Explore price differences between Toulouse and surrounding municipalities.
- Derive unit-price indicators and sort results for comparison.

## Repository contents

```text
assets/                       Selected outputs from the original analysis
data/README.md                Expected input files and data policy
notebooks/01_tweet_rdd_analysis.ipynb
notebooks/02_real_estate_spark_sql.ipynb
requirements.txt
```

The notebooks have been cleaned for public presentation: execution outputs and Colab account-specific paths were removed, imports were reordered, and an incorrect final display variable was corrected.

## What this project demonstrates

- RDD transformations and actions;
- key-value aggregation and joins;
- Spark DataFrames, explicit schemas and temporary views;
- Spark SQL filtering, grouping, aggregation and ordering;
- the difference between low-level RDD processing and structured DataFrame/SQL analysis.

## Scope and limitations

- This is an **academic team project executed in a Colab-style environment**, not a production Spark cluster.
- The datasets are useful for learning distributed APIs, but their size would not require Spark in a typical production decision; Pandas or a database could also handle them.
- The original unit-price calculation divided price by living area plus land area. That was a course simplification, not a standardised real-estate valuation metric. A production analysis should define separate and validated metrics.
- This project does not claim Databricks, Lakehouse, Airflow, streaming, cluster administration or production pipeline experience.

## Running the notebooks

1. Install the dependencies in `requirements.txt`.
2. Place authorised input files in `data/` using the filenames documented in `data/README.md`.
3. Start Jupyter and run each notebook independently.

## My contribution

I contributed to the Spark transformations, SQL queries, result interpretation and visualisation. The repository preserves the original analytical scope while making its limits explicit and interview-safe.
