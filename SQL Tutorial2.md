# SQL Tutorial

## 1. SQL Intro

### 1) SQL은 무엇인가?

- SQL은 데이터베이스의 데이터를 저장하거나 검색 및 조작하기 위한 표준 언어이다.
- SQL은 현재 미국 국립 표준협회(ANSI)와 국제 표준화기구(ISO)의 표준이다.

### 2) SQL로 무엇을 할 수 있는가?

- SQL은 데이터베이스에 대해 쿼리를 실행할 수 있도록 한다.
- 이를 통해서 데이터베이스의 데이터를 검색하고, 레코드를 삽입하거나 삭제, 업데이트 할 수 있다.
- 새로운 데이터베이스나 새 테이블을 만들 수 있으며, 뷰, procedures를 만들고 권한을 부여할 수 있다.

### 3) SQL 주의사항

- SQL은 표준으로 채택되었으나 여러 다른 SQL언어 버전이 있다.
- 그러나 SELECT, UPDATE, DELETE, INSERT, WHERE과 같은 최소한의 기본적인 커맨드는 동일하게 지원한다. 

### 4) SQL을 웹사이트에서 사용하기

- 데이터베이스의 데이터를 활용한 웹사이트 구현을 위해서는,
  1. RDBMS 데이터베이스 프로그램(MS Access, SQL Server, MySQL과 같은)
     - RDBMS(Relational Database Management System): 관계형 데이터베이스 관리 시스템.
     - SQL,  MS SQL, IBM DB2, Oracle, MySQL 등 모든 최신 데이터베이스 시스템의 기초.
  2. PHP, ASP와 같은 서버측 스크립팅 언어를 사용하며
  3. SQL을 활용해 원하는 데이터를 얻고
  4. 웹사이트 페이지 스타일을 위해  HTML/CSS를 사용해야 한다.

### 5) RDBMS의 테이블 구조

- RDBMS예서는 모든 데이터가 열과 행으로 구성된 '테이블'이라는 데이터베이스 객체에 저장된다.

- 테이블은 관련 데이터 항목의 모음으로, 모든 테이블은 필드라는 엔티티(entity)로 구성된다.

- 필드(field)는 테이블의 모든 레코드에 대한 특정 정보들을 모은 테이블의 첫번째 '열'에 해당한다. (데이터 분류 기준)

- 레코드(record)는 테이블에 있는 개별 데이터 항목을 말한다. 테이블의 '행'에 해당하는 엔티티다.

- 컬럼(column)은 특정 필드에 해당하는 모든 데이터를 포함하는 테이블의 '열'이다.

- ex)

  | CustomerID | CustomerName | City        |
  | ---------- | ------------ | ----------- |
  | 1          | Alfreds      | Berlin      |
  | 2          | Ana          | Mexico D.F. |
  | 3          | Antonio      | London      |

- 위 경우 필드는 CustomerID, CustomerName, City이며,

- 첫 번째 컬럼은 CustomerID / 1 / 2 / 3 에 해당하는 테이블의 첫 열 전체를 말한다.

- 레코드는 1, Ana, London과 같이 개별적인 각 행의 데이터들을 지칭한다.



## 2. SQL Syntax

### 1) 데이터베이스 테이블

- 데이터베이스는 보통 하나 이상의 테이블을 포함한다. 그리고 이 데이터베이스에서 수행하는 대부분의 조치는 SQL문으로 수행한다.
- 가령, SELECT * FROM Customers 라는 SQL문은 Customers라는 테이블에서 모든 레코드를 가져온다는 뜻이다. 즉, 위 테이블 전체의 데이터를 모두 가져오는 것을 의미한다.

### 2) 주의할 점!

- SQL은 각 커맨드의 대소문자를 구분하지 않는다. 즉, SELECT와 select는 같은 기능을 수행할 수 있다.
- 종종 어떤 데이터베이스 시스템에서는 SQL 문장 뒤에 세미콜론(;)을 사용하는 경우가 있다. 세미콜론은 데이터베이스 시스템에서 둘 이상의 SQL문을 실행할 수 있도록 하는 표준방법이다.

### 3) 가장 중요한 SQL 커맨드들

1. SELECT : 데이터베이스에서 일부 데이터를 선택해 추출한다.
2. UPDATE : 데이터베이스의 특정 데이터를 업데이트(수정)한다.
3. DELETE : 데이터베이스의 특정 데이터를 삭제한다.
4. INSERT INTO : 새로운 데이터를 데이터베이스에 삽입한다.
5. CREATE DATABASE : 새로운 데이터베이스를 생성한다.
6. ALTER DATABASE : 데이터베이스를 수정한다.
7. DROP TABLE : 테이블을 삭제한다.
8. CREATE INDEX : 인덱스(search key)를 생성한다.
9. DROP INDEX : 인덱스를 삭제한다.

