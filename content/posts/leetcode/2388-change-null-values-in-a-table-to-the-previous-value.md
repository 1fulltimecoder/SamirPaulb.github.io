---
title: 2388 Change Null Values in a Table to the Previous Value
summary: 2388 Change Null Values in a Table to the Previous Value LeetCode Solution Explained
date: 2022-11-25
tags: [leetcode]
series: [leetcode]
keywords: ["2388 Change Null Values in a Table to the Previous Value LeetCode Solution Explained in all languages", "2388 Change Null Values in a Table to the Previous Value", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://res.cloudinary.com/samirpaul/image/upload/w_1100,c_fit,co_rgb:FFFFFF,l_text:Arial_75_bold:2388 Change Null Values in a Table to the Previous Value - Solution Explained/problem-solving.webp
    alt: 2388 Change Null Values in a Table to the Previous Value
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [2388. Change Null Values in a Table to the Previous Value](https://leetcode.com/problems/change-null-values-in-a-table-to-the-previous-value)


## Description

<p>Table: <code>CoffeeShop</code></p>

<pre>
+-------------+---------+
| Column Name | Type    |
+-------------+---------+
| id          | int     |
| drink       | varchar |
+-------------+---------+
id is the primary key (column with unique values) for this table.
Each row in this table shows the order id and the name of the drink ordered. Some drink rows are nulls.
</pre>

<p>&nbsp;</p>

<p>Write a solution to replace the <code>null</code> values of the drink with the name of the drink of the previous row that is not <code>null</code>. It is guaranteed that the drink on the first row of the table is not <code>null</code>.</p>

<p>Return the result table <strong>in the same order as the input</strong>.</p>

<p>The result format is shown in the following example.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input:</strong> 
CoffeeShop table:
+----+-------------------+
| id | drink             |
+----+-------------------+
| 9  | Rum and Coke      |
| 6  | null              |
| 7  | null              |
| 3  | St Germain Spritz |
| 1  | Orange Margarita  |
| 2  | null              |
+----+-------------------+
<strong>Output:</strong> 
+----+-------------------+
| id | drink             |
+----+-------------------+
| 9  | Rum and Coke      |
| 6  | Rum and Coke      |
| 7  | Rum and Coke      |
| 3  | St Germain Spritz |
| 1  | Orange Margarita  |
| 2  | Orange Margarita  |
+----+-------------------+
<strong>Explanation:</strong> 
For ID 6, the previous value that is not null is from ID 9. We replace the null with &quot;Rum and Coke&quot;.
For ID 7, the previous value that is not null is from ID 9. We replace the null with &quot;Rum and Coke;.
For ID 2, the previous value that is not null is from ID 1. We replace the null with &quot;Orange Margarita&quot;.
Note that the rows in the output are the same as in the input.
</pre>

## Solutions

### Solution 1

<!-- tabs:start -->

```sql
# Write your MySQL query statement below
SELECT
    id,
    CASE
        WHEN drink IS NOT NULL THEN @cur := drink
        ELSE @cur
    END AS drink
FROM CoffeeShop;
```

<!-- tabs:end -->

### Solution 2

<!-- tabs:start -->

```sql
# Write your MySQL query statement below
WITH
    S AS (
        SELECT *, ROW_NUMBER() OVER () AS rk
        FROM CoffeeShop
    ),
    T AS (
        SELECT
            *,
            SUM(
                CASE
                    WHEN drink IS NULL THEN 0
                    ELSE 1
                END
            ) OVER (ORDER BY rk) AS gid
        FROM S
    )
SELECT
    id,
    MAX(drink) OVER (
        PARTITION BY gid
        ORDER BY rk
    ) AS drink
FROM T;
```

<!-- tabs:end -->

<!-- end -->