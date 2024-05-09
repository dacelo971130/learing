# Lombok 常用註解

[Doc](https://projectlombok.org/features/)

## val / var 

不常見不常用，我通常會直接用 Groovy & Kotlin 內建的關鍵字

## @NonNull

常見常用，檢查 `Null` 用的

## @Cleanup

常見不常用，關閉資源用的，我更喜歡 `try-catch` 包在裡面，自動關閉的寫法

## @Getter / Setter

自動建立所有屬性的 `getXXX()`、`setXXX()`，這就是你用它最大的理由，

當然現在 IDEA 右鍵 Gen 也能產出來，但屬性夠多的時候，光找到要改的屬性就眼花了，還是需要它

## ToString

常見常用，打印類別所有屬性

## @EqualsAndHashCode

ummm...

## @NoArgsConstructor, @RequiredArgsConstructor and @AllArgsConstructor

常見常用，ummm...

## @Data

常見大禮包融合了 `@Getter`、`@Setter`、`@ToString`、`@EqualsAndHashCode` and `@RequiredArgsConstructor` 

但你最好別用它，理由請看這篇 [什麼? @Data 可能要繳稅](./Lombok@Data坑.md)

## @Slf4j

常見常用，打 log 用

範例

```
log.info("123")
```

## @Value

ummm...

## @Builder

ummm...

## @SneakyThrows

ummm...

## @Synchronized

ummm...

## @Locked

ummm...

## @With

ummm...

## @Getter(lazy=true)

ummm...
