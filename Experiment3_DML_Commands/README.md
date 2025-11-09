 # Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**

<img width="821" height="281" alt="image" src="https://github.com/user-attachments/assets/8c7f0252-9f2d-4c5d-b97c-03b96d051f5f" />
```
UPDATE employees
SET EMAIL = 'Unavailable';
```

**Output:**

<img width="811" height="291" alt="image" src="https://github.com/user-attachments/assets/2f066438-2186-422f-b8c3-560678a4f626" />


**Question 2**

<img width="817" height="424" alt="image" src="https://github.com/user-attachments/assets/a74e8234-5bc7-493f-ab10-5f6cd13dc7ba" />

```
UPDATE suppliers
SET supplier_name = UPPER(supplier_name)
WHERE contact_person LIKE '%Singh%';
```
**Output:**

<img width="813" height="287" alt="image" src="https://github.com/user-attachments/assets/a15311ed-7591-4b3f-ab77-c02f1eda7dc7" />


**Question 3**
<img width="818" height="370" alt="image" src="https://github.com/user-attachments/assets/d9ba9344-b1d6-4be8-8e49-237de15b6000" />

```
UPDATE products
SET reorder_lvl = ROUND(reorder_lvl * 1.3)
WHERE category = 'Food'
    AND quantity < (reorder_lvl * 0.5);
```
**Output:**

<img width="803" height="300" alt="image" src="https://github.com/user-attachments/assets/1b748c9f-aad5-41c3-ab63-fea1cff48996" />


**Question 4**

<img width="823" height="397" alt="image" src="https://github.com/user-attachments/assets/95386136-bb14-47ef-bfe3-8b182749b5c4" />

```
UPDATE products
SET reorder_lvl = ROUND(reorder_lvl * 0.7)
WHERE cost_price > 50
AND quantity < 100;
```
**Output:**

<img width="812" height="341" alt="image" src="https://github.com/user-attachments/assets/f7ff0aac-b88b-4f1f-b134-ac9b24fba8ca" />

**Question 5**

<img width="834" height="334" alt="image" src="https://github.com/user-attachments/assets/01f7cbd1-2f9a-4b82-939c-eb9a931daeff" />

```
UPDATE employees
SET salary = CASE
                    WHEN department_id = 40 THEN ROUND(salary * 1.25)
                    WHEN department_id = 90 THEN ROUND(salary * 1.15)
                    WHEN department_id = 110 THEN ROUND(salary * 1.10)
                    ELSE salary
                    END
WHERE department_id IN (40,90,110);
```


**Output:**

<img width="825" height="340" alt="image" src="https://github.com/user-attachments/assets/7d5bf71b-4cff-4656-8827-56db0a34f5f1" />


**Question 6**

<img width="833" height="368" alt="image" src="https://github.com/user-attachments/assets/aaacfbf0-ea35-4dc2-b1a0-e8e8108fc704" />

```
DELETE FROM Customer
WHERE LOWER(CUST_NAME) LIKE '%holmes%';
```
**Output:**

<img width="815" height="418" alt="image" src="https://github.com/user-attachments/assets/e97d20ee-e1d3-4685-85cd-b055a220c680" />


**Question 7**

<img width="829" height="480" alt="image" src="https://github.com/user-attachments/assets/a16ab649-1a7f-4085-ad97-fbadcdc5e837" />


```
DELETE FROM Surgeries
WHERE surgery_id = 3;
```
**Output:**

<img width="836" height="318" alt="image" src="https://github.com/user-attachments/assets/23d1eb5c-c394-4a28-b11e-a723ff4fddf6" />


**Question 8**

<img width="820" height="159" alt="image" src="https://github.com/user-attachments/assets/ea660f56-b6a7-4697-8eb4-fcc23967ea42" />

```
DELETE FROM Doctors
WHERE doctor_id = 1;
```

**Output:**

<img width="827" height="230" alt="image" src="https://github.com/user-attachments/assets/adf99ce3-3342-427b-a2bf-66df996a84b7" />


**Question 9**

<img width="818" height="349" alt="image" src="https://github.com/user-attachments/assets/961d7e12-0bc6-4287-b975-235890bfeea4" />

```
DELETE FROM Doctors
WHERE doctor_id = 1;
```

**Output:**

<img width="824" height="462" alt="image" src="https://github.com/user-attachments/assets/104d8b6c-e5c9-4b03-b37a-c99d532b707f" />

**Question 10**

<img width="827" height="371" alt="image" src="https://github.com/user-attachments/assets/4b5e7f07-eb94-41dd-b85c-0864759ff388" />

```
DELETE FROM Surgeries
WHERE surgery_date = '2024-02-28';  
```

**Output:**

<img width="835" height="314" alt="image" src="https://github.com/user-attachments/assets/3a52171f-1a92-462f-86c6-231ae95bd55b" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
