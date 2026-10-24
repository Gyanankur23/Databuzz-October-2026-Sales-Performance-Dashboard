# Page 1 - Executive Overview

## Overview
This page provides high-level business metrics for executive decision-making.

## Add Visuals

### Top Row: 3 KPI Cards
1. Click **Card** visualization
2. Drag `[Total Sales]` to card
3. Format: Size 28pt, Navy Blue
4. Title: "Total Sales"

5. Add another **Card**
6. Drag `[Total Profit]` to card
7. Format: Size 28pt, Green
8. Title: "Total Profit"

9. Add another **Card**
10. Drag `[YoY Sales Growth]` to card
11. Format: Size 28pt, Orange
12. Title: "YoY Sales Growth"

### Middle Left: Sales Trend Line Chart
1. Click **Line chart** visualization
2. Drag `Dim_Calendar[Date]` to Axis
3. Drag `[Total Sales]` to Values
4. Format: Add data labels, smooth line
5. Title: "Sales Trend Over Time"

### Middle Right: Top 5 Products by Profit
1. Click **Clustered bar chart**
2. Drag `Dim_Product[ProductName]` to Axis
3. Drag `[Total Profit]` to Values
4. In Visualizations pane → Data → Set "Top N" filter:
   - Filter type: Top N
   - Value: 5
   - By: `[Total Profit]`
5. Title: "Top 5 Products by Profit"

### Bottom Left: AOV KPI
1. Click **KPI** visualization
2. Drag `[AOV KPI]` to Value (use the AOV KPI measure, not regular AOV)
3. Drag `[AOV Target]` to Target
4. Drag `Dim_Calendar[Date]` to Trend axis
5. Format: Size 28pt, Green if above target, Red if below
6. Title: "Average Order Value vs Target"

### Bottom Right: Orders Trend Line Chart
1. Click **Line chart** visualization
2. Drag `Dim_Calendar[Date]` to Axis
3. Drag `[Total Orders]` to Values
4. Format: Add data labels, smooth line
5. Title: "Orders Trend Over Time"

## Add Slicers (Right Side)
1. Click **Slicer**
2. Drag `Dim_Calendar[Year]` to slicer
3. Add another slicer with `Dim_Territory[Region]`
4. Position slicers on right side

## Format the Page
- Apply consistent color theme (Navy Blue, White, Light Gray)
- Add white background
- Ensure proper spacing between visuals
