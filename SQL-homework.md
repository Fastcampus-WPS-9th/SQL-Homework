# SQLTutorial
-------

### 1.데이터 베이스를 액세스하고 조작하기 위한 표준 언어
> 구조화 된 커리 언어
> SQL을 사용하면 DB에 엑세스하고, 조작 할 수 있다.
> 


### 2.할 수 있는 일.
> DB 쿼리 실행

> 데이터 검색
> 
> DB에 레코드 삽입
> 
> DB 레코드 삭제
> 
> DB를 새로 생성
> 
> DB에 새로운 테이블 생성
> 
> DB에 저장 프로시저 생성
> 
> DB에 뷰 생성
> 
> 테이블 , 프로시저 및 뷰에 대한 사용 권한 보유
> 

### 3. 웹 사이트에서 SQL 사용
> DB의 데이터를 보여주는 웹 사이트를 구축 시에 필요한 것들.
> >RDBMS (SQL server, My SQL
> >

> 모든 테이블은 필드라는 작은 엔티티로 나뉜다. 필드는 테이블에 모든 레코드에 대한 특정 정보를 유지, 관리하도록 설계된 테이블의 열.
> 
> 레코드는 테이블에 있는 개별 항목 , 테이블의 가로 엔티티
> 
> 컬럼은 테이블의 특정 필드와 연관된 모든 정보를 포함하는 테이블의 수직 엔티티
> 
## DB Table

### 1. DB는 하나 이상의 테이블을 포함하며 각 테이블은 이름로 식별 , 테이블은 데이터가 잇는 레코드를 포함.

### 2. 가장 중요한 SQL 명령 중 일부
> SELECT = DB에서 데이터 추출.
> 
> UPDATE = DB의 데이터 업데이트
> 
> DELETE = DB에서 데이터 삭제
> 
> INSERT INTO = 새로운 데이터 DB에 삽입
> 
> CREATE DATABASE = 새로운 DB 생성.
> 
> ALTER DATABASE = DB 수정.
> 
> CREATE TABLE = 새로운 테이블을 만듬.
> 
> ALTER TABLE = 테이블을 수정
> 
> DROP TABLE = 테이블 삭제 
> 
> CREATE INDEX = 색인 ( 검색 키 )을 사용. 
> 
> DROP INDEX = 색인 삭제.
> 

## SQL SELECT 문

### 1. DB에서 데이터 선택, 리턴 된 데이터는 결과 세트라고 하는 결과 테이블에 저장
> SELECT column 1, column 2....
> 
> FROM table_name;
> 
> 표에서 사용 가능한 모든 필드를 선택하고 싶으면, SELECT*FROM table_name;
> 

### 2. SELECT 열 예제

> SELECT CustomerName , City FROM Customers;
> > 다음 SQL문은 Customers 테이블에서 CustomerName 및 City 열 선택
> > 
> > 

> SELECT*FROM Customers;
> >Customers 테이블의 모든 열을 선택
> >

## SQL SELECT DISTINCT문

### 1. SELECT DISTINCT은 고유한 값만 리턴하는데 사용
> 예) SELECT DISTINCT Country FROM Customers;
> 

### 2. SQL WHERE
> WHERE 절은 레코드를 필터링 하는 것에 사용
> 
> 조건을 충족하는 레코드만 추출하는데 사용
> 
> > 예 ) SELECT * FROM Customers
> > 
> > WHERE Country = 'Mexico';
> > 
> > -> Customers 테이블에서 Mexico 국가의 모든 고객을 선택.
> > 
> >SELECT * FROM Customers
> >
> >WHERE CustomersID=1;
> >
> >-> SQL은 텍스트 값에 대해 작은 따옴표를 사용해야 한다.
> >
> >그러나 숫자 필드는 따옴표로 묶지 않아야 한다.
> >
> 
> SQL AND OR 및 NOT 연산자.
> >WHERE 절은 AND , OR , NOT 연산자와 결합 할 수 있다.
> >
>>> 예) SELECT Column1 , Column2 ...
>>> 
>>> FROm table_name
>>> 
>>> WHERE Condition1 AND Condition2 AND Condition3....;
>>> 
>>> 
>>> SELECT Column1,Column2....
>>>
>>>  FROM table_name
>>>  
>>> WHERE NOT Condition;
>>>
>>>예)
>>>SELECT * FROM Customers
>>>
>>>WHERE Country = 'Germany' AND City = 'Berlin';
>>>
>>>>-> Country 가 Germany 이고 도시가 Berlin인 Customers의 모든 필드를 선택
>>>>
>>>>예) SELECT * FROM Customers;
>>>>
>>>>WHERE NOT Country = 'Germany';
>>>>
>>>>-> Country가 Germany가 아닌, Customers 의 모든 필드 선택
>>>>


## SQL ORDER BY 키워드

### 1. ORDER BY 키워드는 결과 집합을 오름차순 또는 내림차순으로 집결하는데 사용한다 
ORDER BY 키워드는 기본적으로 레코드를 오름차순으로 정렬 내림차순으로 레코드를 정렬하려면 DESC 키워드 사용

SELECT * FROM Customers

ORDER BY County
-> 고객 테이블의 모든 고객을 국가 열로 정렬함

SELECT * FROM Customers

ORDER BY Country DESC;

-> 고객 테이블의 모든 고객을 국가열로 내림차순 하여 정렬

SELECT * FROM Customers

ORDER BY Country ASC , CustomerName DESC;

-> Customers 테이블의 모든 고객을 Country로 오름차순 정렬 CustomerName 열로 내림차순

## SQL INSERT INTO 

