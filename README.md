## Step 1: Data Preparation

### Overview
To perform the sales performance analysis, you'll need a dataset that contains sales transactions recorded over time. This dataset should include essential columns such as `date` and `sales_amount`. In this section, we outline how to obtain or create such a dataset.

### Option 1: Use an Existing Dataset
If you have access to an existing dataset that meets the criteria, you can use it for your analysis. Ensure that the dataset is in a compatible format, such as CSV or Excel, and that it includes the required columns.

### Option 2: Create a Sample Dataset
If you don't have an existing dataset, you can create a sample dataset for demonstration purposes. Below is an example of a CSV format dataset:

```plaintext
date, sales_amount
2023-01-01, 1000.00
2023-01-02, 1500.50
2023-01-03, 2000.75
2023-01-04, 1200.25
2023-01-05, 1800.60
## Step 2: SQL Queries for Analysis

### Overview
In this step, we provide SQL queries for performing sales performance analysis using SQL window functions. These queries will help you calculate essential metrics and gain insights into your sales data.

### SQL Query 1: Rolling Average Sales
The following SQL query calculates the rolling average sales for your dataset. This metric helps identify trends and patterns in your sales data over a specific time window.

```sql
SELECT
    date,
    sales_amount,
    AVG(sales_amount) OVER (ORDER BY date ROWS BETWEEN 2 PRECEDING AND CURRENT ROW) AS rolling_average
FROM sales_data;
#SQL Query 2: Year-over-Year Growth
SELECT
    date,
    sales_amount,
    sales_amount - LAG(sales_amount) OVER (ORDER BY date) AS year_over_year_growth
FROM sales_data;
#SQL Query 3: Cumulative Sales
SELECT
    date,
    sales_amount,
    SUM(sales_amount) OVER (ORDER BY date) AS cumulative_sales
FROM sales_data;