## 3. SQL SELECT문

- SELECT문은 데이터베이스의 데이터를 선택하는데 사용된다. return된 데이터는 결과 테이블에 저장된다.
- SELECT구문은 다음과 같이 사용된다.
  - SELECT column1, column2, ... FROM table_name;
  - SELECT * FROM table_name;(해당 테이블의 모든 열을 선택한다)
  - SELECT CustomerName, City FROM Customers;



### DISTINCT SELECT문

- DISTINCT SELECT는 중복값을 제외한 고유한 값만을 return한다.

- DISTINCT SELECT 구문은 다음과 같이 사용된다.

  - SELECT DISTINCT column1, coulumn2, ...FROM table_name;

  - SELECT DISTINCT Country FROM Customers;

  - SELECT Count(*) AS DistinctCountries FROM (SELECT DISTINCT Country FROM Customers); 

    (서로 다른 국가의 수를 카운트한다)

## 4. SQL WHERE문

- WHERE는 레코드의 필터링에 사용된다. 지정된 조건을 충족시키는 레코드만을 추출하도록 한다.
- WHERE구문은 다음과 같이 사용된다
  - SELECT column1, column2, ... FROM table_name WHERE condition;
  - SELECT * FROM Customerss WHERE Country='Mexico';
  - SELECT * FROM Customers WHERE CustomerID=1;

## 5. SQL AND, OR, NOT 연산자

- WHERE는 AND, OR, NOT 연산자와 결합하여 조건을 추가적으로 부여해 사용할 수 있다.
- AND, OR는 둘 이상의 조건에 따라 레코드를 필터링한다.
  - 두 조건이 모두 참(TRUE)이면 AND연산자는 레코드를 표시
  - OR연산자는 둘 중 하나 이상이 TRUE일 경우 레코드를 표시
- NOT연산자는 조건이 참이 아닌 경우 레코드를 표시한다. 
- 다음은 AND, OR, NOT연산자를 사용한 조건문의 예시이다.
  - SELECT column1, column2, ... FROM table_name WHERE condition1 AND condition2 AND condition3...;
  - SELECT column1, column2, ... FROM table_name WHERE condition1 OR condition2 OR condition3...;
  - SELECT column1, column2, ... FROM table_name WHERE NOT condition;
  - SELECT  *  FROM Customers  WHERE Country='Germany' AND (City='Berlin' OR City='Munchen');
  - SELECT  *  FROM Customers  WHERE NOT Country='Germany';

## 6. SQL ORDER BY Keyword

- ORDER BY는 return된 결과를 오름차순 혹은 내림차순으로 정렬하는 데 사용된다.

- 디폴트로 레코드는 오름차수으로 정렬되며, 이를 내림차순으로 정렬하기 위해서는 DESC 키워드를 사용한다.

- SELECT column1, column2, ... FROM table_name ORDER BY column1, column2,... ASC | DESC;

- SELECT * FROM Customers ORDER BY Country ; >> 국가 열을 기준으로 오름차순(a로 시작하는 국가부터 정렬)

- SELECT * FROM Customers ORDER BY Country ASC, CustomerName DESC;

  Customers의 모든 고객을 국가 열로 오름차순으로 정렬하고,  그 상태에서 각 고객의 이름들을 내림차순으로 정렬한다.

  즉, Argentina,, Brazil ... 과 같이 정렬된 상태에서, Brazil 내의 CustomerName을 내림차순으로 정렬. Z~A 순으로 이름 정렬

## 7. SQL INSERT INTO문

- INSERT INTO문은 테이블에 새로운 레코드를 삽입할 때 사용한다.
- 두 가지 방법으로 INSERT INTO문을 작성할 수 있다.
  1. INSERT INTO table_name (column1, column2, ...) VALUES (value1, value2, ...)
  2.  INSERT INTO table_name VALUES (value1, value2, ...) > 표의 모든 열(column)에 값을 추가하는 경우. 순서 유의
- 다음과 같은 방식으로 적용할 수 있다.
  1. INSERT INTO Customers (CustomerName, City, Country) VALUES ('Cardinal', 'Stravanger', 'Norway')

## 8. SQL NULL VALUES

- NULL Value는 해당 필드에 값이 존재하지 않는 것을 의미한다. 이는 Space나 0와는 다르다.

- NULL Value를 확인하는 것은 다음과 같은 IS NULL 구문을 이용한다.

  - SELECT column_name FROM table_name WHERE column_name IS (NOT) NULL;

  - SELECT LastName, FirstName, Address FROM Persons WHERE Address IS NULL;

    Address가 등록되지 않은 이름을 추출한다는 의미로 사용된다.

