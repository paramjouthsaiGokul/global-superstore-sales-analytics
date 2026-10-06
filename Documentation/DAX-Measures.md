# DAX Measures

This document contains the key DAX measures developed for the Global Superstore Sales Analytics Dashboard.

The measures are organized into:

1. Core KPIs
2. Sales & Customer Metrics
3. Customer Analytics
4. Time Intelligence
5. Loss Analysis
6. Product Analysis

---

# 1. Core KPI Measures

```DAX
Total Sales =
SUM('Global-Superstore'[Sales])
Total Quantity
Total Quantity =
SUM('Global-Superstore'[Quantity])

Calculates the total quantity of products sold.
Total Profit
Total Profit =
SUM('Global-Superstore'[Profit])

Calculates total profit generated from the transactions.
Total Orders
Total Orders =
DISTINCTCOUNT('Global-Superstore'[Order ID])

Calculates the number of unique orders.
DISTINCTCOUNT is used because a single order can contain multiple transaction rows.
Total Customers
Total Customers =
DISTINCTCOUNT('Global-Superstore'[Customer ID])

Calculates the number of unique customers.
Profit Margin %
Profit Margin % =
DIVIDE(
    [Total Profit],
    [Total Sales],
    0
)

Calculates profit as a percentage of total sales.
2. Sales & Customer Metrics
AOV
AOV =
DIVIDE(
    [Total Sales],
    [Total Orders],
    0
)

Calculates Average Order Value, representing the average sales generated per order.
Sales per Customer
Sales per Customer =
DIVIDE(
    [Total Sales],
    [Total Customers],
    0
)

Calculates the average sales generated per customer.
Profit per Customer
Profit per Customer =
DIVIDE(
    [Total Profit],
    [Total Customers],
    0
)

Calculates the average profit generated per customer.
3. Customer Analytics
Customer Contribution %
Customer Contribution % =
DIVIDE(
    [Total Sales],
    CALCULATE(
        [Total Sales],
        REMOVEFILTERS('Global-Superstore'[Customer Name])
    )
)

Calculates the selected customer's contribution to overall sales while removing the customer-name filter for the denominator.
Purchase Frequency
Purchase Frequency =
DIVIDE(
    [Total Orders],
    [Total Customers]
)

Calculates the average number of orders per customer.
Recency
Recency =
VAR AnalysisDate =
    MAX('Calendar'[Date])
VAR LastPurchaseDate =
    MAX('Global-Superstore'[Order Date])
RETURN
    IF(
        NOT ISBLANK(LastPurchaseDate),
        DATEDIFF(
            LastPurchaseDate,
            AnalysisDate,
            DAY
        )
    )

Calculates the number of days between the analysis date and the customer's latest purchase date.
Customer Health
Customer Health =
VAR RecencyDays = [Recency]
RETURN
    SWITCH(
        TRUE(),
        ISBLANK(RecencyDays), BLANK(),
        RecencyDays > 180, "Churned",
        RecencyDays > 90, "At Risk",
        RecencyDays > 60, "Warning",
        RecencyDays > 30, "Healthy",
        "Active"
    )

Classifies customers based on recency.
Recency	Classification
0–30 days	Active
31–60 days	Healthy
61–90 days	Warning
91–180 days	At Risk
>180 days	Churned


These thresholds are dashboard business rules and can be adjusted according to the business's customer purchase cycle.
4. Time Intelligence
Sales LY
Sales LY =
CALCULATE(
    [Total Sales],
    SAMEPERIODLASTYEAR('Calendar'[Date])
)

Calculates sales for the equivalent period in the previous year.
Sales YoY Change
Sales YoY Change =
[Total Sales] - [Sales LY]

Calculates the absolute difference in sales compared with the previous year.
Sales YoY %
Sales YoY % =
DIVIDE(
    [Sales YoY Change],
    [Sales LY]
)

Calculates the percentage change in sales compared with the previous year.
YoY Growth %
YoY Growth % =
VAR CurrentSales = [Total Sales]
VAR PreviousSales =
    CALCULATE(
        [Total Sales],
        DATEADD('Calendar'[Date], -1, YEAR)
    )
RETURN
    DIVIDE(
        CurrentSales - PreviousSales,
        PreviousSales
    )

Calculates year-over-year sales growth using DATEADD.
QoQ Growth %
QoQ Growth % =
VAR CurrentSales = [Total Sales]
VAR PreviousSales =
    CALCULATE(
        [Total Sales],
        DATEADD('Calendar'[Date], -3, MONTH)
    )
RETURN
    DIVIDE(
        CurrentSales - PreviousSales,
        PreviousSales
    )

Compares the current period's sales with sales three months earlier.
MoM Growth %
MoM Growth % =
VAR CurrentSales = [Total Sales]
VAR PreviousSales =
    CALCULATE(
        [Total Sales],
        DATEADD('Calendar'[Date], -1, MONTH)
    )
RETURN
    DIVIDE(
        CurrentSales - PreviousSales,
        PreviousSales
    )

Calculates month-over-month sales growth.
5. Loss Analysis
Loss Amount
Loss Amount =
CALCULATE(
    [Total Profit],
    'Global-Superstore'[Profit] < 0
)

Calculates the total profit value associated with loss-making transactions.
Loss Amount Display
Loss Amount Display =
ABS([Loss Amount])

Converts the negative loss value into a positive display value for dashboard presentation.
6. Product Analysis
Top Product Sales Contribution %
Top Product Sales Contribution % =
VAR TopProductSales =
    MAXX(
        TOPN(
            1,
            ALL('Global-Superstore'[Product Name]),
            [Total Sales],
            DESC
        ),
        [Total Sales]
    )
RETURN
DIVIDE(
    TopProductSales,
    CALCULATE(
        [Total Sales],
        REMOVEFILTERS('Global-Superstore'[Product Name])
    )
)

Identifies the highest-sales product and calculates its contribution to total sales.
This measure demonstrates the use of TOPN, MAXX, ALL, REMOVEFILTERS, and DIVIDE.
Top Product Rank
Top Product Rank =
VAR SelectedMetric =
    SELECTEDVALUE(
        'Top Product Metric'[Top Product Metric],
        "Total Sales"
    )
RETURN
SWITCH(
    SelectedMetric,

    "Total Sales",
        RANKX(
            ALL('Global-Superstore'[Product Name]),
            [Total Sales],
            ,
            DESC,
            DENSE
        ),

    "Total Profit",
        RANKX(
            ALL('Global-Superstore'[Product Name]),
            [Total Profit],
            ,
            DESC,
            DENSE
        )
)

Provides dynamic product ranking based on the selected metric.



DAX Techniques Used
The project demonstrates the following DAX concepts:
- Aggregation using SUM
- Distinct counting using DISTINCTCOUNT
- Division using DIVIDE
- Filter context modification using CALCULATE
- Filter removal using REMOVEFILTERS and ALL
- Time intelligence using SAMEPERIODLASTYEAR and DATEADD
- Variables using VAR
- Conditional logic using IF and SWITCH
- Ranking using RANKX
- Top-N analysis using TOPN
- Iterator functions using MAXX
- Date calculations using DATEDIFF
- Dynamic metric selection using SELECTEDVALUE