# SQL Constraints

`Constraints`는 테이블에 대한 룰을 지정하는데 사용된다.
제약조건은 테이블에 들어갈 수 있는 데이터의 유형을 제한하는데 사용된다.
이렇게 하면 표의 데이터 **정확성**과 **신뢰성**이 보장된다.
제한조건에 위반되는 행동이 있을경우, 그 행동은 중단된다.

제약조건은 `컬럼 수준` 또는 `테이블 수준`일 수 있다.

### Commonly Used in SQL
- NOT NULL : 열이 NULL 값을 가질 수 없음을 보장한다.
- UNIQUE : 한 열의 값이 모두 다른것을 보장한다.
- PRIMARY KEY : NOT NULL과 UNIQUE의 조합, 테이블의 각 행을 고유하게 식별할 수 있다.
- FOREIGN KEY : 다른 테이블의 행을 고유하게 식별하는 값
- CHECK : 한 열의 모든값이 특정 조건을 만족하는지 확인한다.
- DEFAULT : 값이 지정되지 않는 경우 열의 기본값을 설정한다.
- INDEX : 데이터베이스에서 매우 신속하게 데이터를 작성하고 검색하는데 사용된다.


### SQL CREATE Constraints
`Create Table, Alter Table`시 제한 조건을 지정할 수 있다.
```sql
CREATE TABLE <table_name>(
	<column1> datatype contraint,
	<column2> datatype contraint,
	<column3> datatype contraint,
	...
);
```