## 9. SQL UPDATE문

- UPDATE문은 테이블의 기존 레코드를 수정한다.

  - UPDATE table_name SET column1 = value1, value2, ... WHERE condition;

  - UPDATE Customers SET ContactName = 'Alfred Schmidt', City = 'Frankfurt' WHERE CustomerID = 1;

    CustomerID가 1인 고객의 ContactName과 City를 재설정한다.

  - UPDATE Customers SET ContactName = 'Juan' WHERE Country='Mexico'

    Country가 Mexico인 고객의 ContactName을 모두 Juan으로 바꾼다.

  - WHERE절이 없으면 모든 레코드가 수정되므로 WHERE절을 꼭 사용하도록 주의하자.

## 10. SQL DELETE문

- DELETE문은 테이블의 기존 레코드를 삭제하는 데 사용된다.

  - DELETE FROM table_name WHERE condition;

  - DELETE FROM Customer WHERE CustomerName='Alfred Futterkiste';

    CustomerName이 Alfred Futterkiste인 데이터를 테이블로부터 제거한다.(해당하는 고객의 row전체를 삭제)

  - DELETE FROM table_name ( = DELETE * FROM table_name ) > 테이블의 모든 행 삭제

## 11. SQL TOP(MS, SQL Server), LIMIT(MY SQL)과 ROWNUM(Oracle) 절

- 이들은 SELECT와 함게  return할 레코드의 수를 지정한다. 레코드가 매우 많은 테이블에서 유용하다.

  - SQL Server / MS :

    SELECT TOP number|percent column_name(s)

    FROM table_name WHERE condition;

    - SELECT TOP 3 ( TOP 50 PERCENT) * FROM Customers WHERE Country = 'Germany';

  - MySQL :

    SELECT column_name(s) FROM table_name

    WHERE condition LIMIT number;

    - SELECT * FROM Customers WHERE Country = 'Germany' LIMIT 3 ;

  - Oracle :

    SELECT column_name(s)

    FROM table_name WHERE ROWNUM <= number;

    - SELECT * FROM Customers WHERE Country = 'Germany' AND ROWNUM <= 3;

## 12. SQL Function : MIN() , MAX()

- MIN() 은 선택된 column의 가장 작은 값을 return하며, MAX()는 가장 큰 값을 반환한다.

  - SELECT MIN(column_name) FROM table_name WHERE condition;
  - SELECT MIN(price) AS SmallestPrice FROM Products;



  - SELECT MAX(column_name) FROM talbe_name WHERE condition;
  - SELECT MAX(Price) AS LargestPrice FROM Products;

## 13. SQL Function : COUNT(), AVG(), SUM()

- COUNT()는 지정된 기준과 일치하는 행의 수를 Return한다.

- AVG()는 숫자 열의 평균 값을 반환한다.

- SUM()은 숫자 열의 총 합계를 반환한다.

  - SELECT COUNT(column_name) FROM table_name WHERE condition;

  - SELECT COUNT(ProductID) FROM Products;

  - SELECT AVG(column_name) FROM table_name WHERE condition;

  - SELECT AVG(Price) FROM Products;

  - SELECT SUM(coulumn_name) FROM table_name WHERE condition;

  - SELECT SUM(Quantity) FROM OrderDetails;

## 14. SQL LIKE Operator

- LIKE operator는 WHERE절에서 패턴을 지정해 검색을 할 수 있다.

- LIKE와 함께 %, _  연산자(Wildcard)를 사용할 수 있다.

- %는 0개 이상의 임의의 문자를 의미하며, _은 한 개의 임의의 문자를 나타낸다.

  - SELECT column1, colum2, ... FROM table_name WHERE columnN LIKE pattern;

  - SELECT * FROM Customers WHERE CUstomersName LIKE 'a%';

    CustomerName이 a 로 시작하는 모든 고객을 선택한다.

  - SELECT * FROM Customers WHERE CustomerName LIKE '%a';

    a로 끝나는 모든 고객을 선택한다.

  - SELECT * FROM Customers WHERE CusomerName LIKE '_r%'

    두 번째 위치에 r 이 들어가는 모든 고객을 선택한다.

  - SELECT * FROM Customers WHERE CustomerNAme NOT LIKE 'a%'

    a로 시작하지 않는 모든 고객을 선택한다.

## 15. SQL Wildcards

- 위에서 언급된 %, _ 와 함께 [charlist] 와일드카드 또한 존재한다.

