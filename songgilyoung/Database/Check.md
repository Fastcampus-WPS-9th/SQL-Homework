# SQL CHECK Constraint

열에 배치할 수 있는 값 범위를 제한하느데 사용한다.

### CHECK Constraint Example

```sql
CREATE TABLE Persons(
	ID int NOT NULL,
	LastName varchar(255) NOT NULL,
	FirstName varchar(255),
	Age int CHECK (Age >= 18)
);

# Naming, Multiple
CREATE TABLE Persons(
	ID int NOT NULL,
	LastName varchar(255) NOT NULL,
	FirstName varchar(255),
	Age int,
	City varchar(255),
	CONSTRAINT CHK_Person CHECK (Age>=18 AND City='Sandnes')
);

# ALTER
ALTER  TABLE Persons  
ADD  CHECK (Age>=18);

ALTER  TABLE Persons  
ADD  CONSTRAINT CHK_PersonAge CHECK (Age>=18  AND City='Sandnes');

#DROP
ALTER  TABLE Persons  
DROP  CONSTRAINT CHK_PersonAge;
```
