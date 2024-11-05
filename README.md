## Project Overview
This project contains a comprehensive analysis of sales data across four regions, focused on understanding revenue trends, customer behavior, and key performance metrics. The project aims to identify insights that drive better decision-making in marketing, inventory management, and regional strategy.

## Project Significance
This sales data analysis project plays a crucial role in understanding and driving strategic growth across multiple regions. By analyzing detailed sales patterns, customer preferences, and revenue trends, the project enables businesses to make data-informed decisions on product distribution, inventory management, and marketing focus. With insights derived from this analysis, companies can identify top-performing products and regions, optimize resource allocation, and adapt quickly to changes in customer demand.

With increasing regional variation in consumer behavior, understanding each region's unique sales patterns allows businesses to refine their approach and better meet customer needs. Did you know? Companies that use data-driven strategies are 23 times more likely to acquire customers—highlighting the value of data in creating competitive advantages and sustainable growth.

This project empowers stakeholders with tools for effective decision-making and the potential to uncover trends that might otherwise go unnoticed, ensuring that every region can maximize its growth potential.

## Data Sources/ Data Generation
Capstone Sales Data: The primary dataset used for this analysis is the "Capstone Sales Data" file, containing detailed datapoints which include but not limited to product, orderdate, quantity and unit price. The dataset was generated from different region.

## Data Structure
The sales dataset employed for this analysis was structured (dataset was in a tabular form). 

## Data Description
The dataset contained the essential datapoints:

- OrderID: A unique identifier assigned to each individual transaction or order within the sales dataset
- CustomerID: A unique identifier assigned to each individual customer within the sales dataset
- Product: A specific item available for sale within the dataset
- Region: The geographical area or division where transaction was made
- Order Date: The specific date on which a transaction involving the buying or selling was made
- Quantity: The number of units sold for a given transaction
- Unit Price: The cost per single unit of a product sold, listed in the currency relevant to the dataset
- Revenue: The total monetary value generated from the sale

## Tools Used
- Microsoft Excel [Download Here](https://www.microsoft.com)
  The dataset was ingested, transformed, visualized, analysed and presented
1) For Data Cleaning: The capstone sales dataset was cleaned to ensure duplicates were removed and ensured all columns were properly
2) For Data Analysis: The capstone dataset was analyzed using Microsoft Excel, statistical measures and techniques were deployed over the dataset
3) For Data Visualization: Charts and graphs were deployed to summarize the dataset such as pivot tables, bar charts etc

- SQL- Structured Query Language for Querying of Data [Download Here](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)

- GitHub for Portfolio Building [Join Here](https://github.com/)
  
- Power BI(Business Intelligence) for Data Visualization [Download Here](https://www.microsoft.com)

## Data Cleaning and Preparation
The initial phase of the data cleaning and preparations performed the following actions;
1) Data loading and inspection
2) Handling missing variables
3) Data cleaning and formatting

## Exploratory Data Analysis
EDA involves exploring the dataset
1. Use of pivot tables to summarize total sales by product, region, and month
2. Use of SQL to query and 
- a)  retrieve the total sales for each product category.
- b) find the number of sales transactions in each region.
- c) find the highest-selling product by total sales value.
- d) calculate total revenue per product.
- e) calculate monthly sales totals for the current year.
- f) find the top 5 customers by total purchase amount.
- g) calculate the percentage of total sales contributed by each region.
- h) identify products with no sales in the last quarter.
3. Use of Power BI to create a dashboard that visualizes the insights found in Excel and SQL.
- The dashboard includes a sales overview, top-performing products, and regional breakdowns

## Data Analysis
#### Functions Used in Excel
```
AVERAGEIF, SUMIF
```
#### Query Used in SQL
```
- **Total Sales for Each Product Category**

SELECT PRODUCT, SUM(Quantity) AS total_sales
FROM [dbo].[Sales_Data]
GROUP BY Product
ORDER BY Total_sales DESC

SELECT PRODUCT, SUM(Quantity) AS total_sales
FROM [dbo].[Sales_Data]
GROUP BY Product
ORDER BY Total_sales
```

```
- **Number of Sales Transaction in Each Region**
SELECT Region, Count(Region) AS Number_of_sales
FROM [dbo].[Sales_Data]
GROUP BY Region
ORDER BY Number_of_sales desc
```

