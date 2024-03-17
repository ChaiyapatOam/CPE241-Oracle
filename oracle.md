# SQL statement with Oracle 📑

## 🫂Author

Chaiyapat Meeying 65070501073

## [✨View on Github](https://github.com/ChaiyapatOam/CPE241-Oracle/blob/main/oracle.md)

6.1 All Columns, All Row

```sql
SELECT staffNo, fName, lName,
position, sex, DOB, salary, branchNo
FROM Staff;
```

| Oracle                        |
| ----------------------------- |
| ![alt text](/image/image.png) |

| MariaDB                         |
| ------------------------------- |
| ![alt text](/image/image-1.png) |

```sql
SELECT *
FROM Staff;
```

| Oracle                          |
| ------------------------------- |
| ![alt text](/image/image-2.png) |

| MariaDB                         |
| ------------------------------- |
| ![alt text](/image/image-3.png) |

6.2 Specific Columns, All Rows

```sql
SELECT staffNo, fName, lName, salary
FROM Staff;
```

| Oracle                          |
| ------------------------------- |
| ![alt text](/image/image-4.png) |

| MariaDB                         |
| ------------------------------- |
| ![alt text](/image/image-5.png) |

6.3 Use of DISTINCT

```sql
SELECT propertyNo
FROM Viewing;
```

| Oracle                          |
| ------------------------------- |
| ![alt text](/image/image-6.png) |

| MariaDB                         |
| ------------------------------- |
| ![alt text](/image/image-7.png) |

```sql
SELECT DISTINCT propertyNo
FROM Viewing;
```

| Oracle                          |
| ------------------------------- |
| ![alt text](/image/image-8.png) |

| MariaDB                         |
| ------------------------------- |
| ![alt text](/image/image-9.png) |

6.4 Calculated Fields

```sql
SELECT staffNo, fName, lName, salary/12
FROM Staff;
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-10.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-11.png) |

To name column, use AS clause

```sql
SELECT staffNo, fName, lName, salary/12
AS monthlySalary
FROM Staff;
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-12.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-13.png) |

6.5 Comparison Search Condition

```sql
SELECT staffNo, fName, lName, position, salary
FROM Staff
WHERE salary > 10000;
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-14.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-15.png) |

List addresses of all branch offices in London or Glasgow.

```sql
SELECT *
FROM Branch
WHERE city = 'London' OR city = 'Glasgow';
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-17.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-16.png) |

6.7 Range Search Condition

```sql
SELECT staffNo, fName, lName, position, salary
FROM Staff
WHERE salary BETWEEN 20000 AND 30000;
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-18.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-19.png) |

BETWEEN does not add much to SQL’s expressive power.

```sql
SELECT staffNo, fName, lName, position, salary
FROM Staff
WHERE salary>=20000 AND salary <= 30000;
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-20.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-21.png) |

6.8 Set Membership

```sql
SELECT staffNo, fName, lName, position
FROM Staff
WHERE position IN ('Manager', 'Supervisor');
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-20.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-21.png) |

```sql
SELECT staffNo, fName, lName, position
FROM Staff
WHERE position='Manager' OR
position='Supervisor';
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-20.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-21.png) |

6.9 Pattern Matching

```sql
SELECT clientNo, fName, lName, Region, telNo
FROM client
WHERE Region LIKE '%Glasgow%';
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-31.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-30.png) |

6.10 NULL Search Condition

```sql
SELECT clientID, viewDate
FROM Viewing
WHERE propertyNo = 'PG4' AND
comment IS NULL;
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-23.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-22.png) |

6.11 Single Column Ordering

```sql
SELECT staffNo, fName, lName, salary
FROM Staff
ORDER BY salary DESC;
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-25.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-24.png) |

6.12 Multiple Column Ordering

```sql
SELECT propertyNo, type, rooms, rent
FROM PropertyForRent
ORDER BY type;
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-26.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-27.png) |

```sql
SELECT propertyNo, type, rooms, rent
FROM PropertyForRent
ORDER BY type, rent DESC;
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-28.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-29.png) |

6.13 Use of COUNT(\*)

```sql
SELECT COUNT(*) AS myCount
FROM PropertyForRent
WHERE rent > 350;
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-32.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-33.png) |

6.14 Use of COUNT(DISTINCT)

