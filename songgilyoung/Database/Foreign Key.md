# SQL Foreign KEY Constraint

`Foreign KEY`는 두 테이블을 서로 연결하는 데 사용되는 키이다.

### Foreign KEY Example

```sql
CREATE TABLE Orders (
	OrderID int NOT NULL PRIMARY KEY,
	OrderNumber int NOT NULL,
	PersonID int FOREIGN KEY REFERENCES Persons(PersonID)
);

# naming, multiple
CREATE TABLE Orders(
	OrderID int NOT NULL PRIMARY KEY,
	OrderNumber int NOT NULL,
	PersonID int,
	PRIMARY KEY (OrderID),
	CONSTRAINT FK_PersonOrder FOREIGN KEY (PersonID)
	REFERENCES Persons(PersonID)
);

# ALTER
ALTER TABLE Orders
ADD FOREIGN KEY (PersonID) REFERENCES Persons(PersonID);

ALTER TABLE Orders
ADD CONTRAINT FK_PersonOrder
FOREIGN KEY (PersonID) REFERENCES Persons(PersionID);

# DROP
ALTER TABLE Orders
DROP CONSTRAINT FK_PersonOrder;
```
