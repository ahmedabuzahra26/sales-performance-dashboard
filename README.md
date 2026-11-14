# Sales Performance Dashboard 2024

An interactive sales dashboard built from three linked tables (orders, products, and customers). It shows revenue, orders, units sold, and customers, and lets you filter everything by region, product category, product, and date.

![Sales Performance Dashboard](images/dashboard.png)

## Key metrics

The dashboard opens with these headline figures (no filters applied):

| Metric | Value |
| --- | --- |
| Total Revenue | $101,208,243 |
| Total Orders | 19,606 |
| Units Sold | 108,203 |
| Active Customers | 300 |
| Average Order Value | about $5,162 |

*Average Order Value = Total Revenue / Total Orders.*

## What the dashboard shows

- **Revenue by Product Category**
- **Monthly Revenue Trend, 2024**
- **Revenue by Region**
- **Revenue by Product**
- **Top 5 Customers by Revenue**
- **Orders by Day of Week**

**Filters:** Region, Product Category, Product, and a date timeline. All charts and KPI cards update together when a filter is changed.

## Data

The data is sample data and contains no real customer or company information.

| Table | Rows | Columns |
| --- | --- | --- |
| Orders | 19,606 | OrderID, CustomerID, ProductID, Quantity, Date |
| Products | 25 | ProductID, ProductName, Category, Price |
| Customers | 300 | CustomerID, First name, Last Name, Region |

- **Categories:** Electronics, Furniture, Clothing, Books, Toys
- **Regions:** Cairo, Giza, Alexandria, Mansoura, Aswan
- **Period:** January to December 2024

**Revenue** is calculated as `Quantity x Price` for each order, using the product price from the Products table.

[Add here where the data came from, with a link and its license, if it is a public dataset.]

## Data model

Orders is the central table, linked to the other two:

```
Customers (CustomerID) ---< Orders >--- Products (ProductID)
```

## Calculations (measures)

```
Total Revenue          = SUMX(Orders, Orders[Quantity] * RELATED(Products[Price]))
Total Orders           = DISTINCTCOUNT(Orders[OrderID])
Active Customers       = DISTINCTCOUNT(Orders[CustomerID])
Units Sold             = SUM(Orders[Quantity])
Average Order Value    = DIVIDE([Total Revenue], [Total Orders])
Revenue per Customer   = DIVIDE([Total Revenue], [Active Customers])
```

## Key insights

[Fill these in after checking the numbers in your dashboard. Write only what you have verified, for example:]

- [Which product category earns the most revenue, and its share]
- [Which month is the strongest and which is the weakest]
- [Which region and which products lead]
- [Whether a few customers account for a large share of revenue]

## Tools used

- Microsoft Excel
- [PivotTables, PivotCharts, slicers, and a timeline for filtering]
- [Data Model and DAX measures for the calculations above]
- [Add anything else you actually used]

## How to use

1. Download `Sales_Dashboard.xlsx` and open it in Microsoft Excel.
2. Go to the **Dashboard** sheet.
3. Click the slicers and the timeline to filter by region, category, product, or date. Every chart and KPI updates together.

## Repository contents

| File | Description |
| --- | --- |
| `Sales_Dashboard.xlsx` | Excel workbook with the data, data model, and dashboard |
| `images/dashboard.png` | Screenshot of the dashboard |
| `README.md` | Project description |

## What I learned

[Write 2 or 3 honest lines about what you learned building this dashboard, such as working with a data model and relationships, writing measures, and linking slicers to every chart. Add what you would improve next.]

## Author

**Ahmed Abuzahra**
Retail operations and customer experience professional building data analysis skills with Excel.
[LinkedIn](https://www.linkedin.com/in/ahmed-abuzahra-a040a5104)
