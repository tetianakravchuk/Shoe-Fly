ShoeFly Data Analysis with Pandas

Overview

This project demonstrates various techniques for data aggregation and analysis using Pandas. It provides insights into analyzing sales data, inventory data, and shipment data for the fictional company ShoeFly.com. The examples include tasks like calculating statistics, identifying trends, and cleaning up data using groupby, apply, and other Pandas methods.

Features and Analysis Steps

1. Aggregating Data

	•	Group data by columns: Analyze trends by grouping data based on attributes like month, utm_source, or shoe_type.
	•	Example:

df.groupby(['month', 'utm_source']).id.count().reset_index()


	•	Pivot tables: Reorganize grouped data for easier readability and analysis.

df.groupby(['month', 'utm_source']).id.count()\
    .reset_index()\
    .pivot(columns='month', index='utm_source', values='id')

2. Calculating Column Statistics

Aggregate functions like .max(), .nunique(), and custom functions are used to extract valuable insights:
	•	Most expensive shoes:

most_expensive = orders.price.max()


	•	Number of unique colors of shoes:

num_colors = orders.shoe_color.nunique()


	•	Find the most expensive shoe by type:

pricey_shoes = orders.groupby('shoe_type').price.max()

3. Cleaning Grouped Data

After grouping, use reset_index() to convert grouped Series into DataFrames for cleaner results.
	•	Example:

pricey_shoes = orders.groupby('shoe_type').price.max().reset_index()

4. Custom Aggregations with apply and lambda

For complex operations like calculating percentiles, the apply method is used with lambda functions:
	•	Find 25th percentile for shoe prices by color:

cheap_shoes = orders.groupby('shoe_color').price.apply(lambda x: np.percentile(x, 25)).reset_index()

5. Grouping by Multiple Columns

Analyze trends involving multiple groupings, such as store and day_of_week, to identify patterns across various dimensions:
	•	Example:

df.groupby(['store', 'day_of_week']).sales.mean().reset_index()

Data Sources

Files Used:

	•	inventory.csv: Data about inventory across various store locations.
	•	orders.csv: Data about customer orders, including shoe types, colors, and prices.
	•	shipments.csv: Shipment address information and details.

Key Outputs

	1.	Statistical Insights:
	•	Total sales by source and month.
	•	Most expensive and cheapest items.
	•	Shoe colors available for sale.
	2.	Data Cleaning:
	•	Converted grouped Series into DataFrames for easier processing.
	•	Filtered and cleaned data using conditionals and aggregations.
	3.	Custom Calculations:
	•	Identified 25th percentile of prices for each shoe color.
	•	Calculated the number of unique shipments by state.

How to Use

	1.	Clone the repository and ensure the necessary files (e.g., inventory.csv, orders.csv) are present in the working directory.
	2.	Install dependencies:

pip install pandas numpy


	3.	Run the Python scripts to explore the data and perform the analyses:

python analysis_script.py

Requirements

	•	Python 3.8+
	•	Pandas
	•	NumPy

Example Code Snippets

# Load data and examine
import pandas as pd

df = pd.read_csv('shoeFly.csv')
print(df.head(10))

# Calculate the most expensive shoes
most_expensive = df['price'].max()
print(f"Most expensive shoe price: {most_expensive}")

# Find cheap shoes (25th percentile)
import numpy as np

cheap_shoes = df.groupby('shoe_color').price.apply(lambda x: np.percentile(x, 25)).reset_index()
print(cheap_shoes)

Future Enhancements

	•	Add visualization tools like Matplotlib or Seaborn for better data representation.
	•	Automate reporting with a dashboard.
	•	Enhance data preprocessing for missing or invalid data.