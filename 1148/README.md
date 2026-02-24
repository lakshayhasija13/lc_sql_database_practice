# 1148. Article Views I

**Difficulty:** Easy  
**Topic:** Database  
**Link:** https://leetcode.com/problems/article-views-i/

## Problem Description

Write a solution to find all the authors that viewed at least one of their own articles.

Return the result table sorted by `id` in **ascending order**.

## Table Schema

**Table: Views**

| Column Name | Type |
|-------------|------|
| article_id  | int  |
| author_id   | int  |
| viewer_id   | int  |
| view_date   | date |

There is no primary key for this table; it may have duplicate rows. Each row indicates that some viewer viewed an article (written by some author) on some date. Note that equal `author_id` and `viewer_id` indicate the same person.

## Example

**Input:**

Views table:
| article_id | author_id | viewer_id | view_date  |
|------------|-----------|-----------|------------|
| 1          | 3         | 5         | 2019-08-01 |
| 1          | 3         | 6         | 2019-08-02 |
| 2          | 7         | 7         | 2019-08-01 |
| 2          | 7         | 6         | 2019-08-02 |
| 4          | 7         | 1         | 2019-07-22 |
| 3          | 4         | 4         | 2019-07-21 |
| 3          | 4         | 4         | 2019-07-21 |

**Output:**
| id |
|----|
| 4  |
| 7  |

## Solution

Filter rows where `author_id = viewer_id` (the author viewed their own article), group by `author_id` to deduplicate, and order by `id` ascending.

```sql
SELECT author_id AS id 
FROM Views
WHERE author_id = viewer_id
GROUP BY author_id
HAVING COUNT(*) >= 1
ORDER BY id ASC;
```
