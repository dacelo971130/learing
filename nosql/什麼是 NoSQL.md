# 什麼是 NoSQL

什麼是 `NoSQL` 全名是 Not Only SQL，又稱非關聯式資料庫

## 兩個主要特點

* 資料之間是無關係的，關聯式資料庫有主外鍵約束，而 `NoSQL` 弱化這種觀念

* 資料的結構是鬆散的、可變的

  * 在關聯式資料庫中，如果表有 5 個列，那麼最多只能儲存 5 個列的值

   * 在 `NoSQL` 中沒有所謂的固定列數，甚至連列都沒有，所以，儲存型態的類型、資料的多少都是可變、不固定的

* `RDBMS`(關聯式資料庫)泛指傳統型資料庫，包括 `PostgreSQL`、`Oracle`、`MySQL`、`MS SQL Server`、`DB2`等，也包括雲端資料庫的 `Amazon RDS`、`Google Cloud SQL`、`Microsoft Azure SQL Database` 

* `NoSQL` 指的是 `Redis`、`MongoDB`、`Cassandra`、`Neo4j`、`Riak`、`Couchbase`、`Elasticsearch`、`Apache Kafka`等

## NoSQL 為什麼使用/什麼時候使用 

* 處理 RDBMS 無法處理的問題

* 應用程式開發的生產力

* 大規模的資料量
 
## NoSQL 的優勢

* 面對巨量資料時依然保持良好性能，尤其是**讀寫性能**，得益於它的非關係性和結構簡單

* 靈活的資料格式，使用 `NoSQL` 不必創建列

* 高可用性、高擴展性，具有**主從複製**、**支援叢集**等特點

## NoSQL 的劣勢

* 資料間是無關係的

* 沒有豐富的資料類型 

* 不支援標準 `SQL`，沒有公認的 `NoSQL` 標準

* 沒有 `RDBMS` 的約束，如主鍵約束、主外鍵約束和值範圍約束等，大多數也沒有索引的概念

* 沒有交易復原概念，優先考慮性能、擴展性，因此大部分 `NoSQL` 不能完全實現 `ACID`，少部分則提供支援，像是如 `Couchbase` 和 `MongoDB` 的某些部分

##  NoSQL 種類

* `Key-Value DataBase`

  * 特性 - 採用 `Key-Value` 資料架構建立分散式的資料庫，具有水平擴充性，能按需求增加資料庫

  * 用途 - 儲存社群網或社交遊戲產生的 `TB` 或 `PB` 等級資料

  * 產品 -  `Google BigTable`、`Hadoop HBase`、`Amazon Dynamo`、`Apache Cassandra`、`Hypertable`

* `Document Database`

  * 特性 - 採用 `Key-Value` 資料架構建立分散式的資料庫，具有水平擴充性，能按需求增加資料庫

  * 用途 - 儲存社群網或社交遊戲產生的 `TB` 或 `PB` 等級資料

  * 產品 -  `Google BigTable`、`Hadoop HBase`、`Amazon Dynamo`、`Apache Cassandra`、`Hypertable`

* `Column-Family Database`

  * 特性 - 採用 `Key-Value` 資料架構建立分散式的資料庫，具有水平擴充性，能按需求增加資料庫

  * 用途 - 儲存社群網或社交遊戲產生的 `TB` 或 `PB` 等級資料

  * 產品 -  `Google BigTable`、`Hadoop HBase`、`Amazon Dynamo`、`Apache Cassandra`、`Hypertable`

* `Graph Database`

  * 特性 - 採用 `Key-Value` 資料架構建立分散式的資料庫，具有水平擴充性，能按需求增加資料庫

  * 用途 - 儲存社群網或社交遊戲產生的 `TB` 或 `PB` 等級資料

  * 產品 -  `Google BigTable`、`Hadoop HBase`、`Amazon Dynamo`、`Apache Cassandra`、`Hypertable`
