# Task 7 – Basic Sales Summary Using SQLite + Python (Jupyter Notebook)

This repository contains a **Jupyter Notebook** that performs a simple sales analysis using a tiny SQLite database.  
The goal of this task is to demonstrate how Python and SQL can work together to generate basic sales insights and visualizations.

---

## 🎯 Objective

- Connect to a small SQLite database (`sales_data.db`)
- Run simple SQL queries to extract:
  - Total quantity sold per product  
  - Total revenue per product  
- Display the results using:
  - Basic `print()` statements  
  - A simple bar chart using `matplotlib`

This task helps you understand how Python interacts with SQL databases to perform lightweight data analysis.

---

## 🛠 Tools & Libraries Used

- **Python**
  - `sqlite3` → connect to SQLite databases  
  - `pandas` → read and manipulate query results  
  - `matplotlib` → create basic visualizations  
- **SQLite**
  - Built into Python (no external installation needed)
- **Environment**
  - Jupyter Notebook (`.ipynb`)

---

## 📂 Dataset Information

A small SQLite database is created inside the notebook:

- **Database:** `sales_data.db`  
- **Table:** `sales`  

### Sales Table Columns

| Column   | Type     | Description                 |
|----------|----------|-----------------------------|
| id       | INTEGER  | Auto-increment primary key  |
| date     | TEXT     | Date of sale                |
| product  | TEXT     | Product name                |
| quantity | INTEGER  | Units sold                  |
| price    | REAL     | Price per unit              |

The notebook inserts a few sample rows to simulate real sales data.

---

## 📓 What the Notebook Does (Step-by-Step)

### 1️⃣ Connect to SQLite Database

```python
import sqlite3
conn = sqlite3.connect("sales_data.db")
```
2️⃣ Create the sales Table + Insert Sample Data
The notebook automatically creates the table (if not present) and inserts test rows.

3️⃣ Run SQL Query for Summary
```python
query = """
SELECT product,
       SUM(quantity) AS total_qty,
       SUM(quantity * price) AS revenue
FROM sales
GROUP BY product;
"""
```
4️⃣ Load Query Results Into Pandas
```python

import pandas as pd
df = pd.read_sql_query(query, conn)
print(df)
```
5️⃣ Plot Revenue as a Bar Chart
```python
df.plot(kind='bar', x='product', y='revenue')
```
6️⃣ (Optional) Save the Chart
```python
plt.savefig("sales_chart.png")
```
📈 Output You Can Expect
A DataFrame showing:

Product name

Total quantity sold

Total revenue

A bar chart visualizing revenue by product

Console print statements summarizing the results clearly

📝 Deliverables Included in This Repository
Task7_Sales_Summary.ipynb
Complete Jupyter Notebook with:

Database creation

SQL queries

Pandas summary

Bar chart visualization

sales_data.db
SQLite database created during the notebook run

sales_chart.png (optional)
Saved version of the revenue chart

🎉 Learning Outcomes
By completing this task, you will learn how to:

Write basic SQL queries (SELECT, SUM, GROUP BY)

Connect Python to SQLite using sqlite3

Import SQL results into Pandas DataFrames

Perform simple data summaries

Create your first bar chart for sales analysis

This task is a perfect introduction to combining SQL + Python + Data Visualization in real projects.

This repository is created as beginer for learning purpose only!
