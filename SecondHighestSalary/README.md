# LeetCode SQL Solution — Second Highest Salary

## Problem Statement
Table: `Employee`

| Column Name | Type    |
|-------------|---------|
| id          | int     |
| salary      | int     |

`id` is the primary key for this table.  
Each row contains salary information of an employee.

---

Write a SQL query to report the **second highest salary** from the `Employee` table.  
If there is no second highest salary, the result should be `null`.

---

## Example

**Input:**
| id | salary |
|----|--------|
| 1  | 100    |
| 2  | 200    |
| 3  | 300    |

**Output:**
| SecondHighestSalary |
|---------------------|
| 200                 |

---

**Input:**
| id | salary |
|----|--------|
| 1  | 100    |

**Output:**
| SecondHighestSalary |
|---------------------|
| null                |

---

## SQL Solution

```sql
SELECT 
    (SELECT DISTINCT salary
     FROM Employee
     ORDER BY salary DESC
     LIMIT 1 OFFSET 1) AS SecondHighestSalary;
