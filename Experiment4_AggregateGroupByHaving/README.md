# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
 
 
 Write a SQL query that counts the number of unique salespeople. Return number of salespeople.

```
SELECT COUNT(DISTINCT salesman_id) as COUNT from orders
```

**Output:**

<img width="462" height="283" alt="image" src="https://github.com/user-attachments/assets/1934022b-b777-4e1d-882e-220d73fd9ea9" />


**Question 2**

Write a SQL query to find the shortest email address in the customer table?
```
SELECT name,email,MIN(LENGTH(email)) as min_email_length
from customer;
```

**Output:**

<img width="783" height="193" alt="image" src="https://github.com/user-attachments/assets/777da1ba-cd2f-4a5e-8b57-1bd727503331" />


**Question 3**

How many male and female doctors are there in each medical specialty?
```
select Specialty,Gender,count(DoctorID) as TotalDoctors from Doctors
group by Specialty,Gender;

```
**Output:**



**Question 4**

Write SQL query to extract the email domain from each patient's email address and count the number of patients with the same email domain.
```

SELECT SUBSTR(Email,INSTR(Email,'@')+1) AS EmailDomain,Count(*) as TotalPatients
from Patients
group by EmailDomain;

```

**Output:**
<img width="804" height="304" alt="image" src="https://github.com/user-attachments/assets/c6fc19d8-7fdc-4068-a380-ea3d4306f8cf" />


**Question 5**

Write the SQL query that accomplishes the grouping of data by age, calculates the maximum income for each age group, and includes only those age groups where the maximum income is greater than 2,000,000.


```
SELECT age,MAX(income) from employee
group by age
having MAX(income)>2000000;
```
**Output:**

<img width="658" height="341" alt="image" src="https://github.com/user-attachments/assets/2a9be283-9a4c-4ebb-a302-71acfe26299c" />


**Question 6**

Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the total salary sum for each group, and excludes groups where the total salary sum is not greater than 5000.
```
SELECT (age/5)*5 as age_group,SUM(salary) from customer1
group by (age/5)*5
having sum(salary)>5000;
```
**Output:**

<img width="641" height="328" alt="image" src="https://github.com/user-attachments/assets/10549bbc-a73a-406f-b28d-e4891fdf1d24" />


**Question 7**

Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the average age for each group, and excludes groups where the average age is not less than 24.
```
SELECT (age/5)*5 as age_group,AVG(age) 
from customer1
group by (age/5)*5
having AVG(age) <24;

```
**Output:**

<img width="651" height="275" alt="image" src="https://github.com/user-attachments/assets/09251a69-c67d-49df-9d54-da0c8983aec3" />


**Question 8**

Write a SQL query to return the total number of rows in the 'customer' table where the city is Noida.
```
SELECT COUNT(*) as COUNT FROM Customer
where city='Noida';
```
**Output:**

<img width="510" height="280" alt="image" src="https://github.com/user-attachments/assets/58ee2935-4700-43a9-9d01-940a1894585f" />


**Question 9**

What is the most common diagnosis among patients?
```
SELECT Diagnosis,count(*) as DiagnosisCount from MedicalRecords 
Group BY Diagnosis
order by DiagnosisCount DESC
LIMIT 1;
```
**Output:**

<img width="807" height="223" alt="image" src="https://github.com/user-attachments/assets/7ff1767e-363c-4598-b306-b1445c03a34a" />


**Question 10**

Write the SQL query that accomplishes the selection of product which has lowest price in each category from the "products" table and includes only those products where the minimum price is less than 10.
```
SELECT category_id,min(Price) as Price  from products
group by category_id
having min(Price)<10;
```
**Output:**

<img width="739" height="289" alt="image" src="https://github.com/user-attachments/assets/31145d76-0413-4ffb-b528-3788a249782e" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
