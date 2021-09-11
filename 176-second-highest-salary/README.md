# 176. Second Highest Salary

## SQL Schema
```sql
Create table If Not Exists Employee (Id int, Salary int)
Truncate table Employee
insert into Employee (Id, Salary) values ('1', '100')
insert into Employee (Id, Salary) values ('2', '200')
insert into Employee (Id, Salary) values ('3', '300')
```

Write a SQL query to get the second highest salary from the Employee table.
```
+----+--------+
| Id | Salary |
+----+--------+
| 1  | 100    |
| 2  | 200    |
| 3  | 300    |
+----+--------+
```

For example, given the above Employee table, the query should return 200 as the second highest salary. If there is no second highest salary, then the query should return null.
```
+---------------------+
| SecondHighestSalary |
+---------------------+
| 200                 |
+---------------------+
```

## My Solution

```python
SELECT (
SELECT DISTINCT Salary 
FROM Employee
ORDER BY 1 DESC
LIMIT 1 OFFSET 1) AS 'SecondHighestSalary'
```

## My Submission
![mysub1](mysub1.png)
![mysub2](mysub2.png)