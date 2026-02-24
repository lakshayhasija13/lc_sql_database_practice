# 1068. Product Sales Analysis I

**Difficulty:** Easy  
**Topic:** Database  
**Link:** https://leetcode.com/problems/product-sales-analysis-i/

## Problem Description

Write a solution to report the `product_name`, `year`, and `price` for each `sale_id` in the `Sales` table.

Return the resulting table in **any order**.

## Table Schema

**Table: Sales**

| Column Name | Type |
|-------------|------|
| sale_id     | int  |
| product_id  | int  |
| year        | int  |
| quantity    | int  |
| price       | int  |

`(sale_id, year)` is the primary key for this table. `product_id` is a foreign key referencing the `Product` table.

**Table: Product**

| Column Name  | Type    |
|--------------|---------|
| product_id   | int     |
| product_name | varchar |

`product_id` is the primary key for this table.

## Example

**Input:**

Sales table:
| sale_id | product_id | year | quantity | price |
|---------|------------|------|----------|-------|
| 1       | 100        | 2008 | 10       | 5000  |
| 2       | 100        | 2009 | 12       | 5000  |
| 7       | 200        | 2011 | 15       | 9000  |

Product table:
| product_id | product_name |
|------------|--------------|
| 100        | Nokia        |
| 200        | Apple        |
| 300        | Samsung      |

**Output:**
| product_name | year | price |
|--------------|------|-------|
| Nokia        | 2008 | 5000  |
| Nokia        | 2009 | 5000  |
| Apple        | 2011 | 9000  |

## Solution

Use an `INNER JOIN` between `Sales` and `Product` on `product_id` to retrieve the product name alongside each sale's year and price.

```sql
SELECT product_name, year, price
FROM Sales
INNER JOIN Product
ON Sales.product_id = Product.product_id;
```
