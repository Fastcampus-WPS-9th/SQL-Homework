# SQL UNIQUE Constraint

`UNIQUE`제약조건은 열의 모든 값이 서로 다른것을 보장한다.

### UNIQUE Constraint Example
```sql
# CREATE
CREATE TABLE Persons (
	ID int NOT NULL UNIQUE,
	LastName varchar(255) NOT NULL,
	FirstName varchar(255),
	Age int
);

# Unique 제약조건에 이름을 지정하고 여러 열에 정의할 수 있다.
CREATE TABLE Persons(
	ID int NOT NULL,
	LastName varchar(255)
	FirstName varchar(255)
	Age int,
	CONSTRAINT UC_Person UNIQUE (ID, LastName)
)

# ALTER
ALTER TABLE Persons
ADD UNIQUE (ID);

# 제약조건에 이름을 지정
ALTER TABLE Persons
ADD CONSTRAINT UC_Person UNIQUE (ID, LastName);

# DROP
ALTER TABLE Persons
DROP CONSTRAINT UC_Person;
```
