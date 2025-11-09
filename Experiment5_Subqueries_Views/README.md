# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**

<img width="703" height="325" alt="image" src="https://github.com/user-attachments/assets/69274fc5-366f-452f-acb1-04b7c7f75ef8" />

```
select grade, COUNT(*)
from customer
group by grade
having grade > (
select avg(grade)
from customer
where city='New York');
```
**Output:**

<img width="591" height="364" alt="image" src="https://github.com/user-attachments/assets/3ef44af6-23e0-412a-9287-f857e96bb58e" />


**Question 2**


<img width="718" height="415" alt="image" src="https://github.com/user-attachments/assets/263166af-2769-4bde-b559-0d1eb1edd3e1" />

```
select student_name, grade
from grades g1
where grade=(select MIN(grade)
from grades g2
where g2.subject=g1.subject)


```
**Output:**

<img width="764" height="391" alt="image" src="https://github.com/user-attachments/assets/ea7552ef-8581-48a9-ac96-1cf4648aebd3" />


**Question 3**


<img width="720" height="375" alt="image" src="https://github.com/user-attachments/assets/5865e79b-9038-4bc9-86e9-8a225b5a26cd" />



```
select name
from customer
where phone is NOT NULL
AND phone IN(
select phone
from customer
group by phone
having count(*)=1
);

```

**Output:**

<img width="471" height="412" alt="image" src="https://github.com/user-attachments/assets/6440a57c-6af5-4586-b25c-2948b72084b0" />


**Question 4**

<img width="722" height="401" alt="image" src="https://github.com/user-attachments/assets/bd5d1d33-c88c-4e16-8bfc-9fcdd95dea0c" />

```
select id, name, age, city, income from Employee
where age<(
select avg(age) from Employee
where income>250000);


```

**Output:**

<img width="826" height="405" alt="image" src="https://github.com/user-attachments/assets/b4d4fba6-5d48-4f36-a6fe-e31a56ceeee9" />


**Question 5**

<img width="730" height="269" alt="image" src="https://github.com/user-attachments/assets/c0734196-9e53-49be-8622-bb113eb686c2" />

```
select * from Departments
where length(department_name)>
(
select avg(length(department_name))
from Departments)

```

**Output:**

<img width="778" height="364" alt="image" src="https://github.com/user-attachments/assets/06a5e7b2-8b12-4f5a-ac48-3ad00fdee4c6" />


**Question 6**

<img width="734" height="447" alt="image" src="https://github.com/user-attachments/assets/414ebaed-a7c0-4caa-8b3e-d1247b0e6c60" />


```

select commission from salesman
where salesman_id in(
select salesman_id from customer
where city='Paris');

```

**Output:**


<img width="325" height="337" alt="image" src="https://github.com/user-attachments/assets/e7de0afe-4f56-4524-a369-0bc65c7675ed" />


**Question 7**

<img width="724" height="421" alt="image" src="https://github.com/user-attachments/assets/e5755c68-e513-4208-9063-1a8e6bdc5649" />

```

select * from CUSTOMERS
where id in(
select ID from customers
where SALARY>4500);

```

**Output:**

<img width="823" height="313" alt="image" src="https://github.com/user-attachments/assets/3df1f0a2-7f5a-4079-86e9-15a82c9103b1" />


**Question 8**

<img width="724" height="437" alt="image" src="https://github.com/user-attachments/assets/34a6dd80-9f79-4db8-9383-6973f648b260" />

```

select o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
from orders o
join salesman s on o.salesman_id=s.salesman_id
where s.city='New York';

```

**Output:**


<img width="825" height="369" alt="image" src="https://github.com/user-attachments/assets/e5c73bc4-95b0-4416-94b7-92922b633535" />

**Question 9**

<img width="725" height="362" alt="image" src="https://github.com/user-attachments/assets/50633059-a331-4bd7-925c-5045426867b9" />

```
select * from CUSTOMERS
where id in(
select ID from customers
where ADDRESS='Delhi' and AGE<30);

```

**Output:**

<img width="814" height="235" alt="image" src="https://github.com/user-attachments/assets/2412e5af-a253-46b0-aa96-8b336be6e2e5" />


**Question 10**

<img width="700" height="453" alt="image" src="https://github.com/user-attachments/assets/94ac0211-557e-41ba-9d68-364f3fd87c52" />

```

select o.ord_no, o.purch_amt, o.ord_date, o.customer_id, o.salesman_id
from orders o
join salesman s on o.salesman_id=s.salesman_id
where s.city='New York';
```

**Output:**

<img width="831" height="366" alt="image" src="https://github.com/user-attachments/assets/85e65f3c-33e4-4530-b500-e2949d936658" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
