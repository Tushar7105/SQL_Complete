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

## JOINS
### INNER JOIN
```sql
  SELECT * FROM employees AS em
  INNER JOIN employee_details AS ed
    ON em.employeeId = ed.employeeId
```
`INNER JOIN` will join the tables based on the key specified and the merged result will only contain for key values present in both the tables

### LEFT OUTER JOIN
```sql
  SELECT * FROM employees AS em
  LEFT JOIN employee_details AS ed
    ON em.employeeId = ed.employeeId
```
`LEFT JOIN` will join the tables based on the key specified and the merged result will only contain for all key values present in left table<br>
> If there is no corresponding value in right table then those field will be marked null but shown in the result
### RIGTH OUTER JOIN
```sql
  SELECT * FROM employees AS em
  RIGHT JOIN employee_details AS ed
    ON em.employeeId = ed.employeeId
```
`RIGHT JOIN` will join the tables based on the key specified and the merged result will only contain for all key values present in right table<br>
> If there is no corresponding value in left table then those field will be marked null but shown in the result

## UNION
```sql
  SELECT name, age, "OLD" as label FROM employee WHERE age >= 55
  UNION
  SELECT name, age, "FEMALE" as label FROM employee WHERE age < 55 AND gender="FEMALE"
```
Union is used to merge the result of 2 queries **by default only unique** values are returned in union<br>
The fields selected in UNION queries should always be same to avoid discrepancies.

## STRING functions
1. LENGTH
   > LENGTH(str) will return length of str.
2. UPPER and LOWER
   > will return string in all uppercase / lowercase
3. TRIM
   > will trim the wide spaces from left and right of string. `LTRIM` for left trim and `RTRIM` for right trim.
4. LEFT and RIGHT
   > will accept 2 args `(str, size)` will return prefi/suffix of str of length `size`.
5. SUBSTRING
   > will take 3 args `(str, pos, len)`
6. REPLACE
   > will accept 3 arg `(str, seq1, seq2)` , will replace all occurance of `seq1` with `seq2`.
7. LOCATE
   > will accept 2 args `(seq, str)` , will locate the occurance of `seq` in `str`.
8. CONCAT
   > will take 3 argst `(str1, sep, str2)` , will concatinate `str1` and `str2` seperated by `sep`.<br>
   > the seperator argument is **optional**
