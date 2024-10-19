# LITA-Capstone-Project 1
## Project Overview
This project aims to analyze the sales performance of a retail store. The analysis focuses on key metrics such as total sales, sales growth, best-selling products, and sales performance by region and month. The tools used include Excel for data exploration, SQL for data extraction and manipulation, and Power BI for data visualization and reporting.

### Goals:
- Analyze sales performance across products, regions, and months.
- Identify trends and patterns in sales data.
- Visualize key metrics for data-driven decision-making.

## Data Preparation in Excel

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
![Average total sales](https://github.com/sharifahstella/LITA-Capstone-Project/blob/main/averagesales.JPG)

- calculate metrics such as Total sales per each region
  
  ```
  =SUMIF(D:D,"North",H:H)

  ```

![Productt](https://github.com/sharifahstella/LITA-Capstone-Project/blob/main/Producttt.JPG)

- Categorising of units sold by category of high,Low and medium

i used a conditional function of Nested Ifs to find the category column

![Low](https://github.com/sharifahstella/LITA-Capstone-Project/blob/main/Low.JPG)

 - Used pivot tables to summarize

i) total sales by month.

![Monthly sales](https://github.com/sharifahstella/LITA-Capstone-Project/blob/main/monthly.JPG)

ii) total sales by product

![salesProduct](https://github.com/sharifahstella/LITA-Capstone-Project/blob/main/Region.JPG)

iii) total sales by region

![Monthly sales](https://github.com/sharifahstella/LITA-Capstone-Project/blob/main/region2.JPG)

iv) The Top 3 best selling products

![Top 3](https://github.com/sharifahstella/LITA-Capstone-Project/blob/main/best.JPG)

v) The Top 5 Customers by Total sales

![Top 3](https://github.com/sharifahstella/LITA-Capstone-Project/blob/main/cust.JPG)

vi) Total Units Sold Per Product

![Top 3](https://github.com/sharifahstella/LITA-Capstone-Project/blob/main/units.JPG)

- Also represented all my pivote tables with a bar graph,piechart and line graps to show the summary of monthly sales as shown below:
  
 i) Bar graph showing the Total sales by Region where by South had the highest sales

 ![bargraph](https://github.com/sharifahstella/LITA-Capstone-Project/blob/main/bargraphregio.JPG)

 ii) A pie chart to summarize also the Total sales sold by each product with the shoes having the best sales
 
  ![bargraph](https://github.com/sharifahstella/LITA-Capstone-Project/blob/main/prod.JPG)

 iii)  A line graph that shows the summary of sales monthly

 Used a slicer to give the monthly sales per year in the report 
 
  ![Line graph](https://github.com/sharifahstella/LITA-Capstone-Project/blob/main/high.JPG)

#### Summary of Key Findings

- Top-Selling Products: Used the Pivot Table and charts to identify Shoes,Shirt and Hat being the best 3 selling products with the most revenue generted.
- Regional Performance: Visualized South and East are contributing most to total sales and assess The other regions of West and North require more focus.
- Monthly Sales Trends: Identify feb and jul having the high sales based on the monthly totals in the year of 2023 while in the year 2024 we had jan and feb having the high total sales trending seasonally.
- Customer Insights: Tracked top 5 customers such as Cus1488,Cus1375,Cus1023	28,Cus1059,Cus1367 by Total sales  to support targeted marketing efforts.
- Low-Performing Products: Identified products with low sales such as Jacket and Socks in the past quarter using a combination of Pivot Tables and filters.
 
### 2.2 SQL Queries for Analysis 

- Retrieve the total sales for each product category

```
SELECT Product, SUM(TotalSales) AS TotalSales
FROM LITACapstoneDatasett
GROUP BY Product;

```
This query sums up the TotalSalesAmount for each product and groups the result by product name to get the total sales per product.Where by Shoes had the highest sales and socks with the least sales 

- Find the number of sales transactions in each region

```
SELECT Region, COUNT(OrderID) AS NumberOfSalesTransactions
FROM LITACapstoneDatasett
GROUP BY Region;

```
 This query counts the number of orders (transactions) based on OrderID and groups by Region of which each region has the same number of orders

- Find the highest-selling product by total sales value

```
SELECT  Product, SUM(TotalSales) AS TotalSales
FROM LITACapstoneDatasett
GROUP BY Product
ORDER BY TotalSales DESC
LIMIT 1;

```
This query sums up the TotalSales for each product, orders the result in descending order, and returns the top-selling product.Whereby i found out that the best selling product was shoes 

- Calculate total revenue per product

```
SELECT Product, SUM(TotalSales) AS TotalRevenue
FROM LITACapstoneDatasett
GROUP BY Product;

```
- Find the top 5 customers by total purchase amount

```
SELECT Customer_id, SUM(totalsales) AS TotalPurchaseAmount
FROM LITACapstoneDatasett
GROUP BY Customer_id
ORDER BY TotalPurchaseAmount DESC
Limit 5;

```

- Calculate the percentage of total sales contributed by each region

```
SELECT 
    Region,
    SUM(totalsales) AS region_total_sales,
    (SUM(totalsales) * 100 / (SELECT SUM(totalsales) FROM LITACapstoneDatasett)) AS percentage_of_total_sales
FROM 
    LITACapstoneDatasett
GROUP BY 
    Region
ORDER BY 
    percentage_of_total_sales DESC;

```
#### Summary
The queries provide extract various insights from sales data, including total sales, highest-selling products, top customers, and sales by region. These queries help identify:

- Products driving the highest revenue which is shoes 
- Regions contributing the most to sales which is south
- Top customers in terms of purchase amount.
- Sales trends by month and year.
This information can be used to make data-driven decisions on inventory, marketing, and customer retention strategies

