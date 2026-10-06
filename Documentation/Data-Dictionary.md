# Data Dictionary

## Overview

The Power BI project uses a transactional Global Superstore dataset supported by a dedicated Calendar table created using DAX.

The data model contains two primary tables:

- `Global-Superstore`
- `Calendar`

---

# Global-Superstore

`Global-Superstore` is the primary transactional table containing order, customer, product, geographic, sales, profitability, quantity, discount, and shipping information.

## Customer & Geographic Fields

| Column | Description |
|---|---|
| Customer ID | Unique identifier for the customer |
| Customer Name | Name of the customer |
| Segment | Customer segment |
| Country | Country associated with the transaction |
| Market | Market associated with the transaction |
| Region | Geographic region |
| State | State or administrative region |
| City | City associated with the transaction |
| Postal Code | Postal code associated with the location |

## Order Fields

| Column | Description |
|---|---|
| Row ID | Unique identifier for the transaction row |
| Order ID | Identifier for the order |
| Order Date | Date on which the order was placed |
| Ship Date | Date on which the order was shipped |
| Ship Mode | Shipping method |
| Order Priority | Priority assigned to the order |

## Product Fields

| Column | Description |
|---|---|
| Product ID | Unique identifier for the product |
| Product Name | Name of the product |
| Category | Product category |
| Sub-Category | Product sub-category |

## Financial & Quantity Fields

| Column | Description |
|---|---|
| Sales | Revenue generated from the transaction |
| Profit | Profit generated from the transaction |
| Quantity | Number of units sold |
| Discount | Discount applied to the transaction |
| Shipping Cost | Shipping cost associated with the transaction |

---

# Calendar

`Calendar` is a dedicated DAX-created date table used to support time-based analysis and DAX time-intelligence calculations.

| Field / Measure | Description |
|---|---|
| Date | Date used for time-based analysis |
| Year | Calendar year |
| Month | Month name/number used for monthly analysis |
| Month Number | Numeric month used for chronological sorting |
| Quarter | Quarter of the year |
| Year Month | Year-month reporting field |
| Year Month Sort | Sorting field for chronological year-month order |

---

# Key Analytical Measures

The model also contains DAX measures used for business analysis.

### Sales & Profitability

- Total Sales
- Total Profit
- Total Quantity
- Profit Margin %
- AOV
- Sales per Customer
- Profit per Customer

### Customer Analytics

- Total Customers
- Total Orders
- Customer Contribution %
- Purchase Frequency
- Recency
- Customer Health

### Time Intelligence

- Sales LY
- Sales YoY Change
- Sales YoY %
- YoY Growth %
- QoQ Growth %
- MoM Growth %

### Product & Loss Analysis

- Loss Amount
- Loss Amount Display
- Top Product Sales Contribution %
- Top Product Rank