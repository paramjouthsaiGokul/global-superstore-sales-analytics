# Global Superstore Sales Analytics Dashboard

**Power BI | DAX | Power Query | Data Modeling | Business Intelligence**

## Project Overview

The Global Superstore Sales Analytics Dashboard is an interactive Power BI business intelligence project developed to analyze sales performance, profitability, customer behavior, product performance, geographic trends, and time-based business performance.

The project transforms transactional sales data into an interactive analytical solution that helps users monitor key business KPIs, identify performance trends, investigate sales and profit drivers, analyze customer behavior, evaluate product performance, and explore geographic performance.

The dashboard analyzes approximately:

- **$12.64M Total Sales**
- **$1.47M Total Profit**
- **25K Total Orders**
- **2K Total Customers**

## Business Problem

Raw transactional sales data contains valuable information about customers, products, orders, regions, sales, and profit. However, analyzing large amounts of transaction-level data manually makes it difficult to quickly identify important business trends and performance issues.

This project was developed to help answer questions such as:

- How is overall sales performance changing?
- How profitable is the business?
- Which categories and products generate the most sales?
- Which products generate losses?
- Which customers contribute significantly to sales?
- Which regions perform best?
- How is sales performance changing over time?

## Project Objectives

- Analyze overall sales and profitability
- Monitor key business KPIs
- Analyze YoY, QoQ, and MoM performance
- Identify high-performing and loss-making products
- Analyze customer contribution and purchasing behavior
- Evaluate regional and geographic performance
- Analyze product performance
- Support data-driven business decision-making

## Tools & Technologies

- **Power BI Desktop** — Dashboard development and visualization
- **Power Query** — Data preparation and transformation
- **DAX** — Measures, KPIs, and time-intelligence calculations
- **Data Modeling** — Calendar table and analytical model
- **Power BI Visuals** — KPI cards, charts, tables, maps, slicers, and interactive analysis

## Dataset & Data Model

The project uses the Global Superstore transactional sales dataset.

### Main Data Table

**Global-Superstore**

The main table contains transactional information related to:

- Customers
- Orders
- Products
- Sales
- Profit
- Quantity
- Discount
- Shipping
- Geography

### Supporting Tables

**Calendar**

A DAX-created calendar table used for time-based analysis and time-intelligence calculations.

**Top Product Metric**

A supporting selector table used to dynamically rank products based on:

- Total Sales
- Total Profit

### Data Preparation

Data preparation was performed using Power Query. The main data table was loaded and structured by promoting headers and applying appropriate data types.

The Calendar table was created using DAX to support time-based analysis such as:

- Year
- Month
- Quarter
- Year-over-Year analysis
- Month-over-Month analysis
- Quarter-over-Quarter analysis

## Key DAX Measures

The dashboard uses DAX measures to calculate business KPIs, customer metrics, profitability indicators, and time-based performance.

### Core KPIs

- Total Sales
- Total Profit
- Total Quantity
- Total Orders
- Total Customers
- Profit Margin %

### Sales & Customer Metrics

- Average Order Value (AOV)
- Sales per Customer
- Profit per Customer
- Purchase Frequency

### Customer Analytics

- Customer Contribution %
- Customer Health
- Recency

Customer Health is classified using the following business rules:

| Recency | Customer Health |
|---|---|
| 0–30 days | Active |
| 31–60 days | Healthy |
| 61–90 days | Warning |
| 91–180 days | At Risk |
| >180 days | Churned |

### Time Intelligence

- Sales LY
- Sales YoY Change
- Sales YoY %
- YoY Growth %
- QoQ Growth %
- MoM Growth %

### Product & Profitability Analysis

- Loss Amount
- Loss Amount Display
- Top Product Sales Contribution %
- Top Product Rank

The Top Product Rank measure dynamically ranks products based on either Total Sales or Total Profit.

## Dashboard Pages

The Power BI report contains multiple analytical pages designed for different business perspectives.

### 1. Sales Performance Overview

Provides a high-level view of:

- Total Sales
- Total Profit
- Total Orders
- Total Customers
- Monthly Sales Trend
- Sales by Category
- Sales by Segment
- Sales by Region

### 2. Executive Summary

Provides an executive-level overview of:

- Sales and Profit KPIs
- Profit Margin
- YoY Sales Growth
- Monthly Sales Performance
- Monthly Profit Performance
- Sales by Segment
- Sales by State

### 3. Sales Analysis

Focuses on sales trends and performance using:

- YoY Growth
- QoQ Growth
- MoM Growth
- Sales by Region
- Top States by Sales
- Sales by Category
- Sales by Segment

### 4. Profitability Analysis

Analyzes profitability using:

- Total Profit
- Profit Margin
- Loss Amount
- Profit Margin Trend
- Profit by Category
- Loss-making Products

### 5. Customer Analysis

Analyzes customer behavior and contribution using:

- Sales per Customer
- Profit per Customer
- Purchase Frequency
- Sales and Profit by Segment
- Customer Sales Contribution
- Top Customers
- Sales per Customer by Segment

### 6. Product Analysis

Provides detailed product-level analysis including:

- Product Sales
- Product Profit
- Sales Contribution
- Sales vs Profit Margin
- Product-level performance
- Dynamic Top Product analysis

### 7. Geographic Analysis

Analyzes geographical performance across:

- Regions
- States
- Cities
- Sales by State
- Profit by Region
- Regional and geographic filters

## Business Insights

The dashboard enables analysis of several important business areas:

- Identify overall sales and profitability performance.
- Compare sales performance across different time periods.
- Identify high-performing and low-performing product categories.
- Detect loss-making products that may require further investigation.
- Analyze customer contribution to overall sales.
- Evaluate purchasing behavior using purchase frequency and recency.
- Compare performance across regions, states, and cities.
- Identify products and segments contributing significantly to revenue and profit.
- Use interactive filtering and drill-through analysis to investigate performance at a more detailed level.


## Project Structure

```text
Global-Superstore-Sales-Analytics/
│
├── PowerBI/
│   └── GSS_sales.pbix
│
├── Screenshots/
│   ├── 01-sales-performance-overview.png
│   ├── 02-executive-summary.png
│   ├── 03-sales-analysis.png
│   ├── 04-profitability-analysis.png
│   ├── 05-customer-analysis.png
│   ├── 06-product-analysis.png
│   └── 07-geographic-analysis.png
│
├── Documentation/
│   ├── Data-Dictionary.md
│   ├── Data-Model.md
│   ├── DAX-Measures.md
│   └── Dashboard-Pages.md
│
├── Data/
│
└── README.md


## Documentation

Detailed project documentation is available in the `Documentation` folder:

- [Data Dictionary](Documentation/Data-Dictionary.md) — Dataset fields and measures
- [Data Model](Documentation/Data-Model.md) — Data model and table structure
- [DAX Measures](Documentation/DAX-Measures.md) — Key DAX calculations used in the dashboard
- [Dashboard Pages](Documentation/Dashboard-Pages.md) — Explanation of each dashboard page