# SQL CREATE TABLE Statement

## CREATE TABLE Example

```sql
CREATE TABLE Persons {
	PersonID int,
	LastName varchar(255),
	FirstName varchar(255),
	Address varchar(255),
	City varchar(255),
};
```

### CREATE TABLE Using Another Table

다른 테이블을 복사하여 가져오게되면 값들 또한 모두 가져오게된다.

```sql
# copy all columns
CREATE TABLE suppliers AS
( SELECT * FROM companies )

# Copy Select columns
CREATE TABLE suppliers AS
( SELECT * FROM companies
	WHERE id > 1000 );

## Copy Selected Columns from multiple tables
CREATE TABLE suppliers AS
( SELECT companies.id, companies.address, cat_type
	FROM companies, categories
	WHERE companies.id = categories.id
	AND companies.id > 1000 )

## Copy table without Values
CREATE TABLE suppliers AS
( SELECT * FROM companies WHERE 1=2 );
```