```sql
SELECT COUNT(DISTINCT propertyNo) AS myCount
FROM Viewing
WHERE viewDate BETWEEN '1-May-04'
AND '31-May-04';
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-34.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-35.png) |

6.15 Use of COUNT and SUM

```sql
SELECT COUNT(staffNo) AS myCount,
SUM(salary) AS mySum
FROM Staff
WHERE position = 'Manager';
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-38.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-37.png) |

6.16 Use of MIN, MAX, AVG

```sql
SELECT MIN(salary) AS myMin,
MAX(salary) AS myMax,
AVG(salary) AS myAvg
FROM Staff;
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-39.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-40.png) |

6.17 Use of GROUP BY

```sql
SELECT branchNo,
COUNT(staffNo) AS myCount,
SUM(salary) AS mySum
FROM Staff
GROUP BY branchNo
ORDER BY branchNo;
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-41.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-42.png) |

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

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-43.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-44.png) |

6.19 Subquery with Equality

```sql
SELECT staffNo, fName, lName, position
FROM Staff
WHERE branchNo =
(SELECT branchNo
FROM Branch
WHERE street = '163 Main St');
```

```sql
SELECT staffNo, fName, lName, position
FROM Staff
WHERE branchNo = 'B003';
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-45.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-46.png) |

6.20 Subquery with Aggregate

```sql
SELECT staffNo, fName, lName, position,
salary - (SELECT AVG(salary) FROM Staff) As SalDiff
FROM Staff
WHERE salary >
(SELECT AVG(salary)
FROM Staff);
```

| Oracle                            |
| --------------------------------- |
| ![alt text](/image/image-101.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-48.png) |

```sql
SELECT staffNo, fName, lName, position,
salary - 17000 As salDiff
FROM Staff
WHERE salary > 17000;
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-49.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-50.png) |

6.21 Nested subquery: use of IN

```sql
SELECT propertyNo, street, city, postcode, type, rooms, rent
FROM PropertyForRent
WHERE staffNo IN
(SELECT staffNo
FROM Staff
WHERE branchNo =
(SELECT branchNo
FROM Branch
WHERE street = '163 Main St'));
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-51.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-52.png) |

6.22 Use of ANY/SOME

```sql
SELECT staffNo, fName, lName, position, salary
FROM Staff
WHERE salary > SOME
(SELECT salary
FROM Staff
WHERE branchNo = 'B003');
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-53.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-54.png) |

6.23 Use of ALL

```sql
SELECT staffNo, fName, lName, position, salary
FROM Staff
WHERE salary > ALL
(SELECT salary
FROM Staff
WHERE branchNo = 'B003');
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-55.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-56.png) |

6.24 Simple Join

```sql
SELECT c.clientNo, fName, lName,
propertyNo, 'comments'
FROM Client c, Viewing v
WHERE c.ID = v.clientID;
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-57.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-58.png) |

6.25 Sorting a join

```sql
SELECT s.branchNo, s.staffNo, fName, lName,
propertyNo
FROM Staff s, PropertyForRent p
WHERE s.staffNo = p.staffNo
ORDER BY s.branchNo, s.staffNo, propertyNo;
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-59.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-60.png) |

6.26 Three Table Join

```sql
SELECT b.branchNo, b.city, s.staffNo, fName, lName,
propertyNo
FROM Branch b, Staff s, PropertyForRent p
WHERE b.branchNo = s.branchNo AND
s.staffNo = p.staffNo
ORDER BY b.branchNo, s.staffNo, propertyNo;
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-62.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-61.png) |

6.27 Multiple Grouping Columns

```sql
SELECT s.branchNo, s.staffNo, COUNT(*) AS myCount
FROM Staff s, PropertyForRent p
WHERE s.staffNo = p.staffNo
GROUP BY s.branchNo, s.staffNo
ORDER BY s.branchNo, s.staffNo;
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-63.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-64.png) |

6.28 Left Outer Join

```sql
SELECT b.*, p.*
FROM Branch b LEFT JOIN
PropertyForRent p ON b.City = p.City;
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-65.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-66.png) |

6.29 Right Outer Join

```sql
SELECT b.*, p.*
FROM Branch b RIGHT JOIN
PropertyForRent p ON b.City = p.City;
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-68.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-67.png) |

6.30 Full Outer Join

```sql
SELECT b.*, p.*
FROM Branch b FULL JOIN
PropertyForRent p ON b.City = p.City;

