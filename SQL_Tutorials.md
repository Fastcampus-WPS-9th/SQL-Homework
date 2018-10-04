# SQL Tutorials

-

### Contents
1. Basic SQL Queries
 1. Syntax
 2. SELECT, WHERE syntax
 3. INSERT, UPDATE, DELETE syntax
 4. Bulit-in functions
 5. Joins
 6. UNION, GROUP BY, HAVING
2. SQL Databases
 1. CREATE, DROP, ALTER Tables
 2. Constraints (unique, PK, FK, Check, Default, Auto-increment, etc.)
 3. Difference between SQL INDEX and VIEW

-

## 1. Basic SQL Queries

### 1. SQL(Structured Query Language)

* DB에 접근이 가능.
* CRUD를 효율적으로 수행 가능.
* 기본적으로 RDBMS(Relational-DBMS)를 먼저 학습함.

#### 1.1. Syntax

DB는 테이블을 갖고있고 그 테이블에 컬럼으로 값을 어떻게 넣을지 정의해둔다. 컬럼이 정의되었다면 레코드(행)에 데이터를 채워나간다.

SQL 구문은 DB 테이블의 데이터에 기본적으로 접근한다.

SQL구문은...

* SQL 키워드는 `not case-sensitive`이다. 하지만 보통 키워드는 모두 대문자로 쓴다.
* 각 DBMS는 SQL Statement 끝에 `;` 을 붙인다.

이런식으로 쓰임:

```
SELECT * FROM Customers;
```

#### 1.2. SELECT, WHERE Syntax

`SELECT` 구문은 DB로부터 값을 'select'하는 문장을 의미한다. 리턴되는 값은 결과 테이블에 저장되는데, 이는 `result-set`이라고 부른다.

```
SELECT column1, column2, ...
FROM table_name;
```
---

`SELECT DISTINCT` 구문은 'dictinct value'를 리턴해준다. 말 그대로 result-set의 중복되는 값을 없앤다는 말.

```
SELECT DISTINCT column1, column2, ...
FROM table_name;
```
---

`WHERE` 절(clause)은 result-set을 필터링 해준다. `SELECT` 뿐 아니라 다른 CRUD 모든 동작에서 쓰일 수 있다.

```
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

아래 표에서는 `WHERE` 절에서의 다양한 Operator들을 소개한다:

Operator |	Description
-------- | --------------
= |	Equal
<>	| Not equal. Note: In some versions of SQL this operator may be written as !=
> | Greater than
< | Less than
>=	| Greater than or equal
<= | Less than or equal
BETWEEN | Between an inclusive range
LIKE | Search for a pattern
IN | To specify multiple possible values for a column

---

`WHERE` 절은 `AND, OR, NOT` Operator와 함께 사용할 수 있다.

* AND: A AND B가 참이어야 참. (B도 참이어야됨)
* OR: A OR B가 참이어야함. (B는 아니어도 됨)
* NOT: 조건이 참이 아니면 출력.

#### AND Syntax
```
SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2 AND condition3 ...;
```
#### OR Syntax
```
SELECT column1, column2, ...
FROM table_name
WHERE condition1 OR condition2 OR condition3 ...;
```
#### NOT Syntax
```
SELECT column1, column2, ...
FROM table_name
WHERE NOT condition;
```

각 구문은 **조합**도 가능하다.

#### 모두 고르시오: Customer 중에 국가가 Germany이고, 도시가 Berlin 혹은 München인 사람을.

```
SELECT * FROM Customers
WHERE Country='Germany' AND (City='Berlin' OR City='München');
```

#### 모두 고르시오: Customer 중에 국가가 Germany가 아니고, USA가 아닌 사람을.
```
SELECT * FROM Customers
WHERE NOT Country='Germany' AND NOT Country='USA';
```

`ORDER BY` 키워드는 result-set을 오름차순/내림차순 정렬해줄 수 있다. `ASC`를 붙이면 _오름차순_, `DESC`를 붙이면 _내림차순_ 으로 사용가능.

```
SELECT column1, column2, ...
FROM table_name
ORDER BY column1, column2, ... ASC|DESC;
```

--

### 1.3 INSERT, UPDATE, DELETE syntax

`INSERT INTO` 구문은 새로운 record를 테이블에 **추가**할 때 사용한다. `INSERT INTO` 구문은 두가지 방식으로 작성될 수 있다.

특정 컬럼에 값을 넣으려면 다음과 같이 수행한다:

```
INSERT INTO table_name (column1, column2, column3, ...) 
VALUES (value1, value2, value3, ...);
```

모든 컬럼에 값을 넣으려면 값만 **순서에 맞게** 입력해주면 된다:

```
INSERT INTO table_name
VALUES (value1, value2, value3, ...);
```

---

* SQL NULL Value?

필드값에 `NULL`이 있으면 값이 `'없는'`것으로 취급된다. `NULL`값에 비교연산자(`=, <, <>`)를 사용할 수도 있지만, `IS NULL` 혹은 `IS NOT NULL`을 사용하는 것이 좋다.

---

`UPDATE SET` 구문은 테이블에 존재하는 값을 **수정**할 때 사용한다:

```
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

