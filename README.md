# 📊 E-Commerce Sales Analysis Using Power BI & DAX

## 📌 Project Overview

This project is part of my journey toward becoming a **Data Analyst**. In this project, I use **Microsoft Power BI and DAX (Data Analysis Expressions)** to analyze e-commerce sales, profit, order performance, and sales target achievement.

The project uses three datasets: **List of Orders, Order Details, and Sales Target**. I created calculated columns and measures using DAX and developed interactive visualizations to understand business performance across categories, sub-categories, months, and geographical locations.

The main goal is to transform sales data into meaningful business insights using data modeling, DAX calculations, and interactive Power BI reports.

---

## 🎯 Project Objectives

- Create calculated columns using DAX.
- Develop measures for sales, profit, and order analysis.
- Calculate year-to-date (YTD) sales.
- Compare actual sales with sales targets.
- Analyze profit margins across sub-categories.
- Identify monthly sales trends.
- Compare profit and quantity sold.
- Analyze sales performance across states and cities.
- Build interactive Power BI visualizations.
- Communicate business insights through data storytelling.

---

## 📁 Dataset Description

The project uses three datasets.

### 1. List of Orders

| Column | Description |
|---|---|
| Order ID | Unique order identifier |
| Order Date | Date of the order |
| Customer Name | Name of the customer |
| City | Customer/order city |
| State | State associated with the order |
| Category | Product category |
| Amount | Order amount |
| Profit | Profit generated |

### 2. Order Details

| Column | Description |
|---|---|
| Order ID | Order identifier |
| Category | Main product category |
| Sub-Category | Product sub-category |
| Quantity | Quantity sold |
| Amount | Sales amount |
| Profit | Profit generated |

### 3. Sales Target

| Column | Description |
|---|---|
| Category | Product category |
| Month of Order Date | Month associated with the sales target |
| Target | Sales target value |

---

## 🛠️ Tools & Technologies

- **Microsoft Power BI Desktop**
- **DAX (Data Analysis Expressions)**
- Power Query
- Data Modeling
- Calculated Columns
- Measures
- Interactive Charts and Visualizations
- Business Intelligence and Reporting

---

## 🧮 DAX Calculations

### 1. Calculated Columns

#### Category Type

Created a calculated column in the `Order Details` table by combining Category and Sub-Category.

```dax
Category Type =
'Order Details'[Category] & " - " &
'Order Details'[Sub-Category]
```

**Purpose:** Combines category information into one descriptive field.

#### Revenue per Order

Created a calculated column to calculate revenue using Amount multiplied by Quantity, as specified in the assignment.

```dax
Revenue per Order =
'Order Details'[Amount] *
'Order Details'[Quantity]
```

**Purpose:** Calculates the revenue value using the specified fields.

#### Sales Category

Created a calculated column to categorize sales amounts as Above Average or Below Average.

```dax
Sales Category =
IF(
    'Order Details'[Amount] >
        AVERAGE('Order Details'[Amount]),
    "Above Average",
    "Below Average"
)
```

**Purpose:** Classifies records based on the average Amount.

*Note: Calculated-column average logic should be validated against the intended overall average because calculated columns are evaluated row by row. The equality case is classified as Below Average in this example.*

---

### 2. Calculated Measures

#### Order Count

```dax
Order Count =
DISTINCTCOUNT('Order Details'[Order ID])
```

**Purpose:** Counts unique orders. This is appropriate when one order can contain multiple detail rows.

#### Average Profit in Delhi

```dax
Average Profit in Delhi =
CALCULATE(
    AVERAGE('List of Orders'[Profit]),
    'List of Orders'[City] = "Delhi"
)
```

**Purpose:** Calculates average profit for records associated with Delhi.

#### Year-to-Date (YTD) Sales

```dax
YTD Sales =
TOTALYTD(
    SUM('Order Details'[Amount]),
    'List of Orders'[Order Date]
)
```

**Purpose:** Calculates cumulative sales from the beginning of the year through the current date context.

*Note: The YTD measure depends on a valid relationship between the tables and a suitable date column. A dedicated Date table marked as a date table is recommended for reliable time-intelligence calculations.*

---

## 📊 Data Visualization

The following visuals are included in the assignment.

### 1. Sales Target Achievement by Category

**Visual:** Clustered Column Chart

Compares actual sales with sales targets for each category.

