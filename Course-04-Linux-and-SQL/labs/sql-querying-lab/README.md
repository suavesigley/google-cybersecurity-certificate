# Security Analysis: Querying Employee Devices and Login Logs with SQL

## Overview
In this lab activity, I acted as a security analyst investigating organization asset updates and auditing user login activity. Using SQL within a MariaDB environment, I executed targeted database queries against the `machines` and `log_in_attempts` tables to retrieve specific hardware details and security logs.

## Database & Table Schema
* **Database:** `organization`
* **`machines` Table:** Tracks hardware assets (`device_id`, `operating_system`, `email_client`, `OS_patch_date`, `employee_id`).
* **`log_in_attempts` Table:** Tracks user authentication events (`event_id`, `username`, `login_date`, `login_time`, `country`, `ip_address`, `success`).

---

## Portfolio Media & Screenshot Mapping

| Original Filename | Recommended Professional Name | Query / Evidence Shown |
| :--- | :--- | :--- |
| `gcsclab01.png` | `01-select-device-id-email-client.png` | `SELECT device_id, email_client FROM machines;` |
| `gcsclab02.png` | `02-select-device-os-patch-date.png` | Syntax error handling and successful query for `device_id`, `operating_system`, `OS_patch_date` |
| `gcsclab03.png` | `03-select-event-id-country.png` | `SELECT event_id, country FROM log_in_attempts;` |
| `gcsclab04.png` | `04-select-username-login-date-time.png` | `SELECT username, login_date, login_time FROM log_in_attempts;` |

---

## Lab Execution & Key Queries

### Task 1: Auditing Hardware Assets for Patch Management
To identify outdated employee systems needing operating system updates and software reviews, I queried specific columns from the `machines` table.

1. **Full Device Audit:**
   SELECT * FROM machines;
   *Purpose:* Retrieved all device attributes across 200 security records.

2. **Isolating Email Clients:**
   SELECT device_id, email_client FROM machines;
   *Purpose:* Extracted software environment data for potential email security compliance checks.
   
   ![Select Device ID and Email Client](01-select-device-id-email-client.png)

3. **OS Patch Tracking:**
   SELECT device_id, operating_system, OS_patch_date FROM machines;
   *Purpose:* Mapped device IDs against operating systems and patch dates to target update deployment schedules.
   
   ![Select Device OS and Patch Date](02-select-device-os-patch-date.png)

### Task 2: Investigating User Login Activity
To audit authentication patterns across geographic origins and user activity timelines:

1. **User Login Timestamps:**
   SELECT username, login_date, login_time FROM log_in_attempts;
   *Purpose:* Analyzed access times to spot anomalous login patterns outside regular working hours.
   
   ![Select Username, Login Date, and Time](04-select-username-login-date-time.png)

2. **Geographic Event Mapping:**
   SELECT event_id, country FROM log_in_attempts;
   *Purpose:* Mapped authentication event IDs to country codes (`CAN`, `USA`, `MEX`) for geo-velocity check requirements.
   
   ![Select Event ID and Country](03-select-event-id-country.png)

---

## Troubleshooting & Analysis Insights

During execution, a syntax error occurred due to missing spacing between the final column name and the `FROM` clause:

ERROR 1054 (42S22): Unknown column 'OS_patch_dateFROM' in 'field list'

* **Root Cause:** A missing space between `OS_patch_date` and `FROM machines;` caused the SQL parser to read the column as `OS_patch_dateFROM`.
* **Resolution:** Corrected the query structure by properly delimiting keywords:
  SELECT device_id, operating_system, OS_patch_date FROM machines;

---

## Key Takeaways for Security Operations
* **Targeted Extraction:** Filtering specific columns instead of running `SELECT *` improves query efficiency and maintains focus during incident triage.
* **Audit Trail Analysis:** Correlating `username`, `login_date`, and `login_time` is critical for establishing baseline user behaviour during breach investigations.
* **Patch Management:** Querying patch release timelines directly assists vulnerability management teams in mitigating unpatched system exploits.
