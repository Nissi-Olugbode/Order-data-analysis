# Inventory-Analysis
This project was done from the perspective of a Business Intelligence Analyst,tasked with analyzing historical order data for Kultra Mega Stores (KMS) — a technology, office supplies and furniture provider.  To uncover key performance metrics and identify opportunities for strategic business improvement.

## Kultra Mega Stores (KMS) Inventory Analysis

### Project Overview
The project involved analyzing order records between 2009 and 2012 to address real-world business questions using Microsoft SQL Server and developing an BI dashboard to visualize insights for stakeholders.

### Data Sources
The dataset tables were provided in CSV format. Contains records of product orders, customers, sales, profits, categories, shipping methods, order priority, and a table with returns for over a 4-year period.

### Objectives
- Identify the relationship between product category and sales
- Analyze regions by total sales
- Provide recommendations to improve revenue from the bottom 10 customers
- Identify the most valuable customers and their purchase patterns
- Identify customers who returned items and their segments
- Analyze whether shipping cost spending aligns with order priority levels
- Create a dashboard to visualize 

### Tools
- Microsoft SQL Server: Data querying, joining, and aggregation
- Microsoft Power BI:Data modelling, data visualization and dashboard creation.
  
### SQL Analysis
Download full .sql file [here.](https://github.com/Nissi-Olugbode/Order-data-analysis/blob/main/KMS_SQL.sql)
- Aggregations for sales, profit, shipping cost, and order count
- Filtering by region, segment, and product category
- Window Functions to rank customers by revenue and profit
- Joins across order, customer, and returns tables
- CASE statements for evaluating shipping cost appropriateness by order priority
- Grouping and Sorting to extract Top/Bottom performers

### Power BI Analysis
Download full .pbix file [here.](https://github.com/Nissi-Olugbode/Order-data-analysis/blob/main/KMS_dashboard.pbix)
The analysis includes a interactive Power BI dashboard with the following visualizations;
- Relationship between customer segment and sales
- Region with the highest sales
- Product categories with their sales
- Customers with the highest and lowest sales
- Customers with the most returns
  
![Here is a preview of the dashboard](https://github.com/Nissi-Olugbode/Order-data-analysis/blob/main/KMS%20dashboard.JPG)

### Exploratory Data Analysis
This involved exloring of the data to analyze the following:
1. Identify the product category with the highest sales
2. Determine the Top 3 and Bottom 3 regions by total sales
3. Calculate total appliance sales in Ontario
4. Provide recommendations to improve revenue from the bottom 10 customers
5. Identify which shipping method incurred the highest shipping costs
6. Identify the most valuable customers and their purchase patterns
7. Find the highest-spending small business customer
8. Determine which corporate customer placed the most orders (2009–2012)
9. Highlight the most profitable consumer customer
10. Identify customers who returned items and their segments
11. Analyze whether shipping cost spending aligns with order priority levels
    
### Data Analysis
This includes some lines on some of the SQL queries;
- Product with highest sales
  ```
  SELECT PRODUCT_CATEGORY, SUM(SALES)AS TOTAL_SALES
  FROM KMS_SQL
  GROUP BY PRODUCT_CATEGORY
	ORDER BY TOTAL_SALES DESC;
  ```

- Customer with returned items and customer segments

	```
	SELECT DISTINCT KMS_SQL.CUSTOMER_NAME, KMS_SQL.CUSTOMER_SEGMENT
	FROM KMS_SQL
	JOIN ORDER_STATUS 
		ON KMS_SQL.ORDER_ID=ORDER_STATUS.ORDER_ID;
 	```

- Shipping cost vs order priority
  	```
  	SELECT ORDER_PRIORITY, SHIP_MODE, COUNT(*)AS ORDER_COUNT, SUM(SHIPPING_COST)AS TOTAL_SHIPPING_COST
   	FROM KMS_SQL
	GROUP BY ORDER_PRIORITY, SHIP_MODE
	ORDER BY ORDER_PRIORITY, TOTAL_SHIPPING_COST DESC;
 	```


### Insight
From the data analysis it was observed that;
- Technology category had the highest sales
- West, Ontario and Prarie are the regions with the highest sales
- Nunavut, NorthWest territories, Yukon are the regions with the lowest sales
- The shipping method that acquired the most expense is the delivery truck
- Top customer was from the consumer segments, with a prefrence for products from the office supply and technology categories.
- If the delivery truck is most economical, the company did not appropriately disparse shipping cost based on order priority because, delivery truck was the second highest order count on all order priority level including the low priority and express air had the lowest order count in all order piority level including the critical and high priority orders.

