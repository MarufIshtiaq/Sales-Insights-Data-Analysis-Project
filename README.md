# Sales-Insights-Data-Analysis-Project

 SQL database Sales_Insights_Data_Analysis_Project is in Sales_Insights_Data_Analysis_Project.sql file above. Download `Sales_Insights_Data_Analysis_Project` file to your local computer and import it.

### Data Analysis Using SQL

1. Show total number of customers
SELECT count(*) FROM customers;

2. Show transactions for Chennai market (market code for chennai is Mark001)
SELECT * FROM transactions where market_code='Mark001';

3. Show distrinct product codes that were sold in chennai
SELECT distinct product_code FROM transactions where market_code='Mark001';

4. Show transactions where currency is US dollars
SELECT * from transactions where currency="USD"

5. Show transactions in 2020 join by date table
SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;

6. Show total revenue in year 2020,
SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR" or transactions.currency="USD";
	
7. Show total revenue in year 2020, January Month,
SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR" or transactions.currency="USD");

8. Show total revenue in year 2020 in Chennai
SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020
and transactions.market_code="Mark001";

9. Show Total Revenue
select sum(sales.transactions.sales_amount) as revenue from sales.transactions;

10. Show Total Quantity Sold
select sum(sales.transactions.sales_qty) as sales_qty from sales.transactions;

11. Show Total Profit Margin
select round(sum(sales.transactions.profit_margin)) as total_profit_margin from sales.transactions;

12. Show Total Revenue by Markets
select sales.markets.markets_name, sum(sales.transactions.sales_amount) as revenue
from sales.transactions
inner join sales.markets on sales.markets.markets_code = sales.transactions.market_code
group by sales.markets.markets_name;

13. Show Total Quantity Sold by Markets
select sales.markets.markets_name, sum(sales.transactions.sales_qty) as sales_qty
from sales.transactions
inner join sales.markets on sales.markets.markets_code = sales.transactions.market_code
group by sales.markets.markets_name;

14. Show Top 5 Customers
select sales.customers.custmer_name, sum(sales.transactions.sales_amount) as revenue
from sales.transactions
inner join sales.customers on sales.customers.customer_code = sales.transactions.customer_code
group by sales.customers.custmer_name
limit 5;

15. Show Top 5 Products
select sales.products.product_code, sum(sales.transactions.sales_amount) as revenue
from sales.transactions
inner join sales.products on sales.products.product_code = sales.transactions.product_code
group by sales.products.product_code
limit 5;

16. Show Profit Percentage by Markets
select sales.markets.markets_name, round(sum(sales.transactions.profit_margin_percentage))
from sales.transactions
inner join sales.markets on sales.markets.markets_code = sales.transactions.market_code
group by sales.markets.markets_name;
