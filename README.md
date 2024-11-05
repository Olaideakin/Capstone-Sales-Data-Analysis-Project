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
    FROM [dbo].[Sales_Data]
    WHERE OrderDate >= DATEADD(QUARTER, -1, GETDATE())
);
```

## Data Visualization & Inferences

### 1. **AVERAGE SALES PER REGION**

#### Pivot Table
![Average Sales per Product](https://github.com/user-attachments/assets/2e515958-6894-4860-8ae4-9e476f80bf20)

#### **Inference**
Based on the analysis of Average Sales per Product, the following inferences are drawn:
- Top Performing Products: Gloves and Shirts have the highest average sales, with Gloves slightly leading at 8.33, followed closely by Shirts at 8.33 as well. This suggests that these two items are particularly popular or frequently purchased, potentially due to higher demand or seasonality.

- Moderate Performance: Hats also perform relatively well with an average sale of 8.00, indicating steady demand. Shoes, with an average sale of 7.25, are close in performance, suggesting they are also a popular choice among customers.

- Lower Performing Products: Socks and Jackets have lower average sales, with Jackets at the lowest (3.66) and Socks slightly higher (5.34). This might suggest these items are either less in demand or possibly seasonal items with less consistent sales.

#### **Recommendations**:
- To maximize sales, focusing on maintaining the availability and potentially promoting high-performing products like Gloves and Shirts could be beneficial.
- For lower-performing items like Jackets, consider evaluating pricing strategies or bundling options to boost sales.




### 2. TOTAL REVENUE PER REGION

#### Pivot Table
![Total Revenue per Region](https://github.com/user-attachments/assets/69808ea5-0a28-4781-b9d0-ef0baffb0f83)

#### **Inference**
Based on the Total Revenue by Region data, here are some key inferences:

- Highest Revenue: The South region has the highest total revenue, generating 927,820. This indicates strong sales performance and a significant customer base in the South, making it a crucial region for the business.

- Moderate Revenue: The East region follows with a total revenue of 485,925. While it's considerably lower than the South, it still represents a substantial share, suggesting steady sales activity in this area.

- Lower Revenue: The North and West regions show the lowest revenue, with 387,000 and 300,345 respectively. This might indicate lower demand or market potential in these areas, or it could signal an opportunity for targeted marketing efforts to boost sales.

#### **Recommendations:**
- South Region: Continue supporting and possibly expanding in the South, as it’s the top-performing region.
- East Region: Consider strategies to increase sales further in the East, as it has a promising revenue base.
- North and West Regions: Explore ways to improve sales in these regions, such as promotional activities, new product launches, or localized marketing, to increase their contribution to overall revenue.




### 3. **TOTAL SALES BY PRODUCT**

#### Pivot Table
![Total Sales per Product](https://github.com/user-attachments/assets/f3b45c56-6b47-4f73-b901-b5f4d3b600b4)

#### Chart
![Total Sales by Product1](https://github.com/user-attachments/assets/29fdb218-c0ec-4b26-8537-9cb0301d8881)

#### **Inference**
- Here are some observations and inferences based on the pivot table above

- Top-Selling Product: Hat is the highest-selling product, with a quantity of 15,929 units sold. This indicates strong demand and popularity, making it a key product in the sales portfolio.

- High Performers: Shoes, Shirt, and Gloves are also top performers, with sales quantities of 14,402, 12,388, and 12,369 respectively. These products have substantial sales, suggesting they are also popular and contribute significantly to overall revenue.

- Moderate Sales: Socks have a moderate sales quantity of 7,921 units, indicating a decent demand, though it’s lower than the high-performing products.

- Lowest-Selling Product: Jacket has the lowest total sales, with only 5,452 units sold. This may indicate lower demand or higher pricing, potentially making it a candidate for targeted promotions or bundling to boost sales.

#### **Conclusion**
- With a grand total of 68,461 units sold across all products, this breakdown allows for a focused approach in inventory management and marketing efforts to maximize overall sales.
  
#### **Recommendations**:
- Focus on High Performers: Continue supporting Hat, Shoes, Shirt, and Gloves, as they are the main contributors to total sales.
- Promote Lower-Performing Products: Consider promotional strategies for Jackets and possibly Socks to improve their sales performance.

  


### 4. **TOTAL SALES TRANSACTION IN EACH REGION**
#### Pivot Table
![Total Sales by Region](https://github.com/user-attachments/assets/22c509e3-7326-44aa-a175-ae7d7a2d36cb)

#### Chart
![Total Sales by Region1](https://github.com/user-attachments/assets/63e6e5e5-b4d6-4639-8201-3a6bee3c5d1b)

#### **Inference**

- Regional Performance: The South region leads in total sales quantity with 24,298 units sold, which is significantly higher than any other region. It accounts for approximately 35.5% of the total sales.

- Comparative Analysis: The East region follows as the second highest, with 20,361 units sold, making up about 29.7% of the total sales. In contrast, the West region has the lowest sales with 11,400 units, which represents only about 16.6% of the total. This indicates a disparity in sales performance across regions.

- Total Sales Context: The grand total of sales across all regions is 68,461 units. This figure highlights the overall volume of sales and serves as a benchmark for evaluating the performance of each region.

- Opportunity for Growth: The West region may present opportunities for growth or targeted marketing strategies to increase its sales, given its lower performance compared to the other regions.

- Market Focus: Given that the South and East regions account for a significant portion of total sales, they might be prioritized for future business strategies, promotions, or resource allocation to capitalize on their performance.

#### Conclusion
- Overall, the data suggests a strong market presence in the South and East regions, while the West region may require further investigation to understand its lower sales figures.



### 5. **COUNT OF SALES IN EACH REGION**
#### Pivot Table
![Count of Sales by Region](https://github.com/user-attachments/assets/06cf1336-b94b-4e01-9107-ca1bd3841715)

#### Chart
![Count of Sales by Region1](https://github.com/user-attachments/assets/e725cd38-67df-4c41-bcdf-f92e9afded73)

#### **Inference**
- Sales Volume Consistency: The total count of sales across all regions is 9,921 transactions. The number of sales is relatively consistent across the regions, with only slight variations in counts.

- Region Performance: The East region has the highest count of sales at 2,483 transactions, closely followed by North (2,481) and South (2,480). The West region has the lowest count at 2,477. This suggests that while the East has the highest transaction volume, the other regions are closely competitive in terms of the number of sales.

- Sales Engagement: The relatively uniform distribution of sales counts across the regions indicates that customer engagement is similarly strong, particularly in the North and South regions, which have nearly the same transaction counts.

- Comparison with Quantity Sold: When comparing these sales counts to the total sales quantity from the previous data (Sales Transaction per region), it appears that the East region, while having the highest count, also has a significant total sales quantity (20,361 units). This might suggest that while sales transactions are high, the average quantity per transaction varies between regions, with East possibly having higher average sales per transaction.

- Opportunity for Optimization: Since the West region has the lowest count of sales, there may be opportunities to analyze customer behavior and preferences in this area to boost transaction counts. Targeted marketing strategies could be beneficial to increase engagement and sales in this region.

#### Conclusion
Overall, the data suggests a strong level of engagement across all regions, with the East region standing out in transaction counts, indicating a potentially larger customer base or more effective sales strategies.





### 6. **TOTAL SALES BY MONTH**
#### Pivot Table
![Total Sales by Month](https://github.com/user-attachments/assets/86f5b115-b63f-48a2-ae29-edb04ad22aeb)

#### **Inference**
- Based on the total sales by month for the years 2023 and 2024,

- Overall Growth: There is a noticeable increase in total sales from 38,681 units in 2023 to 29,780 units in the first eight months of 2024, indicating a growth trajectory. This growth suggests an overall positive trend in sales performance year-over-year.

- Monthly Sales Patterns: In 2023, sales peaked in July (5,940 units), indicating strong mid-year performance, while the lowest sales occurred in May (994 units).
In 2024, January and February show strong sales (3,968 and 4,980 units, respectively), with March having the highest sales for that year so far (5,478 units). This month-to-month growth indicates increased customer activity or successful marketing efforts.

- Seasonal Trends: Sales in July and June in 2023 were particularly high, suggesting a possible seasonal trend where summer months drive higher sales. In contrast, sales in the early months of the year (January and February) show promising engagement in 2024.

- Quarterly Comparison: The sales for the first quarter of 2024 (January to March) indicate strong performance (around 14,426 units), which is significantly higher than the total sales for the same months in 2023 (about 10,923 units). This could indicate successful strategies in place or an expanding market.

- Potential for Q4: Given the sales figures for November and December in 2023, there is potential for strong performance in the fourth quarter of 2024, especially considering that holiday seasons typically drive up sales.

#### Conclusion
The data indicates a positive trend in total sales, with opportunities to optimize sales strategies around seasonal patterns and specific months that have historically low sales. Continued monitoring of these trends will be essential for forecasting and improving sales performance.

#### Recommendation
- Need for Analysis in Low Months: The notably low sales in May 2023 (994 units) and the decrease observed in July 2024 (2,480 units) warrant further investigation to understand the causes behind these dips and to develop strategies to boost sales during those periods.



### 7. **TOTAL REVENUE BY PRODUCT**
#### Pivot Table
![Total Revenue by Product](https://github.com/user-attachments/assets/728ecab8-1168-47af-a230-53206749d069)

#### **Inference**
- Top Revenue Generators: Shoes are the highest revenue-generating product, accounting for (Currency)613,380, which represents about 29.2% of the total revenue of (Currency)2,101,090. This indicates that shoes are likely the most popular or in-demand product among customers.

- Comparative Revenue Analysis: The shirt category follows as the second highest revenue contributor at (Currency)485,600, comprising approximately 23.1% of the total revenue. Together, shoes and shirts make up over half of the total revenue, highlighting their importance to the product lineup.

- Strong Performance of Clothing: The jacket ((Currency)208,230) and gloves ((Currency)296,900) categories also contribute significantly to overall revenue, indicating a robust performance in outerwear and accessories. The total for jackets and gloves combined ((Currency)505,130) is substantial, showcasing a potential market for seasonal clothing.

- Lower Revenue Products: Socks ((Currency)180,785) and hats ((Currency)316,195) have the lowest and moderate revenue levels, respectively. While they do contribute to total revenue, their figures are significantly lower compared to shoes, shirts, and gloves. This suggests a possible opportunity to enhance marketing strategies or promotions for these items to boost sales.

 #### Conclusion
 The analysis suggests that while several product categories are performing well, there is significant potential to optimize and expand upon the highest revenue-generating products, especially shoes and shirts, to further increase overall revenue.

 #### Recommendation
 - Potential for Product Focus: The data indicates that footwear and upper-body clothing items are primary revenue drivers. Retail strategies could be focused on promoting shoes and shirts more heavily, as they are already performing well.

- Inventory and Development Focus: Given the revenue contributions, the company may consider expanding the product lines of shoes and shirts, possibly by introducing new styles or variations to capture even more market share.


### 8.Other Analysis  
#### Average Revenue by Product
#### Pivot Table

![Average Revenue by Product](https://github.com/user-attachments/assets/28848088-fabc-44de-adc7-112a63e37fec)

#### Average Revenue by Region
#### Pivot Table

![Average Revenue by Region](https://github.com/user-attachments/assets/10a0071c-810e-4f6e-a5f1-6cfd08b392fd)


### POWER BI 
![Sales Data PowerBI Visuals](https://github.com/user-attachments/assets/86e09272-73b4-4ca3-8a97-857f499ace3a)

![Sales Data PowerBI Visuals2](https://github.com/user-attachments/assets/3dfde917-a181-40be-8715-fc8b874e67a8)



