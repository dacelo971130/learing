# SQL 達人的工作現場攻略筆記 - (1) - CASE 陳述句的用法

撰寫 SQL 條件分歧的重要技術，近似於 Java 的 switch - case，有諸多優點也有增加複雜度的缺點，是一把雙面刃。

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

在 ORACLE 中為 `DECODE` 但他仍劣於 CASE 有大概以下四點

1. 為官方方言
2. 分歧條件上限 127 (可能隨版本上調  )
