# Excel to Python: Data Analysis Migration Guide

## 🌟 Introduction

Transitioning from Excel to Python is a critical skill for modern data professionals. This repository provides a comprehensive guide to help analysts, researchers, and data enthusiasts migrate their data analysis workflows from Excel to Python efficiently.

## 🎯 Repository Purpose

The goal is to provide a structured, practical approach to:
- Translate Excel functions to Python
- Improve data analysis capabilities
- Provide real-world migration strategies

## 📋 Table of Contents

1. [Data Loading](#1-data-loading)
2. [Data Cleaning](#2-data-cleaning)
3. [Data Manipulation](#3-data-manipulation)
4. [Calculations](#4-calculations)
5. [Pivot Tables](#5-pivot-tables)
6. [Visualizations](#6-visualizations)

## 🚀 Getting Started
### Prerequisites
Python 3.8+
pandas
numpy
matplotlib
seaborn

Installation

```pip install pandas numpy matplotlib seaborn```

## 1. Data Loading

### Excel Approach
Open file in Excel

Manual data import

### Python Equivalent
```python
import pandas as pd

# Reading Excel files
df = pd.read\_excel('data.xlsx')

# Reading CSV files
df = pd.read\_csv('data.csv')

# Reading specific sheets
df = pd.read\_excel('data.xlsx', sheet\_name='Sheet1')
```

## 2. Data Cleaning

### Excel Approach

Manual filtering

Removing duplicates

Finding blank cells

### Python Equivalent
```python
# Remove missing values

df\_cleaned = df.dropna()

# Remove duplicates

df\_unique = df.drop\_duplicates()

# Replace missing values

df\_filled = df.fillna(0)

# Conditional cleaning

df\_filtered = df[df['column'] > value]

#Multiple condition filtering
advanced\_filter = df[
    (df[`age`] > 25) & 
    (df[`salary`] < 100000) & 
    (df[`department`] == `Sales`)
]

#Regex-based filtering
df\_filtered = df[df[`email`].str.contains(`@gmail.com`)]
```

## 3. Data Manipulation

### Excel Approach
VLOOKUP

INDEX-MATCH

Manual sorting
### Python Equivalent
```python
# Merging dataframes
result = df1.merge(df2, on='key\_column')

# Sorting
df\_sorted = df.sort\_values('column')

# Grouping and aggregation
grouped = df.groupby('category')['value'].agg(['mean', 'sum'])
```

## 4. Calculations

### Excel Approach
SUM

AVERAGE

COUNT

### Python Equivalent
```python
# Basic calculations
total = df['column'].sum()
average = df['column'].mean()
count = df['column'].count()

# Advanced calculations
\` Column-wise Calculations
df[`total_sales`] = df[`quantity`] * df[`price`]

\` Multi-column Operations
df[`profit_margin`] = (df[`revenue`] - df[`cost`]) / df[`revenue`] * 100

\` Conditional Calculations
df[`bonus`] = np.where(
    df[`performance`] > 90, 
    df[`salary`] * 0.2,  \` 20% bonus for high performers
    df[`salary`] * 0.1   \` 10% bonus for others
)
```
## 5. Pivot Tables
### Excel Approach
Pivot Table Wizard

Manual aggregation

### Python Equivalent
```python
# Creating pivot tables
pivot = df.pivot\_table(
    index='category', 
    values='sales', 
    aggfunc='sum'
)

# Advanced Pivot Table
pivot_advanced = df.pivot_table(
    index=['region', 'category'],    # Multi-level rows
    columns='year',                  # Spread data across time
    values='sales',                  # Metric to analyze
    aggfunc=['sum', 'mean'],         # Multiple calculations at once
    fill_value=0,                    # Replace NaNs with 0
    margins=True,                    # Add 'All' totals for rows/cols
    margins_name='Grand Total'       # Rename the total label
)
```

## 6. Visualizations
### Excel Approach
Chart Wizard

Limited customization

### Python Equivalent
```python
import matplotlib.pyplot as plt
import seaborn as sns

# Bar plot
df.plot(kind='bar')

# Customised visualization
plt.figure(figsize=(10, 6))
sns.barplot(x='category', y='sales', data=df)
plt.title('Sales by Category')

# Advanced visualization
# 1. Pick a nice 'skin' for your chart (makes it look professional instantly)
sns.set_theme(style="white")

# 2. Create the plot with one extra trick: 'ci=None' removes those messy black lines
plt.figure(figsize=(8, 5))
ax = sns.barplot(x='category', y='sales', data=df, palette='viridis', ci=None)

# 3. Add the numbers on top so people don't have to guess
ax.bar_label(ax.containers[0])

# 4. Give it a clear title and clean up the edges
plt.title('Sales Breakdown by Category')
sns.despine() # This removes the top and right borders

plt.show()
```
## 🤝 Contributing
### Contributions are welcome! Please feel free to submit a Pull Request.
