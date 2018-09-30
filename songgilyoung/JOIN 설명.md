![SQL JOINS](http://rapapa.net/wp/wp-content/uploads/2012/06/Visual_SQL_JOINS_V2.png)

`line`, `player` 테이블로 조인.

```sql
> select * from line;
```
| lname | time | pid |
|--|--|--|
| TOP | 03:00 | 1 |
| MID | 01:00 | 2 |
| BOTTOM | 01:30 | 3 |
| Jungle | 00:00 | 4 |

```sql
> select * from player;
```
| pid | spid | player |
|--|--|--|
| 1 | 1 | Smeb |
| 3 | 2 | Uzi |
| 3 | 3 | Bang |
| 3 | 4 | Pray |
| 4 | 5 | Karsa |

## 일반적 조인

`pid`가 같은 것 끼리 일반적인 조인을 하면 결과는 다음과 같다.
```sql
> select lname, player
>> from line
>> join player on player.pid=line.pid;
```
| lname | player |
|--|--|
| TOP | Smeb |
| Bottom | Uzi |
| Bottom | Bang |
| Bottom | Pray |
| Jungle | Karsa |

`PID`가 같은 것이 있는것만 가져오게된다.

## Left Join

```sql
> select lname, player
>> from line
>> join player on line.pid=player.pid
```

| lname | player |
|--|--|
| TOP | Smeb |
| **==MID==** | **==NULL==** | 
| BOTTOM | Uzi |
| BOTTOM | Bang |
| BOTTOM | Pray |
| Jungle | Karsa |

`LEFT JOIN`은 왼쪽 테이블을 기준으로 ==반드시 한줄 이상 나오는 보장==을 받게된다.
또한 왼쪽 테이블에 해당하는 오른쪽 테이블의 중복 PID를 가질경우 여러줄이 나오게된다.
`RIGHT JOIN`은 반대겠지?
