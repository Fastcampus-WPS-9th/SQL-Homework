# SQL NOT NULL Constraint

기본적으로 열은 NULL 값을 포함할 수 있다.
`NOT NULL`제약조건은 열이 `NULL`값을 허용하지 않도록 강제한다.

### NOT NULL Example

"ID", "LastName", "FirstName"열이 NULL을 허용하지 않도록 한다.

```sql
CREATE TABLE Persons (
	ID int NOT NULL,
	LastName varchar(255) NOT NULL,
	FirstName varchar(255) NOT NULL,
	Age int
);
```
