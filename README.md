# Sales-analytics-powerbi-project
**🔹 1. Project Overview**
Built an end-to-end Sales Analytics Dashboard using Microsoft SQL Server and Microsoft Power BI to analyze revenue trends, customer behavior, and regional performance.
The project focuses on transforming raw transactional data into meaningful business insights through data modeling, DAX calculations, and interactive visualizations.

**🔹 2. Tools Used**
1. SQL: Data extraction, joins, aggregations
2. SQL Server Management Studio: Query execution and database management
3. Power BI: Data modeling and dashboard development
4. DAX: KPI calculations and business logic

**🔹 3. Data Model**

   Designed a relational data model connecting:
   1. Sales Orders (SalesOrderHeader, SalesOrderDetail)
   2. Customer (Customer, Person, Store)
   3. Territory (SalesTerritory)
      
   Implemented proper relationships:
   1. Customer → Sales (1-to-many)
   2. Territory → Customer → Sales
      
   Resolved real-world challenges:
   
   1. Fixed many-to-many relationship issues
   2. Handled NULL values in customer data
   3. Built unified Customer Name logic (Person + Store)
   4. Prevented double-counting in revenue calculations

**🔹 4. SQL Analysis & Queries**

🔸 Top Customers by Revenue(Identifies top revenue-generating customers for targeted business strategies):

```sql
SELECT TOP 10 
    CustomerID, 
    SUM(TotalDue) AS Revenue
FROM Sales.SalesOrderHeader
GROUP BY CustomerID
ORDER BY Revenue DESC;
```
🔸 Monthly Sales Trend(Analyzes revenue trends over time to identify seasonality and growth patterns):

```sql
SELECT 
    YEAR(OrderDate) AS Year,
    MONTH(OrderDate) AS Month,
    SUM(TotalDue) AS Revenue
FROM Sales.SalesOrderHeader
GROUP BY YEAR(OrderDate), MONTH(OrderDate)
ORDER BY Year, Month;
```
🔸 Customer Segmentation(Segregates customers into individual and business categories for comparative analysis):

```sql
SELECT 
    COUNT(CASE WHEN PersonID IS NOT NULL THEN 1 END) AS PersonCustomers,
    COUNT(CASE WHEN StoreID IS NOT NULL THEN 1 END) AS StoreCustomers
FROM Sales.Customer;
```

**🔹 5. Key KPIs**

1. Total Revenue = Total sales amount
2. Total Orders = Count of orders
3. Average Order Value (AOV) = Revenue per order
4. Revenue per Customer = Revenue per unique customer
5. Customer Segmentation = Individual vs Business customers

**🔹 6. Dashboard Screenshots**
Visuals: 

1. KPI Cards (Revenue, Orders, AOV, Revenue per Customer)
2. Sales Trend (Month-wise)
3. Region-wise Revenue
4. Customer Type Split (Person vs Store)
5. Top 10 Customers by Revenue

**Sales Overview:**

<img width="2706" height="1528" alt="image" src="https://github.com/user-attachments/assets/9556944f-e50a-4aaf-91e7-f8b42644d22c" />

**Customer Insights**

<img width="2724" height="1530" alt="image" src="https://github.com/user-attachments/assets/6a7d0fe8-2264-4435-854f-6ad4d3822d82" />




**🔹 7. Business Insights**

Revenue is distributed across a large number of customers, with each contributing a small percentage
A small group of top customers contributes significantly higher revenue compared to the average
Business (store) customers contribute a major portion of total revenue
Seasonal trends observed in monthly sales performance
Regional variation highlights key high-performing territories


🚀 **Project Outcome****

Built a scalable and accurate data model for analytics
Delivered an interactive dashboard for business decision-making
Demonstrated strong skills in SQL, Power BI, DAX, and data modeling


🎯 **Key Learning****
Importance of correct relationships in Power BI
Handling NULLs and multiple customer types
Avoiding double counting in measures
Writing efficient DAX using CALCULATE and filter context