- SELECT * FROM Customers WHERE City LIKE '[bsp]%';

  [charlist]는 해당 리스트 안에 있는 문자 중 1가지를 말하는 것이다.

  따라서 위 구문은 테이블에서 City가 b, s, p 중 하나의 알파벳으로 시작하는 레코드를 말한다.

- SELECT * FROM Customers WHERE City LIKE '[a-c]%';

- SELECT * FROM Customers WHERE City LIKE'[!a-c]%;

  이 경우는 b, s, p 중 하나로 시작하지 않는 모든 고객을 의미한다. ! 대신 NOT LIKE을 사용할 수 있다.

## 16. SQL IN Operator

- WHERE절에 다른 조건을 지정할 수 있으며, 여러 OR조건을 축약해놓은 것이라고 볼 수 있다.

- SELECT column_name(s) FROM table_name WHERE column_name IN (value1, value2, ..);

- SELECT * FROM  Customers WHERE Country IN ('Germany', 'France');

- SELECT * FROM  Customers WHERE Country NOT IN ('Germany', 'France');


- SELECT column_name(s) FROM table_name WHERE column_name IN (SELECT STATEMENT);

- SELECT * FROM  Customers WHERE Country IN (SELECT Country FROM Suppliers);

  공급업체(Suppliers)의 Country와 Customer의 Country가 같은 레코드만 가져온다

## 17. SQL BETWEEN Operator

- BETWEEN 연산자는 주어진 범위 내의 값을 선택하는 것으로, 텍스트나 숫자, 날짜 또한 가능하며, 시작과 끝 값이 포함된다.

- SELECT column_name(s) FROM table_name WHERE column_name BETWEEN value1 AND value2;

- SELECT * FROM Products WHERE Price BETWEEN 10 AND 20;

- SELECT * FROM Products WHERE Price NOT BETWEEN 10 AND 20;

- SELECT * FROM Products WHERE (Price BETWEEN 10 AND 20) AND NOT CategoryID IN (1,2,3);

- SELECT * FROM Products WHERE ProductName BETWEEN 'Carnarvon Tigers' AND 'Mozzarella di Giovanni'

  ORDER BY ProductName;

  알파벳 상으로 Carnarvon~Mozzarella 사이에 위치하는 레코드들이 모두 포함된다.

- SELECT * FROM Orders WHERE OrderDate BETWEEN '1996 - 07 - 01' AND '1996 - 07 - 31';

## 18. SQL Aliases(별칭)

- SQL Aliases는 테이블 또는 테이블의 열에 임시로 Name을 지정하는데 사용된다.

- 별칭은 쿼리에 두 개 이상의 테이블이 관련되어 있거나, 열 이름이 크거나 읽기 어려운 경우 등에 사용하면 좋다.

- SELECT column_name AS alias_name FROM table_name;

- SELECT CustomerID AS ID, CustomerName AS Customer FROM Customers;

- SELECT CustomerName AS Customer, ContactName AS [Contact Person] FROM Customers;

  ** Customer, ContactName > [Contact Person]의 이름으로 설정. 공백이 들어가면 [ ] 나 " " 안에 써야한다.

- SELECT CustomerName, Address + ', ' + PostalCode + ', ' + City As Address FROM Customers;

- SELECT column_name(s) FROM table_name AS alias_name;

- SELECT o.OrderID, o.OrderDate, c.CustomerName
  FROM Customers AS c, Orders AS o
  WHERE c.CustomerName="Around the Horn" AND c.CustomerID=o.CustomerID;

## 19. SQL JOIN

- JOIN절은 두 개 이상의 테이블에 있는 행을 결합하는 데 사용된다.

- SELECT Orders.OrderID, Customers.CustoemrName, Orders.OrderDate

  FROM Orders

  INNER JOIN Customers ON Orders.CustomerID=Customers.CustomerID;

- 이외에도 여러 유형의 JOIN이 존재한다

## 20. SQL JOIN : INNER JOIN

- INNER) JOIN : 두 테이블에서 값이 일치하는 레코드를 반환합니다.
- SELECT column_name(s) FROM table1 INNER JOIN table2 ON table1.column_name = table2.column_name;
- SELECT Orders.OrderID, Customers.CustomerName, Shippers.ShipperName
  FROM ((Orders
  INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID)
  INNER JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID);

## 21. SQL JOIN : LEFT JOIN

- LEFT (OUTER) JOIN : 왼쪽 테이블 모든 레코드를 반환하고 오른쪽 테이블에서 일치하는 레코드를 반환한다.
- SELECT *column_name(s)* FROM *table1* LEFT JOIN *table2* ON *table1.column_name* = *table2.column_name*;
- SELECT Customers.CustomerName, Orders.OrderID
  FROM Customers
  LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID
  ORDER BY Customers.CustomerName;

