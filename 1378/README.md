# 1378. Replace Employee ID With The Unique Identifier

**Difficulty:** Easy  
**Topic:** Database  
**Link:** https://leetcode.com/problems/replace-employee-id-with-the-unique-identifier/

## Problem Description

Write a solution to show the **unique ID** of each user. If a user does not have a unique ID, show `null` instead.

Return the result table in **any order**.

## Table Schema

**Table: Employees**

| Column Name | Type    |
|-------------|---------|
| id          | int     |
| name        | varchar |

`id` is the primary key for this table. Each row contains the id and the name of an employee in a company.

**Table: EmployeeUNI**

| Column Name | Type |
|-------------|------|
| id          | int  |
| unique_id   | int  |

`(id, unique_id)` is the primary key for this table. Each row contains the id and the corresponding unique id of an employee in the company.

## Example

**Input:**

Employees table:
| id | name     |
|----|----------|
| 1  | Alice    |
| 7  | Bob      |
| 11 | Meir     |
| 90 | Winston  |
| 3  | Jonathan |

EmployeeUNI table:
| id | unique_id |
|----|-----------|
| 3  | 1         |
| 11 | 2         |
| 90 | 3         |

**Output:**
| unique_id | name     |
|-----------|----------|
| null      | Alice    |
| null      | Bob      |
| 2         | Meir     |
| 3         | Winston  |
| 1         | Jonathan |

## Solution

Use a `LEFT JOIN` to include all employees from the `Employees` table. Employees without a matching entry in `EmployeeUNI` will have `NULL` as their `unique_id`.

```sql
SELECT unique_id, name 
FROM Employees
LEFT JOIN EmployeeUNI
USING (id);
```