### 1. INSET INTO 문은 테이블에 새 레코드를 삽입하는데 사용됨

### 2. 두가지 방법으로 INSERT INTO 문을 작성
>1. 삽입할 열과 값 모두 지정
>> INSERT INTO table_name(Column 1, Column2....)
>> 
>> VALUES( Value1,Value2...);
>> 
>
>2. 모든 열에 추가 할 경우 , 값의 순서가 표의 열과 동일한 순서인지 확인
>
>> INSERT INTO table_name
>> 
>> VALUES(Value1, Value2....);
>> 
>
> INSERT INTO 예제.
> > INSERT INTO Customers (CustomerName , ContactName , Address , City, PostCode , Country)
> > 
> > VALUES ( 'Cardinal','Tom B'~~~~);
> > 
> >
>
>지정된 열에만 데이터 삽입
>>특정 열에만 삽입 가능 , 빈칸은 NULL
>>> INSERT INTO Customers(CustomerName , City , Country)
>>> 
>>> VALUES ( 'Cardinal','Staranger','Norway');
>>> 

## NULL 값을 테스트 하는 방법

### 1. IS NULL과 IS NOT NULL

### 2. IS NULL 연산자
>SELECT LastName,First Name, Address , FROM Persons
>
>WHERE Address IS NULL;
>
>* NULL을 찾으려면 항상 IS NULL 사용
>
>

### 3. IS NOT NULL 연산자
> SELECT LAstName,FistName,Address FROM Persons
> 
> WHERE Address IS NOT NULL;
> >주소가 있는 사람 나열
> >
> >

## SQL UPDATE 문

### 1. 테이블의 기존 레코드를 수정하는데 사용

### 2. UPDATE table_name
> SET Coulmn1 = Value1 , Column2 = Value2 ...
> 
> WHERE Condition;
> 
> * 테이블에서 레코드를 업데이트 할 때 주의 UPDATE 문에서 WHERE절 확인 WHERE은 갱신해야 할 레코드를 지정 WHERE절을 생략하면 모든 레코드 업데이트.
> 
> 

### 3.테이블 업데이트
>UPDATE Customers
>
>SET CoutactName = 'Alfred Submit' , City = 'FrankFurt'
>
>WHERE CustomerID = 1;
>
>> ->첫번째 고객 (Customer ID=1)을 새 담당자 및 새 도시로 업데이트
>> 


### 4. 여러 레코드 업데이트
> 업데이트 될 레코드 수를 결정하는 것은 WHERE 절
> 
> 예) UPDATE Customers
> 
> SET ContactName = 'Juon'
> 
> WHERE Country = 'Mexico';
> 
> -> Country가 Mexico인 모든 레코드에 대해 연락처 이름을 'Juon'으로 업데이트
> 


## SQL DELETE문

>테이블의 기존 레코드를 삭제하는데 사용 
>
>* 레코드 삭제시 주의사항, DELETE문의 WHERE절 확인 WHERE절 생략시 모든 레코드가 삭제
>
>

###1. 예
> DELETE FROM Customers
> 
> WHERE CustomerName = 'Alfreds Futterkiste';
> 
> -> Customers 테이블에서 고객 Alfred Futterkiste를 삭제
> 

### 2. 모든 레코드 삭제
>DELETE FROM table_name;
>


##SQL SELECT TOP 절 

> 리턴할 레코드 수를 지정하는데 사용
> > 수천개의 레코드가 있는 큰 테이블에 유용
> > 
> 
> 모든 DB시스템이 SELECT TOP 절을 지원하는데 사용
> 
> MySQL은 제한된 수의 레코드를 선택하기 위해 LIMIT절 지원 oracle은 ROWMIN 을 사용

###1. SQL Server / MS 액세스 구문 
>SELECT TOP number|percent column_name(s)
>
>FROM table_name
>
>WHERE condition;


###2.MySQL 구문 
>SELECT column_name(s)
>
>FROM table_name
>
>WHERE condition
>
>LIMIT number;

###3.Oracle 구문 
>SELECT column_name(s)
>
>FROM table_name
>
>WHERE ROWNUM <= number;

### 4.다음 SQL 문은 "Customers"테이블에서 처음 세 개의 레코드를 선택합니다.
>SELECT TOP 3 * FROM Customers;

### 5.다음 SQL 문은 LIMIT 절을 사용하는 동일한 예제를 보여줍니다.

>SELECT * FROM Customers
>
>LIMIT 3;


### 6.다음 SQL 문은 ROWNUM을 사용하는 동일한 예제를 보여줍니다.

>SELECT * FROM Customers
>
>WHERE ROWNUM <= 3;

###SQL TOP PERCENT 예제
>다음 SQL 문은 "Customers"테이블에서 레코드의 처음 50 %를 선택합니다.
>>SELECT TOP 50 PERCENT * FROM Customers;
>
>다음 SQL 문은 "Customers"테이블에서 국가가 "Germany"인 처음 세 개의 레코드를 선택합니다.
>>SELECT TOP 3 * FROM Customers
>>
>>WHERE Country='Germany';

>다음 SQL 문은 LIMIT 절을 사용하는 동일한 예제를 보여줍니다.

>>SELECT * FROM Customers
>>
>>WHERE Country='Germany'
>>
>>LIMIT 3;

>다음 SQL 문은 ROWNUM을 사용하는 동일한 예제를 보여줍니다.
>>SELECT * FROM Customers
>>
>>WHERE Country='Germany' AND ROWNUM <= 3;

