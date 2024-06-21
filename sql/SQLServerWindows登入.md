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

使用 `integratedSecurity=true;` 就可以不必對 username、password 進行設置，對簡單 demo 專案來說很方便

application.properties
```
spring.datasource.url=jdbc:sqlserver://localhost:1433;databaseName=TSR;integratedSecurity=true;
spring.datasource.driver-class-name=com.microsoft.sqlserver.jdbc.SQLServerDriver
spring.jpa.database-platform=org.hibernate.dialect.SQLServerDialect
spring.jpa.hibernate.ddl-auto=none
```

## 連線問題 - TCP/IP 未啟動

連線時遇到
```
[08S01] 連接到主機 localhost (連接埠 1433) 的 TCP/IP 連接已經失敗。錯誤: "Connection refused: getsockopt。
確認連接屬性。確認 SQL Server 執行個體是否在主機上執行並接受在通訊埠的 TCP/IP 連接。
確認防火牆未封鎖通訊埠的 TCP 連接。"。.
```

1. 搜尋 - SQL Server 20xx 設定管理員

2. 找到 SQL Server 網路組太 -> MSSQLSERVER 的通訊協定 -> 點兩下 -> TCP/IP 右鍵 -> 啟用
<img width="485" alt="image" src="https://github.com/dacelo971130/learing/assets/83411220/ce148767-c806-496f-a3fb-62505fc92c5c">

3. 到上方點選 SQL SERVER 服務，點選 SQL SERVER(MSSQLSERVE) 右鍵 -> 重啟

<img width="581" alt="image" src="https://github.com/dacelo971130/learing/assets/83411220/4a40db13-6e8d-43a2-adba-a9d2c9868847">

## 新增 SQL SERVER 使用者

流程: 安全性 -> 登入 -> 右鍵，新增使用者 -> 選擇 SQL Server 驗證 -> 輸入 username/password，確認 -> 可以改成 user 登入

<img width="127" alt="image" src="https://github.com/dacelo971130/learing/assets/83411220/653e6190-2bbf-4705-a6d6-7b447c39aa23">

## 參考

[SQL Server 快速上手 (3) - 建立你的第一個關聯式資料庫](https://devbricker.github.io/post/database/sql-server/sqlserverbasic3/)

[連線問題 - TCP/IP 未啟動](https://medium.com/@nick841005/java-%E4%BD%BF%E7%94%A8jdbc%E5%A0%B1%E9%8C%AF-5383fbe676ed)
