## LITA-PROJECT 1 

INCUBATOR HUB: THIS REPOSITORY CONTAINS DETAILED ANALYSIS OF THE SALES PERFORMANCE OF A RETAIL STORE, USING EXCEL SHEET, SQL, POWERBI FOR VISUALIZATION.

### PROJECT TITLE: SALES PERFORMANCE ANALYSIS

### PROJECT OVERVIEW.


The aim of this project is to analysis the sales performance of a retail store by exploring sales data to cover key insight. It also focus on sales data such as sales transaction, product category, regional sales transaction..

### Data sources


The primary of this data used is  LITA Capstone Dataset.xlsx…

### Tools
---
- Microsoft Excel:
  1. For data cleaning
  2. For Analysis
  3. For Data Visualization


- SQL (Stuctured Query Language)
  1. To retrieve and analysis
  2. To manipulate the data set
  3. To create an amazing dashboard content

### Data Cleaning

 1. To create an insight found in excel & Sql
 2. To overview the sales by transformating
 3. To visualize and report data

### Data cleaning 
---

- Sorting & removing of duplicate records on the excel sheets
- Filter the headers column

Below is the cleansed data 
![CustomerData](https://github.com/user-attachments/assets/ddba7546-798e-4d19-916a-f7dbfd9e3e70)

And here follows the barchart on the customer data sheet
![CustomerData Barchart](https://github.com/user-attachments/assets/0cf0b257-fb7e-4054-8a57-b4dbec6bad37)

![Pivot Table customerDate](https://github.com/user-attachments/assets/8ff12378-cff4-4ad1-ae84-9b5a2535c3ac)

### Exploratory Data Analysis
This includes Line some lines of code or queries

SQL

SELECT * FROM TABLE

----RETRIEVE THE TOTAL SALES FOR EACH PRODUCT CATEROGY-----
SELECT SUM(Total_Sales) AS Total_Revenue FROM SalesData;

------FIND THE NUMBER OF SALES TRANSACTIONS IN EACH REGION---
SELECT Region, SUM(Total_Sales) AS Total FROM SalesData
GROUP BY Region;

-----FIND THE HIGHEST-SELLING PRODUCT BY PRODUCT BY TOTAL SALES VALUE----
SELECT TOP 5 Product, SUM(Total_Sales) AS Total_Product_Sales
 FROM SalesData
 GROUP BY Product
 ORDER BY Total_Product_Sales DESC;

 -----CALCULATE TOTAL REVENUE PER PRODUCT----
 SELECT Product, AVG(Total_Sales) AS Average_Sales_Per_Product
  FROM SalesData
  GROUP BY Product;

  -----CALCULATE MONTHLY SALES TOTAL FOR THE CURRENTS YEAR----
SELECT DATEPART(YEAR, OrderDate) AS Year, SUM(Total_Sales) AS Total_Yearly_Sales
 FROM SalesData
 GROUP BY DATEPART(YEAR, OrderDate);

 ----FIND THE TOP 5 CUSTOMERS BY TOTAL PURCHASE AMOUNT------
 SELECT CUSTOMER_ID, SUM(Total_Sales) AS Totalsales from [dbo].[SALESDATA]
  GROUP BY Customer_id
  ORDER BY TotalSales desc;


 --------IDENTIFY PRODUCTS WITH NO SALES IN THR LAST QUARTER------
	   SELECT DISTINCT Product FROM [dbo].[SALESDATA]
	   WHERE product Not In (select product from [dbo].[SALESDATA]
	   Where OrderDate >= dateadd (quarter, -1, getdate ()) ) 
    
    [CustomerDate SQL](https://github.com/user-attachments/assets/81e95e60-9c60-4416-8ecc-b64dd859effc)

### Visualization on PowerBi
 ---
 Importing the data from the excel sheet to the powerbi 
 Follow by cleaning and sorting down to the visuals
 
 ![Screenshot (70)](https://github.com/user-attachments/assets/884f6d8d-211d-4c18-a90d-2dd3e225b9f1)





 ### LITA-PROJECT2

## INCUBATOR HUB: This repository contains a comprehensive analysis of aims to generate insights into the sales performance of a sales data. Using Excel, SQL & PowerBI for analysis, report & visualization.

### Project Title: Customer Data

### Project Overview
---
This project aims to analysis customer data for subsciption service as well as identify the segment and trends. The goal is to understand the customer behavior, track subscription types & identify key trends.

### Data sources

The primary sorce of tis data is [LITA Capstone Dataset.xlsx](https://github.com/user-attachments/files/17638564/LITA.Capstone.Dataset.xlsx)

### Tools & Technologies
---
- Microsoft Excel:
  1. For data analysis & visualization.
  2. For summary of the data set
  3. For creating charts & reports.

  - Structured Query Language
    1. To retrieve and analyze data.
    2. To manage and manipulate data.
    3. To create queries and modify data.
       
       - PowerBi:
         1. For data visualization
         2. For data modeling
         3. For creating amazing insight on the dashboard.
        
         ### Data Cleaning
         ---
 - Identify the duplicate in the column
 ![Cleansed Salesdata](https://github.com/user-attachments/assets/087d0cbf-86b4-4263-bf00-1c38e8a65a13)
-  Filter the column headers
-  Adding column to generate the subscription duration
  ![Screenshot (71)](https://github.com/user-attachments/assets/65b99101-2c8c-4b5e-bfd2-3c704bd009b7)

![BarChart CustomerData](https://github.com/user-attachments/assets/23066a9a-f102-4779-8566-cb4b64cf9a33)


![Pivot Table customerDate](https://github.com/user-attachments/assets/6efcda45-1c0c-49a6-83fc-9853e820354f)

### Data Analysis Exploratory
---
This part includes lines of code or queries
SELECT * FROM [dbo].[LITA PJ ]

---Retrieve the total number of customers from each region.---
SELECT Region, COUNT(CustomerID) AS Total_No_of_Customers
FROM [dbo].[LITA PJ ]
GROUP BY Region

---Find the most popular subscription type by the number of customers---
SELECT SubscriptionType,COUNT(CustomerID)AS NO_Of_Customers
FROM [dbo].[LITA PJ ]
GROUP BY SubscriptionType

--Find customers who canceled their subscription within 6 months----
SELECT CustomerName,Canceled,SubscriptionStart
FROM [dbo].[LITA PJ ]
WHERE Canceled =0 AND MONTH(SubscriptionStart) BETWEEN 1 AND 6

---Calculate the average subscription duration for all customers----
SELECT Count(CustomerID) As
All_Customers,AVG(DATEDIFF(DAY,SubscriptionStart,SubscriptionEnd)) AS
Average_Subscription_Duration
FROM [dbo].[LITA PJ ]
WHERE SubscriptionEnd IS NOT NULL

----Find customers with subscriptions longer than 12 months.DATEDIFF---
SELECT CustomerName,SubscriptionType,SubscriptionStart,SubscriptionEnd
FROM [dbo].[LITA PJ ]
WHERE DATEDIFF(MONTH,SubscriptionStart,SubscriptionEnd) >=12

--- Calculate total revenue by subscription type---
SELECT SubscriptionType,SUM(Revenue) AS Total_Revenue
FROM[dbo].[LITA PJ ]
GROUP BY SubscriptionType

---Find the top 3 regions by subscription cancellations---
   SELECT TOP 3 Region,Canceled
   FROM [dbo].[LITA PJ ]

---Find the total number of active and canceled subscriptions---
SELECT SUM( CASE WHEN Canceled = 0 THEN 1 ELSE 0 END) AS ActiveSubscriptions,
       SUM (CASE WHEN Canceled = 1 THEN 1 ELSE 0 END) AS CanceledSubscriptions
       FROM [dbo].[LITA PJ ]
       GROUP BY CustomerID

![Screenshot (75)](https://github.com/user-attachments/assets/8d4a5b33-7fa0-4c82-a582-20183dbb8474)

 ### PowerBi
 ---
 This includes data visualization, data cleaning and preparation

![CustomerData PowerBi](https://github.com/user-attachments/assets/1795b169-3b00-45ee-8117-f54e206f46ad)