> 테이블에서 `UPDATE`구문을 사용할 때, `WHERE` 구문을 생략하면 테이블 내의 **모든** 레코드가 수정된다!

---

`DELETE FROM` 구문은 테이블에 존재하는 값을 **삭제**할 때 사용한다:

```
DELETE FROM table_name
WHERE condition;
```

# 조심!
> 테이블에서 `DELETE`구문을 사용할 때, `WHERE` 구문을 생략하면 테이블 내의 **모든** 레코드가 **`삭제`**된다!

---

* SQL TOP, LIMIT 혹은 ROWNUM 구절

SELECT TOP 절은 리턴 할 레코드 수를 지정하는 데 쓰인다.
주로 많은 레코드를 가진 큰 테이블에 유용하다. 리턴받은 레코드 수는 DB성능에 큰 영향을 끼친다.

> 모든 DBMS가 TOP 키워드를 지원하지는 않는다. MySQL은 LIMIT 구문으로 몇몇개의 레코드 수만 설정하여 쿼리할 수 있고 Oracle은 ROWNUM이란 것을 쓴다.

SQL 문의 TOP과 LIMIT, ROWNUM은 다음과 같이 쓰인다. 이 메시지에서는 MySQL과 Oracle DB만을 다룬다.

```
SELECT TOP 3 * FROM Customers;
```

MySQL에서는 다음과 같이 쓴다.

```
SELECT * FROM Customers
LIMIT 3;
```

Oracle DB에서는 다음과 같이 쓴다.

```
SELECT * FROM Customers
WHERE ROWNUM <= 3;
```

### 1.5 Built-in functions

* MIN(): 선택한 컬럼의 최소값 리턴
* MAX(): 선택한 컬럼의 최대값 리턴
* COUNT(): 구체적인 기준값에 부합하는 행의 갯수를 구함.
* AVG(): 숫자 컬럼값의 평균을 구함
* SUM(): 숫자 컬럼값의 합계를 구함

MIN() Syntax:

```
SELECT MIN(column_name)
FROM table_name
WHERE condition;
```

MAX() Syntax:

```
SELECT MAX(column_name)
FROM table_name
WHERE condition;
```

COUNT() Syntax:

```
SELECT COUNT(column_name)
FROM table_name
WHERE condition;
```

AVG() Syntax:

```
SELECT AVG(column_name)
FROM table_name
WHERE condition;
```

SUM() Syntax:

```
SELECT SUM(column_name)
FROM table_name
WHERE condition;
```

* LIKE Operator

`LIKE` Operator 는 `WHERE` 구문안에 쓰이며, 컬럼의 특정 `패턴`에 맞는 값을 찾는다.

