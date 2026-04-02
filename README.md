# Zepto-
Zepto SQL project involves designing a database for an e-commerce platform to manage customers, products, orders, and payments, with SQL queries for data retrieval and manipulation.

-data exploration

--count of rows
select count(*) from zepto;

--sample data
select * from zepto
LIMIT 10;

--null values
SELECT * FROM zepto
where name is null
OR
category is null
OR
mrp is null
OR
discountpercent is null
OR
discountedsellingprice is null
OR
weightingms is null
OR
availablequantity is null
OR
outofstock is null
OR
quantity is null;


--different product categories
SELECT DISTINCT category
from zepto
ORDER BY category;

--products in stock vs out of stock
SELECT outofstock, count(sku_id)
FROM Zepto
GROUP BY outofstock;

--product names present multiple times
SELECT name, COUNT(sku_id) as "Number of SKUs"
FROM zepto
GROUP BY name
HAVING Count(sku_id) > 1
ORDER BY count(sku_id)DESC;

-- data cleaning

--products with price = 0
SELECT * FROM zepto
where mrp = 0 OR discountedsellingprice = 0;

DELETE FROM zepto
where mrp = 0;

--convert paisa to rupees
UPDATE zepto
SET mrp = mrp/100.0,
 discountedsellingprice =  discountedsellingprice/100.0;

 SELECT mrp, discountedsellingprice FROM zepto;
 
