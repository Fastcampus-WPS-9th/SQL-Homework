# SQL Primary KEY Constraint

`Primary Key` 제약조건은 데이터베이스 테이블의 각 레코드를 고유하게 식별한다.
기본키는 UNIQUE해야하며 NULL을 포함할 수 없다.

### Primary KEY Example

```sql
# CREATE
CREAT TABLE Persons (
	ID int NOT NULL PRIMARY KEY,
	LastName varchar(255) NOT NULL,
	FirstName varchar(255),
	age int
);

# Naming 가능
CREAT TABLE Persons (
	ID int NOT NULL,
	LastName varchar(255) NOT NULL,
	FirstName varchar(255),
	age int,
	CONSTRAINT PK_Person PRIMARY KEY (ID, LastName)
);
# Primary KEY는 테이블에서 오직 하나만 있어야한다.
# 만약 이렇게 적어준 경우, 두개가 합쳐서 Primary Key가 된다.
# 즉, ID값은 중복될 수 있지만 ID와 LastName 각각 둘다 중복될 수는 없다는 뜻이다.

# ALTER
ALTER TABLE Persons
ADD PRIMARY KEY (ID);

# Naming
ALTER TABLE Perons
ADD CONSTRAINT PK_Person PRIMARY KEY (ID, LastName);

# DROP
ALTER TABLE Persons
DROP CONSTRAINT PK_Person;
```