`LIKE` 구문은 `%`, `_`과 같은 위 두개의 _wildcard_ 가 있다. 와일드카드는 문자열 내의 단어를 대체하는 값이다. `LIKE` 명령어와의 연결 처럼 쓰인다. 이는 `WHERE` 절에서 또한 쓸 수 있다. 상세한 설명은 아래와 같다:

```
% : The percent sign represents 
	zero, one, or multiple characters(0, 1, 2, ...)
	0, 1, 2글자 이상 겹쳐도 가능.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      
_ : The underscore represents a single character(only 1)
	1글자'만' 겹쳐야 가능.
```

아래의 표는 `LIKE` Operator의 다양한 예시를 소개한다:

LIKE | Operator	Description
-----|----------------------
WHERE CustomerName LIKE 'a%' | 시작을 "a"로 하는 모든 값 찾기
WHERE CustomerName LIKE '%a' | 끝값이 "a"로 끝나는 모든 값 찾기
WHERE CustomerName LIKE '%or%' | 어느 위치든 "or"이 있는 값을 찾기
WHERE CustomerName LIKE '\_r%' | _두번째 위치_ 에 "r"이 있는 모든 값 찾기
WHERE CustomerName LIKE 'a\_%\_%' | "a"로 시작하고, 최소길이 3 이상인 모든 값 찾기
WHERE ContactName LIKE 'a%o' | "a"로 시작하고 "o"로 끝내는 모든 값 찾기( 중간길이 _신경쓰지 않음_ )
WHERE CustomerName NOT LIKE 'a%' | "a"로 시작하지 **않는** 모든 값 찾기

---

* IN Operator

`IN` Operator는 `WHERE` 절에서 여러 값을 구체화할 수 있게 한다. 다시말해 `'어디' 안의 '무슨 값'을 CRUD하라` 하는 쿼리를 작성할 수 있게된다.

IN Operator는 크게 아래 두가지 형태로 쓰인다:

```
SELECT column_name(s)
FROM table_name
WHERE column_name IN (value1, value2, ...);
```

혹은..

```
SELECT column_name(s)
FROM table_name
WHERE column_name IN (SELECT STATEMENT);
```

---

* BETWEEN Operator

주어진 값 사이의 값을 선택한다. '값'은 숫자, 텍스트, 날짜가 될 수 있다. 시작값, 끝값은 유저가 명시해주어야 한다.

BETWEEN Syntax

```
SELECT column_name(s)
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```

#### 1.5 Joins

`JOIN` 절은 서로 관련있는 컬럼이 있는 둘 이상의 테이블에서 레코드를 뽑아내는 것이다.

테이블 둘을 집합으로 이해하고 둘 사이의 교집합, 합집합, 차집합, 여집합 연산을 생각한다고 이해하면 빠르다.

`JOIN` 절은 다음과 같이 사용한다:

1. `SELECT` 구문으로 찾을 요소를 고르고
2. `FROM` 구문으로 table1을 설정한 후
3. `JOIN` 구문으로 JOIN 연산 할 table2를 고른 다음
4. `ON` 구문으로 JOIN 연산을 수행할 요소를 찾느다.

```
SELECT Orders.OrderID, Customers.CustomerName, Orders.OrderDate
FROM Orders
INNER JOIN Customers ON Orders.CustomerID=Customers.CustomerID;
```

위 문장을 해석하면,

```
Orders 테이블의 OrderID와, 
Customers 테이블의 CustomerName,
그리고 Orders 테이블의 OrderDate값을 result-set으로 '선택'하고싶다.

Order 테이블과 Customers 테이블을 Inner Join하여 찾는다.

찾는 조건은 ON 구문 아래이다.
(Orders의 CustomerID와 Customers의 CustomerID가 같은 값)
```


* (INNER) JOIN: 두 테이블 모두에서 겹치는 값을 가진 레코드를 리턴

