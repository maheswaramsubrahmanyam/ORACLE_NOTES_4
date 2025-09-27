# ORACLE_NOTES_4


---

#  Student Database – SQL Practice

##  Aim

To create a table `student010` with constraints:

* Student name (`sname`) must not be `NULL`.
* Marks (`m1` and `m2`) must lie between **0 and 100**.

---

##  Algorithm

1. Open **SQL Plus**

   ```bash
   Start → Programs → SQL Plus
   ```

2. Create a table `student010` with constraints:

   ```sql
   CREATE TABLE student010 (
       sname VARCHAR2(10) NOT NULL,
       sno NUMBER(5) PRIMARY KEY,
       m1 NUMBER(3) CHECK (m1 >= 0 AND m1 <= 100),
       m2 NUMBER(3) CHECK (m2 >= 0 AND m2 <= 100)
   );
   ```

3. Insert student details:

   ```sql
   INSERT INTO student010 VALUES ('Reka', 100, 90, 80);
   INSERT INTO student010 VALUES ('Vicky', 101, 60, 60);
   INSERT INTO student010 VALUES ('Raju', 102, 30, 20);
   INSERT INTO student010 VALUES ('Ramu', 103, 50, 45);
   INSERT INTO student010 VALUES ('Arun', 104, 15, 12);
   ```

4. Display all student records:

   ```sql
   SELECT * FROM student010;
   ```

5. Retrieve specific student names (Reka, Vicky, Raju, Arun):

   ```sql
   SELECT * 
   FROM student010
   WHERE sname = 'Reka'
      OR sname = 'Vicky'
      OR sname = 'Raju'
      OR sname = 'Arun';
   ```

6. Retrieve students based on **Total Marks**:

   ```sql
   SELECT * 
   FROM student010
   WHERE (m1 + m2) >= 120 
     AND (m1 + m2) <= 150;
   ```

7. Save the program:

   ```sql
   COMMIT;
   ```

8. Close SQL Plus.

---

##  Result

* A table `student010` is created successfully with given constraints.
* Student records are inserted and queries are executed correctly to filter data.

---

##  Explanation

* **Constraints**: Ensure data validity (name cannot be null, marks must be between 0–100).
* **Primary Key**: `sno` uniquely identifies each student.
* **CHECK Constraint**: Used for validation of marks.
* **Queries**:

  * `SELECT *` → displays all records.
  * `WHERE` with `OR` → filters specific student names.
  * `WHERE (m1+m2)` → calculates and filters based on total marks.
* **COMMIT**: Saves the changes permanently in the database.

---



#  SQL Exercises – Employee & Relational Operations

---

##  Exercise 2 – Employee Database

###  Aim

To create an **Employee Table** using SQL and perform **basic queries** like `INSERT`, `UPDATE`, `DELETE`, and `SELECT`.

---

###  Algorithm

**Step 1:** Open Oracle SQL Plus.

```bash
Start → Programs → Oracle SQL Plus
```

**Step 2:** Create a table `company10` with constraints.

```sql
CREATE TABLE company10 (
    cname      VARCHAR2(10) NOT NULL,
    ename      VARCHAR2(10),
    location   VARCHAR2(15),
    salary     NUMBER(10) CHECK (salary > 0),
    designation VARCHAR2(15),
    manager_no NUMBER(10)
);
```

**Step 3:** Insert sample records into the table.

```sql
INSERT INTO company10 VALUES ('TCS', 'Anil', 'Delhi', 55000, 'Programmer', 1001);
INSERT INTO company10 VALUES ('CTS', 'Raju', 'Mysore', 45000, 'Programmer', 1045);
INSERT INTO company10 VALUES ('Capgemini', 'Ramu', 'Bangalore', 60000, 'Team Leader', 1006);
INSERT INTO company10 VALUES ('HCL', 'Adithya', 'Chennai', 40000, 'HR', 1010);
INSERT INTO company10 VALUES ('Wipro', 'Reshmi', 'Nagpur', 23000, 'Analyst', 1020);
```

**Step 4:** View the table.

```sql
SELECT * FROM company10;
```

**Step 5:** Perform queries.

* **Query 1: Update location**

```sql
UPDATE company10 SET location = 'Mumbai' WHERE location = 'Nagpur';
SELECT * FROM company10;
```

* **Query 2: Delete record**

```sql
DELETE FROM company10 WHERE location = 'Delhi';
SELECT * FROM company10;
```

* **Query 3: Select by company name**

```sql
SELECT location FROM company10 WHERE cname = 'CTS';
```

* **Query 4: Select manager number of salary 60000**

```sql
SELECT manager_no FROM company10 WHERE salary = 60000;
```

**Step 6:** Save changes.

```sql
COMMIT;
```

---

###  Result

* The `company10` table was successfully created.
* Records were inserted, updated, deleted, and retrieved using SQL queries.

---

###  Second Table – CompanyB10

**Step 1: Create another table.**

```sql
CREATE TABLE companyB10 (
    designation VARCHAR2(25),
    basic_pay   NUMBER(5),
    allowance   NUMBER(3)
);
```

**Step 2: Insert data.**

```sql
INSERT INTO companyB10 VALUES ('Senior Engineer', 11000, 200);
INSERT INTO companyB10 VALUES ('Assistant Engineer', 9000, 250);
INSERT INTO companyB10 VALUES ('Trainee', 4000, 150);
```

**Step 3: View the table.**

```sql
SELECT * FROM companyB10;
```

---

##  Exercise 3 – Relational Operations

###  Aim

To perform a **comparative analysis** between data from two competitor companies using relational operations.

---

###  Algorithm

**Step 1:** Open Oracle SQL Plus.

**Step 2:** Create tables.

```sql
CREATE TABLE companyA10 (
    designation VARCHAR2(25),
    basic_pay   NUMBER(5),
    allowance   NUMBER(3)
);

CREATE TABLE companyB10 (
    designation VARCHAR2(25),
    basic_pay   NUMBER(5),
    allowance   NUMBER(3)
);
```

**Step 3:** Insert sample data.

```sql
INSERT INTO companyA10 VALUES ('Senior Engineer', 12000, 500);
INSERT INTO companyA10 VALUES ('Assistant Engineer', 10000, 200);

INSERT INTO companyB10 VALUES ('Senior Engineer', 11000, 200);
INSERT INTO companyB10 VALUES ('Assistant Engineer', 9000, 250);
INSERT INTO companyB10 VALUES ('Trainee', 4000, 150);
```

**Step 4:** Relational Queries

* **Query 1: Compare designations**

```sql
SELECT companyA10.designation, companyB10.designation
FROM companyA10, companyB10;
```

* **Query 2: Compare basic pay**

```sql
SELECT companyA10.designation, companyA10.basic_pay, companyB10.basic_pay
FROM companyA10, companyB10;
```

* **Query 3: Select common designations**

```sql
SELECT companyA10.designation
FROM companyA10, companyB10
WHERE companyA10.designation = companyB10.designation;
```

* **Query 4: Compare designations and salaries**

```sql
SELECT companyA10.designation, companyA10.basic_pay, companyB10.basic_pay
FROM companyA10, companyB10
WHERE companyA10.designation = companyB10.designation
  AND companyA10.basic_pay = companyB10.basic_pay;
```

* **Query 5: List designation and pay differences**

```sql
SELECT companyA10.designation, companyA10.basic_pay, companyB10.basic_pay
FROM companyA10, companyB10
WHERE companyA10.designation = companyB10.designation;
```

---

###  Result

* Both company tables were created.
* Comparative analysis between companies using **relational queries** was successfully executed.

---
