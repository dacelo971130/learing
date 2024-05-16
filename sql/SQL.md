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