##SQL MIN () 및 MAX () 함수
>SQL MIN () 및 MAX () 함수
>>MIN () 함수는 선택된 컬럼의 가장 작은 값을 리턴합니다.
>>
>>MAX () 함수는 선택된 열의 가장 큰 값을 반환합니다.

###1.MIN () 구문
>SELECT MIN(column_name)
>
>FROM table_name
>
>WHERE condition;

###2.MAX () 구문
>SELECT MAX(column_name)
>
>FROM table_name
>
>WHERE condition;

###MIN () 예제
>다음 SQL 문은 가장 저렴한 제품의 가격을 찾습니다.
>>SELECT MIN(Price) AS SmallestPrice
>>
>>FROM Products;

###MAX () 예제
>다음 SQL 문은 가장 비싼 제품의 가격을 찾습니다.
>>SELECT MAX(Price) AS LargestPrice
>>
>>FROM Products;


##SQL COUNT (), AVG () 및 SUM () 함수
###1.SQL COUNT (), AVG () 및 SUM () 함수
>COUNT () 함수는 지정된 기준과 일치하는 행 수를 반환합니다.
>
>AVG () 함수는 숫자 열의 평균값을 반환합니다.
>
>SUM () 함수는 숫자 열의 총 합계를 반환합니다.

###2.COUNT () 구문
>SELECT COUNT(column_name)
>
>FROM table_name
>
>WHERE condition;

###3.AVG () 구문
>SELECT AVG(column_name)
>
>FROM table_name
>
>WHERE condition;

###4.SUM () 구문
>SELECT SUM(column_name)
>
>FROM table_name
>
>WHERE condition;

###5.COUNT () 예제
>다음 SQL 문은 제품 수를 찾습니다.
>>SELECT COUNT(ProductID)
>>
>>FROM Products;

###6.AVG () 예제
>다음 SQL 문은 모든 제품의 평균 가격을 찾습니다.
>>SELECT AVG(Price)
>>
>>FROM Products;

###7.SUM () 예제
>다음 SQL 문은 OrderDetails 테이블의 "Quantity"필드의 합계를 찾습니다.

>>SELECT SUM(Quantity)
>>
>>FROM OrderDetails;

##SQL LIKE 연산자
>SQL LIKE 연산자
>>LIKE 연산자는 WHERE 절에서 열의 지정된 패턴을 검색하는 데 사용됩니다.
>>
>>LIKE 연산자와 함께 사용되는 두 개의 와일드 카드가 있습니다.

* % - 백분율 기호는 0, 1 또는 복수 문자를 나타냅니다.

* _ - 밑줄은 한 문자를 나타냅니다.
###1.LIKE 구문
>SELECT column1, column2, ...
>
>FROM table_name
>
>WHERE columnN LIKE pattern;

###2.SQL LIKE 예제
>다음 SQL 문은 CustomerName이 "a"로 시작하는 모든 고객을 선택합니다.

>>SELECT * FROM Customers
>>
>>WHERE CustomerName LIKE 'a%';

>다음 SQL 문은 CustomerName이 "a"로 끝나는 모든 고객을 선택합니다.
>>SELECT * FROM Customers
>>
>>WHERE CustomerName LIKE '%a';

>다음 SQL 문은 CustomerName이 "or"인 모든 고객을 선택합니다.
>>SELECT * FROM Customers
>>
>>WHERE CustomerName LIKE '%or%';

>다음 SQL 문은 두 번째 위치에 "r"이있는 CustomerName을 가진 모든 고객을 선택합니다.
>>SELECT * FROM Customers
>>
>>WHERE CustomerName LIKE '_r%';

>다음 SQL 문은 CustomerName이 "a"로 시작하고 길이가 3 자 이상인 모든 고객을 선택합니다.

>>SELECT * FROM Customers
>>
>>WHERE CustomerName LIKE 'a_%_%';

##SQL 와일드 카드
SQL 와일드 카드 문자
와일드 카드 문자는 문자열의 다른 문자를 대체하는 데 사용됩니다.

와일드 카드 문자는 SQL LIKE 연산자 와 함께 사용됩니다 . LIKE 연산자는 WHERE 절에서 열의 지정된 패턴을 검색하는 데 사용됩니다. 

LIKE 연산자와 함께 사용되는 두 개의 와일드 카드가 있습니다.

% - 백분율 기호는 0, 1 또는 복수 문자를 나타냅니다.
_ - 밑줄은 한 문자를 나타냅니다.
MS Access 및 SQL Server에서는 다음을 사용할 수도 있습니다.

[ charlist ] - 일치시킬 문자와 세트의 범위를 정의합니다.
[^ charlist ] 또는 [! charlist ] - 일치하지 않는 문자의 집합과 범위를 정의합니다.
와일드 카드는 조합하여 사용할 수도 있습니다!

다음은 '%'와 '_'와일드 카드가있는 다른 LIKE 연산자를 보여주는 몇 가지 예입니다.

###1.% 와일드 카드 사용
>다음 SQL 문은 City가 "ber"로 시작하는 모든 고객을 선택합니다.
>>SELECT * FROM Customers
>>
>>WHERE City LIKE 'ber%';

>다음 SQL 문은 패턴이 "es"인 City가있는 모든 고객을 선택합니다. 
>>SELECT * FROM Customers
>>
>>WHERE City LIKE '%es%';

###2._ 와일드 카드 사용
>다음 SQL.은 임의의. 자로 시작하고 "erlin"다음에 City가있는 모든 고객을 선택합니다.
>>SELECT * FROM Customers
>>
>>WHERE City LIKE '_erlin';

