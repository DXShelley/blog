---
title: oracle基本使用
tags:
  - db
  - oracle
  - syntax
  - base
categories:
  - programming
  - db
date: 2022-01-11 09:20:28
---

#oracle 基本使用



## 技巧

### 联表更新

```sql
-- -- 方法1
UPDATE T2
   SET T2.C =
       (SELECT B FROM T1 WHERE T1.A = T2.A)
 WHERE EXISTS (SELECT 1 FROM T1 WHERE T1.A = T2.A)
-- -- 方法2
update student A  
set (A.name,a.dq) =  
(select B.bname,b.bdq  
from newstudent B  
where B.Bid = A.id  
and A.dq = 10 
)  
where exists (select 1  
from newstudent B  
where B.Bid = A.id  
and A.dq = 10 
);  
-- -- 方法3
MERGE INTO T2
USING T1
ON (T2.A = T1.A)
WHEN MATCHED THEN
  UPDATE SET T2.C = T1.B
```