## 22. SQL JOIN : RIGHT JOIN

- RIGHT (OUTER) JOIN : 오른쪽 테이블에서 모든 레코드를 반환하고 왼쪽 테이블에서 일치하는 레코드를 반환한다.
- SELECT *column_name(s)* FROM *table1* RIGHT JOIN *table2* ON *table1.column_name* = *table2.column_name*;
- SELECT Orders.OrderID, Employees.LastName, Employees.FirstName
  FROM Orders
  RIGHT JOIN Employees ON Orders.EmployeeID = Employees.EmployeeID
  ORDER BY Orders.OrderID;

## 23.SQL JOIN : FULL OUTER JOIN

- FULL (OUTER) JOIN : 왼쪽 또는 오른쪽 테이블에서 일치하는 모든 레코드를 반환한다.
- SELECT *column_name(s)* FROM table1 FULL OUTER JOIN *table2* ON *table1.column_name* = *table2.column_name*;
- SELECT Customers.CustomerName, Orders.OrderID
  FROM Customers
  FULL OUTER JOIN Orders ON Customers.CustomerID=Orders.CustomerID
  ORDER BY Customers.CustomerName;

## 24. SQL JOIN : SELF JOIN

- Self JOIN은 테이블 자체와 조인한다.
- SELECT *column_name(s)*
  FROM *table1 T1, table1 T2*
  WHERE *condition*;

## 25. SQL UNION Operator

- UNION 연산자는 두 개 이상의 SELECT문의 결과를 결합한다.

  - 이 때, UNION 내의 각 SELECT문은 같은 수의 열을 가져야 하며, 열끼리 유사한 데이터 형식이어야 한다.

  - 또한 그 열의 순서가 같은 순서여야만 한다.

-  SELECT *column_name(s)* FROM *table1*
  UNION
  SELECT *column_name(s)* FROM *table2*;

- SELECT *column_name(s)* FROM *table1*
  UNION ALL
  SELECT *column_name(s)* FROM *table2*;

  ** UNION은 중복값을 허용하지 않는다. 따라서 중복값을 허용하기 위해서는 UNION ALL 을 사용해야 한다.

- SELECT City, Country FROM Customers
  WHERE Country='Germany'
  UNION ALL
  SELECT City, Country FROM Suppliers
  WHERE Country='Germany'
  ORDER BY City;

- SELECT 'Customer' As Type, ContactName, City, Country
  FROM Customers
  UNION
  SELECT 'Supplier', ContactName, City, Country
  FROM Suppliers;

## 26. SQL GROUP BY

- GROUP BY문은 집계 함수(COUNT, MAX, MIN, SUM, AVG)와 함께 사용되어 결과 집합을 하나 이상의 열로 그룹화한다.

- SELECT *column_name(s)*
  FROM *table_name*
  WHERE *condition*
  GROUP BY *column_name(s)* ORDER BY column_name(s);

- SELECT COUNT(CustomerID), Country
  FROM Customers
  GROUP BY Country
  ORDER BY COUNT(CustomerID) DESC;

  Country의 고객수(CustomerID의 수)를 Country를 기준으로 그룹화하고, 고객수에 따라 정렬.

## 27. SQL HAVING

- WHERE를 집계함수와 함께 사용할 수 없기 때문에, HAVING절을 사용한다.

  HAVING절에 집계함수를 사용한 조건을 WHERE에 추가할 수 있게 된다.

- SELECT *column_name(s)*
  FROM *table_name*
  WHERE *condition*
  GROUP BY *column_name(s)*HAVING condition ORDER BY column_name(s);

- SELECT COUNT(CustomerID), Country
  FROM Customers
  GROUP BY Country
  HAVING COUNT(CustomerID) > 5;

- SELECT Employees.LastName, COUNT(Orders.OrderID) AS NumberOfOrders
  FROM (Orders INNER JOIN Employees ON Orders.EmployeeID = Employees.EmployeeID)
  GROUP BY LastName
  HAVING COUNT(Orders.OrderID) > 10;

  ** 10개 이상의 주문을 등록한 직원을 나타낸다.

## 28. SQL EXIST Operator

- EXIST는 하위 쿼리(Query)로 찾고자 하는 레코드가 있는지 테스트할 때 사용된다.

  해당 쿼리에 해당하는 레코드가 하나 이상 존재한다면(return한다면) True를 반환한다.

- SELECT *column_name(s)*
  FROM *table_name*
  WHERE EXISTS
  (SELECT *column_name* FROM *table_name* WHERE *condition*);

- 