**Business purpose:** Identifies categories that meet, exceed, or fall below their targets.

### 2. Maximum Profit Margin by Sub-Category

**Visual:** Donut Chart

Displays the maximum profit margin for each sub-category.

**Business purpose:** Helps compare the highest profit-margin values across product sub-categories.

### 3. Monthly Sales Trend

**Visual:** Line Chart

Shows how sales change over time by month.

**Business purpose:** Helps identify sales trends and changes in performance.

### 4. Profit vs Quantity by Sub-Category

**Visual:** Scatter Chart

Compares profit and quantity sold across sub-categories.

**Business purpose:** Helps explore the relationship between sales volume and profitability.

### 5. Total Sales Amount and Target

**Visuals:** Card and Multi-row Card

- Displays total sales amount.
- Displays the total sales target.
- Shows the minimum target for each segment or category, as configured in the report.

**Business purpose:** Provides a quick overview of sales performance against targets.

### 6. Sales Performance Matrix

**Visual:** Matrix

Compares actual sales and sales targets across categories and months.

**Business purpose:** Highlights differences between actual and planned sales.

### 7. Geographic Sales Analysis

**Visual:** Map

Displays total sales by city.

**Business purpose:** Identifies geographical sales patterns and high-performing locations.

### 8. Sales Distribution by Sub-Category

**Visual:** Treemap

Shows the distribution of sales across product sub-categories.

**Business purpose:** Highlights the relative contribution of each sub-category to sales.

### 9. Order Count Analysis by State

**Visual:** Funnel Chart

Displays order counts across different states.

**Business purpose:** Provides a visual comparison of order volumes by state.

---

## 📈 Key Business Questions

This project explores the following questions:

- Which categories perform best against their sales targets?
- How does monthly sales performance change over time?
- Which sub-categories have the highest profit margins?
- What is the relationship between profit and quantity sold?
- How do actual sales compare with sales targets?
- Which cities contribute the most to sales?
- Which sub-categories contribute most to total sales?
- Which states have higher order counts?
- What is the average profit for orders associated with Delhi?

---

## 🔍 Key Insights

The Power BI report is designed to identify:

- Sales target achievement by category.
- Monthly sales patterns.
- Profit-margin differences across sub-categories.
- Relationships between profit and quantity sold.
- Sales contributions by city and sub-category.
- Order distribution across states.
- Differences between actual sales and planned targets.

**Final findings:** The specific highest-performing categories, cities, states, and sub-categories should be documented after reviewing the completed report visuals and their actual values.

---

## 📂 Project Structure

```text
powerbi-ecommerce-sales-analysis/
│
├── README.md
├── dax-assignment.pbix
└── screenshots/
    ├── sales-target-analysis.png
    ├── monthly-sales-trend.png
    ├── profit-margin-analysis.png
    ├── sales-performance-matrix.png
    └── powerbi-dashboard.png
```

---

## 💡 Key Learnings

Through this project, I practiced:

- Writing DAX calculated columns and measures.
- Applying conditional logic in DAX.
- Calculating order counts and average profit.
- Understanding YTD calculations.
- Comparing actual sales with sales targets.
- Building charts and interactive reports in Power BI.
- Analyzing sales, profit, quantity, and geographical performance.
- Presenting business information through visual storytelling.

---

## 🚀 Future Improvements

As I continue developing my Data Analyst skills, I plan to:

- Add more advanced DAX measures.
- Create KPI cards for sales, profit, and profit margin.
- Develop a dedicated Date table for time intelligence.
- Add year-over-year sales comparisons.
- Analyze customer purchasing patterns.
- Improve dashboard interactivity with slicers and drill-through.
- Explore the same dataset using SQL and Python.
- Expand the report with additional business insights.

---

## 👨‍💻 About Me

I am an aspiring **Data Analyst** building my portfolio through practical projects using Excel, Power BI, and data analysis techniques.

This project demonstrates my learning in **DAX, data modeling, sales analysis, target comparison, and interactive reporting**.

I am continuously improving my skills in:

- 📊 Microsoft Excel
- 📈 Microsoft Power BI
- 🧮 DAX
- 🗄️ SQL
- 🐍 Python
- 🧹 Data Cleaning
- 📉 Data Visualization

---

⭐ **This project is part of my Data Analyst portfolio and continuous learning journey.**
