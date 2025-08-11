# LeetCode SQL Solution — Combine Two Tables

## Problem Statement
Table: `Person`

| Column Name | Type    |
|-------------|---------|
| PersonId    | int     |
| FirstName   | varchar |
| LastName    | varchar |

`PersonId` is the primary key for this table.  
Each row contains personal information about a person.

---

Table: `Address`

| Column Name | Type    |
|-------------|---------|
| AddressId   | int     |
| PersonId    | int     |
| City        | varchar |
| State       | varchar |

`AddressId` is the primary key for this table.  
Each row contains address information about a person.

---

Write a SQL query to report the **FirstName, LastName, City, and State** of each person in the `Person` table. If the address of a `PersonId` is not present in the `Address` table, return `null` for City and State.

---

## Example

**Input:**

**Person table:**
| PersonId | FirstName | LastName |
|----------|-----------|----------|
| 1        | Allen     | Wang     |
| 2        | Bob       | Alice    |
| 3        | Brayden   | Miller   |

**Address table:**
| AddressId | PersonId | City     | State |
|-----------|----------|----------|-------|
| 1         | 2        | New York | NY    |
| 2         | 3        | Chicago  | IL    |

---

**Output:**
| FirstName | LastName | City     | State |
|-----------|----------|----------|-------|
| Allen     | Wang     | null     | null  |
| Bob       | Alice    | New York | NY    |
| Brayden   | Miller   | Chicago  | IL    |

---

## SQL Solution

```sql
SELECT p.FirstName,
       p.LastName,
       a.City,
       a.State
FROM Person p
LEFT JOIN Address a
ON p.PersonId = a.PersonId;