- SELECT SupplierName
  FROM Suppliers
  WHERE EXISTS

  (SELECT ProductName FROM Products WHERE SupplierId = Suppliers.supplierId AND Price < 20);

  ** True를 반환하며, Price가 20 미만인 공급업체를 나열할 것이다.

# SQL DATABASE Tutorial

## 1. SQL CREATE DATABASE

- CREATE DATABASE는 새로운 데이터베이스를 만드는 데 사용된다.
- CREATE DATABASE databasename;
- CREATE DATABASE testDB;

## 2. SQL DROP DATABASE

- DROP DATABASE는 기존 SQL 데이터베이스를 삭제할 때 사용된다.
- DROP DATABASE databasename;
- DROP DATABASE testDB;

## 3. SQL CREATE TABLE

- CREATE TABLE은 데이터베이스에 새 테이블을 만들 때 사용한다.

  테이블에 필요한 필드(열)을 지정하고, 자료형을 설정해준다.

- CREATE TABLE *table_name* (
  ​    column1 datatype,
  ​    column2 datatype,
  ​    column3 datatype,
     ....

  );

- CREATE TABLE Persons (
  ​    PersonID int,
  ​    LastName varchar(255),
  ​    FirstName varchar(255),
  ​    Address varchar(255),
  ​    City varchar(255) 
  );

- CREATE TABLE TestTable AS
  SELECT customername, contactname
  FROM customers;

  ** 위와 같이 AS를 사용하여 기존에 존재하는 테이블을 사용해서 복사본 테이블을 만들 수 있다.

## 4. SQL DROP TABLE

- DROP TABLE은 데이터베이스에서와 마찬가지로 기존의 테이블을 삭제하는 데 사용한다.

- DROP TABLE table_name;

- DROP TABLE Shippers;

- TRUNCATE TABLE table_name;

  ** TRUNCATE TABLE은 테이블 내부의 데이터는 모두 삭제하지만 테이블 자체를 삭제하지는 않는다.

## 5. SQL ATLER TABLE

- ALTER TABLE은 기존 테이블에 열을 추가하거나 삭제, 수정하는 데 사용된다.

  또한 기존 테이블에 다양한 제한 조건을 추가할 수도 있다.

- ADD : 테이블에 열을 추가할 경우

  - ALTER TABLE *table_name*
    ADD *column_name datatype*;
  - ALTER TABLE Customers
    ADD Email varchar(255);

- DROP : 테이블의 열을 삭제할 경우

  - ALTER TABLE *table_name*
    DROP COLUMN *column_name*;
  - ALTER TABLE Customers
    DROP COLUMN Email;

- ALTER/MODIFY : 테이블이 열 데이터 형식을 변경할 경우

  - ALTER TABLE *table_name*
    ALTER( MODIFY : MySQL / MODIFY COLUMN : Oracle ) COLUMN *column_name datatype*;
  - ALTER TABLE Persons
    ALTER COLUMN DateOfBirth year;

## 6. SQL Constraints(제약 조건)

- CREATE TABLE으로 테이블이 작성될 때, ALTER TABLE로 테이블이 수정될 때 제약 조건을 지정할 수 있다.

  SQL 제약 조건은 테이블의 데이터에 대한 규칙을 지정해준다.

  테이블에 들어갈 수 있는 데이터의 유형을 제한하는데, 이를 통해 테이블의 데이터 정확성과 신뢰성을 보장한다.

  다양한 제약 조건이 존재한다.

   

- CREATE TABLE *table_name* (
  ​    *column1 datatype* *constraint*,
  ​    *column2 datatype* *constraint*,
  ​    *column3 datatype* *constraint*,
  ​    ....
  );

## 7. SQL Constraints : NOT NULL

- 기본적으로 각 열은 NULL 값을 포함할 수 있도록 설정되어 있는데,

  NOT NULL 조건을 추가할 경우 NULL값이 허용되지 않는다. 항상 필드에 해당하는 데이터 레코드가 존재해야한다.

- CREATE TABLE Persons (
  ​    ID int NOT NULL,
  ​    LastName varchar(255) NOT NULL,
  ​    FirstName varchar(255) NOT NULL,
  ​    Age int
  );

## 8. SQL Constraints : UNIQUE

- UNIQUE 제약 조건은 열의 모든 값이 서로 다른지 확인하는 역할을 한다.

  UNIQUE와 PRIMARY KEY 제약 조건은 열의 고유성을 보장한다.

  PRIMARY KEY 제약 조건에는 자동으로 UNIQUE 제약 조건이 포함된다.

  그러나 PRIMARY KEY는 테이블 당 단 하나만 가능하지만 UNIQUE는 여러 열에 사용 가능하다.

