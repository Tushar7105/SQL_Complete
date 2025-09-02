# SQL_Complete

## SELECT 
```sql
  SELECT {fieldNames} FROM {database}.{table};
```
we need not always specify database, by default the SQL will look for the table in current database<br>
we can also use multiple funtion/operations here like `DISTINCT`, `LIMIT`
### PEMDAS
> `PEMDAS` stands for Parentheses, Exponents, Multiplication, Division, Addition, and Subtraction.<br>
> It describes the precedance of operators in SQL query.
```sql
  SELECT name, salary, (salary+10)*2 FROM employees;
```
## WHERE
```sql
  SELECT * FROM {table} WHERE {Condition};
```
we can also logically combine multiple logical conditions by useing logical operations like `AND`, `OR`, `NOT`
## LIKE
> the `LIKE` statement is used to look for some sequence in targeted field
```sql
  SELECT name, salary FROM employees WHERE name LIKE 'A%';
```
`%` means any number of characters<br> 
`_` specifies the number of characters
## GROUP BY
```sql
  SELECT occupation, gender, AVG(salary), MIN(salary), MAX(salary)
  FROM employees GROUP BY occupation, gender;
```
If a `SELECT` statement includes columns that are not part of the `GROUP BY` clause, those columns must be used within an aggregate function
## ORDER BY
```sql
  SELECT * FROM employees ORDER BY name;
```
we can also specify `ASC` for ascending or `DESC` for descending
```sql
  SELECT * FROM employees ORDER BY gender, age DESC;
```
nultiple field based sorting. Here all females are listed first in descending order of age
## HAVING 
It is very similar to `WHERE` caluse just that it works at column level 
```sql
  SELECT occupation, AVG(salary)
  FROM employees
  WHERE occupation LIKE '%manager%'
  GROUP BY occupation
  HAVING AVG(salary) > 50000;
```
> The `WHERE` will work before `GROUP BY` and shrink the overall selection and hence cant be used on aggregate functions<br>
> On the other hand `HAVING` will work after grouping filtering based on aggregate functions

