# SQL DEFAULT Constraint

열의 기본값을 제공하는데 사용한다. 다른값을 지정하지 않으면 기본값이 모든새 레코드에 추가된다.

### DEFAULT Constraint Example

```sql
CREATE  TABLE Persons (  
	ID int NOT  NULL,  
	LastName varchar(255) NOT  NULL,  
	FirstName varchar(255),  
	Age int,  
	City varchar(255) DEFAULT  'Sandnes'  
);

# 함수를 사용하여 시스템 값을 넣을 수 있다.
CREATE  TABLE Orders (  
	ID int NOT  NULL,  
	OrderNumber int NOT  NULL,  
	OrderDate date DEFAULT GETDATE()  
);

# ALTER
ALTER  TABLE Persons  
ALTER  COLUMN City SET  DEFAULT  'Sandnes';

# DROP
ALTER  TABLE Persons  
ALTER  COLUMN City DROP  DEFAULT;

```
