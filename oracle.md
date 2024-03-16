# SQL statement with Oracle

6.1 All Columns, All Row

```sql
SELECT staffNo, fName, lName, address,
position, sex, DOB, salary, branchNo
FROM Staff;
```

```sql
SELECT *
FROM Staff;
```

6.2 Specific Columns, All Rows

```sql
SELECT staffNo, fName, lName, salary
FROM Staff;
```

6.3 Use of DISTINCT

```sql
SELECT propertyNo
FROM Viewing;
```

```sql
SELECT DISTINCT propertyNo
FROM Viewing;
```

6.4 Calculated Fields

```sql
SELECT staffNo, fName, lName, salary/12
FROM Staff;
```

To name column, use AS clause

```sql
SELECT staffNo, fName, lName, salary/12
AS monthlySalary
FROM Staff;
```

6.5 Comparison Search Condition

```sql
SELECT staffNo, fName, lName, position, salary
FROM Staff
WHERE salary > 10000;
```

List addresses of all branch offices in London or Glasgow.

```sql
SELECT *
FROM Branch
WHERE city = ‘London’ OR city = ‘Glasgow’;
```

6.7 Range Search Condition

```sql
SELECT staffNo, fName, lName, position, salary
FROM Staff
WHERE salary BETWEEN 20000 AND 30000;
```

BETWEEN does not add much to SQL’s expressive power.

```sql
SELECT staffNo, fName, lName, position, salary
FROM Staff
WHERE salary>=20000 AND salary <= 30000;
```

• Useful, though, for a range of values.

6.8 Set Membership

```sql
SELECT staffNo, fName, lName, position
FROM Staff
WHERE position IN (‘Manager’, ‘Supervisor’);
```

```sql
SELECT staffNo, fName, lName, position
FROM Staff
WHERE position=‘Manager’ OR
position=‘Supervisor’;
```

6.9 Pattern Matching

```sql
SELECT ownerNo, fName, lName, address, telNo
FROM PrivateOwner
WHERE address LIKE ‘%Glasgow%’;
```

6.10 NULL Search Condition

```sql
SELECT clientNo, viewDate
FROM Viewing
WHERE propertyNo = ‘PG4’ AND
comment IS NULL;
```

6.11 Single Column Ordering

```sql
SELECT staffNo, fName, lName, salary
FROM Staff
ORDER BY salary DESC;
```

6.12 Multiple Column Ordering

```sql
SELECT propertyNo, type, rooms, rent
FROM PropertyForRent
ORDER BY type;
```

```sql
SELECT propertyNo, type, rooms, rent
FROM PropertyForRent
ORDER BY type, rent DESC;
```

6.13 Use of COUNT(\*)

```sql
SELECT COUNT(*) AS myCount
FROM PropertyForRent
WHERE rent > 350;
```

6.14 Use of COUNT(DISTINCT)

```sql
SELECT COUNT(DISTINCT propertyNo) AS myCount
FROM Viewing
WHERE viewDate BETWEEN ‘1-May-04’
AND ‘31-May-04’;
```

6.15 Use of COUNT and SUM

```sql
SELECT COUNT(staffNo) AS myCount,
SUM(salary) AS mySum
FROM Staff
WHERE position = ‘Manager’;
```

6.16 Use of MIN, MAX, AVG

```sql
SELECT MIN(salary) AS myMin,
MAX(salary) AS myMax,
AVG(salary) AS myAvg
FROM Staff;
```

6.17 Use of GROUP BY

```sql
SELECT branchNo,
COUNT(staffNo) AS myCount,
SUM(salary) AS mySum
FROM Staff
GROUP BY branchNo
ORDER BY branchNo;
```

6.18 Use of HAVING

```sql
SELECT branchNo,
COUNT(staffNo) AS myCount,
SUM(salary) AS mySum
FROM Staff
GROUP BY branchNo
HAVING COUNT(staffNo) > 1
ORDER BY branchNo;
```