>다음 SQL 문은 도시가 "L"로 시작하고 모든 문자, 그 다음에 "n"다음에 문자가오고 "on"이 오는 모든 고객을 선택합니다.
>>SELECT * FROM Customers
>>
>>WHERE City LIKE 'L_n_on';

###3.[charlist] 와일드 카드 사용
>다음 SQL 문은 City가 "b", "s"또는 "p"로 시작하는 모든 고객을 선택합니다.

>>SELECT * FROM Customers
>>
>>WHERE City LIKE '[bsp]%';

>다음 SQL 문은 도시가 "a", "b"또는 "c"로 시작하는 모든 고객을 선택합니다.
>>SELECT * FROM Customers
>>
>>WHERE City LIKE '[a-c]%';

###4.[! charlist] 와일드 카드 사용
>다음 두 SQL 문은 "b", "s"또는 "p"로 시작하는 도시가 아닌 모든 고객을 선택합니다.
>>SELECT * FROM Customers
>>
>>WHERE City LIKE '[!bsp]%';

##SQL IN 연산자
SQL IN 연산자
IN 연산자를 사용하여 WHERE 절에 여러 값을 지정할 수 있습니다.

IN 연산자는 여러 OR 조건의 줄임말입니다.
###1.IN 구문
>SELECT column_name(s)
>
>FROM table_name
>
>WHERE column_name IN (value1, value2, ...);

###2.IN 연산자 예제
다음 SQL 문은 "Germany", "France"및 "UK"에있는 모든 고객을 선택합니다.

>SELECT * FROM Customers
>
>WHERE Country IN ('Germany', 'France', 'UK');

##SQL BETWEEN 연산자
SQL BETWEEN 연산자
BETWEEN 연산자는 주어진 범위 내의 값을 선택합니다. 값은 숫자, 텍스트 또는 날짜 일 수 있습니다.

BETWEEN 연산자는 시작과 끝 값이 포함됩니다. 
###1.BETWEEN 구문
>SELECT column_name(s)
>
>FROM table_name
>
>WHERE column_name BETWEEN value1 AND value2;

###2.BETWEEN 예제
다음 SQL 문은 가격이 10과 20 사이 인 모든 제품을 선택합니다.

>SELECT * FROM Products
>
>WHERE Price BETWEEN 10 AND 20;

###3.제외 예제
앞의 예제 범위를 벗어난 제품을 표시하려면 NOT BETWEEN :
>SELECT * FROM Products
>
>WHERE Price NOT BETWEEN 10 AND 20;

###4.IN 예제에서 BETWEEN
다음 SQL 문은 가격이 10과 20 사이 인 모든 제품을 선택합니다. CategoryID가 1,2 또는 3 인 제품을 표시하지 않습니다.

>SELECT * FROM Products
>
>WHERE (Price BETWEEN 10 AND 20)
>
>AND NOT CategoryID IN (1,2,3);

###5.텍스트 값과의 차이점 예제
다음 SQL 문은 'Carnarvon Tigers'와 'Mozzarella di Giovanni'사이에 ProductName이있는 모든 제품을 선택합니다.

>SELECT * FROM Products
>
>WHERE ProductName BETWEEN 'Carnarvon Tigers' AND 'Mozzarella di Giovanni'
>
>ORDER BY ProductName;

###6.텍스트 값과는 다른 예
다음 SQL 문은 ProductName이 'Carnarvon Tigers'및 'Mozzarella di Giovanni'가 아닌 모든 제품을 선택합니다.

>SELECT * FROM Products
>
>WHERE ProductName NOT BETWEEN 'Carnarvon Tigers' AND 'Mozzarella di Giovanni'
>
>ORDER BY ProductName;

###7.날짜와 예제
다음 SQL.은 OrderDate BETWEEN '01 -July-1996 'W '31-Junly-1996'이있는 모든 주.을 선택합니다.

>SELECT * FROM Orders
>
>WHERE OrderDate BETWEEN #01/07/1996# AND #31/07/1996#;

##SQL 별칭

SQL 별칭
SQL 별칭은 테이블 또는 테이블의 열에 임시 이름을 지정하는 데 사용됩니다.

앨리어스 (alias)는 컬럼 이름을 읽기 쉽게하기 위해 자주 사용됩니다.

별명은 조회 기간 동안 만 존재합니다.

###1.별칭 열 구문
>SELECT column_name AS alias_name
>
>FROM table_name;

###2.별칭 테이블 구문
>SELECT column_name(s)
>
>FROM table_name AS alias_name;

###3.열의 별칭 예제
다음 SQL 문은 CustomerID 열과 CustomerName 열의 두 가지 별칭을 만듭니다.
>SELECT CustomerID AS ID, CustomerName AS Customer
>
>FROM Customers;

###4.별칭은 다음과 같은 경우에 유용합니다.

* 쿼리에 두 개 이상의 테이블이 관련되어 있습니다.
* 함수는 쿼리에서 사용됩니다.
* 열 이름이 크거나 매우 읽을 수 없습니다.
* 두 개 이상의 열이 결합되었습니다.

##SQL 조인
SQL JOIN
JOIN 절은 두 개 이상의 테이블에있는 행을 결합하는 데 사용됩니다.

'주문'표에서 선택 항목을 살펴 보겠습니다

다양한 유형의 SQL JOIN
다음은 SQL에있는 JOIN의 여러 유형입니다.

###1.(INNER) JOIN : 
>두 테이블에서 값이 일치하는 레코드를 반환합니다.

###2.LEFT (OUTER) JOIN : 
>왼쪽 테이블에서 모든 레코드를 반환하고 오른쪽 테이블에서 일치하는 레코드를 반환합니다.

