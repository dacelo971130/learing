# 如何使用 SQLServer Windows登入驗證並創建資料庫

## 起始畫面

<img width="271" alt="image" src="https://github.com/dacelo971130/learing/assets/83411220/ff823997-938f-4744-8a15-924116bfaa8b">

## 設置伺服器

流程1: 伺服器名稱 -> 瀏覽其他 -> 資料庫引擎 -> 找到自己的電腦名稱

`CASPER_INFOT(你的電腦名稱)` 是我們的目標，但預設應該是不會有

<img width="250" alt="image" src="https://github.com/dacelo971130/learing/assets/83411220/79b3ac33-eaa0-4dad-89a3-f09621d386e7">

<img width="198" alt="image" src="https://github.com/dacelo971130/learing/assets/83411220/3a4c01b1-e49e-44fa-ac96-125afd07cca7">

流程2: 驗證 -> Windows 驗證

## 連線安全性

流程3: 勾選信任伺服器憑證，並將加密改成強制

<img width="224" alt="image" src="https://github.com/dacelo971130/learing/assets/83411220/de3ee970-dd42-4565-b62d-9ee1e2ce99e5">

## 如何設定 Spring boot SQL Server 2022 config(Windows登入)

application.properties
```
spring.datasource.url=jdbc:sqlserver://localhost:1433;databaseName=TSR;integratedSecurity=true;
spring.datasource.driver-class-name=com.microsoft.sqlserver.jdbc.SQLServerDriver
spring.jpa.database-platform=org.hibernate.dialect.SQLServerDialect
spring.jpa.hibernate.ddl-auto=none
```

## 參考

[SQL Server 快速上手 (3) - 建立你的第一個關聯式資料庫](https://devbricker.github.io/post/database/sql-server/sqlserverbasic3/)
