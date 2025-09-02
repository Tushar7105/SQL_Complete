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