###3.RIGHT (OUTER) JOIN : 
>오른쪽 테이블에서 모든 레코드를 반환하고 왼쪽 테이블에서 일치하는 레코드를 반환합니다.

###4.FULL (OUTER) JOIN : 
>왼쪽 또는 오른쪽 테이블에 일치하는 항목이 있으면 모든 레코드를 반환합니다. 

##SQL INNER JOIN 키워드
SQL INNER JOIN 키워드
INNER JOIN 키워드는 두 표에서 모두 일치하는 값을 가진 레코드를 선택합니다.

###1.INNER JOIN 구문
>SELECT column_name(s)
>
>FROM table1
>
>INNER JOIN table2 ON table1.column_name = table2.column_name;

###2.SQL INNER JOIN 예제
>다음 SQL.은 고객 정보가있는 모든 주.을 선택합니다.

>SELECT Orders.OrderID, Customers.CustomerName
>
>FROM Orders
>
>INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID;
 
 
##SQL LEFT JOIN 키워드
SQL LEFT JOIN 키워드
LEFT JOIN 키워드는 왼쪽 테이블 (table1)의 모든 레코드와 오른쪽 테이블 (table2)의 일치 레코드를 반환합니다. 일치하는 것이 없으면 오른쪽에서 결과가 NULL입니다.

###1. LEFT JOIN 구문
>SELECT column_name(s)
>
>FROM table1
>
>LEFT JOIN table2 ON table1.column_name = table2.column_name;
 
##SQL RIGHT JOIN 키워드
SQL RIGHT JOIN 키워드
RIGHT JOIN 키워드는 오른쪽 테이블 (table2)의 모든 레코드와 왼쪽 테이블 (table1)의 일치 레코드를 반환합니다. 일치가없는 경우 결과는 왼쪽에서 NULL입니다.

###1.RIGHT JOIN 구문
>SELECT column_name(s)
>
>FROM table1
>
>RIGHT JOIN table2 ON table1.column_name = table2.column_name;
 
##SQL 전체 외부 조인 키워드
SQL 전체 외부 조인 키워드
FULL OUTER JOIN 키워드는 왼쪽 (table1) 또는 오른쪽 (table2) 테이블 레코드가 일치 할 때 모든 레코드를 리턴합니다.

*참고 : FULL OUTER JOIN은 잠재적으로 매우 큰 결과 집합을 반환 할 수 있습니다!

###1.전체 외부 조인 구문
>SELECT column_name(s)
>
>FROM table1
>
>FULL OUTER JOIN table2 ON table1.column_name = table2.column_name;

##SQL 자체 조인
SQL 자체 조인
self JOIN은 정규 조인이지만 테이블 자체는 조인됩니다.

###1.자체 조인 구문
>SELECT column_name(s)
>
>FROM table1 T1, table1 T2
>
>WHERE condition;

##SQL UNION 연산자
SQL UNION 연산자
UNION 연산자는 두 개 이상의 SELECT 문의 결과 집합을 결합하는 데 사용됩니다.

* UNION 내의 각 SELECT 문은 같은 수의 열을 가져야합니다.
* 열은 유사한 데이터 형식을 가져야합니다.
* 각 SELECT 문의 열은 같은 순서로 있어야합니다
###1.UNION 구문
>SELECT column_name(s) FROM table1
>
>UNION
>
>SELECT column_name(s) FROM table2;

###2.UNION ALL 구문
UNION 연산자는 기본적으로 고유 값만 선택합니다. 중복 값을 허용하려면 UNION ALL을 사용하십시오.

>SELECT column_name(s) FROM table1
>
>UNION ALL
>
>SELECT column_name(s) FROM table2;

* SQL UNION 예제
다음 SQL 문은 "Customers"및 "Suppliers"에서 모든 다른 도시 (고유 한 값만)를 선택합니다.

>SELECT City FROM Customers
>
>UNION
>
>SELECT City FROM Suppliers
>
>ORDER BY City;

*SQL UNION ALL 예제
다음 SQL.은 "Customers"W "Suppliers"에서 모든 도시 (중복 값도)를 선택합니다.

>SELECT City FROM Customers
>
>UNION ALL
>
>SELECT City FROM Suppliers
>
>ORDER BY City;

##SQL GROUP BY 문
SQL GROUP BY 문
GROUP BY 문은 집계 함수 (COUNT, MAX, MIN, SUM, AVG)와 함께 사용되어 결과 집합을 하나 이상의 열로 그룹화합니다.
###1.GROUP BY 구문
>SELECT column_name(s)
>
>FROM table_name
>
>WHERE condition
>
>GROUP BY column_name(s)
>
>ORDER BY column_name(s);

###2.SQL GROUP BY 예제
다음 SQL 문은 각 국가의 고객 수를 나열합니다.

>SELECT COUNT(CustomerID), Country
>
>FROM Customers
>
>GROUP BY Country;

###3.JOIN 예제를 사용한 GROUP BY
다음 SQL 문은 각 발송인이 보낸 주문 수를 나열합니다.

>SELECT Shippers.ShipperName, COUNT(Orders.OrderID) AS NumberOfOrders 
>
>FROM Orders
>
>LEFT JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID
>
>GROUP BY ShipperName;

##SQL HAVING 절
SQL HAVING 절
WHERE 키워드를 집계 함수와 함 2 사용할 수 없으므로 HAVING 절이 SQL에 추가되었습니다.

