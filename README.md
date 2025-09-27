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