```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-69.png) |

| MariaDB                                                       |
| ------------------------------------------------------------- |
| MariaDB doesn't has full join![alt text](/image/image-70.png) |

6.31 Query using EXISTS

```sql
SELECT staffNo, fName, lName, position
FROM Staff s
WHERE EXISTS
(SELECT *
FROM Branch b
WHERE s.branchNo = b.branchNo AND
city = 'London');
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-71.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-72.png) |

```sql
SELECT staffNo, fName, lName, position FROM Staff
WHERE true;
```

| Oracle                                                  |
| ------------------------------------------------------- |
| oracle cant where true ![alt text](/image/image-73.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-74.png) |

6.32 Use of UNION

```sql
SELECT city
FROM Branch
WHERE city IS NOT NULL

UNION

SELECT city
FROM PropertyForRent
WHERE city IS NOT NULL;
```

| Oracle                                             |
| -------------------------------------------------- |
| oracle cant use ()![alt text](/image/image-75.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-76.png) |

6.33 Use of INTERSECT

```sql
SELECT city FROM Branch
INTERSECT
SELECT city FROM PropertyForRent;
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-78.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-77.png) |

6.34 Use of EXCEPT

for oracle

```sql
SELECT city FROM Branch
MINUS
SELECT city FROM PropertyForRent;
```

for sql(MariaDB)

```sql
(SELECT city FROM Branch)
EXCEPT
(SELECT city FROM PropertyForRent);
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-80.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-79.png) |

6.35 INSERT ... VALUES

```sql
INSERT INTO Staff
VALUES ('SG16', 'Alan', 'Brown', 'Assistant', 'M',Date'1957-05-
25', 8300, 'B003','12345','0879890001','example@mail.com');
```

this is use for me

```sql
INSERT INTO Staff
VALUES ('SG16', 'Alan', 'Brown', 'Assistant', 'M','1945-10-01 00:00:00', 8300, 'B003','12345','0879890001','example@mail.com');
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-81.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-82.png) |

6.36 INSERT using Defaults

```sql
INSERT INTO Staff (staffNo, fName, lName,
position, salary, branchNo)
VALUES ('SG44', 'Anne', 'Jones',
'Assistant', 8100, 'B003');
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-84.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-83.png) |

Or

```sql
INSERT INTO Staff
VALUES ('SG44', 'Anne', 'Jones', 'Assistant', NULL,
NULL, 8100, 'B003');
```

6.37 INSERT ... SELECT

```sql
INSERT INTO StaffPropCount
(SELECT s.staffNo, fName, lName, COUNT(*)
FROM Staff s, PropertyForRent p
WHERE s.staffNo = p.staffNo
GROUP BY s.staffNo, fName, lName)
UNION
(SELECT staffNo, fName, lName, 0
FROM Staff
WHERE staffNo NOT IN
(SELECT DISTINCT staffNo
FROM PropertyForRent));
```

run this before (to create table)

```sql
create table StaffPropCount (
    staffNo varchar2(50),
    fName varchar2(50),
    lName varchar2(50),
    propCnt number
);
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-87.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-85.png) |

Result
![alt text](/image/image-86.png)

6.38/39 UPDATE All Rows

```sql
UPDATE Staff
SET salary = salary*1.03;
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-88.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-89.png) |

Result
![alt text](/image/image-90.png)

```sql
UPDATE Staff
SET salary = salary*1.05
WHERE position = 'Manager';
```

Result
![alt text](/image/image-92.png)

6.40 UPDATE Multiple Columns

```sql
UPDATE Staff
SET position = 'Manager', salary = 18000
WHERE staffNo = 'SG14';
```

Before
![alt text](/image/image-93.png)
After
![alt text](/image/image-94.png)

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-95.png) |

6.41/42 DELETE Specific Rows

```sql
DELETE FROM Viewing
WHERE propertyNo = 'PG4';
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-96.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-97.png) |

```sql
DELETE FROM Viewing;
```

| Oracle                           |
| -------------------------------- |
| ![alt text](/image/image-99.png) |

| MariaDB                          |
| -------------------------------- |
| ![alt text](/image/image-98.png) |

Result
![alt text](/image/image-100.png)
