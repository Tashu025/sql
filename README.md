/* is 
  a comment*/
  -- Retrieve all customer data 
  SELECT *
  FROM customers
  -- Retrieve all order data 
  SELECT *
  FROM orders
  -- Retrieve each customer's name,country and score
 SELECT 
  first_name,
  country,
  score
 FROM customers
-- Retrieve customers with a score not equal to zero.
SELECT *
FROM customers
WHERE score!=0
--Retrieve customers from germany.
SELECT 
first_name,
country
FROM customers
WHERE country = 'Germany'
-- ORDER BY
SELECT *
FROM customers
ORDER BY score DESC
--Retrieve all customers and sort the results by the countr and then by the highest score
SELECT *
FROM customers
ORDER BY country ASC , score DESC
/* GROUP BY
 IND THE TOTAL SCORE FOR EACH COUNTRY */
 SELECT 
    country,
    first_name,
    SUM(score) AS total_score
 FROM customers
 GROUP BY country,first_name
 --Find the total score and total number of customers for each country.
 SELECT 
  country,
  SUM(score) AS total_score,
  COUNT(id) AS total_customers
 FROM customers
 GROUP BY country
 /* HAVING - CAN BE USED ONLY WITH GROUP BY 
 FIND the average score for each country 
 considering only customers with a score not equal to zero
 and return only countries with an average score greater than 430*/
 SELECT 
 country,
 AVG(score) AS avg_score
 FROM customers
 WHERE score!=0
 GROUP BY country
 HAVING AVG(score)>430
 /* DISTINCT- REMOVES DUPLICACY ,each value appears only once we use it after select
 Return unique list for all countries*/
 SELECT DISTINCT country
 FROM customers
 /* TOP 
 RETRIEVE ONLY 3 CUSTOMERS*/
 SELECT TOP 3*
 FROM customers
 --Retrieve the top 3 customers with the highest scores
 SELECT TOP 3*
 FROM customers
 ORDER BY score DESC
 --ReTRIEVE THE LOWEST 2 CUSTOMERS BASED ON THE SCORE
 SELECT TOP 2 *
 FROM customers
 ORDER BY score ASC
 -- GET THE TWO MOST RECENT ORDERS 
 SELECT TOP 2*
 FROM orders
 ORDER BY order_date DESC
