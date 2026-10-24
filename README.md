# Sales Performance Dashboard - Databuzz October 2026 Challenge

## Overview
This Power BI dashboard provides comprehensive sales performance analysis with executive-level KPIs and regional insights. Built for the Databuzz Ltd October 2026 Power BI Challenge.

## Dashboard Pages

### Page 1: Executive Overview
High-level business metrics for executive decision-making.

![Executive Overview](screenshots/Screenshot%202026-10-25%20033733.png)

**Visuals:**
- Top Row: 3 KPI Cards (Total Sales, Total Profit, YoY Sales Growth)
- Middle Left: Line Chart - Sales Trend Over Time
- Middle Right: Bar Chart - Top 5 Products by Profit
- Bottom Left: KPI - Average Order Value vs Target ($950)
- Bottom Right: Line Chart - Orders Trend Over Time
- Right Side: Slicers (Year, Region)

**Key Metrics:**
- Total Sales: $24.98M
- Total Profit: $10.51M
- Profit Margin: 42.08%
- YoY Growth: 171.98%
- Average Order Value: ~$992 (Target: $950)

### Page 2: Regional & Product Analysis
Geographic and product-level performance analysis.

![Regional & Product Analysis](screenshots/Screenshot%202026-10-25%20033750.png)

**Visuals:**
- Top Row: 4 Cards (Total Sales, Total Profit, Total Orders, Profit Margin)
- Bottom Left: Bar Chart - Sales by Territory Group
- Bottom Right: Donut Chart - Sales by Product Category
- Right Side: Slicers (Category, Country)

## Data Model

### Star Schema Architecture
- **Fact Tables:** Fact_Sales, Fact_Returns
- **Dimension Tables:** Dim_Customer, Dim_Date, Dim_Product, Dim_ProductCategory, Dim_ProductSubcategory, Dim_Territory
- **Measures Table:** Dedicated table for DAX measures

### Relationships
All relationships set to bidirectional filtering (Both) for flexible analysis:
- Dim_Date[Date] → Fact_Sales[OrderDate]
- Dim_Date[Date] → Fact_Returns[ReturnDate]
- Dim_Product[ProductKey] → Fact_Sales[ProductKey]
- Dim_Customer[CustomerKey] → Fact_Sales[CustomerKey]
- Dim_Territory[TerritoryKey] → Fact_Sales[TerritoryKey]
- Dim_ProductCategory[ProductCategoryKey] → Dim_Product[ProductCategoryKey]
- Dim_ProductSubcategory[ProductSubcategoryKey] → Dim_Product[ProductSubcategoryKey]

Dim_Date marked as Date Table with Date column for time intelligence functions.

## DAX Measures

### Core Measures
- **Total Sales:** SUMX with CALCULATE(MAX) for product price lookup
- **Total Cost:** SUMX with CALCULATE(MAX) for product cost lookup
- **Total Profit:** Total Sales - Total Cost
- **Profit Margin:** DIVIDE(Total Profit, Total Sales)
- **YoY Sales Growth:** Year-over-year growth using YEAR() function
- **Total Orders:** DISTINCTCOUNT of OrderNumber
- **Return Rate:** DIVIDE(Total Returns, Total Orders)
- **Average Order Value:** DIVIDE(Total Sales, Total Orders)
- **AOV Target:** Static target value of $950
- **AOV KPI:** AOV measure optimized for KPI visualization

## Key Challenges & Solutions

### Challenge 1: Product Price/Cost in Dimension Table
ProductPrice and ProductCost columns exist in Dim_Product, not Fact_Sales.

**Solution:** Used CALCULATE with MAX and FILTER to look up values per row context within SUMX iteration.

### Challenge 2: KPI Visual Showing Blank
Average Order Value measure returned BLANK when used with trend axis.

**Solution:** Created AOV KPI measure with ALLSELECTED(Dim_Calendar) to remove problematic date filter context.

### Challenge 3: YoY Sales Growth Showing 0%
SAMEPERIODLASTYEAR and DATEADD functions not working with date table structure.

**Solution:** Used YEAR() function on Date column with explicit year comparison. Result: 171.98% growth (accurate based on multi-year data).

## Business Insights

1. **Strong Growth:** 171.98% YoY sales growth indicates significant business expansion
2. **Healthy Margins:** 42.08% profit margin suggests strong pricing strategy
3. **AOV Opportunity:** Current AOV ($850) below target ($950) - opportunity for upselling
4. **Product Performance:** Mountain-200 Black, 48 is top profit contributor
5. **Regional Focus:** Territory analysis identifies high-performing regions for investment

## Files Included

- **Sales_Dashboard.pbix** - Power BI Dashboard file
- **Insights_and_Methodology.txt** - Detailed documentation with methodology
- **documentation/** - Build instructions and DAX measures
  - measures.md - DAX measure formulas
  - page1.md - Page 1 build instructions
  - page2.md - Page 2 build instructions
- **data/** - Source CSV files
- **screenshots/** - Dashboard screenshots

## Technical Details

- **Tool:** Power BI Desktop
- **Data Model:** Star schema for optimal performance
- **Relationships:** Bidirectional for flexible filtering
- **Date Table:** Properly marked for time intelligence functions
- **Measures:** CALCULATE, FILTER, EARLIER for complex lookups
- **ALLSELECTED:** Used to handle KPI visualization context issues

## Submission

Challenge: Databuzz Ltd October 2026 Power BI Challenge
Email: chiranjeevi.kudupudi@databuzzltd.com
