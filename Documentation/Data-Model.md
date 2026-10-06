# Data Model

## Model Overview

The Power BI project uses a star-schema-oriented data model consisting of a central transactional sales table and a dedicated Calendar date dimension.

## Tables

### Global-Superstore

The `Global-Superstore` table acts as the primary transactional table.

It contains:

- Order information
- Customer information
- Product information
- Geographic information
- Sales and profit
- Quantity
- Discount
- Shipping information

### Calendar

The `Calendar` table is a dedicated DAX-created date dimension.

It provides the date structure required for:

- Monthly analysis
- Quarterly analysis
- Yearly analysis
- YoY analysis
- QoQ analysis
- MoM analysis

## Relationship

The Calendar table is related to the Global-Superstore table through the order date.

Conceptually:

Calendar[Date]

↓

Global-Superstore[Order Date]

This relationship allows Calendar fields to filter transactional sales data and enables time-intelligence calculations.

## Model Architecture

Calendar
    |
    | Date → Order Date
    |
    v
Global-Superstore
    |
    ├── Customers
    ├── Products
    ├── Categories
    ├── Segments
    ├── Geography
    ├── Sales
    ├── Profit
    └── Orders