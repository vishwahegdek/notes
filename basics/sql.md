# SQL Roadmap for Cognizant – **4 Weeks Plan (1–1.5 hrs/day)**

Each week builds on the previous one. You'll practice both **concepts** and **problems** side-by-side.

## ✅ Week 1: **SQL Foundations (Basics to Intermediate)**

### 📌 **Goal**: Be comfortable writing basic SELECT queries, filters, and sorting.

#### 🔹 Topics:
* SELECT, FROM, WHERE, ORDER BY
* LIMIT, OFFSET
* DISTINCT
* Aggregate functions: `COUNT()`, `SUM()`, `AVG()`, `MIN()`, `MAX()`
* GROUP BY and HAVING
* Basic WHERE with `AND`, `OR`, `NOT`, `IN`, `BETWEEN`

#### 🧪 Practice:
* HackerRank SQL Easy problems
* LeetCode Easy SQL set
* Use your existing PostgreSQL local setup and create dummy tables (e.g. tasks, users)

## ✅ Week 2: **Joins & Subqueries**

### 📌 **Goal**: Get comfortable with multi-table queries & data relationships

#### 🔹 Topics:
* INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL JOIN
* Aliasing (`AS`)
* Subqueries (in SELECT, FROM, and WHERE clauses)
* EXISTS, IN vs EXISTS

#### 🧪 Practice:
* LeetCode Medium SQL (esp. ones with JOINs)
* Write queries like:
   * "List users who have not created any tasks"
   * "Get tasks along with the user who created them"
   * "Tasks created this week by users in a specific department"

## ✅ Week 3: **Advanced SQL**

### 📌 **Goal**: Learn to solve real-world and interview-level queries

#### 🔹 Topics:
* Window functions:
   * `ROW_NUMBER()`, `RANK()`, `DENSE_RANK()`
   * `PARTITION BY`, `OVER()`
* CTEs (WITH clause)
* CASE WHEN statements
* COALESCE, NULL handling
* Date functions: `DATE_PART()`, `AGE()`, `CURRENT_DATE`, etc.

#### 🧪 Practice:
* Write queries for leaderboards, rankings, trends
* Create challenge-like problems from your task manager project

## ✅ Week 4: **Optimization, Practice Sets & Mock Interviews**

### 📌 **Goal**: Be confident writing, explaining, and optimizing SQL in interviews

#### 🔹 Topics:
* Indexing basics
* Explain query plan (optional but good to know for PostgreSQL)
* Common optimization techniques (avoiding nested subqueries, minimizing joins, indexing, using LIMIT)

#### 🧪 Practice:
* Mix of Medium+ LeetCode/InterviewBit/Striver SQL Sheet
* Try to solve queries without using ORM—pure SQL
* Take a few mock SQL interview challenges

## 🎯 BONUS: What Cognizant-Like Companies Ask

Here are **common SQL tasks asked** in interviews:
* "Second highest salary" type queries
* Top-N per group (e.g., Top 3 tasks per user)
* Users with no activity
* Query optimization problems
* Queries involving dense RANK/ROW_NUMBER
* Joins across 3–4 tables with filters

## 🛠️ Tools for Practicing:
* LeetCode SQL
* HackerRank SQL
* Mode SQL Tutorial
* Use your local PostgreSQL DB with pgAdmin or DBeaver
* Company-style database schemas for practice

## 📌 Summary Table

| Week | Focus | Outcome |
|------|-------|---------|
| 1 | Basics + Aggregation | Write simple, grouped queries |
| 2 | Joins & Subqueries | Handle multi-table real-world queries |
| 3 | Advanced SQL | Use window functions, CTEs, CASE |
| 4 | Practice & Optimization | Be interview-ready with real challenges |