![alt-text](https://www.w3schools.com/sql/img_innerjoin.gif)

* LEFT (OUTER) JOIN: LEFT TABLE의 모든 레코드와, RIGHT TABLE과 겹치는 모든 레코드를 리턴

![alt-text](https://www.w3schools.com/sql/img_leftjoin.gif)

* RIGHT (OUTER) JOIN: RIGHT TABLE의 모든 레코드와, LEFT TABLE과 겹치는 모든 레코드를 리턴

![alt-text](https://www.w3schools.com/sql/img_rightjoin.gif)

* FULL (OUTER) JOIN: LEFT, RIGHT 테이블 중 어디든 있는 레코드를 리턴.

![alt-text](https://www.w3schools.com/sql/img_fulljoin.gif)

이 정보 또한 참조하면 좋다:

![alt-text](https://www.codeproject.com/KB/database/Visual_SQL_Joins/Visual_SQL_JOINS_orig.jpg)

---

* (INNER) JOIN

**양쪽 테이블 모두**가 가지고 있는 요소를 가지고옴. 교집합을 생각하면 편하다.

```
SELECT column_name(s)
FROM table1
INNER JOIN table2 ON table1.column_name = table2.column_name;
```

table1과 table2를 inner join 한다. result-set을 구성하는 조건은 `ON`구절 다음과 같다.


* LEFT (OUTER) JOIN

LEFT JOIN 키워드는 table1(왼쪽 테이블)의 모든 레코드와 조건에 부합하는 table2(오른쪽 테이블) 레코드를 리턴한다. 매치되는 결과가 없다면 table2에서 가져오는 결과는 NULL이 된다.

```
SELECT column_name(s)
FROM table1
LEFT JOIN table2 ON table1.column_name = table2.column_name;
```


* RIGHT (OUTER) JOIN

RIGHT JOIN 키워드는 table2(오른쪽 테이블)의 모든 레코드와 조건에 부합하는 table1(왼쪽 테이블)의 레코드를 리턴한다. 매치되는 결과가 없다면 table1에서 가져오는 결과는 NULL이 된다.

```
SELECT column_name(s)
FROM table1
RIGHT JOIN table2 ON table1.column_name = table2.column_name;
```

* FULL OUTER JOIN

FULL OUTER JOIN 키워드는 table1(왼쪽 테이블)에 있거나, table2(오른쪽 테이블)에 있는 값이라면 모두 리턴한다.

> FULL OUTER JOIN은 굉장히 큰 result-set을 리턴할 가능성이 있다!
> 
> 모든 키워드를 가져오는 요소 때문에, table1에 있지만 table2에는 없는 요소들과 table2에는 없지만 table1에는 있는 요소들이 모두 result-set에 포함된다.
 

* Self JOIN

A self JOIN은 정규 join이지만, 자기 스스로를 join한다.

```
SELECT column_name(s)
FROM table1 T1, table1 T2
WHERE condition;
```

--

#### 1.6 UNION, GROUP BY, HAVING

* UNION Operator

`UNION` operator는 두개 이상의 SELECT 문 결과를 합치는데 쓰인다. 몇가지 특징을 아래에서 나열하도록 한다.

* `UNION` 속의 각 `SELECT` 문은 반드시 같은 수의 컬럼을 가져야 한다.
* 컬럼은 반드시 같은 데이터타입을 가져야 한다.
* 각 `SELECT`구문 속의 컬럼은 반드시 같은 순서대로 있어야 한다.

`UNION` 구문은 다음과 같이 사용가능하다:

```
SELECT column_name(s) FROM table1
UNION
SELECT column_name(s) FROM table2;
```

`UNION ALL` 은 중복되는 값 또한 포함한다. 기본적으로 `UNION`은 중복을 허용하지 않는다.

> result-set의 컬럼값은 보통 SELECT UNION 구문 속 첫번째 컬럼 이름을 따라간다.

---

* GROUP BY 구문

`GROUP BY` 구문은 `COUNT`, `MAX`, `MIN`, `SUM`, `AVG`와 같은 _aggregate functions_와 주로 쓰이며 result-set을 하나 이상의 컬럼으로 묶어준다.

```
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
ORDER BY column_name(s);
```

SELECT로 보려하는 column을 _aggregate functions(집계함수)_ 와 함께 쓰고, GROUP BY로 그룹화해준다는 말이다. 아래에는 다소 복잡한 예시다.

```
SELECT Shippers.ShipperName, COUNT(Orders.OrderID) AS NumberOfOrders FROM Orders
LEFT JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID
GROUP BY ShipperName;
```

이 예시는 다음과 같다:

```
SELECT하라:
Shippers.ShipperName과 COUNT(Orders.OrderID) 값을. 
근데 얘네는 NumberOfOrders라고 result-set에 부르겠다

Orders와 Shippers를 LEFT JOIN 하겠다.

찾는 값은
Orders.ShipperID=Shippers.ShipperID 인 값.

COUNT로 모은건 ShipperName으로 묶어라.
```

정도의 의미가 되겠다.

---

* HAVING 구문

`HAVING` 구절은 `WHERE` 키워드가 _aggregate functions(집계함수)_ 와 함께 쓰이지 못하기 때문에 추가되었다.

HAVING 구문은 다음과 같이 사용된다:

```
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
HAVING condition
ORDER BY column_name(s);
```

사용예시 두가지를 보고 구문을 이해해보자.

구문1)

```
SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country
HAVING COUNT(CustomerID) > 5;

CustomerID의 갯수와 Country를 result-set에 저장하려고 한다.
Customers에서 찾아서.
Country로 값을 묶을 것.
Count(CustomerID)한 결과가 5이상인 값에 대해서.
```

구문2)

```
SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country
HAVING COUNT(CustomerID) > 5
ORDER BY COUNT(CustomerID) DESC;

CustomerID의 갯수와 Country를 result-set에 저장하려고 한다.
Customers에서 찾아서.
Country로 값을 묶을 것.
Count(CustomerID)한 결과가 5이상인 값에 대해서.
Count(CustomerID)한 결과를 내림차순으로 보여달라(큰 수부터).
```

이 아래는 좀더 복잡한 예시다.

```
SELECT Employees.LastName, COUNT(Orders.OrderID) AS NumberOfOrders
FROM Orders
INNER JOIN Employees ON Orders.EmployeeID = Employees.EmployeeID
WHERE LastName = 'Davolio' OR LastName = 'Fuller'
GROUP BY LastName
HAVING COUNT(Orders.OrderID) > 25;

Employees의 LastName과 Orders.OrderID의 갯수를 NumberOfOrders로 result-set에 저장하려한다.
Orders와, Employees를 INNER JOIN 하여.. 조건은 Orders의 EmployeeID와 Employees의 EmployeeID가 같은 값에 대해서.
LastName이 Davolio이거나(OR) Fuller인 사람이다.
LastName을 그룹화하여 묶고,
result-set에 담으려면 Orders의 OrderID가 25이상이어야 한다.

```

[Aggregate Function이란?](http://www.gurubee.net/lecture/1031)

[Aggregate Function에 대한 MS의 설명](https://docs.microsoft.com/en-us/sql/t-sql/functions/aggregate-functions-transact-sql?view=sql-server-2017)

[실전압축 GROUP BY, HAVING 강좌](https://thebook.io/006696/part01/ch05/02/)

---

## 2. Basic SQL Queries

### 1. CREATE, DROP, ALTER Tables

하기 전에 앞서 DB를 만들고 삭제하는 것은 이렇게 한다.

```
CREATE DATABASE databasename;
DROP DATABASE databasename;
```

이 명령은 관리자권한이 있어야 한다. DB 리스트를 보려면 `SHOW DATABASES` 하면 보임.

* CREATE TABLE

`CREATE TABLE` 구문은 DB에 새로운 테이블을 만들 때 쓰인다.

```
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
   ....
);
```

아래 예시는 `CREATE`로 `Person`이라는 테이블에 PersonID, LastName, FirstName, Address, 그리고 City로 이루어진 5개의 컬럼을 만다는 예시다.

```
CREATE TABLE Persons (
    PersonID int,
    LastName varchar(255),
    FirstName varchar(255),
    Address varchar(255),
    City varchar(255) 
);
```

* DROP TABLE

`DROP TABLE` 구문은 존재하는 테이블을 DB에서 없앨 때 사용한다.

```
DROP TABLE table_name;
```

`TRUNCATE TABLE` 테이블 내의 모든 내용을 삭제하나, 테이블을 삭제하지는 않는다.

```
TRUNCATE TABLE table_name;
```

* ALTER TABLE

`ALTER TABLE` 구문은 존재하는 테이블의 컬럼을 추가, 삭제, 수정할 떄 사용한다.

ALTER TABLE - 컬럼 추가

```
ALTER TABLE table_name
ADD column_name datatype;
```

ALTER TABLE - 컬럼 삭제

```
ALTER TABLE table_name
DROP COLUMN column_name;
```

ALTER TABLE - 컬럼 수정

```
ALTER TABLE table_name
ALTER COLUMN column_name datatype;
```

--

### 2. Constraints (unique, PK, FK, Check, Default, Auto-increment, etc.)

SQL Create의 Constraints(제약조건)

`CREATE TABLE` 구문을 사용할 때, `ALTER TABLE` 구문을 사용할 때 테이블의 컬럼에 대해 제약조건을 걸 수 있다. 방법은 다음과 같다.

```
CREATE TABLE table_name (
    column1 datatype constraint,
    column2 datatype constraint,
    column3 datatype constraint,
    ....
);
```

SQL의 제약조건은 테이블 내 데이터들에 규칙을 부여하는데 쓰인다.

이 제약조건은 테이블에 들어가는 데이터타입을 제한하는데 쓰인다. 이는 테이블내 데이터의 정확성과 신뢰성을 보장한다. 제약조건에 어긋나는 생성/추가/수정이 있을 시, 쿼리가 수행되지 않는다.

제약조건은 컬럼레벨, 테이블레벨에 또한 있을 수 있다. 컬럼레벨 제약조건은 특정 컬럼에, 테이블레벨 제약조건은  모든 테이블에 제약조건을 걸 수 있다.

아래의 요소들은 SQL에서 자주 쓰이는 제약조건이다:

* NOT NULL - 컬럼이 `NULL`값을 가지지 않게 보장해준다
* UNIQUE - 모든 컬럼 내 값이 _같지 않음_ 을 보장해준다
* PRIMARY KEY - NOT NULL + UNIQUE. 테이블의 각 행마다 유일하게 식별한다
* FOREIGN KEY - 다른 테이블에서 유일하게 행/레코드를 식별한다
* CHECK - 모든값이 특정 조건을 만족시키는지 보장해준다
* DEFAULT - 아무런 값이 들어가있지 않다면 기본값을 설정해준다
* INDEX - DB로부터 값을 빠르게 만들거나 생성한다.


* NOT NULL

컬럼은 NULL값을 들고있을 수 있지만, 해당 제약조건이 달린다면 NULL값을 허용하지 않는다.

이는 필드가 항상 어느 값을 '가지고'있도록 한다. 이는 값을 추가, 수정할때 값이 없으면 되지 않는다는 말.

```
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255) NOT NULL,
    Age int
);
```

* UNIQUE, PRIMARY KEY(이하 PK)

UNIQUE 제약조건은 모든 컬럼의 값이 다름을 보장한다.

UNIQUE와 PK 모두 컬럼 혹은 컬럼의 집합에 대해 유일함을 보장한다. UNIQUE와의 차이점은 다음과 같다. UNIQUE constraint는 한 테이블에 여럿 있을 수 있지만, PK는 한 테이블에 하나만 존재한다.

PK는 자동으로 UNIQUE 제약조건, NOT NULL 제약조건이 걸린다.

UNIQUE, PK 구문은 문법마다 다르므로 공부시 참조하길 바란다.

[참조링크](https://www.w3schools.com/sql/sql_unique.asp)

* FOREIGN KEY(이하 FK)

FK는 두 테이블을 연결시킬 때 사용한다.

FK는 한 테이블 내의 필드(혹은 필드의 컬렉션)이다. 이는 다른 테이블의 PK를 가리킨다.

FK를 포함하는 테이블은 child table이라고 부른다. Candidate Key(후보키)를 포함하는 테이블은 부모 테이블 혹은 the referenced라고 부른다.

다음 두개의 테이블, Persons, Orders가 있다고 가정하자.

* Persons 테이블:

PersonID|LastName|FirstName|Age
--------|--------|---------|----
1|Hansen|Ola|30
2|Svendson|Tove|23
3|Pettersen|Kari|20

* Orders 테이블:

OrderID|OrderNumber|PersonID
-------|-----------|--------
1|77895|3
2|44678|3
3|22456|2
4|24562|1


Orders 테이블의 PersonID 컬럼은 Persons 테이블의 PersonID 컬럼을 가리킨다.

Persons 테이블의 PersonID 컬럼은 Persons 테이블의 PK이다.
Orders 테이블의 PersonID 컬럼은 Orders 테이블의 FK이다.

FK 제약조건은 두 테이블간의 링크가 끊어지는것을 방지하는데 쓰인다.

FK 제약조건은 또한 유효하지 않은 데이터가 FK 컬럼에 들어가는것을 방지한다. 왜냐하면 테이블이 가리키는 곳에 하나 이상의 값이어야하기 때문이다.

* CHECK

CHECK 제약조건은 컬럼에 위치할 값의 범위를 한정짓는다.

단일 컬럼에 CHECK 제한 조건을 정의하면 이 열에 대해 특정 값만 허용된다.

테이블에 CHECK 제한조건을 걸면 한 행의 다른 컬럼값에 기초하여 특정 컬럼의 값을 제한할 수 있다.

* DEFAULT

DEFAULT 제약조건은 컬럼에 대해 기본값을 제공한다. 기본값은 다른값이 구체화되어있지 않을 때 들어간다.

* INDEX

인덱스는 데이터베이스에서 데이터를 매우 빨리 검색하는 데 쓰인다. 유저는 색인을 볼 수 없으며 검색 / 쿼리 속도를 높이기 위해 사용된다.

중복을 허용하는 케이스:

```
CREATE INDEX index_name
ON table_name (column1, column2, ...);
```

중복을 허용하지 않는 케이스:

```
CREATE UNIQUE INDEX index_name
ON table_name (column1, column2, ...);
```

* AUTO_INCREMENT

AUTO_INCREMENT는 새 레코드가 테이블에 삽입될 때 유일한 숫자가 자동으로 생성되게 한다.

이것은 새로운 레코드가 삽입 될 때마다 자동으로 생성되기를 원하는 기본 키 필드이다.

* DB 날짜정보

[링크참조](https://www.w3schools.com/sql/sql_dates.asp)

* Views

SQL의 View는 SQL 문의 result-set으로 구성된 가상테이블이다.

뷰에는 실제 테이블과 마찬가지로 행과 열이 포함된다. 뷰의 필드는 데이터베이스에있는 하나 이상의 실제 테이블의 필드이다.

SQL 함수, WHERE 및 JOIN 문을 뷰에 추가하고 데이터가 하나의 단일 테이블에서 온 것처럼 데이터를 표시 할 수 있다.

```
CREATE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

> View는 항상 갱신된 데이터를 보여준다. DB엔진은 View의 SQL구문을 이용하여 매 유저가 뷰에 쿼리할 때 새로 View를 만든다.

[예제참조](https://www.w3schools.com/sql/sql_view.asp)