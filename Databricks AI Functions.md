# Databricks AI Functions: Customer Sentiment Analysis


# 1. The Challenge

An analyst wants to enrich a customer feedback table by automatically assigning sentiment labels to each comment.

For example:

| Customer Feedback | Sentiment |
|---|---|
| I love this product! | Positive |
| The service was terrible. | Negative |
| The product is okay. | Neutral |


The analyst wants to use an AI model without:

Building an AI application.
Deploying an application.
Managing a model-serving endpoint.
Writing complex integration code.


# 2. Recommended Approach: Databricks AI Functions

Correct answer: Use Databricks AI Functions.

AI Functions allow analysts to call AI models directly from SQL or notebooks.

They provide a low-code way to apply AI to existing data without building or deploying a separate application.

For this example, we can use:
```
ai_analyze_sentiment()
```
This function analyzes text and returns a sentiment classification.

# 3. SQL Model Example

Assume we have a table named customer_feedback with a column named feedback.

We can apply sentiment analysis directly using SQL.

```
sql
SELECT
    feedback,
    ai_analyze_sentiment(feedback) AS sentiment
FROM customer_feedback;
```

***The AI Function analyzes each comment and returns a sentiment label.**


# 4. Python Notebook Example

AI Functions can also be used from Databricks notebooks.

```
python
from pyspark.sql.functions import expr
```
```
# Read customer feedback
df = spark.table("customer_feedback")
```
```
# Apply sentiment analysis
result = df.withColumn(
    "sentiment",
    expr("ai_analyze_sentiment(feedback)")
)
```
```
# Display the results
display(result)
```

This adds a new sentiment column to the existing DataFrame.

# 5. Workflow

       +---------------------------+
       |   Customer Feedback       |
       |       Data Table          |
       +-------------+-------------+
                     |
                     v
       +---------------------------+
       |       Databricks          |
       |      SQL / Notebook       |
       +-------------+-------------+
                     |
                     v
       +---------------------------+
       |       AI Function         |
       |                           |
       |  ai_analyze_sentiment()  |
       +-------------+-------------+
                     |
                     v
       +---------------------------+
       |     AI Model Analysis     |
       |                           |
       |  Analyzes customer text   |
       +-------------+-------------+
                     |
                     v
       +---------------------------+
       |    Sentiment Results      |
       |                           |
       | Positive / Negative /     |
       | Neutral                   |
       +-------------+-------------+
                     |
                     v
       +---------------------------+
       |      Enriched Table       |
       |                           |
       | Feedback + Sentiment      |
       +---------------------------+

# 6. Why Is This the Lowest-Code Approach?

AI Functions are useful because:

**Low code**: AI models can be called using simple SQL functions.

**No application required**: There is no need to build a separate AI application.

**No endpoint management**: The analyst does not need to manage their own model-serving endpoint.

**Direct data integration**: AI results can be added to existing tables and DataFrames.

**Easy to use**: Analysts can work with familiar SQL and Python notebooks.


# 7. Conclusion

Databricks AI Functions allow analysts to apply AI directly to their data using SQL or notebooks.

For customer sentiment analysis, ai_analyze_sentiment() classifies feedback without requiring the analyst to build or deploy an application.

## AI Functions = AI directly inside SQL and notebooks.