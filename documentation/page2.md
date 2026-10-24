# Page 2 - Regional & Product Analysis

## Overview
This page focuses on regional performance and product-level insights.

## Add Visuals

### Top Row: 4 Cards
1. Click **Card** visualization
2. Drag `[Total Sales]` to card
3. Title: "Total Sales"
4. Format: Size 24pt, Navy Blue

5. Add another **Card**
6. Drag `[Total Profit]` to card
7. Title: "Total Profit"
8. Format: Size 24pt, Green

9. Add another **Card**
10. Drag `[Total Orders]` to card
11. Title: "Total Orders"
12. Format: Size 24pt, Dark Gray

13. Add another **Card**
14. Drag `[Profit Margin]` to card
15. Title: "Profit Margin"
16. Format: Size 24pt, Purple

### Bottom Left: Sales by Territory (Bar Chart)
1. Click **Clustered bar chart**
2. Drag `Dim_Territory[Group]` to Axis
3. Drag `[Total Sales]` to Values
4. Sort by Total Sales descending
5. Title: "Sales by Territory Group"

### Bottom Right: Sales by Product Category (Donut Chart)
1. Click **Donut chart** visualization
2. Drag `Dim_ProductCategory[CategoryName]` to Legend
3. Drag `[Total Sales]` to Values
4. Title: "Sales by Category"
5. Format: Add percentage labels, distinct colors

## Add Slicers (Right Side)
1. Click **Slicer**
2. Drag `Dim_ProductCategory[CategoryName]` to slicer
3. Add another slicer with `Dim_Territory[Country]`
4. Position slicers on right side

## Format the Page
- Apply consistent color theme (Navy Blue, White, Light Gray)
- Add white background
- Ensure proper spacing between visuals
