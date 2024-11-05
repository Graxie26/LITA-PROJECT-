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

```SQL

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
 
 
 
 
 







