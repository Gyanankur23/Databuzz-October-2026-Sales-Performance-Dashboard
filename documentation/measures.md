# Power BI Dashboard - DAX Measures Guide

## DAX Measures

### Total Sales
```
Total Sales = 
SUMX(
    Fact_Sales,
    Fact_Sales[OrderQuantity] * 
    CALCULATE(
        MAX(Dim_Product[ProductPrice]),
        FILTER(Dim_Product, Dim_Product[ProductKey] = EARLIER(Fact_Sales[ProductKey]))
    )
)
```
Format as Currency

### Total Cost
```
Total Cost = 
SUMX(
    Fact_Sales,
    Fact_Sales[OrderQuantity] * 
    CALCULATE(
        MAX(Dim_Product[ProductCost]),
        FILTER(Dim_Product, Dim_Product[ProductKey] = EARLIER(Fact_Sales[ProductKey]))
    )
)
```
Format as Currency

### Total Profit
```
Total Profit = [Total Sales] - [Total Cost]
```
Format as Currency

### Profit Margin
```
Profit Margin = DIVIDE([Total Profit], [Total Sales])
```
Format as Percentage

### YoY Sales Growth
```
YoY Sales Growth = 
VAR CurrentYear = YEAR(MAX(Dim_Calendar[Date]))
VAR CurrentYearSales = [Total Sales]
VAR PreviousYearSales = 
    CALCULATE(
        [Total Sales],
        YEAR(Dim_Calendar[Date]) = CurrentYear - 1,
        ALL(Dim_Calendar)
    )
RETURN
    DIVIDE(CurrentYearSales - PreviousYearSales, PreviousYearSales)
```
Format as Percentage

### Total Orders
```
Total Orders = DISTINCTCOUNT(Fact_Sales[OrderNumber])
```
Format as Whole Number

### Return Rate
```
Return Rate = 
VAR TotalReturns = SUM(Dim_Returns[ReturnQuantity])
VAR TotalOrders = [Total Orders]
RETURN
    DIVIDE(TotalReturns, TotalOrders)
```
Format as Percentage

### Average Order Value
```
Average Order Value = DIVIDE([Total Sales], [Total Orders])
```
Format as Currency

### AOV Target
```
AOV Target = 950
```
Format as Currency

### AOV KPI (for KPI visualization)
```
AOV KPI = 
CALCULATE(
    DIVIDE([Total Sales], [Total Orders]),
    ALLSELECTED(Dim_Calendar)
)
```
Format as Currency
