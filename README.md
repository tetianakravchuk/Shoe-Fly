Calculating Column Statistics

Overview

This project demonstrates how to use Pandas for analyzing and calculating statistics from datasets. It explores concepts such as aggregating, grouping, and summarizing data using Pandas DataFrames. The examples include real-world scenarios like analyzing user activity, inventory management, and pricing information from ShoeFly.com.

Features

Key Concepts Covered:

	1.	Loading and Inspecting Data
	•	Load data using pandas.read_csv().
	•	Examine the first 10 rows of a DataFrame with .head().
	2.	Grouping and Aggregating Data
	•	Use groupby() to calculate counts, sums, and averages grouped by one or more columns.
	•	Example: Count users visiting a website by month and traffic source.
	3.	Data Reshaping with Pivot Tables
	•	Convert grouped data into a pivot table using .pivot() for better readability.
	4.	Finding Maximum and Unique Values
	•	Identify the most expensive item in a dataset with .max().
	•	Count unique values in a column using .nunique().
	5.	Advanced Grouping
	•	Group by multiple columns for multi-dimensional analysis.
	•	Example: Calculate average sales by location and day of the week.
	6.	Using Lambda Functions
	•	Apply custom calculations like percentiles within groups using .apply() and lambda functions.
	7.	Cleaning Grouped Data
	•	Reset indices of grouped data to convert back to a standard DataFrame using .reset_index().

Example Use Cases

1. Website Analytics

Analyze user traffic across different months and sources:

df.groupby(['month', 'utm_source']).id.count().reset_index()

2. Inventory Management

List product types and their quantities, and calculate the total inventory value:

data['total_value'] = data['price'] * data['quantity']

3. Most Expensive Shoes

Identify the most expensive shoe for each shoe type:

pricey_shoes = orders.groupby('shoe_type').price.max().reset_index()

4. Percentile Analysis

Calculate the 25th percentile for shoe prices by color:

cheap_shoes = orders.groupby('shoe_color').price.apply(lambda x: np.percentile(x, 25)).reset_index()

5. Pivoting for Multi-Dimensional Analysis

Create pivot tables to summarize grouped data:

shoe_counts_pivot = shoe_counts.pivot(
  columns='shoe_color',
  index='shoe_type',
  values='id'
).reset_index()

Example Dataset Descriptions

	1.	shoeFly.csv
	•	Contains user visit data from an e-commerce website.
	•	Columns: utm_source, month, id.
	2.	orders.csv
	•	Includes product orders with pricing and color information.
	•	Columns: shoe_type, shoe_color, price.

Installation and Usage

Prerequisites

Ensure you have Python installed with the following libraries:
	•	pandas
	•	numpy

Running the Code

	1.	Clone this repository:

git clone https://github.com/your_username/column-statistics.git
cd column-statistics


	2.	Install dependencies:

pip install pandas numpy


	3.	Run the Python scripts:

python analyze_data.py

Folder Structure

.
├── analyze_data.py   # Main script for data analysis
├── shoeFly.csv       # User visit data
├── orders.csv        # Product orders data
└── README.md         # Project documentation

Key Learnings

This project demonstrates:
	•	Efficient data manipulation with Pandas.
	•	Generating insights from real-world datasets.
	•	Using advanced features like pivot tables and lambda functions for custom analysis.

Feel free to contribute, suggest improvements, or fork this repository!