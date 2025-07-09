# Inventory-Analysis
This project was done from the perspective of a Business Intelligence Analyst,tasked with analyzing historical order data for Kultra Mega Stores (KMS) — a leading office supplies and furniture provider headquartered in Lagos, Nigeria. The focus was on supporting the Abuja division by uncovering key performance metrics and identifying opportunities for strategic business improvement.

## Kultra Mega Stores (KMS) Inventory Analysis

### Project Overview
The project involved analyzing order records between 2009 and 2012 to address real-world business questions using Microsoft SQL Server and developing an Excel dashboard to visualize insights for stakeholders.

### Data Sources
The data set was provided in CSV format. It contains records of product orders, customers, sales, profits, categories, shipping methods, and returns over a 4-year period.

### Objectives
1. Identify the product category with the highest sales
2. Determine the Top 3 and Bottom 3 regions by total sales
3. Calculate total appliance sales in Ontario
4. Provide recommendations to improve revenue from the bottom 10 customers
5. Identify which shipping method incurred the highest shipping costs
6. dentify the most valuable customers and their purchase patterns
7. Find the highest-spending small business customer
8. Determine which corporate customer placed the most orders (2009–2012)
9. Highlight the most profitable consumer customer
10. Identify customers who returned items and their segments
11. Analyze whether shipping cost spending aligns with order priority levels

### Tools
- Microsoft SQL Server: Data querying, joining, and aggregation

### SQL Analysis
- Aggregations for sales, profit, shipping cost, and order count
- Filtering by region, segment, and product category
- Window Functions to rank customers by revenue and profit
- Joins across order, customer, and returns tables
- CASE statements for evaluating shipping cost appropriateness by order priority
- Grouping and Sorting to extract Top/Bottom performers

### Exploratory Data Analysis
### Data Analysis
This includes some basic lines on how I created the custom columns;
- Product Category with Highest Sales
``` SELECT PRODUCT_CATEGORY, SUM(SALES)AS TOTAL_SALES
FROM KMS_SQL
	GROUP BY PRODUCT_CATEGORY
	ORDER BY TOTAL_SALES DESC; ```
- Total sales of appliances in ontario
``` SELECT SUM(SALES)AS TOTAL_SALES
FROM KMS_SQL
	WHERE PRODUCT_SUB_CATEGORY='Appliances' AND PROVINCE='Ontario'; ```
- Customer with returned items and customer segments
``` SELECT DISTINCT KMS_SQL.CUSTOMER_NAME, KMS_SQL.CUSTOMER_SEGMENT
FROM KMS_SQL
	JOIN ORDER_STATUS 
		ON KMS_SQL.ORDER_ID=ORDER_STATUS.ORDER_ID; ```

- Shipping cost vs order priority
``` SELECT ORDER_PRIORITY, SHIP_MODE, COUNT(*)AS ORDER_COUNT, SUM(SHIPPING_COST)AS TOTAL_SHIPPING_COST
FROM KMS_SQL
	GROUP BY ORDER_PRIORITY, SHIP_MODE
	ORDER BY ORDER_PRIORITY, TOTAL_SHIPPING_COST DESC; ```
	
### Insights

