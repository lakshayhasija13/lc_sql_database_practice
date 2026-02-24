# 1683. Invalid Tweets

**Difficulty:** Easy  
**Topic:** Database  
**Link:** https://leetcode.com/problems/invalid-tweets/

## Problem Description

Write a solution to find the IDs of the invalid tweets. A tweet is invalid if the number of characters used in the content of the tweet is **strictly greater than** `15`.

Return the result table in **any order**.

## Table Schema

**Table: Tweets**

| Column Name | Type    |
|-------------|---------|
| tweet_id    | int     |
| content     | varchar |

`tweet_id` is the primary key for this table. Each row contains the id and the content of a tweet.

## Example

**Input:**

Tweets table:
| tweet_id | content                          |
|----------|----------------------------------|
| 1        | Vote for Biden                   |
| 2        | Let us make America great again! |

**Output:**
| tweet_id |
|----------|
| 2        |

**Explanation:** Tweet 1 has a content length of 14 characters, so it is valid. Tweet 2 has a content length of 32 characters, so it is invalid.

## Solution

Use `LENGTH()` to filter tweets whose content exceeds 15 characters.

```sql
SELECT tweet_id
FROM Tweets 
WHERE LENGTH(content) > 15;
```
