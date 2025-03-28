# 🛒 Mega-Mart Sales Data Analysis

## 📌 About

This project explores Mega-Mart sales data to analyze top-performing branches and products, sales trends, and customer behavior. The goal is to identify opportunities for optimizing sales strategies and improving performance.

> 📢 "In this recruiting competition, job-seekers are provided with historical sales data for 45 Mega-Mart stores located in different regions. Each store contains many departments, and participants must project the sales for each department in each store. To add to the challenge, selected holiday markdown events are included in the dataset. These markdowns are known to affect sales, but it is challenging to predict which departments are affected and the extent of the impact."

## 🎯 Project Objectives

The primary objective of this project is to gain insights into Mega-Mart's sales data and understand the various factors influencing sales across different branches.

## 📊 Dataset Overview

The dataset contains sales transactions from three Mega-Mart branches located in Mandalay, Yangon, and Naypyitaw. It includes 17 columns and 1,000 rows:

| 📌 Column                  | 📖 Description                             | 🔢 Data Type      |
|-------------------------|-----------------------------------------|---------------|
| invoice_id              | Invoice identifier                     | VARCHAR(30)   |
| branch                  | Store branch code                      | VARCHAR(5)    |
| city                    | Branch location                        | VARCHAR(30)   |
| customer_type           | Type of customer                       | VARCHAR(30)   |
| gender                  | Gender of the customer                 | VARCHAR(10)   |
| product_line            | Product category                       | VARCHAR(100)  |
| unit_price              | Price per unit                         | DECIMAL(10,2) |
| quantity                | Number of units sold                   | INT           |
| VAT                     | Value-added tax amount                 | FLOAT(6,4)    |
| total                   | Total transaction amount               | DECIMAL(10,2) |
| date                    | Purchase date                          | DATE          |
| time                    | Purchase time                          | TIMESTAMP     |
| payment_method          | Payment method used                    | VARCHAR(30)   |
| cogs                    | Cost of goods sold                     | DECIMAL(10,2) |
| gross_margin_percentage | Gross margin percentage                | FLOAT(11,9)   |
| gross_income            | Gross income                           | DECIMAL(10,2) |
| rating                  | Customer rating                        | FLOAT(2,1)    |

## 📌 Data Analysis Scope

### 1️⃣ Product Analysis
- Identify top-performing product lines.
- Assess underperforming product lines that require improvement.

### 2️⃣ Sales Analysis
- Analyze sales trends across different products and branches.
- Measure the effectiveness of sales strategies and suggest optimizations.

### 3️⃣ Customer Analysis
- Segment customers based on purchase behavior.
- Determine the profitability of different customer segments.

## 🛠 Approach

### 🔍 1. **Data Wrangling**
- Identify and handle missing values.
- Load data into a structured database.
- Ensure data integrity by setting constraints (e.g., `NOT NULL`).

### 🔨 2. **Feature Engineering**
- **🕒 `time_of_day`**: Categorizes purchases into Morning, Afternoon, and Evening sales.
- **📆 `day_name`**: Extracts the weekday (e.g., Mon, Tue, Wed) to analyze peak sales days.
- **📅 `month_name`**: Extracts the transaction month to identify seasonal trends.

### 📊 3. **Exploratory Data Analysis (EDA)**
- Visualize key sales trends.
- Address business questions using statistical analysis.

## 📌 Business Questions Addressed

### 📍 General Questions
1. 🌍 How many unique cities are represented in the data?
2. 🏙️ In which city is each branch located?

### 📦 Product-Related Questions
1. 🔢 How many unique product lines are available?
2. 💳 What is the most common payment method?
3. 🛍️ Which product line has the highest sales?
4. 💰 What is the total revenue by month?
5. 📆 Which month had the highest COGS?
6. 📈 Which product line generated the most revenue?
7. 🌆 Which city generated the highest revenue?
8. 🏷️ Which product line had the highest VAT?
9. 📊 Which branch sold more products than the average sales volume?
10. 🚻 What is the most common product line by gender?
11. ⭐ What is the average rating per product line?

### 💵 Sales-Related Questions
1. 🕒 Sales distribution by time of day (per weekday).
2. 👥 Which customer type contributes the most to revenue?
3. 🌍 Which city has the highest tax percentage (VAT)?
4. 💳 Which customer type pays the most in VAT?

### 🛍️ Customer-Related Questions
1. 🔢 How many unique customer types exist?
2. 💳 How many unique payment methods are there?
3. 👥 What is the most common customer type?
4. 🏷️ Which customer type buys the most?
5. 🚻 What is the predominant gender of customers?
6. 🏢 What is the gender distribution per branch?
7. ⭐ Which time of the day receives the most customer ratings?
8. 📅 Which day of the week has the highest average rating?
9. 📊 Which branch receives the highest customer ratings?

## 💰 Revenue and Profit Calculations

Formulas used in analysis:

\[ 📈 COGS = \text{unit price} \times \text{quantity} \]

\[ 🏷️ VAT = 5\% \times COGS \]

\[ 💵 \text{Total Sales} = COGS + VAT \]

\[ 💰 \text{Gross Income} = \text{Total Sales} - COGS \]

\[ 📊 \text{Gross Margin Percentage} = \frac{\text{Gross Income}}{\text{Total Sales}} \times 100 \]

### 📌 Example Calculation:

**Given Data:**
- 🏷️ Unit Price = $45.79$
- 🔢 Quantity = $7$

\[ COGS = 45.79 \times 7 = 320.53 \]

\[ VAT = 5\% \times 320.53 = 16.0265 \]

\[ 💵 \text{Total Sales} = 320.53 + 16.0265 = 336.5565 \]

\[ 📊 \text{Gross Margin Percentage} = \frac{16.0265}{336.5565} \times 100 \approx 4.76\% \]

## 🖥️ Code Implementation

For SQL queries used in data analysis, refer to [SQL_queries.sql](sql_queries.sql).

```sql
-- 📂 Create database
CREATE DATABASE IF NOT EXISTS megamartSales;

-- 📋 Create sales table
CREATE TABLE IF NOT EXISTS sales(
    invoice_id VARCHAR(30) NOT NULL PRIMARY KEY,
    branch VARCHAR(5) NOT NULL,
    city VARCHAR(30) NOT NULL,
    customer_type VARCHAR(30) NOT NULL,
    gender VARCHAR(30) NOT NULL,
    product_line VARCHAR(100) NOT NULL,
    unit_price DECIMAL(10,2) NOT NULL,
    quantity INT NOT NULL,
    tax_pct FLOAT(6,4) NOT NULL,
    total DECIMAL(12,4) NOT NULL,
    date DATETIME NOT NULL,
    time TIME NOT NULL,
    payment VARCHAR(15) NOT NULL,
    cogs DECIMAL(10,2) NOT NULL,
    gross_margin_pct FLOAT(11,9),
    gross_income DECIMAL(12,4),
    rating FLOAT(2,1)
);
```
