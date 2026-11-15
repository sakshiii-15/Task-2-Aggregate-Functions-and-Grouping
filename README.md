# 📊 Task 2 — Aggregate Functions and Grouping (SQL)

A hands-on SQL project demonstrating **aggregate functions** (`SUM`, `COUNT`, `AVG`, `MIN`, `MAX`) and **grouping** (`GROUP BY`, `HAVING`) using a realistic **Company Sales** database.

---

## 🎯 Objective

Use aggregate functions and grouping to **summarize data** and extract meaningful business insights from relational tables.

---

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| **DB Browser for SQLite** | Run queries locally (no server setup) |
| **GitHub** | Version control & submission |

---

## 🗄️ Database Schema

**Database name:** `task2`

Two related tables model a simple company sales system:

### 1. `employees`
| Column | Type | Description |
|--------|------|-------------|
| `emp_id` | INTEGER (PK) | Unique employee ID |
| `emp_name` | VARCHAR(50) | Employee name |
| `department` | VARCHAR(30) | Department (Sales, Marketing, IT, HR) |
| `city` | VARCHAR(30) | City of posting |
| `salary` | DECIMAL(10,2) | Monthly salary |

### 2. `sales`
| Column | Type | Description |
|--------|------|-------------|
| `sale_id` | INTEGER (PK) | Unique sale ID |
| `emp_id` | INTEGER (FK) | References `employees.emp_id` |
| `product` | VARCHAR(40) | Product sold |
| `quantity` | INTEGER | Units sold |
| `unit_price` | DECIMAL(10,2) | Price per unit |
| `sale_date` | DATE | Date of sale |


---

## 📊 Queries Covered

### 🔹 Basic Aggregate Functions
| # | Query | Concept |
|---|-------|---------|
| 1 | Total sales revenue | `SUM()` |
| 2 | Total number of sales | `COUNT(*)` |
| 3 | Average employee salary | `AVG()` |
| 4 | Min & max salary | `MIN()`, `MAX()` |

### 🔹 GROUP BY
| # | Query | Concept |
|---|-------|---------|
| 5 | Count employees per department | `GROUP BY` |
| 6 | Average salary per department | `GROUP BY` + `AVG` |
| 7 | Total quantity sold per product | `GROUP BY` + `SUM` |


### 🔹 GROUP BY + HAVING
| # | Query | Concept |
|---|-------|---------|
| 8 | Departments with avg salary > 60,000 | `HAVING` + `AVG` |
| 9 | Products sold more than 10 units | `HAVING` + `SUM` |

---

## 📈 Sample Queries 

### Total Revenue
```sql
SELECT SUM(quantity * unit_price) AS total_revenue
FROM sales;
```

### Employees Per Department
```sql
SELECT department, COUNT(*) AS employee_count
FROM employees
GROUP BY department
ORDER BY employee_count DESC;
```

### Highest-Paid Employee Per Department
```sql
SELECT department, MAX(salary) AS highest_salary
FROM employees
GROUP BY department;
```

### Departments with Avg Salary > 60,000
```sql
SELECT department, AVG(salary) AS avg_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 60000;
```

---
## ✅ Conclusion
This task taught me how to turn raw data into meaningful insights using SQL aggregation. I now confidently write grouped reports, filter with HAVING, handle NULLs correctly, and format results professionally — a strong foundation for real-world SQL development.
