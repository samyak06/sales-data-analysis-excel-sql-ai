-- =========================================
-- Project: Business Performance Analysis
-- Author: Your Name
-- =========================================

-- 1. Create Table
CREATE TABLE business_report (
    date DATE,
    product VARCHAR(50),
    category VARCHAR(50),
    region VARCHAR(50),
    revenue DECIMAL(10,2),
    cost DECIMAL(10,2),
    profit DECIMAL(10,2)
);

-- 2. Insert Data
INSERT INTO business_report VALUES
('2025-07-01','Laptop','Electronics','North',75000,55000,20000),
('2025-07-02','Mobile','Electronics','South',40000,30000,10000),
('2025-07-03','Shoes','Fashion','West',15000,8000,7000),
('2025-07-04','Watch','Accessories','East',12000,7000,5000),
('2025-07-05','Laptop','Electronics','West',80000,60000,20000),
('2025-07-06','Mobile','Electronics','North',42000,31000,11000),
('2025-07-07','Shoes','Fashion','South',18000,9000,9000);

-- 3. Business Analysis Queries

-- Top 2 Products by Profit
SELECT product, SUM(profit) AS total_profit
FROM business_report
GROUP BY product
ORDER BY total_profit DESC
LIMIT 2;

-- Least Performing Product
SELECT product, SUM(profit) AS total_profit
FROM business_report
GROUP BY product
ORDER BY total_profit ASC
LIMIT 1;

-- Revenue by Category
SELECT category, SUM(revenue) AS total_revenue
FROM business_report
GROUP BY category
ORDER BY total_revenue DESC;

-- Profit Margin by Product
SELECT product,
       SUM(profit) AS total_profit,
       SUM(revenue) AS total_revenue,
       (SUM(profit)/SUM(revenue))*100 AS profit_margin
FROM business_report
GROUP BY product
ORDER BY profit_margin DESC;


#OUTPUT:-
1st 
product	total_profit
Laptop	40000
Mobile	21000
2nd 
product	total_profit
Watch	5000
3rd
category	total_revenue
Electronics	237000
Fashion	33000
Accessories	12000
3rd
product	total_profit	total_revenue	profit_margin
Watch	5000	12000	0
Shoes	16000	33000	0
Mobile	21000	82000	0
Laptop	40000	155000	0
