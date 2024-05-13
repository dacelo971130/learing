# 什麼是 NoSQL

什麼是 NoSQL 全名是 Not Only SQL，又稱非關聯式資料庫

## 特色

* 資料之間是無關係的，關聯式資料庫有主外鍵約束，而 NoSQL 弱化這種觀念

* 資料的結構是鬆散的、可變的

  * 在關聯式資料庫中，如果表有 5 個列，那麼最多只能儲存 5 個列的值

   * 在 NoSQL 中沒有所謂的固定列數，甚至連列都沒有，所以，儲存型態的類型、資料的多少都是可變、不固定的

## 常見 SQL/NoSQL

* RDBMS(關聯式資料庫)泛指
 
  * 傳統型資料庫 - `PostgreSQL`、`Oracle`、`MySQL`、`MS SQL Server`、`DB2`
 
  * 雲端資料庫 - `Amazon RDS`、`Google Cloud SQL`、`Microsoft Azure SQL Database` 

* NoSQL - `Redis`、`MongoDB`、`Cassandra`、`Neo4j`、`Riak`、`Couchbase`、`Elasticsearch`、`Kafka`

## NoSQL 為什麼使用/什麼時候使用 

* 處理 RDBMS 無法處理的問題

* 應用程式開發的生產力

* 大規模的資料量
 
## NoSQL 的優勢

* 面對巨量資料時依然保持良好性能，尤其是**讀寫性能**，得益於它的非關係性和結構簡單

* 靈活的資料格式，使用 NoSQL 不必創建列

* 高可用性、高擴展性，具有**主從複製**、**支援叢集**等特點

## NoSQL 的劣勢

* 資料間是無關係的

* 沒有豐富的資料類型 

* 不支援標準 `SQL`，沒有公認的 NoSQL 標準

* 沒有 `RDBMS` 的約束，如主鍵約束、主外鍵約束和值範圍約束等，大多數也沒有索引的概念

* 沒有交易復原概念，優先考慮性能、擴展性，因此大部分 NoSQL 不能完全實現 `ACID`，少部分則提供支援，像是如 `Couchbase` 和 `MongoDB` 的某些部分

##  NoSQL 種類

* `Key-Value DataBase`

  * 特性 - 採用 `Key-Value` 資料架構建立分散式的資料庫，具有水平擴充性，能按需求增加資料庫

  * 用途 - 儲存社群網或社交遊戲產生的 `TB` 或 `PB` 等級資料

  * 產品 -  `Google BigTable`、`Hadoop HBase`、`Amazon Dynamo`、`Apache Cassandra`、`Hypertable`

* `Document Database`

  * 特性 - 可儲存結構鬆散或非結構性的資料

  * 用途 - 適合用來儲存網頁料或 `XML`、JSON 格式的文件，也可以儲存圖片或影片資料

  * 產品 -  `CouchDB`、`MongoDB`、`Riak`

* `In-memory DataBase`

  * 特性 - 利用記憶體建立分散式資料庫，增加 `cache` 讀取資料速度

  * 用途 - 網站快取

  * 產品 - `Redis`、`Memcached`

* `Graph Database`

  * 特性 - 運用圖學架構來儲存節點間關係資料庫，基本的資料結構包刮節點、關係和屬性

  * 用途 - 樹狀結構紀錄社交網站的朋友關係，儲存地圖上每一點和鄰近點的關係，可以計算點與點之間最短距離

  * 產品 - `Neo4j`、`InfoGrid`、`AllegroGrph`

## 參考

[什麼是 NoSQL？](https://aws.amazon.com/tw/nosql/)

[快速認識4類主流NoSQL資料庫](https://www.ithome.com.tw/news/92507)

[NoSQL Databases: What Every Data Scientist Needs to Know](https://www.datacamp.com/blog/nosql-databases-what-every-data-scientist-needs-to-know)
