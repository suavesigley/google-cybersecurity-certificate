# SQL Querying Lab – Employee Devices & Login Activity

**Course:** Course 4 – Tools of the Trade: Linux and SQL  
**Lab Focus:** Retrieving and organizing data from a relational database using SQL

---

## Objective

As a security analyst, retrieve information about employee devices that may need updates and examine user login activity for potential unusual behavior.

Data was stored in the `organization` database with two key tables:

- `machines` – device and operating system information
- `log_in_attempts` – user login activity

---

## Tools Used

- MariaDB (MySQL-compatible database)
- SQL (`SELECT`, `FROM`, `ORDER BY`)

---

## Tasks Performed

### 1. Retrieve all device information
```sql
SELECT *
FROM machines;

2. Select device ID and email client
SQLSELECT device_id, email_client
FROM machines;

3. Select device ID, operating system, and OS patch date
SQLSELECT device_id, operating_system, OS_patch_date
FROM machines;

4. Select event ID and country
SQLSELECT event_id, country
FROM log_in_attempts;

5. Select username, login date, and login time
SQLSELECT username, login_date, login_time
FROM log_in_attempts;

6. Sort login attempts by date and time
SQLSELECT *
FROM log_in_attempts
ORDER BY login_date, login_time;
