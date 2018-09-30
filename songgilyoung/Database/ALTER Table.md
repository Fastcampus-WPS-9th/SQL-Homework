# SQL ALTER TABLE Statement

### ALTER TABLE ADD Column
```sql
ALTER TABLE <table_name>
ADD <column_name> <datatype>;
```

### ALTER TABLE DROP Column
```sql
ALTER TABLE <table_name>
DROP COLUMN <column_name>;
```

### ALTER TABLE ALTER/MODIFY Column
```sql
# SQL Server / MS Access
ALTER TABLE <table_name>
ALTER COLUMN <column_name> <datatype>;

# MySQL / Oracle(prior version 10G)
ALTER TABLE <table_name>
MODIFY COLUMN <column_name> <datatype>;

# Oracle 10G later
ALTER TABLE <table_name>
MODIFY <column_name> <datatype>;
```
