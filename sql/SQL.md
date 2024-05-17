## 基本型態

* 4515

## 基本語法

### 常用語法

* `SELECT` - extracts data from a database
* `UPDATE` - updates data in a database
* `DELETE` - deletes data from a database
* `INSERT INTO` - inserts new data into a database
* `CREATE DATABASE` - creates a new database
* `ALTER DATABASE` - modifies a database
* `CREATE TABLE` - creates a new table
* `ALTER TABLE` - modifies a table
* `DROP TABLE` - deletes a table
* `CREATE INDEX` - creates an index (search key)
* `DROP INDEX` - deletes an index

### 

語法 :
```
SELECT column1, column2, ...FROM table_name;
```

範例 :
```
SELECT CustomerName, City FROM Customers;
```

### SELECT

語法 :
```
SELECT column1, column2, ...FROM table_name;
```

範例 :
```
SELECT CustomerName, City FROM Customers;
```

### SELECT DISTINCT

語法 :
```
SELECT DISTINCT column1, column2, ...FROM table_name;
```

範例 :
```
SELECT DISTINCT Country FROM Customers;
```

說明: `DISTINCT` 會對後方 `column1` 做篩選，只取出 Table 中 `column1` 不重複的部分。

### WHERE

語法 :
```
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

範例 :
```
SELECT * FROM Customers WHERE Country='Mexico';

SELECT * FROM Customers WHERE CustomerID=1;

SELECT * FROM Customers WHERE CustomerID > 80;

SELECT * FROM Products WHERE Price BETWEEN 50 AND 60;

SELECT * FROM Customers WHERE City LIKE 's%';

SELECT * FROM Customers WHERE City IN ('Paris','London');
```

其他相關:
| 運算符  | 說明 |
| ------------- | ------------- |
| =  | 等於  |
| >  | 大於  |
| <  | 小於 |
| >= | 大於等於  |
| <= | 小於等於  |
| <> | 不等於，有些版本為 !=  |
| BETWEEN  | 某數到某數之間 |
| LIKE  | regex 的用法  |
| IN  | 包含在某個列表內  |

### ORDER

語法 :
```
SELECT column1, column2, ...
FROM table_name
ORDER BY column1, column2, ... ASC|DESC;
```

範例 :
```
SELECT * FROM Products ORDER BY Price;
```

說明: `DISTINCT` 會對後方 `column1` 做篩選，只取出 Table 中 `column1` 不重複的部分。

### 創建 Database

```
create database `sql_tutorial`;
```

### 查詢所有 Database

```
show databases;
```

### 刪除 Database

```
drop database `sql_tutorial`;
```

## 什麼是 Foreign key

已下列表格為例

Employee

| *emp_id  | name | birth_date | sex | salary | *branch_id |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
| 206 | 小王 | 1999/10/07 | M | 50000 | 1 |
| 207 | 小倩 | 1999/10/08 | F | 40000 | 2 |
| 208 | 小名 | 1999/10/09 | M | 30000 | 3 |
| 209 | 小夫 | 1999/10/10 | M | 20000 | 4 |

其中 `emp_id` 為此 Table 主鍵(PK)，`branch_id` 則為外鍵(FK)

Branch

| *branch_id | branch_name |
| ------------- | ------------- |
| 1 | 研發 |
| 2 | 行政 |
| 3 | 人資 |
| 4 | 業務 |

那會有這樣這一個 `branch_id` 屬性的設立，原因是我在 Employee 我想知道每個部門是哪一個部門的!所以，新增了 `branch_id(外鍵，外鍵必定為另一張 table Branch 的 PK)

![image](https://github.com/dacelo971130/learing/assets/83411220/7d670845-0eb2-4f33-b2bf-4c67e674d162)


### 問題 - 直接在 employee 設定部門不就好了
