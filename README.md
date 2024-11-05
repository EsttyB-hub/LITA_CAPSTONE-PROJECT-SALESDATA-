# LITA_CAPSTONE_PROJECT_SALESDATA

[Project Overview](Project-Overview)

[Data Analyzed](Data-Analyzed)

[Project Objective](Project-Objective)

[Key Metrics](Key-Metrics)

[Data Sources](Data-Sources)

[Tools and Method used](Tools-and-Method-used)

[Exploratory Data Analysis](Exploratory-Data-Analysis)

[Data Analysis and Inference](Data-Analysis-and-Inference)

[Conclusion](Conclusion)

## Project Overview

This project aims at analyzing the sales performance of a retail store. It is meant to uncover key insights such as top-selling products, regional performance and monthly sales trend.

## Data Analyzed

The datasets used for this project include the following:
- OrderID: This relates to individual product in each year, it helps to identify the frequency at which a particular product is being offered for sale in a particular year.
- CustomerID: This is distinct to each customer and used to differntiate individual customer to a particular product.
- Product: This is the item being offered for sale.
- Region: It covers a particular geographical location where the product is being offered for sale.
- Order Date: This refers to the period that a particular product is offered for sale.
- Quantity: It symbolizes the number of each product being offered for sale.
- Unit Price: It is the amount at which a quantity of a particular product is being offered for sale.
- Total revenue: This aggregates the total sales of the products sold.

## Project Objective

The project emphasizes on achieving the following goals:
- Total sales by Product: This is achieved by calculating the total sales of each product in a particular period.
- Total sales by region: This shows the total sales generated in each region at a particular period.
- Total sales per month/year: This reflects the total sales generated on the products on a monthly/ yearly basis.

## Key Metrics

- Average sales per product: Average total revenue of different classes of products in each periodi.e using Averageif function argument box to apply the formula . This reflects the average sales of the products in that region.
- Total revenue by region: Sum of the total revenue grouped by each region i.e using Sumif function argument box to apply the formula. This shows the total revenue generated in that region.

## Data Sources

The primary source of this data considering is Capstone Project and this is an open source data which can be downloaded freely from an Open source online such as Kaggle or any other data repository site. 

## Tools and Method used

The tools and method used in this project analysis include:
1. Excel: Using Excel formulas to clean the data and to calculate the key metrics.
2. Pivot table: where the project is summarised in an understandable manner.
3. SQL: where queries are written and validated to extract key insights.
4. GitHub: For Portfolio building, where the report is being recorded.
5. Power BI: This is used for data visualization of the insights found in Excel & SQL.

## Exploratory Data Analysis

This is where the exploration of data takes place to answer some questions such as:
- What is the overall Sales trend?
- Which of the product performs the best?
- Which of the region recorded the highest sales?
- Which Year recorded the highest sales?


## Data Analysis and Inference

This is where we include some basic line of codes, functions or queries used in analyzing the data.

## Excel 

### Metrics such as Total Revenue for each Region, Average Revenue for each product, the lowest and highest revenue.

