# Sales Performance Analysis for a Retail Store
## Project Overview
This project aims to analyze the sales performance of a retail store. The analysis focuses on key metrics such as total sales, sales growth, best-selling products, and sales performance by region and month. The tools used include Excel for data exploration, SQL for data extraction and manipulation, and Power BI for data visualization and reporting.

### Goals:
- Analyze sales performance across products, regions, and months.
- Identify trends and patterns in sales data.
- Visualize key metrics for data-driven decision-making.

## 1. Data Preparation in Excel

### 1.1 Data Overview

The sales data includes the following columns:

- Product: The name of the product sold.
- Region: The geographical location of the sale.
- OrderDate: The date of the transaction.
- Total Sales Amount: The total revenue from the sale.
- Quantity Sold: The number of sales sold.
- OrderID: unique identifier assigned to each individual order placed in a system.
- CustomerID: unique identifier assigned to each customer in a database
- Unit price: The number for each sale sold.

#### Data Example:

![sales data set](https://github.com/sharifahstella/LITA-Capstone-Project/blob/main/sales.JPG)

### 1.2 Data Cleaning

In Excel, i took the following steps to clean the data:

Handling missing values: Using filtering and ISBLANK() to identify and handle missing entries of which i did not find any missing value
Date format correction: Ensured all dates were formatted as Date.
Data types: Verified that all columns had appropriate data types (e.g., numbers for sales and quantities).

### 1.3 Metrics Calculated in Excel

Several key metrics were calculated using Excel formulas:

- calculate metrics such as average sales per product

Used AVERAGEIF() to calculate the average sales for each product

```
=AVERAGEIF(C:C,"shirt",H:H)

```
![Average total sales](https://github.com/sharifahstella/LITA-Capstone-Project1/blob/main/Average.JPG)

- calculate metrics such as Total Revenue per each region
  
  ```
  =SUMIF(D:D,"North",H:H)

  ```

![Productt](https://github.com/sharifahstella/LITA-Capstone-Project1/blob/main/sumif.JPG)

- Categorising of units sold by category of high,Low and medium

i used a conditional function of Nested Ifs to find the category column

![Low](https://github.com/sharifahstella/LITA-Capstone-Project/blob/main/Low.JPG)

 - Used pivot tables to summarize

i) Total sales by month.

![Monthly sales](https://github.com/sharifahstella/LITA-Capstone-Project1/blob/main/monthly.JPG)

ii) Total sales by product

![salesProduct](https://github.com/sharifahstella/LITA-Capstone-Project1/blob/main/salesproduct.JPG)

iii) Total sales by region

![Monthly sales](https://github.com/sharifahstella/LITA-Capstone-Project1/blob/main/regionsales.JPG)

iv) The Top 3 best selling products

![Top 3](https://github.com/sharifahstella/LITA-Capstone-Project1/blob/main/Tope.JPG)

v) Total Units Sold Per Product

![Top 3](https://github.com/sharifahstella/LITA-Capstone-Project1/blob/main/units.JPG)

- Also represented all my pivote tables with a bar graph,piechart and line graps to show the summary of monthly sales as shown below:
  
 i) Bar graph showing the Total sales by each Product where by Shoes had the highest sales

 ![bargraph](https://github.com/sharifahstella/LITA-Capstone-Project1/blob/main/bar.JPG)

 ii) A pie chart to summarize also the Total sales sold by each region with the south having the best sales
 
  ![bargraph](https://github.com/sharifahstella/LITA-Capstone-Project1/blob/main/pie.JPG)

 iii)  A line graph that shows the summary of sales monthly

 Used a slicer to give the monthly sales per year in the report 
 
  ![Line graph](https://github.com/sharifahstella/LITA-Capstone-Project1/blob/main/line2.JPG)

#### Summary of Key Findings

- Top-Selling Products: Used the Pivot Table and charts to identify Shoes,Shirt and Hat being the best 3 selling products with the most revenue generted.
- Regional Performance: Visualized South and East are contributing most to total sales and assess The other regions of West and North require more focus.
- Monthly Sales Trends: Identify feb and jul having the high sales based on the monthly totals in the year of 2023 while in the year 2024 we had jan and feb having the high total sales trending seasonally.
- Customer Insights: Tracked top 5 customers such as Cus1488,Cus1375,Cus1023	28,Cus1059,Cus1367 by Total sales  to support targeted marketing efforts.
- Low-Performing Products: Identified products with low sales such as Jacket and Socks in the past quarter using a combination of Pivot Tables and filters.
 
### 2. SQL Queries for Analysis 

- Retrieve the total sales for each product category

```
SELECT Product, SUM(TotalSales) AS TotalSales
FROM [dbo].[LITA Capstone Dataset]
GROUP BY Product;

```
 ![Line graph](https://github.com/sharifahstella/LITA-Capstone-Project1/blob/main/result1.PNG) 
 
This query sums up the TotalSalesAmount for each product and groups the result by product name to get the total sales per product.Where by Shoes had the highest sales and socks with the least sales 

- Find the number of sales transactions in each region

```
SELECT Region, COUNT(OrderID) AS NumberOfSalesTransactions
FROM [dbo].[LITA Capstone Dataset]
GROUP BY Region;

```

 ![Line graph](https://github.com/sharifahstella/LITA-Capstone-Project1/blob/main/result2.PNG)
 
 This query counts the number of orders (transactions) based on OrderID and groups by Region of which each region has the same number of orders

- Find the highest-selling product by total sales value

```
SELECT  Product, SUM(TotalSales) AS TotalSales
FROM [dbo].[LITA Capstone Dataset]
GROUP BY Product
ORDER BY TotalSales DESC
LIMIT 1;

```

 ![Line graph](https://github.com/sharifahstella/LITA-Capstone-Project1/blob/main/result3.PNG) 
 
This query sums up the TotalSales for each product, orders the result in descending order, and returns the top-selling product.Whereby i found out that the best selling product was shoes 

- Calculate total revenue per product

```
SELECT Product, SUM(TotalSales) AS TotalRevenue
FROM [dbo].[LITA Capstone Dataset]
GROUP BY Product;

```
 ![Line graph]()
 
 Calculates the total revenue for each product. It highlights top revenue-generating products, aiding in revenue optimization efforts.
 
- calculate monthly sales totals for the current year.
```
SELECT 
    YEAR(OrderDate) AS Year,               -- Extract the year
    MONTH(OrderDate) AS Month,             -- Extract the month
    SUM(Total_Sales) AS MonthlySales  -- Sum total sales for the month
FROM 
   [dbo].[LITA Capstone Dataset]
WHERE 
    YEAR(OrderDate) = YEAR(GETDATE())      -- Filter for the current year
GROUP BY 
    YEAR(OrderDate), MONTH(OrderDate)      -- Group by year and month
ORDER BY 
    Year, Month;                           -- Order by year and month

```

 ![Line graph](https://github.com/sharifahstella/LITA-Capstone-Project1/blob/main/result4.PNG)
 
Summarizes total monthly sales for the current year. This data can reveal seasonal trends and high-demand periods.

- Find the top 5 customers by total purchase amount

```
SELECT Customer_id, SUM(totalsales) AS TotalPurchaseAmount
FROM [dbo].[LITA Capstone Dataset]
GROUP BY Customer_id
ORDER BY TotalPurchaseAmount DESC
Limit 5;

```

 ![Line graph](https://github.com/sharifahstella/LITA-Capstone-Project1/blob/main/result5.PNG)
 
Identifies the top 5 customers by their purchase amounts. This helps in recognizing high-value customers and prioritizing loyalty initiatives.

- Calculate the percentage of total sales contributed by each region

```
SELECT 
    Region,
    SUM(totalsales) AS region_total_sales,
    (SUM(totalsales) * 100 / (SELECT SUM(totalsales) FROM [dbo].[LITA Capstone Dataset])) AS percentage_of_total_sales
FROM 
    [dbo].[LITA Capstone Dataset]
GROUP BY 
    Region
ORDER BY 
    percentage_of_total_sales DESC;

```

 ![Line graph]()
 
This is valuable for identifying dominant markets and potential expansion areas.

- Identify products with no sales in the last quarter
  
```
SELECT p.Product
FROM (SELECT DISTINCT Product FROM [dbo].[LITA Capstone Dataset]) p
LEFT JOIN [dbo].[LITA Capstone Dataset] s
    ON p.Product = s.Product
    AND s.OrderDate >= DATEADD(QUARTER, -1, GETDATE())
WHERE s.OrderID IS NULL;
```

 ![Line graph]()
 
Products Jacket, Shirt,socks and Gloves had no sales transactions within the last quarter, assisting in inventory and sales strategy adjustments to avoid overstocking low-demand items.

#### Key Insights

Challenge: Socks and Jacket have seen declining sales, particularly in specific regions, indicating potential issues with market alignment or demand. Furthermore, the data reveals Jacket, Shirt,socks and Gloves have not sold in the last quarter, suggesting possible inventory inefficiencies.

Opportunity: Using customer purchase patterns and identifying top-selling products such as Shoes,Shirt and Hat enables targeted marketing and personalized sales approaches. High-demand regions such as south and East can also benefit from increased inventory and targeted promotions to maximize revenue.

Outcome: The SQL-driven analysis provides a comprehensive sales view, informing business strategies and inventory planning to align with market demands. By visualizing insights from Excel and Power BI, the retail store can make informed decisions, ultimately optimizing performance and meeting customer needs effectively.

#### Summary
The queries provide extract various insights from sales data, including total sales, highest-selling products, top customers, and sales by region. These queries help identify:

- Products driving the highest revenue which is shoes 
- Regions contributing the most to sales which is south
- Top customers in terms of purchase amount.
- Sales trends by month and year.
This information can be used to make data-driven decisions on inventory, marketing, and customer retention strategies

## 3. Power BI

This project analyzes sales performance for a retail store, focusing on uncovering trends in product performance, regional sales, and monthly revenue. The insights derived will be showcased on an interactive Power BI dashboard to help the business make informed, data-driven decisions.

#### 3.1 Power BI Dashboard Components and Storytelling Insights

Created visuals such as line charts, bar charts, and tables, enabling detailed analysis with slicers to filter by Year.

 ![bargraph](https://github.com/sharifahstella/LITA-Capstone-Project1/blob/main/bp.PNG)
 
#### 3.2 Storytelling Outcomes

The Power BI dashboard provides a narrative-driven overview of sales performance. Insights drawn include:

- Best-Selling Products:Shoes,Shirt and Hat with the highest revenue contributions can be prioritized in stocking and promotion.
- Regional Performance: Key revenue-generating regions such as South and East can be targeted for expansion, while low-performing regions may require strategic interventions.
- Seasonal Trends: Monthly sales trends in the current Year guide inventory management, helping the store prepare for high-demand periods.
- Customer Loyalty: Recognizing top customers enables the business to foster loyalty and increase customer lifetime value.

By visualizing these metrics, the dashboard enables actionable insights that improve sales strategy, marketing efforts, and operational efficiency.


