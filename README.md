# pizza-sales
 The goal of this project is to perform a comprehensive analysis of pizza sales data to help stakeholders make data driven decisions.this include identiying:
 -TOP SELLING PIZZA TYPES
 -REVENUE BY PIZZA CATEGORY AND SIZE
 MONTHLY AND WEEKLI SALES TRENDS
 WORST PIZZA 
#DATA/#Raw and cleanded data files (csv,excel)
SQL/#SQL scripts for data cleaning and transformation
#POWERBI/Dashboard and chart 
#SQL QUERIES
select * from pizza_sales
select DISTINCT  order_id from pizza_sales

select distinct  pizza_size from  pizza_sales

SELECT * from pizza_sales where pizza_size='m' 

select SUM(quantity)/COUNT(distinct order_id) from pizza_sales

select CAST(cast(sum(quantity)as decimal(10,2))/
cast(count(distinct order_id )AS decimal(10,2))as decimal(10,2))as avg_pizza_per_order from pizza_sales


select DATENAME(dw ,order_date)as order_day,COUNT(DISTINCT ORDER_ID ) AS total_orders
FROM pizza_sales
group by datename(dw,order_date)

select DATENAME (month,order_date)as month_name,COUNT(distinct order_id)as total_orders
from pizza_sales
group by DATENAME (month,order_date)
order by total_orders desc

select top 5 pizza_name,SUM (total_price)as total_revenue from pizza_sales
group by pizza_name
order by total_revenue ASC