###1.HAVING 구문
>SELECT column_name(s)
>
>FROM table_name
>
>WHERE condition
>
>GROUP BY column_name(s)
>
>HAVING condition
>
>ORDER BY column_name(s);
###2.SQL의 예
다음 SQL.은 각 국가의 고객 수를 나열합니다. 5 명 이상의 고객이있는 국가 만 포함 :

>SELECT COUNT(CustomerID), Country
>
>FROM Customers
>
>GROUP BY Country
>
>HAVING COUNT(CustomerID) > 5;

##SQL EXISTS 연산자
SQL EXISTS 연산자
EXISTS 연산자는 하위 쿼리에 레코드가 있는지 테스트하는 데 사용됩니다.

EXISTS 연산자는 하위 쿼리가 하나 이상의 레코드를 반환하면 true를 반환합니다.

###1.존재 구문
>SELECT column_name(s)
>
>FROM table_name
>
>WHERE EXISTS
>
>(SELECT column_name FROM table_name WHERE condition);
###2.SQL EXISTS 예제
다음 SQL 문은 TRUE를 반환하고 제품 가격이 20 미만인 공급 업체를 나열합니다.

>SELECT SupplierName
>
>FROM Suppliers
>
>WHERE EXISTS (SELECT ProductName FROM Products WHERE SupplierId = 
>Suppliers.supplierId AND Price < 20);


#SQL 데이터베이스
-----------
##SQL CREATE DATABASE 문
CREATE DATABASE 문은 새 SQL 데이터베이스를 만드는 데 사용됩니다.

>CREATE DATABASE databasename;
CREATE DATABASE 예제
>다음 SQL 문은 "testDB"라는 데이터베이스를 생성합니다.
>>CREATE DATABASE testDB;


##SQL DROP DATABASE 문
###1.SQL DROP DATABASE 문
>DROP DATABASE 문은 기존 SQL 데이터베이스를 삭제하는 데 사용됩니다.

>>DROP DATABASE databasename;

###2.DROP DATABASE 예제
>다음 SQL 문은 기존 데이터베이스 "testDB"를 삭제합니다.
>>DROP DATABASE testDB;

##DROP DATABASE testDB;
###1.SQL CREATE TABLE 문
CREATE TABLE 문은 데이터베이스에 새 테이블을 만드는 데 사용됩니다.

>CREATE TABLE table_name (
>
>    column1 datatype,
> 
>    column2 datatype,
> 
>    column3 datatype,
> 
>   ....
> 
>);

column 매개 변수는 테이블의 열 이름을 지정합니다.

datatype 매개 변수는 열에서 보유 할 수있는 데이터 유형 (예 : varchar, 정수, 날짜 등)을 지정합니다.

팁 : 사용 가능한 데이터 유형에 대한 개요는 전체 데이터 유형 참조로 이동하십시오 .
###2.SQL CREATE TABLE 예제
다음 예에서는 PersonID, LastName, FirstName, Address 및 City라는 다섯 개의 열이 포함 된 "Persons"라는 테이블을 만듭니다.

>CREATE TABLE Persons (
>
>    PersonID int,
> 
>    LastName varchar(255),
> 
>    FirstName varchar(255),
> 
>    Address varchar(255),
> 
>    City varchar(255) 
> 
>);


PersonID 열은 int 유형이며 정수를 포함합니다.

LastName, FirstName, Address 및 City 열은 varchar 유형이며 문자를 포함하며이 필드의 최대 길이는 255 자입니다.

빈 "Persons"테이블은 이제 다음과 같이 보입니다.

###3.다른 테이블을 사용하여 테이블 만들기
기존 테이블의 사본은 CREATE TABLE.과 SELECT.의 조합을 사용하여 작성할 수 있습니다.

새 테이블은 동일한 열 정의를 가져옵니다. 모든 열 또는 특정 열을 선택할 수 있습니다.

기존 테이블을 사용하여 새 테이블을 만들면 새 테이블은 이전 테이블의 기존 값으로 채워집니다.

>CREATE TABLE new_table_name AS
>
>    SELECT column1, column2,...
> 
>    FROM existing_table_name
> 
>    WHERE ....;

##SQL DROP TABLE 문
###1.SQL DROP TABLE 문
>DROP TABLE 문은 데이터베이스의 기존 테이블을 삭제하는 데 사용됩니다.
>
>DROP TABLE table_name;

###2.SQL DROP TABLE 예제
>다음 SQL 문은 기존 테이블 "Shippers"를 삭제합니다.

>DROP TABLE Shippers;

###3.SQL TRUNCATE TABLE
>TRUNCATE TABLE 문은 테이블 내부의 데이터는 삭제하지만 테이블 자체는 삭제하지 않습니다.
>
>TRUNCATE TABLE table_name;

##SQL ALTER TABLE 문

###1.SQL ALTER TABLE 문
ALTER TABLE 문은 기존 테이블의 열을 추가, 삭제 또는 수정하는 데 사용됩니다.

ALTER TABLE.은 기존 테이블에 다양한 제한 조건을 추가 W h 제하는 데에도 사용됩니다.

###2.ALTER TABLE - 열 추가
>ALTER TABLE - 열 추가
>
>ALTER TABLE table_name
>
>ADD column_name datatype;

###3.ALTER TABLE - DROP COLUMN
테이블의 열을 삭제하려면 다음 구문을 사용하십시오 (일부 데이터베이스 시스템에서는 열 삭제가 허용되지 않음).

>ALTER TABLE table_name
>
>DROP COLUMN column_name;

###4.ALTER TABLE - ALTER / MODIFY COLUMN
테이블에있는 열의 데이터 형식을 변경하려면 다음 구문을 사용합니다.

SQL Server / MS 액세스 :

