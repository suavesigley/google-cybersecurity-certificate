# 🔍 Security Analysis: Asset Auditing & SQL Data Filtering

![SQL](https://img.shields.io/badge/Language-SQL-blue?style=for-the-badge&logo=sqlite)
![Environment](https://img.shields.io/badge/Environment-MariaDB-g?style=for-the-badge&logo=mariadb)
![Domain](https://img.shields.io/badge/Domain-SecOps%20%26%20IAM-red?style=for-the-badge)

## 📌 Executive Summary
During a security audit of organizational infrastructure, I executed targeted database queries to map hardware assets and inspect departmental access controls. Using SQL within a MariaDB environment, I retrieved schemas and applied conditional filtering logic (`WHERE`, `LIKE`, wildcards) to isolate high-value user profiles and physical office locations for incident response readiness.

---

## 📂 Visual Evidence & Mapping

| Evidence ID | Screenshot | Query Executed | Security Purpose |
| :---: | :--- | :--- | :--- |
| **01** | `01-describe-table-schemas.png` | `DESCRIBE machines;`<br>`DESCRIBE employees;` | Inspected primary keys, null constraints, and structural schemas. |
| **02** | `02-where-department-finance.png` | `SELECT * FROM employees`<br>`WHERE department = 'Finance';` | Audited user profiles assigned to sensitive financial assets. |
| **03** | `03-where-office-like-south.png` | `SELECT * FROM employees`<br>`WHERE office LIKE 'South%';` | Mapped user IDs to physical facility zones using wildcard matching. |

---

## 🛠️ Detailed Lab Execution

<details>
<summary><b>Task 1: Inspecting Database Schemas</b> (Click to expand)</summary>

### Objective
Verify data types and identify primary key links between hardware records and employee profiles before running security filters.

### Queries Executed
```sql
DESCRIBE machines;
DESCRIBE employees;
