# LITA_CAPSTONE_PROJECT_SALESDATA

[Project Overview](Project-Overview)

[Data Analyzed](Data-Analyzed)

[Project Objective](Project-Objective)

[Key Metrics](Key-Metrics)

[Tools and Method used](Tools-and-Method-used)

[Visual Analysis and Inference](Visual-Analysis-and-Inference)

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
- Total sales per month: This reflects the total sales generated on the products on a monthly basis.

## Key Metrics

- Average sales per product: Average total revenue of different classes of products in each periodi.e using Averageif function argument box to apply the formula . This reflects the average sales of the products in that region.
- Total revenue by region: Sum of the total revenue grouped by each region i.e using Sumif function argument box to apply the formula. This shows the total revenue generated in that region.

## Tools and Method used

The tools and method used in this project analysis include:
1. Excel: Using Excel formulas to clean the data and to calculate the key metrics.
2. Pivot table: where the project is summarised in an understandable manner.
3. SQL: where queries are written and validated to extract key insights.
4. GitHub: For Portfolio building, where the report is being recorded.
5. Power BI: This is used for data visualization of the insights found in Excel & SQL.

## Visual Analysis and Inference

## Excel 

### Metrics such as Total Revenue for each Region, Average Revenue for each product, the lowest and highest revenue.

![Screenshot (111)](https://github.com/user-attachments/assets/1761b434-a2b9-4078-bcef-5084aa01744a)

## Pivot Table

### 1. Total sales by product

![Screenshot (83)](https://github.com/user-attachments/assets/a26ffc45-99e0-453c-9fbe-89211cc05043)

### 2. Total sales by Region

![Screenshot (84)](https://github.com/user-attachments/assets/ac27b920-98d7-4b25-9eab-22aef8e55977)

### 3. Total Sales per month

![Screenshot (87)](https://github.com/user-attachments/assets/0b793aed-6a46-4fc4-a898-036c3c09494b)

![Screenshot (88)](https://github.com/user-attachments/assets/900d9f1d-2537-4aed-89ab-3ed103d7b3c6)

![Screenshot (96)](https://github.com/user-attachments/assets/c1527c80-b187-4de6-8619-d35107387ebb)

### 4. Average sales per product

![Screenshot (98)](https://github.com/user-attachments/assets/5ec01ce0-eb2b-4e3d-8bd0-7c2796d18d94)

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


--Monthly sales total for the current year--

select SUM (*) as Monthly_Sales
from [dbo].[LITA Capstone-Dataset] 
where OrderDate = '2024'

--
select MONTH (OrderDate) As month, SUM(*) As Total_Sales
from [dbo].[LITA Capstone-Dataset]  
where Year = '2024'
group by month (OrderDate)

--Top 5 Customers by total purchase amount--

select Top 5 Customer_Id, SUM (Total_Revenue) as Total_Purchase
from [dbo].[LITA Capstone-Dataset] 
group by Customer_Id

---Percentage of total sales in each region---

select Region, % (Total_Revenue) as TotalSales_Percentage
from [dbo].[LITA Capstone-Dataset]
group by Region


--- Product with no sales in the last quarter---

select product, nill (Total_Revenue) as No_Sales
from [dbo].[LITA Capstone-Dataset]
group by Product
```

## Power BI VISUALIZATION

This is where the visualization takes place on the analysis done in Excel, Pivot & SQL and showing the Sales overview, top performing product and Regional breakdown among others.

![Screenshot (120)](https://github.com/user-attachments/assets/e9ec30e0-a698-4f8e-8fbd-a6b562de38cb)


### Inference

- Sales Overview: It was deduced that the sales decline in Year 2024 with N109,570 lower than the revenue for the year 2023. There are many factors that might have caused the decline in revenue, it can be that there was a change in customer taste, rise of competition and this has to be addressed by having sales promotion and avertisement to increase the revenue.

- Top performing products: By using the exel & SQL, the product "Shoes" was considered to be the top performing product base on the total revenue it generated which is higher than the other products.

- Regional Breakdown:
  1. East: In Year 2023, the total revenue generated was N393,945. However, there was a significant decline in 2024 with the  total revenue coming down to N91,980 representing 62% decrease. This decrease in revenue may suggest increase in competitors, difficulty in maintaining sales and/or market contraction. This indicate a potential area of concern which requires immediate attention.
  2. North: There was a notable increase in the total turnover from N143,960 in Year 2023 to N243,040 in Year 2024 with 26% increase. The company should invest more products in this region to better boost the total revenue.
  3. South: This region also performs well in generating revenue to the company. However, there was a slight decrease in revenue generated as decrease of N33,820 was recorded representing 4% decrease. This is not a major challenge but the reason for the drop in revenue have to be investigate so as to maintan/increase the revenue in a subsequent year.
  4. West: There is a significant increase in the revenue recorded in this region as N127,135 increase was recorded in between 2023 & 2024. It might be that the company is a monopoly. This need to be maintain for the region to keep on recording increase in revenue.
  

### Conclusion

Based on the data sets analyzed for year 2023 and 2024, it was confirmed that the company recorded a declined revenue generation in South and most importantly East which need to be addressed so as to improve the total revenue in the future. The company is advised to do a market survey so as to understand the customers' preference, improve/maintain the product quality and make a strategy plan on how to deliver and capture the heart of the customers.




