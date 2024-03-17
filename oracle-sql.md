# SQL statement with Oracle

6.1 All Columns, All Row

```sql
SELECT staffNo, fName, lName,
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
WHERE city = 'London' OR city = 'Glasgow';
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

6.8 Set Membership

```sql
SELECT staffNo, fName, lName, position
FROM Staff
WHERE position IN ('Manager', 'Supervisor');
```

```sql
SELECT staffNo, fName, lName, position
FROM Staff
WHERE position='Manager' OR
position='Supervisor';
```

6.9 Pattern Matching

```sql
SELECT clientNo, fName, lName, Region, telNo
FROM client
WHERE Region LIKE '%Glasgow%';
```

6.10 NULL Search Condition

```sql
SELECT clientID, viewDate
FROM Viewing
WHERE propertyNo = 'PG4' AND
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
WHERE viewDate BETWEEN '1-May-04'
AND '31-May-04';
```

6.15 Use of COUNT and SUM

```sql
SELECT COUNT(staffNo) AS myCount,
SUM(salary) AS mySum
FROM Staff
WHERE position = 'Manager';
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

6.20 Subquery with Aggregate

```sql
SELECT staffNo, fName, lName, position,
salary - (SELECT AVG(salary) FROM Staff) As SalDiff
FROM Staff
WHERE salary >
(SELECT AVG(salary)
FROM Staff);
```

```sql
SELECT staffNo, fName, lName, position,
salary - 17000 As salDiff
FROM Staff
WHERE salary > 17000;
```

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

6.22 Use of ANY/SOME

```sql
SELECT staffNo, fName, lName, position, salary
FROM Staff
WHERE salary > SOME
(SELECT salary
FROM Staff
WHERE branchNo = 'B003');
```

6.23 Use of ALL

```sql
SELECT staffNo, fName, lName, position, salary
FROM Staff
WHERE salary > ALL
(SELECT salary
FROM Staff
WHERE branchNo = 'B003');
```

6.24 Simple Join

```sql
SELECT c.clientNo, fName, lName,
propertyNo, 'comments'
FROM Client c, Viewing v
WHERE c.ID = v.clientID;
```

6.25 Sorting a join

```sql
SELECT s.branchNo, s.staffNo, fName, lName,
propertyNo
FROM Staff s, PropertyForRent p
WHERE s.staffNo = p.staffNo
ORDER BY s.branchNo, s.staffNo, propertyNo;
```

6.26 Three Table Join

```sql
SELECT b.branchNo, b.city, s.staffNo, fName, lName,
propertyNo
FROM Branch b, Staff s, PropertyForRent p
WHERE b.branchNo = s.branchNo AND
s.staffNo = p.staffNo
ORDER BY b.branchNo, s.staffNo, propertyNo;
```

6.27 Multiple Grouping Columns

```sql
SELECT s.branchNo, s.staffNo, COUNT(*) AS myCount
FROM Staff s, PropertyForRent p
WHERE s.staffNo = p.staffNo
GROUP BY s.branchNo, s.staffNo
ORDER BY s.branchNo, s.staffNo;
```

6.28 Left Outer Join

```sql
SELECT b.*, p.*
FROM Branch b LEFT JOIN
PropertyForRent p ON b.City = p.City;
```

6.29 Right Outer Join

```sql
SELECT b.*, p.*
FROM Branch b RIGHT JOIN
PropertyForRent p ON b.City = p.City;
```

6.30 Full Outer Join

```sql
SELECT b.*, p.*
FROM Branch b FULL JOIN
PropertyForRent p ON b.City = p.City;

```

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

```sql
SELECT staffNo, fName, lName, position FROM Staff
WHERE true;
```

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

6.33 Use of INTERSECT

```sql
SELECT city FROM Branch
INTERSECT
SELECT city FROM PropertyForRent;
```

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

6.36 INSERT using Defaults

```sql
INSERT INTO Staff (staffNo, fName, lName,
position, salary, branchNo)
VALUES ('SG44', 'Anne', 'Jones',
'Assistant', 8100, 'B003');
```

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

6.38/39 UPDATE All Rows

```sql
UPDATE Staff
SET salary = salary*1.03;
```

```sql
UPDATE Staff
SET salary = salary*1.05
WHERE position = 'Manager';
```

6.40 UPDATE Multiple Columns

```sql
UPDATE Staff
SET position = 'Manager', salary = 18000
WHERE staffNo = 'SG14';
```

6.41/42 DELETE Specific Rows

```sql
DELETE FROM Viewing
WHERE propertyNo = 'PG4';
```

```sql
DELETE FROM Viewing;
```
