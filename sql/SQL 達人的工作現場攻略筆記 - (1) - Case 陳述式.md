# SQL 達人的工作現場攻略筆記 - (1) - CASE 陳述句的用法

撰寫 SQL 條件分歧的重要技術，近似於 Java 的 switch - case

```
-- 單純 CASE 陳述句
CASE SEX
  WHEN '1' THEN '男'
  WHEN '2' THEN '女'
ELSE '其他' END

-- 搜尋 CASE 陳述句
CASE WHEN SEX = '1' THEN '男'
     WHEN SEX = '2' THEN '女'
ELSE '其他' END
```
