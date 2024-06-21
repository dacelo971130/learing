# Gradle Java 專案版本無法切換

## 問題

new 新專案 `build` 失敗，顯示指定 JDK 17，但 JVM 要求 JDK 8

***
Could not resolve org.springframework.boot:spring-boot-gradle-plugin:3.3.1. 
Required by: project : > org.springframework.boot:org.springframework.boot.gradle.plugin:3.3.1 > 
Dependency requires at least JVM runtime version 17. This build uses a Java 8 JVM.
***

## 嘗試方式

已確認事項

1. `JAVA_HOME` 設置 RedHat 17 完畢，且 cmd -> `java -version` 正常。(無效)

2. gradle.properties 裡面的 `JAVA_HOME`、`classpath` 指向確認正常。(無效)

3. 清除 cache 後重啟。(無效)

4. 刪除 `C:/USER/gradle`，重載 gradle。(無效)

5. 刪除 .m2 重載依賴。(不太可能沒嘗試)

6. Setting -> Build, Execution, Deployment -> Gradle，gradle -> intellij。(無效)

7. Project Structure -> 設置 Project 裡面的 SDKs。(無效)

8. Project Structure -> Modules -> Dependencies -> Modules SDKs Setting。(無效)

9. Project Structure -> SDKs 刪除其他版本 JDK。(無效)

## 結果

關閉 idea，至專案資料夾下刪除 .idea Floder，開啟專案讓它重載。(成功)

## 如何想到刪除 .idea ?

我也不知道，猜的，浪費我一小時

## 原始推測原因

1. 使用 oracle .exe 安裝 JDK 時候有吃到它的新設定

2. IDEA Setting 未設置或設定不佳

3. `Java_HOME` 未設置或設定不佳

4. build.gradle 未設置或設定不佳

5. Cache 或 .m2 髒掉
