# Pizza_Sales_KPI_Dashboard_Project
MySQL & Excel project including data validation and data cleaning

1.	Total Revenue
Query : SELECT SUM(total_price) AS Total_Revenue FROM pizza_sales;

2.	Average Order Value
Query : SELECT SUM(total price)/COUNT(DISTINCT order_id) AS Avg_order_value 
FROM pizza_sales;
 
3.	Total Pizza Sold
Query : SELECT SUM(quantity) AS Total_Pizza_Sold FROM pizza_sales;
 
4.	Total Orders 
Query : SELECT COUNT(DISTINCT order_id) AS Total_Orders FROM pizza_sales;

5.	Average Pizza Per Order
Query : SELECT ROUND(SUM(quantity)/COUNT(DISTINCT order_id),2) AS Avg_Pizza_Per_Order FROM pizza_sales;
 
Daily Trend For Total Orders 
Query : SELECT DAYNAME(order_date) AS Order_day,
COUNT(DISTINCT order_id) as Num_of_Orders
FROM pizza_sales
GROUP BY Order_day
ORDER BY Num_of_Orders DESC; 
 
Hourly Trend For Total Orders 
Query : ELECT HOUR(order_time) AS Order_Hour,
COUNT(DISTINCT order_id) AS Num_of_Orders
FROM pizza_sales
GROUP BY Order_Hour;
 
% Of Sales By Pizza Category 
Query : SELECT pizza_category,ROUND(SUM(total_price)/
(SELECT SUM(total_price) FROM pizza_sales)*100,2) AS Total_Sales_Percentage
FROM pizza_sales
GROUP BY pizza_category
ORDER BY Total_Sales_Percentage DESC;

% Of Sales By Pizza Size
Query : SELECT pizza_size, ROUND(SUM(total_price)/
(SELECT SUM(total_price) FROM pizza_sales)*100,2)  as Sales_Percentage
FROM pizza_sales
GROUP BY pizza_size
ORDER BY Sales_Percentage DESC;
 
Total Pizzas Sold by Pizza Category
Query : SELECT pizza_category,SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_category
ORDER BY 2 DESC;
 
Top 5 Best Sellers 
Query : SELECT pizza_name, SUM(quantity) AS Quantity_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Quantity_Sold DESC
LIMIT 5;
 
Bottom 5 Worst Sellers 
Query : SELECT pizza_name, SUM(quantity) AS Quantity_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Quantity_Sold
LIMIT 5; 

Business insights
**Busiest days and times**
* Orders are highest on Thursday,Friday & Saturday.
* Maximum orders are from 12-1PM & 5-7PM.

**Sales by Categoty and Size** 
* Classic category contributes the  maximum sales.
* Large & Large & Medium sizes have the  highest demand.

**Best 5 & Worst 5 Sellers**
* Classic Deluxe And Barbecue Chicken Pizzas are best revenue generators.
* Brie Carre has the lowest demand.