>ALTER TABLE table_name
>
>ALTER COLUMN column_name datatype;

##SQL 제약
SQL constraints are used to specify rules for data in a table.

번역 : SQL 제한 조건은 테이블의 데이터에 대한 j을 지정하는 데 사용됩니다.

###1.SQL 제약 조건 만들기
CREATE TABLE.으로 테이블이 작성 될 때 또는 ALTER TABLE.으로 테이블이 작성된 후에 제한 조건을 지정할 수 있습니다.

>CREATE TABLE table_name (
>
>    column1 datatype constraint,
> 
>    column2 datatype constraint,
> 
>    column3 datatype constraint,
> 
>    ....
>
>);

###2.SQL 제약
SQL 제약 조건은 테이블의 데이터에 대한 규칙을 지정하는 데 사용됩니다.

제약 조건은 테이블에 들어갈 수있는 데이터 유형을 제한하는 데 사용됩니다. 이렇게하면 표의 데이터 정확성과 신뢰성이 보장됩니다. 제한 조건과 데이터 조치 사이에 위반이 있으면 조치가 중단됩니다.

제약 조건은 열 수준 또는 테이블 수준 일 수 있습니다. 컬럼 레벨 제한 조건은 컬럼에 적용되고 테이블 레벨 제한 조건은 전체 테이블에 적용됩니다.

SQL에서 일반적으로 사용되는 다음 제약 조건이 있습니다.

* NOT NULL - 열이 NULL 값을 가질 수 없음을 보장합니다.
* UNIQUE - 열의 모든 값이 서로 다른지 확인합니다.
* PRIMARY KEY - NOT NULL과 UNIQUE의 조합. 테이블의 각 행을 고유하게 식별합니다.
* 외부 키 - 다른 테이블의 행 / 레코드를 고유하게 식별합니다.
* CHECK - 열의 모든 값이 특정 조건을 충족하는지 확인합니다.
* DEFAULT - 값이 지정되지 않은 경우 열의 기본값을 설정합니다.
* INDEX - 데이터베이스에서 데이터를 매우 신속하게 생성 및 검색하는 데 사용됩니다.

##SQL NOT NULL 제약 조건
###1.SQL NOT NULL 제약 조건
기본적으로 열은 NULL 값을 포함 할 수 있습니다.

NOT NULL 제약 조건은 열이 NULL 값을 허용하지 않도록 강제합니다.

이렇게하면 필드에 항상 값이 포함될 수 있습니다. 즉, 새 레코드를 삽입하거나이 필드에 값을 추가하지 않고 레코드를 업데이트 할 수 없습니다.

* 다음 SQL은 "ID", "LastName"및 "FirstName"열이 NULL 값을 허용하지 않도록합니다.

>CREATE TABLE Persons (
>
>    ID int NOT NULL,
> 
>    LastName varchar(255) NOT NULL,
> 
>    FirstName varchar(255) NOT NULL,
> 
>    Age int
> 
>);
>

##SQL UNIQUE 제약 조건
###1.SQL UNIQUE 제약 조건
UNIQUE 제약 조건은 열의 모든 값이 서로 다른지 확인합니다.

UNIQUE 및 PRIMARY KEY 제약 조건은 열 또는 열 집합의 고유성을 보장합니다.

PRIMARY KEY 제약 조건에는 자동으로 UNIQUE 제약 조건이 있습니다.

그러나 테이블 당 많은 UNIQUE 제약 조건을 가질 수 있지만 테이블 당 하나의 PRIMARY KEY 제약 조건 만 가질 수 있습니다

###2.CREATE TABLE에 대한 SQL UNIQUE 제약 조건
다음 SQL은 "Person"테이블을 만들 때 "ID"열에 UNIQUE 제약 조건을 만듭니다.

**SQL Server / Oracle / MS 액세스 :**
>CREATE TABLE Persons (
>
>    ID int NOT NULL UNIQUE,
> 
>    LastName varchar(255) NOT NULL,
> 
>    FirstName varchar(255),
> 
>    Age int
> 
>);

###3.ALTER TABLE에 대한 SQL UNIQUE 제약
테이블이 이미 만들어 졌을 때 "ID"열에 UNIQUE 제약 조건을 만들려면 다음 SQL을 사용하십시오.

**MySQL / SQL 서버 / 오라클 / MS 액세스 :**
>ALTER TABLE Persons
>
>ADD UNIQUE (ID);

###4.UNIQUE 제약 조건 삭제
UNIQUE 제약 조건을 삭제하려면 다음 SQL을 사용하십시오.

>ALTER TABLE Persons
>
>DROP CONSTRAINT UC_Person;

##SQL PRIMARY KEY 제약
###1.SQL PRIMARY KEY 제약
PRIMARY KEY 제약 조건은 데이터베이스 테이블의 각 레코드를 고유하게 식별합니다.

기본 키는 UNIQUE 값을 포함해야하며 NULL 값을 포함 할 수 없습니다.

테이블에는 기본 키가 하나만있을 수 있습니다. 기본 키는 하나 또는 여러 개의 필드로 구성 될 수 있습니다.
###2.CREATE TABLE의 SQL PRIMARY KEY
다음 SQL은 "Person"테이블이 생성 될 때 "ID"열에 PRIMARY KEY를 만듭니다.
CREATE TABLE Persons (
  **ID int NOT NULL PRIMARY KEY,**
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int
);
###3.ALTER TABLE에 대한 SQL PRIMARY KEY
ALTER TABLE Persons
ADD CONSTRAINT PK_Person PRIMARY KEY (ID,LastName);
>PRIMARY KEY 제약 조건의 이름 지정을 허용하고 여러 열에 대해 PRIMARY KEY 제약 조건을 정의하려면 다음 SQL 구문을 사용합니다.

