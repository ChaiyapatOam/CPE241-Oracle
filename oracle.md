# SQL statement with Oracle

6.1 All Columns, All Row

```sql
SELECT staffNo, fName, lName,
position, sex, DOB, salary, branchNo
FROM Staff;
```

| Oracle                 |
| ---------------------- |
| ![alt text](image.png) |

| MariaDB                  |
| ------------------------ |
| ![alt text](image-1.png) |

```sql
SELECT *
FROM Staff;
```

| Oracle                   |
| ------------------------ |
| ![alt text](image-2.png) |

| MariaDB                  |
| ------------------------ |
| ![alt text](image-3.png) |

6.2 Specific Columns, All Rows

```sql
SELECT staffNo, fName, lName, salary
FROM Staff;
```

| Oracle                   |
| ------------------------ |
| ![alt text](image-4.png) |

| MariaDB                  |
| ------------------------ |
| ![alt text](image-5.png) |

6.3 Use of DISTINCT

```sql
SELECT propertyNo
FROM Viewing;
```

| Oracle                   |
| ------------------------ |
| ![alt text](image-6.png) |

| MariaDB                  |
| ------------------------ |
| ![alt text](image-7.png) |

```sql
SELECT DISTINCT propertyNo
FROM Viewing;
```

| Oracle                   |
| ------------------------ |
| ![alt text](image-8.png) |

| MariaDB                  |
| ------------------------ |
| ![alt text](image-9.png) |

6.4 Calculated Fields

```sql
SELECT staffNo, fName, lName, salary/12
FROM Staff;
```

| Oracle                    |
| ------------------------- |
| ![alt text](image-10.png) |

| MariaDB                   |
| ------------------------- |
| ![alt text](image-11.png) |

To name column, use AS clause

```sql
SELECT staffNo, fName, lName, salary/12
AS monthlySalary
FROM Staff;
```

| Oracle                    |
| ------------------------- |
| ![alt text](image-12.png) |

| MariaDB                   |
| ------------------------- |
| ![alt text](image-13.png) |

6.5 Comparison Search Condition

```sql
SELECT staffNo, fName, lName, position, salary
FROM Staff
WHERE salary > 10000;
```

| Oracle                    |
| ------------------------- |
| ![alt text](image-14.png) |

| MariaDB                   |
| ------------------------- |
| ![alt text](image-15.png) |

List addresses of all branch offices in London or Glasgow.

```sql
SELECT *
FROM Branch
WHERE city = 'London' OR city = 'Glasgow';
```

| Oracle                    |
| ------------------------- |
| ![alt text](image-17.png) |

| MariaDB                   |
| ------------------------- |
| ![alt text](image-16.png) |

6.7 Range Search Condition

```sql
SELECT staffNo, fName, lName, position, salary
FROM Staff
WHERE salary BETWEEN 20000 AND 30000;
```

| Oracle                    |
| ------------------------- |
| ![alt text](image-18.png) |

| MariaDB                   |
| ------------------------- |
| ![alt text](image-19.png) |

BETWEEN does not add much to SQL’s expressive power.

```sql
SELECT staffNo, fName, lName, position, salary
FROM Staff
WHERE salary>=20000 AND salary <= 30000;
```

| Oracle                    |
| ------------------------- |
| ![alt text](image-20.png) |

| MariaDB                   |
| ------------------------- |
| ![alt text](image-21.png) |

6.8 Set Membership

```sql
SELECT staffNo, fName, lName, position
FROM Staff
WHERE position IN (‘Manager’, ‘Supervisor’);
```

| Oracle                    |
| ------------------------- |
| ![alt text](image-20.png) |

| MariaDB                   |
| ------------------------- |
| ![alt text](image-21.png) |

```sql
SELECT staffNo, fName, lName, position
FROM Staff
WHERE position=‘Manager’ OR
position=‘Supervisor’;
```

| Oracle                    |
| ------------------------- |
| ![alt text](image-20.png) |

| MariaDB                   |
| ------------------------- |
| ![alt text](image-21.png) |

6.9 Pattern Matching

```sql
SELECT clientNo, fName, lName, Region, telNo
FROM client
WHERE Region LIKE '%Glasgow%';
```

| Oracle                    |
| ------------------------- |
| ![alt text](image-31.png) |

| MariaDB                   |
| ------------------------- |
| ![alt text](image-30.png) |

6.10 NULL Search Condition

```sql
SELECT clientID, viewDate
FROM Viewing
WHERE propertyNo = 'PG4' AND
comment IS NULL;
```

| Oracle                    |
| ------------------------- |
| ![alt text](image-23.png) |

| MariaDB                   |
| ------------------------- |
| ![alt text](image-22.png) |

6.11 Single Column Ordering

```sql
SELECT staffNo, fName, lName, salary
FROM Staff
ORDER BY salary DESC;
```

| Oracle                    |
| ------------------------- |
| ![alt text](image-25.png) |

| MariaDB                   |
| ------------------------- |
| ![alt text](image-24.png) |

6.12 Multiple Column Ordering

```sql
SELECT propertyNo, type, rooms, rent
FROM PropertyForRent
ORDER BY type;
```

| Oracle                    |
| ------------------------- |
| ![alt text](image-26.png) |

| MariaDB                   |
| ------------------------- |
| ![alt text](image-27.png) |

```sql
SELECT propertyNo, type, rooms, rent
FROM PropertyForRent
ORDER BY type, rent DESC;
```

| Oracle                    |
| ------------------------- |
| ![alt text](image-28.png) |

| MariaDB                   |
| ------------------------- |
| ![alt text](image-29.png) |

6.13 Use of COUNT(\*)

```sql
SELECT COUNT(*) AS myCount
FROM PropertyForRent
WHERE rent > 350;
```

| Oracle                    |
| ------------------------- |
| ![alt text](image-32.png) |

| MariaDB                   |
| ------------------------- |
| ![alt text](image-33.png) |

6.14 Use of COUNT(DISTINCT)

```sql
SELECT COUNT(DISTINCT propertyNo) AS myCount
FROM Viewing
WHERE viewDate BETWEEN '1-May-04'
AND '31-May-04';
```

| Oracle                    |
| ------------------------- |
| ![alt text](image-34.png) |

| MariaDB                   |
| ------------------------- |
| ![alt text](image-35.png) |

6.15 Use of COUNT and SUM

```sql
SELECT COUNT(staffNo) AS myCount,
SUM(salary) AS mySum
FROM Staff
WHERE position = 'Manager';
```

| Oracle                    |
| ------------------------- |
| ![alt text](image-38.png) |

| MariaDB                   |
| ------------------------- |
| ![alt text](image-37.png) |

6.16 Use of MIN, MAX, AVG

```sql
SELECT MIN(salary) AS myMin,
MAX(salary) AS myMax,
AVG(salary) AS myAvg
FROM Staff;
```

| Oracle                    |
| ------------------------- |
| ![alt text](image-28.png) |

| MariaDB                   |
| ------------------------- |
| ![alt text](image-29.png) |

6.17 Use of GROUP BY

```sql
SELECT branchNo,
COUNT(staffNo) AS myCount,
SUM(salary) AS mySum
FROM Staff
GROUP BY branchNo
ORDER BY branchNo;
```

| Oracle                    |
| ------------------------- |
| ![alt text](image-28.png) |

| MariaDB                   |
| ------------------------- |
| ![alt text](image-29.png) |

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

| Oracle                    |
| ------------------------- |
| ![alt text](image-28.png) |

| MariaDB                   |
| ------------------------- |
| ![alt text](image-29.png) |
