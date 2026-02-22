# 175. Combine Two Tables

**Difficulty:** Easy  
**Topic:** Database  
**Link:** https://leetcode.com/problems/combine-two-tables/

## Problem Description

Write a solution to report the first name, last name, city, and state of each person in the `Person` table. If the address of a `personId` is not present in the `Address` table, report `null` instead.

Return the result table in **any order**.

## Table Schema

**Table: Person**

| Column Name | Type    |
|-------------|---------|
| personId    | int     |
| lastName    | varchar |
| firstName   | varchar |

`personId` is the primary key for this table.

**Table: Address**

| Column Name | Type    |
|-------------|---------|
| addressId   | int     |
| personId    | int     |
| city        | varchar |
| state       | varchar |

`addressId` is the primary key for this table.

## Example

**Input:**

Person table:
| personId | lastName | firstName |
|----------|----------|-----------|
| 1        | Wang     | Allen     |
| 2        | Alice    | Bob       |

Address table:
| addressId | personId | city          | state      |
|-----------|----------|---------------|------------|
| 1         | 2        | New York City | New York   |
| 2         | 3        | Leetcode      | California |

**Output:**
| firstName | lastName | city          | state    |
|-----------|----------|---------------|----------|
| Allen     | Wang     | null          | null     |
| Bob       | Alice    | New York City | New York |

## Solution

A `LEFT JOIN` is used to include all rows from the `Person` table, even if there is no matching row in the `Address` table. When no match exists, the city and state columns will be `NULL`.

```sql
SELECT firstName, lastName, city, state
FROM Person
LEFT JOIN Address
USING (personId);
```