```
SELECT Region, Count(Region) AS Number_of_sales
FROM [dbo].[Sales_Data]
GROUP BY Region
ORDER BY Number_of_sales
```

```
- **Highest-Selling Product by Total Sales Value**
SELECT Top 1 Product, SUM(Quantity * UnitPrice) as TotalSalesValue
from [dbo].[Sales_Data]
Group by Product
order by TotalSalesValue desc
```

```
- **Highest-Selling Product by Total Sales**
SELECT Top 1 Product, SUM(Quantity) as TotalSales
from [dbo].[Sales_Data]
Group by Product
order by TotalSales desc
```

```
- **Total Revenue Per Product**
SELECT PRODUCT, SUM(UnitPrice*Quantity) AS total_revenue
FROM [dbo].[Sales_Data]
GROUP BY Product
```

```
- **Monthly Sales Totals for the Year 2023 & 2024**
SELECT MONTH(OrderDate) AS Month, 
       SUM(Quantity * UnitPrice) AS TotalRevenue
FROM [dbo].[Sales_Data]
WHERE YEAR(OrderDate) IN (2023, 2024)
GROUP BY MONTH(OrderDate)
ORDER BY Month
```

```
- **Monthly Sales Totals for the Current Year**
SELECT MONTH(OrderDate) AS Month, 
       SUM(Quantity * UnitPrice) AS TotalRevenue
FROM [dbo].[Sales_Data]
WHERE YEAR(OrderDate) IN (2024)
GROUP BY MONTH(OrderDate)
ORDER BY Month
```

```
-**Top 5 Customers by Total Purchase Amount**
SELECT Top 5 Customer_id, 
       SUM(Quantity * UnitPrice) AS Total_Purchase_Amount
FROM [dbo].[Sales_Data]
GROUP BY Customer_id
ORDER BY Total_Purchase_Amount DESC
```

```
- **Percentage of total sales contributed by each region**
WITH TotalSales AS (
    SELECT SUM(Quantity * UnitPrice) AS OverallTotalSales
    FROM [dbo].[Sales_Data]
),
RegionSales AS (
    SELECT Region, 
           SUM(Quantity * UnitPrice) AS RegionTotalSales
    FROM [dbo].[Sales_Data]
    GROUP BY Region
)
SELECT Region, 
       RegionTotalSales,
       (RegionTotalSales * 100.0 / OverallTotalSales) AS PercentageOfTotalSales
FROM RegionSales, TotalSales;
```

```
- **Products with no sales in the last quarter**
SELECT DISTINCT Product
FROM [dbo].[Sales_Data]
WHERE Product NOT IN (
    SELECT Product
    FROM [dbo].[Capstone_Sales_Data]
    WHERE OrderDate >= DATEADD(QUARTER, -1, GETDATE())
);
```

## Data Visualization & Inferences
- 1. AVERAGE SALES PER REGION

![Average Sales per Product](https://github.com/user-attachments/assets/2e515958-6894-4860-8ae4-9e476f80bf20)

Based on the analysis of Average Sales per Product, we can draw the following inferences:
- Top Performing Products: Gloves and Shirts have the highest average sales, with Gloves slightly leading at 8.33, followed closely by Shirts at 8.33 as well. This suggests that these two items are particularly popular or frequently purchased, potentially due to higher demand or seasonality.

- Moderate Performance: Hats also perform relatively well with an average sale of 8.00, indicating steady demand. Shoes, with an average sale of 7.25, are close in performance, suggesting they are also a popular choice among customers.

- Lower Performing Products: Socks and Jackets have lower average sales, with Jackets at the lowest (3.66) and Socks slightly higher (5.34). This might suggest these items are either less in demand or possibly seasonal items with less consistent sales.

- Recommendation for Focus: To maximize sales, focusing on maintaining the availability and potentially promoting high-performing products like Gloves and Shirts could be beneficial. For lower-performing items like Jackets, consider evaluating pricing strategies or bundling options to boost sales.




![Total Revenue per Region](https://github.com/user-attachments/assets/69808ea5-0a28-4781-b9d0-ef0baffb0f83)