- SQL Server / Oracle / MS Access :

  - CREATE TABLE Persons (
    ​    ID int NOT NULL UNIQUE,
    ​    LastName varchar(255) NOT NULL,
    ​    FirstName varchar(255),
    ​    Age int
    );

  - ALTER TABLE Persons
    DROP CONSTRAINT UC_Person;

    ** UNIQUE 제약 조건 삭제

- MySQL :

  - CREATE TABLE Persons (
    ​    ID int NOT NULL,
    ​    LastName varchar(255) NOT NULL,
    ​    FirstName varchar(255),
    ​    Age int,
    ​    UNIQUE (ID)
    );

  - ALTER TABLE Persons
    DROP INDEX UC_Person;

    ** UNIQUE 제약 조건 삭제

## 9. SQL Constraints : PRIMARY KEY

- PRIMARY KEY(기본키) 제약 조건은 데이터베이스 테이블의 각 레코드를 고유하게 식별한다.

  해당 열에는 NULL값이 들어갈 수 없고, UNIQUE 속성을 포함한다(즉, 중복된 데이터가 존재할 수 없다)

  테이블 당 단 하나의 PRIMARY KEY가 존재할 수 있다.

- CREATE TABLE Persons (
  ​    ID int NOT NULL,
  ​    LastName varchar(255) NOT NULL,
  ​    FirstName varchar(255),
  ​    Age int,
  ​    CONSTRAINT PK_Person PRIMARY KEY (ID,LastName)
  );

  ** PRIMARY KEY가 두 개의 Column으로 구성되어, 두 개의 값을 key로 참조한다.

- ALTER TABLE Persons
  ADD PRIMARY KEY (ID);

- ALTER TABLE Persons
  ADD CONSTRAINT PK_Person PRIMARY KEY (ID,LastName);

- PRIMARY KEY 제약조건 삭제

  - SQL Server / Oracle / MS Access :

    ALTER TABLE Persons
    DROP PRIMARY KEY;

  - MySQL :

    ALTER TABLE Persons
    DROP CONSTRAINT PK_Person;

## 10. SQL Constraints : FOREIGN KEY

- FOREIGN KEY(외래키)는 두 테이블을 서로 연결할 때 사용되는 키다.

  FOREIGN KEY는 다른 테이블의 PRIMARY KEY를 참조하는 테이블의 필드( 혹은 필드의 집합)이다.

  FOREIGN KEY로 지정된 테이블이 하위 테이블이 되며, Candidate Key(후보키)인 테이블을 참조된 테이블 혹은

  상위 테이블이라고 부른다.

- Person Table

  | PersonID | LastName  | FirstName | Age  |
  | -------- | --------- | --------- | ---- |
  | 1        | Hansen    | Ola       | 30   |
  | 2        | Svendson  | Tove      | 23   |
  | 3        | Pettersen | Kari      | 20   |

- Order Table

  | OrderID | OrderNumber | PersonID |
  | ------- | ----------- | -------- |
  | 1       | 77895       | 3        |
  | 2       | 44678       | 3        |
  | 3       | 22456       | 2        |
  | 4       | 24562       | 1        |

- 위 테이블에서, Order 테이블의 PersonID열이 Person테이블의 PersonID열을 가리킨다.

  Person테이블의 PersonID열은 Person테이블의 PRIMARY KEY다.

  Order테이블의 PersonID열은 Order테이블의 FOREIGN KEY다.

- FOREIGN KEY는 테이블 간의 연결을 파괴하는 작업에 대해 제한을 걸기 위해 존재한다.

  FOREIGN KEY의 데이터 값들은 모두 참조하고 있는 PRIMARY KEY에 존재하는 값이어야만 한다.

  PRIMARY KEY에 없는 값을 FOREIGN KEY로 설정된 열에 넣을 수 없다.

- My SQL : 

  - CREATE TABLE Orders (
    ​    OrderID int NOT NULL,
    ​    OrderNumber int NOT NULL,
    ​    PersonID int,
    ​    PRIMARY KEY (OrderID),
    ​    FOREIGN KEY (PersonID) REFERENCES Persons(PersonID)
    );

  - FOREIGN KEY 삭제

    ALTER TABLE Orders
    DROP FOREIGN KEY FK_PersonOrder;

- SQL Server / Oracle / MS Access :

  - CREATE TABLE Orders (
    ​    OrderID int NOT NULL PRIMARY KEY,
    ​    OrderNumber int NOT NULL,
    ​    PersonID int FOREIGN KEY REFERENCES Persons(PersonID)
    );

  - FOREIGN KEY 삭제

    ALTER TABLE Orders
    DROP CONSTRAINT FK_PersonOrder;

