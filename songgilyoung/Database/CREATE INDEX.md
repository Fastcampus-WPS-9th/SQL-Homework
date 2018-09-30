# SQL CREATE INDEX Statement

테이블에 인덱스를 만들 때 사용된다.
사용자는 색인을 볼 수 없으며 검색과  쿼리 속도를 높이기위해 사용됨.

### CREATE INDEX Example
```sql
CREATE INDEX idx_lastname
ON Persons (LastName);

# 조합 색인도 가능하다.
CREATE INDEX idx_pname
ON Persons (LastName, FirstName);

# DROP, 테이블마다 다르네..
DROP INDEX
```