###4.PRIMARY KEY 제약 조건 삭제
ALTER TABLE Persons
DROP CONSTRAINT PK_Person;
>PRIMARY KEY 제약 조건을 삭제하려면 다음 SQL을 사용하십시오.

##SQL FOREIGN KEY 제약
###1.SQL FOREIGN KEY 제약
외래 키는 두 테이블을 서로 연결하는 데 사용되는 키입니다.
외부 키는 다른 테이블의 PRIMARY KEY를 참조하는 테이블의 필드 (또는 필드 모음)입니다.
외래 키가 들어있는 테이블을 하위 테이블이라고하고 후보 키가 들어있는 테이블을 참조 된 테이블 또는 상위 테이블이라고합니다.

##SQL CHECK 제약
CHECK 제약 조건은 열에 배치 할 수있는 값 범위를 제한하는 데 사용됩니다.
단일 열에 CHECK 제한 조건을 정의하면이 열에 대해 특정 값만 허용됩니다.

##SQL DEFAULT 제약 조건
###1.SQL DEFAULT 제약 조건
>DEFAULT 제약 조건은 열의 기본값을 제공하는 데 사용됩니다.
>
>다른 값을 지정하지 않으면 기본값이 모든 새 레코드에 추가됩니다.


##SQL CREATE INDEX 문
###1.SQL CREATE INDEX 문
>CREATE INDEX 문은 테이블에 인덱스를 만드는 데 사용됩니다.
>
>인덱스는 데이터베이스에서 데이터를 매우 빨리 검색하는 데 사용됩니다. 사용자는 색인을 볼 수 없으며 검색 / 쿼리 속도를 높이기 위해 사용됩니다.


###2.CREATE INDEX 구문
>테이블에 인덱스를 만듭니다. 중복 된 값이 허용됩니다.
CREATE INDEX index_name
ON table_name (column1, column2, ...);

###3.CREATE UNIQUE INDEX 구문
>테이블에 고유 인덱스를 작성합니다. 중복 값은 허용되지 않습니다.

CREATE UNIQUE INDEX index_name
ON table_name (column1, column2, ...);

**참고 : 인덱스를 만드는 구문은 데이터베이스마다 다릅니다. 따라서 데이터베이스의 인덱스 작성 구문을 확인하십시오.**

###4.CREATE INDEX 예제
>아래의 SQL 문은 "Persons"테이블의 "LastName"열에 "idx_lastname"이라는 인덱스를 만듭니ㅈ다.
>

CREATE INDEX idx_lastname
ON Persons (LastName);

###5.DROP INDEX 문
>DROP INDEX 문은 테이블의 인덱스를 삭제하는 데 사용됩니다.

ALTER TABLE table_name
DROP INDEX index_name;

##SQL AUTO INCREMENT 필드

###1.AUTO INCREMENT 필드
자동 증가는 새 레코드가 테이블에 삽입 될 때 고유 번호가 자동으로 생성되도록합니다.

종종 이것은 새로운 레코드가 삽입 될 때마다 자동으로 생성되기를 원하는 기본 키 필드입니다.

###2.MySQL 구문
>다음 SQL 문은 "Person"테이블의 자동 증가 기본 키 필드로 "ID"열을 정의합니다.

CREATE TABLE Persons (
    ID int NOT NULL AUTO_INCREMENT,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    PRIMARY KEY (ID)
);
AUTO_INCREMENT 키워드를 사용하여 자동 증가 기능을 수행합니다.
기본적으로 AUTO_INCREMENT의 시작 값은 1이며 새 레코드마다 1 씩 증가합니다.
AUTO_INCREMENT 시퀀스를 다른 값으로 시작하려면 다음 SQL 문을 사용하십시오.

ALTER TABLE Persons AUTO_INCREMENT=100;

"Persons"테이블에 새 레코드를 삽입하려면 "ID"열에 값을 지정할 필요가 없습니다 (고유 한 값이 자동으로 추가됩니다).

INSERT INTO Persons (FirstName,LastName)
VALUES ('Lars','Monsen');

위의 SQL 문은 "Persons"테이블에 새 레코드를 삽입합니다. "ID"열에 고유 한 값이 할당됩니다. 

"FirstName"열은 "Lars"로 설정되고 "LastName"열은 "Monsen"으로 설정됩니다.

##SQL Dates
**Dates 작업을 할 때 가장 어려운 부분은 삽입하려는 Dates 형식이 데이터베이스의 Dates 열 형식과 일치하는지 확인하는 것입니다.**

데이터에 날짜 부분 만 포함되어 있으면 쿼리가 예상대로 작동합니다. 그러나 시간 부분이 관련되면 더 복잡해집니다.

###1.SQL 날짜 데이터 유형
**MySQL** 에는 데이터베이스에 날짜 또는 날짜 / 시간 값을 저장하기위한 다음 데이터 유형이 있습니다.

* DATE - YYYY-MM-DD 형식
* DATETIME - 형식 : YYYY-MM-DD HH : MI : SS
* TIMESTAMP - 형식 : YYYY-MM-DD HH : MI : SS
* YEAR - YYYY 또는 YY 형식

###2.SQL 작업 날짜
관련된 시간 구성 요소가 없으면 두 데이터를 쉽게 비교할 수 있습니다!

**팁** : 검색어를 간단하고 쉽게 유지하려면 데이터에 시간 구성 요소를 허용하지 마십시오!