## 11. SQL Constraints : CHECK

- CHECK 제약 조건은 열에 배치할 수 있는 값의 범위를 제한한다.

  다른 column의 값을 기준으로 테이블에도 CHECK를 적용할 수 있다.

- MySQL :

  - CREATE TABLE Persons (
    ​    ID int NOT NULL,
    ​    LastName varchar(255) NOT NULL,
    ​    FirstName varchar(255),
    ​    Age int,
    ​    CHECK (Age>=18)
    );

  - CHECK 조건 삭제:

    ALTER TABLE Persons
    DROP CONSTRAINT CHK_PersonAge;

- SQL Server/ Oracle / MS Access :

  - CREATE TABLE Persons (
    ​    ID int NOT NULL,
    ​    LastName varchar(255) NOT NULL,
    ​    FirstName varchar(255),
    ​    Age int CHECK (Age>=18)
    );

  - CHECK 조건 삭제 :

    ALTER TABLE Persons
    DROP CHECK CHK_PersonAge;

## 12. SQL Constraints: DEFAULT

- DEFAULT 제약 조건은 열의 기본값을 제공하는 기능이다.

  다른 값을 지정하지 않고 비워둔 경우 해당 설정된 기본값이 들어간다.

- CREATE TABLE Persons (
  ​    ID int NOT NULL,
  ​    LastName varchar(255) NOT NULL,
  ​    FirstName varchar(255),
  ​    Age int,
  ​    City varchar(255) DEFAULT 'Sandnes'
  );

- CREATE TABLE Orders (
  ​    ID int NOT NULL,
  ​    OrderNumber int NOT NULL,
  ​    OrderDate date DEFAULT GETDATE()
  ); ** 시스템 값을 사용한 케이스(GETDATE())

- DEFAULT 제약조건 삭제 :

  ALTER TABLE Persons
  ALTER COLUMN(ALTER : MySQL) City DROP DEFAULT;

## 13. SQL CREATE INDEX

- CREATE INDEX 는 테이블에 인덱스를 만든다.

  인덱스는 데이터베이스에서 데이터를 빠르게 검색할 때 사용되는데, 검색과 쿼리 속도를 높이는 용도이다.

- CREATE INDEX *index_name*
  ON *table_name* (*column1*, *column2*, ...);

- CREATE UNIQUE INDEX *index_name*
  ON *table_name* (*column1*, *column2*, ...);

  ** 기본적으로는 중복을 허용하나, UNIQUE를 추가해 중복 인덱스를 허용하지 않도록 할 수 있다.

- CREATE INDEX idx_lastname
  ON Persons (LastName);

- DROP INDEX를 통해 테이블의 인덱스를 삭제할 수 있다.

  - DROP INDEX *index_name* ON *table_name*;

## 14. SQL AUTO INCREMENT

- AUTO INCREMENT는 새 레코드가 테이블에 삽일될 때마다 고유 번호가 자동으로 생성되는 기능이다.

  레코드 삽입 시에 자동 생성되는 PRIMARY KEY로 사용되기도 한다.

- CREATE TABLE Persons (
  ​    ID int NOT NULL **AUTO_INCREMENT**,
  ​    LastName varchar(255) NOT NULL,
  ​    FirstName varchar(255),
  ​    Age int,
  ​    PRIMARY KEY (ID)
  );  ** MySQL 기준

- MySQL은 AUTO_INCREMENT를 사용해 자동 생성 기능을 구현한다.

  위에서는 ID 값에 이를 사용해 1부터 계속 증가하도록 했다.

  기본적으로 시작값은 1이며, 새 레코드마다 1씩 증가한다.

  - 이 시작값을 바꾸려면 ALTER TABLE Persons AUTO_INCREMENT=100; 와 같이 설정한다.

- 새 레코드를 추가하더라도 ID값을 넣지 않아도 된다. 그냥 LastName, FirstName만 입력하면 된다.

## 15. SQL Dates(시간 관련 작업 수행)

- MySQL 에는 데이터베이스에 날짜 또는 날짜 / 시간 값을 저장하기 위해 다음의 데이터 유형을 취한다.
  - DATE - YYYY-MM-DD 형식
  - DATETIME - 형식 : YYYY-MM-DD HH : MI : SS
  - TIMESTAMP - 형식 : YYYY-MM-DD HH : MI : SS
  - YEAR - YYYY 또는 YY 형식
- SELECT * FROM Orders WHERE OrderDate='2008-11-11'
- 주의할 점은 시간 단위(2008-11-11 13:23:44)까지 추가해 찾을 경우 날짜만으로 SELECT할 때 검색이 어렵다는 점이다.