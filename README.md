# CPS510 Assignment 5 – E-Commerce Database System

This project implements a simple **E-Commerce Database System** in **Oracle SQL**, originally designed for CPS510 (Database Systems) Assignment 5.  
It demonstrates the use of **DDL**, **DML**, **Views**, and **Advanced SQL Queries** — all combined into a single executable `.sql` file for easy setup.

---

## 📦 Contents

| File | Description |
|------|--------------|
| `CPS510_A5_Group57.sql` | Main SQL script – creates, populates, and queries the database |
| `README.md` | Project documentation |
| *(Optional)* `.sh` scripts | Original shell-based scripts used for automation (`menu.sh`, `create_tables.sh`, etc.) |

---

## 🧩 Features

- **Automated Database Setup**
  - Drops existing tables (if any)
  - Creates all required tables with constraints and relationships
  - Populates initial dataset (users, staff, students, products, orders, etc.)
- **Views for Reporting**
  - `STAFF_REPORT_SUMMARY`
  - `VW_TOP_RATED_PRODUCTS`
  - `VW_SALES_SUMMARY`
- **Advanced SQL Queries**
  - Grouping and filtering (`GROUP BY`, `HAVING`)
  - Subqueries with `EXISTS`
  - Set operations (`UNION`, `MINUS`)
  - Aggregations (`COUNT`, `SUM`, `AVG`)

---

## ⚙️ Setup Instructions

### **Option 1 – Run in Oracle SQL Developer**
1. Open Oracle SQL Developer (or any SQL client connected to TMU’s Oracle server).
2. Connect using your **student Oracle credentials**.
3. Open the file:
   ```sql
   @CPS510_A5_Group57.sql
   ```
4. Execute the script.
5. View results in the output panel.

### **Option 2 – Run in SQL*Plus (Command Line)**
```bash
sqlplus64 cs_username/cs_password@(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(Host=oracle.scs.ryerson.ca)(Port=1521))(CONNECT_DATA=(SID=orcl))) @CPS510_A5_Group57.sql
```

---

## 🧱 Database Schema Overview

**Tables:**
- `USERS` – Base entity for all users (students, staff)
- `STUDENT`, `STAFF` – Subtypes referencing `USERS`
- `PRODUCT`, `ORDERS`, `ORDER_PRODUCT` – Core e-commerce entities
- `PAYMENT`, `REPORT`, `REVIEW`, `RETURNREQUEST` – Supporting modules

**Relationships:**
- `USERS` ↔ `ORDERS` (1-to-many)
- `ORDERS` ↔ `ORDER_PRODUCT` ↔ `PRODUCT`
- `STAFF` ↔ `REPORT`
- `PRODUCT` ↔ `REVIEW` and `RETURNREQUEST`

---

## 🧠 Example Outputs

**1️⃣ Staff Report Summary**
```sql
SELECT * FROM STAFF_REPORT_SUMMARY;
```

**2️⃣ Top Rated Products**
```sql
SELECT * FROM VW_TOP_RATED_PRODUCTS;
```

**3️⃣ High-Earning Departments**
```sql
SELECT Department, SUM(Salary)
FROM Staff
GROUP BY Department
HAVING SUM(Salary) > 60000;
```

---

## 👥 Authors

**Group 57**  
- Eshwar Vetrichelvan  
- Ashwin Jakanathan  
- Jihan Chowdury  
- Clara Lee  
- David Wong  
- Jassar Surinder  

---

## 🧾 License

This project is provided for **educational use only** under the [MIT License](LICENSE).

---

## 🏫 Course Information

**Course:** CPS 510 — Database Systems  
**Institution:** Toronto Metropolitan University (TMU)  
**Semester:** Fall 2025  
**Instructor:** *[Insert instructor name]*  

---

## ⭐ Acknowledgments

Special thanks to TMU’s Oracle Database environment and the CPS510 teaching team for providing the infrastructure and guidance that made this project possible.
