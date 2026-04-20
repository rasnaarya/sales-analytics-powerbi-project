# Sales-analytics-powerbi-project
**🔹 1. Project Overview**
Built an end-to-end Sales Analytics Dashboard using Microsoft SQL Server and Microsoft Power BI to analyze revenue trends, customer behavior, and regional performance.
The project focuses on transforming raw transactional data into meaningful business insights through data modeling, DAX calculations, and interactive visualizations.
**🔹 2. Tools Used**
SQL: Data extraction, joins, aggregations
SQL Server Management Studio: Query execution and database management
Power BI: Data modeling and dashboard development
DAX: KPI calculations and business logic

**🔹 3. Data Model**
Designed a relational data model connecting:
Sales Orders (SalesOrderHeader, SalesOrderDetail)
Customer (Customer, Person, Store)
Territory (SalesTerritory)
Implemented proper relationships:
Customer → Sales (1-to-many)
Territory → Customer → Sales
Resolved real-world challenges:
Fixed many-to-many relationship issues
Handled NULL values in customer data
Built unified Customer Name logic (Person + Store)
Prevented double-counting in revenue calculations

**🔹 4. SQL Analysis & Queries**
🔸 Top Customers by Revenue(Identifies top revenue-generating customers for targeted business strategies):

SELECT TOP 10 
    CustomerID, 
    SUM(TotalDue) AS Revenue
FROM Sales.SalesOrderHeader
GROUP BY CustomerID
ORDER BY Revenue DESC;

🔸 Monthly Sales Trend(Analyzes revenue trends over time to identify seasonality and growth patterns):

SELECT 
    YEAR(OrderDate) AS Year,
    MONTH(OrderDate) AS Month,
    SUM(TotalDue) AS Revenue
FROM Sales.SalesOrderHeader
GROUP BY YEAR(OrderDate), MONTH(OrderDate)
ORDER BY Year, Month;

🔸 Customer Segmentation(Segregates customers into individual and business categories for comparative analysis):

SELECT 
    COUNT(CASE WHEN PersonID IS NOT NULL THEN 1 END) AS PersonCustomers,
    COUNT(CASE WHEN StoreID IS NOT NULL THEN 1 END) AS StoreCustomers
FROM Sales.Customer;



**🔹 5. Key KPIs**
Total Revenue = Total sales amount
Total Orders = Count of orders
Average Order Value (AOV) = Revenue per order
Revenue per Customer = Revenue per unique customer
Customer Contribution % = Share of each customer in total revenue
Customer Segmentation = Individual vs Business customers

**🔹 6. Dashboard Screenshots**
Visuals: 
KPI Cards (Revenue, Orders, AOV, Revenue per Customer)
Sales Trend (Month-wise)
Region-wise Revenue
Customer Type Split (Person vs Store)
Top 10 Customers by Revenue

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
