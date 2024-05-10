# Lombok 常用註解

## val / var 

類似 Groovy 的 `def`，Java 17 也有支援，通常建議使用原生或 Groovy & Kotlin 較好

## @NonNull

檢查 `Null` 用的，已有許多取代方式

## @Cleanup

關閉資源用的，我更喜歡 `try-catch` 包在裡面，自動關閉的寫法

## @Getter / Setter

自動建立所有屬性的 `getXXX()`、`setXXX()`，用於 Class 上，IDEA 右鍵本身也產快速產製

```

```

## @Getter(lazy=true)

ummm...

## @ToString

打印物件用的，用於 Class 上

```
@ToString
public class A{}
```

## @EqualsAndHashCode

坑爹小鞭炮，用於 Class 上，產製 `equals()` & `hashcode()`

## @NoArgsConstructor, @RequiredArgsConstructor and @AllArgsConstructor

常見常用，ummm...

## @Data

坑爹大禮包，融合了 `@Getter`、`@Setter`、`@ToString`、`@EqualsAndHashCode` and `@RequiredArgsConstructor` 

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

## 參考

[官方 Doc](https://projectlombok.org/features/)