![Screenshot (131)](https://github.com/user-attachments/assets/d2e4be33-3729-4f3e-8c7f-56bbd12b4844)

## Pivot Table

### 1. Total sales by product

![Screenshot (129)](https://github.com/user-attachments/assets/42195950-347c-4bf4-ad6e-06d7d0969cc4)

### 2. Total sales by Region

![Screenshot (122)](https://github.com/user-attachments/assets/e057d7a5-1d08-436f-8369-ef11059ff7c5)


### 3. Total Sales per year and month

![Screenshot (126)](https://github.com/user-attachments/assets/ff190dbf-76a0-40b5-945d-f846ddcd60b6)

![Screenshot (127)](https://github.com/user-attachments/assets/3a26bfcf-f6a4-414a-8fd4-d1db8deac766)

![Screenshot (130)](https://github.com/user-attachments/assets/f063d898-29cf-4fc4-9ccd-48f9a5cd13c0)


### 4. Average sales per product

![Screenshot (123)](https://github.com/user-attachments/assets/d8dcf629-a9f9-47da-8d9b-fe44e4644ba2)

### 5. Top Performing product

![Screenshot (125)](https://github.com/user-attachments/assets/68486201-c7c7-4eb1-b5f7-7a5f524de580)

### 6. Top 5 Customers

![Screenshot (136)](https://github.com/user-attachments/assets/c025bb1a-df4f-4990-8dfc-b35cbd42e0d2)

### 7. Products sold in the last quarters in 2023 & 2024

![Screenshot (134)](https://github.com/user-attachments/assets/9f664741-a57d-4707-8909-f515d573a0ec)

![Screenshot (133)](https://github.com/user-attachments/assets/eb898072-db59-45ee-849f-d41a8a6c9f98)


## SQL
``` SQL
create database Capstone_Project

select * from [dbo].[LITA Capstone-Dataset]

---retrieving the total sales for each product category---

select Product, sum(Total_Revenue) as Total_Sales
from [dbo].[LITA Capstone-Dataset]
group by Product;

--Number of sales transaction in each region--

select Region, count (*) as Sales_Transaction
from [dbo].[LITA Capstone-Dataset]
group by Region

--Highest-selling product by total sales value--

select Top 1 Product, SUM (Total_Revenue) as Total_Sales
from [dbo].[LITA Capstone-Dataset] 
group by Product

--Total Revenue per product--

select Product, SUM (Total_Revenue) as Total_Revenue
from [dbo].[LITA Capstone-Dataset] 
group by Product

--- calculate monthly sales totals for the current year---

SELECT Month(OrderDate) AS Month,
    SUM(Sales) AS MonthlySalesTotal
FROM SalesData WHERE YEAR(OrderDate) = 2024
GROUP BY Month(OrderDate)
ORDER BY Month

--Top 5 Customers by total purchase amount--

select Top 5 Customer_Id, SUM (Total_Revenue) as Total_Purchase
from [dbo].[LITA Capstone-Dataset] 
group by Customer_Id

----identify products with no sales in the last quarter.---
SELECT Product FROM salesdata
GROUP BY Product
HAVING SUM(CASE 
WHEN OrderDate BETWEEN '2024-06-01' AND '2024-08-31' 
THEN 1 ELSE 0 END) = 0
```

## Power BI VISUALIZATION

This is where the visualization takes place on the analysis done in Excel, Pivot & SQL and showing the Sales overview, top performing product and Regional breakdown among others.

![Screenshot (120)](https://github.com/user-attachments/assets/d9dfddee-738d-4c32-a278-dac6fb3d8141)


### Inference

- Sales Overview: It was discovered that the sales decline in Year 2024 with N109,570 lower than the revenue for the year 2023. In the last quarter of 2023, 3 products out of 6 were not purchased by the customers, these products include; Shirt, Hat an Shoes. Also in the last quarter in the year 2024, only hat and shoes were sold leaving Jacket, Shirt, Gloves and socks unsold. There are many factors that might have caused the decline in revenue, it can be that there was a change in customer taste, rise in competition and this has to be addressed by having sales promotion and avertisement to increase the revenue.

- Top performing products: By using the exel & SQL, the product "Shoes" was considered to be the top performing product base on the total revenue it generated which is higher than the other products.

- Regional Breakdown:
  1. East: In Year 2023, the total revenue generated was N393,945. However, there was a significant decline in 2024 with the  total revenue coming down to N91,980 representing 62% decrease. This decrease in revenue may suggest increase in competitors, difficulty in maintaining sales, economic conditions and/or market contraction. This indicate a potential area of concern which requires immediate attention. The company should attempt to increase sales & marketing techniques, reaching more customers, maintaining good relationship with the current and new customers, create special incentives, develop a public reputation for quality and expertise, offer discount, rebates and coupons, review the current prices of products among others.
  2. North: There was a notable increase in the total turnover from N143,960 in Year 2023 to N243,040 in Year 2024 with 26% increase. The company should invest more products in this region to better boost the total revenue.
  3. South: This region also performs well in generating revenue to the company. However, there was a slight decrease in revenue generated as decrease of N33,820 was recorded representing 4% decrease. This is not a major challenge but the reason for the drop in revenue have to be investigate so as to maintan/increase the revenue in a subsequent year.
  4. West: There is a significant increase in the revenue recorded in this region as N127,135 increase was recorded in between 2023 & 2024. It might be that the company is a monopoly. This need to be maintain for the region to keep on recording increase in revenue.
  

### Conclusion

Based on the data sets analyzed for year 2023 and 2024, it was confirmed that the company recorded a declined revenue generation in South and most importantly East which raised a great concern. The company is advised to do a market survey so as to understand the customers' preference, improve/maintain the product quality and make a strategy plan on how to deliver and capture the heart of the customers. The company is also expected to maintain good relationship with the customers in the remaining region that recorded increase in revenue which are North and West as this will help to keep on recording increased revenue in future years.




