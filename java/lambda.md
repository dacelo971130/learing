# 為什麼使用 lambda?

* 避免過多的 if-else
* 增加可讀性
* 提升在大量資料下的集合處理效率

## 使用前後差別

題目: 查詢未成年作家的評分在70以上的書籍，但作家和書籍可能出現重複，需要進行篩選

* Normal
```
List<Book> bookList = new ArrayList<>();
        Set<Book> uniqueBookValues = new HashSet<>();
        Set<Author> uniqueAuthorValues = new HashSet<>();
        for (Author author : authors) {
            if (uniqueAuthorValues.add(author)) {
                if (author.getAge() < 18) {
                    List<Book> books = author.getBooks();
                    for (Book book : books) {
                        if (book.getScore() > 70) {
                            if (uniqueBookValues.add(book)) {
                                bookList.add(book);
                            }
                        }
                    }
                }
            }
            System.out.println(bookList);
        }
```

* Lambda

```
List<Book> collect = authors.stream()
                .distinct()
                .filter(author -> author.getAge() < 18)
                .map(author -> author.getBooks())
                .flatMap(Collection::stream)
                .filter(book -> book.getScore() > 70)
                .distinct()
                .collect(Collectors.toList());
        System.out.println(collect);
```

## 格式

```
(parameters) -> {statements;}

(參數) -> {代碼}
```

## 範例一

重點1 : 只關心參數或要做的事情，lambda 不關心類別、方法名

重點2 : 簡化的條件，匿名內部類是接口，且只有一個抽象方法需要重寫，就可以進行簡化

啟動執行緒時，使用內部匿名類別

```
new Thread(new Runnable() {
            @Override
            public void run() {
                System.out.println("hello lambda");
            }
        }).start();
```

使用 lambda 簡化匿名類別

```
new Thread(() -> System.out.println("hello lambda")).start();
```

## 範例二

首先我們先看下面這段 code

```
import java.util.function.IntBinaryOperator;

public static int calculateNum(IntBinaryOperator operator) {
        int a = 10;
        int b = 20;
        return operator.applyAsInt(a, b);
    }
```

`calculateNum`方法的參數`IntBinaryOperator`是一個 `@FunctionalInterface`並且只有一個抽象方法，符合 lambda 簡化條件

`IntBinaryOperator.java`

```
package java.util.function;

@FunctionalInterface
public interface IntBinaryOperator {
    int applyAsInt(int var1, int var2);
}
```

接下來我們來呼叫`calculateNum`這個方法，並嘗試簡化他

```
int i = calculateNum(new IntBinaryOperator() {
            @Override
            public int applyAsInt(int left, int right) {
                return left + right;
            }
        });

// 簡化後
int i = calculateNum((left, right) -> left + right);

// 再簡化，這裡 :: 使用的是引用
int i = calculateNum(Integer::sum);
```

## 範例三

同上題範例，再來一次

```
import java.util.function.IntBinaryOperator;

public static void printNum(IntPredicate predicate) {
        int[] arr = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
        for (int i : arr) {
            if (predicate.test(i)) {
                System.out.println(i);
            }
        }
    }
```

`IntPredicate.java`

```
import java.util.Objects;

@FunctionalInterface
public interface IntPredicate {
    boolean test(int var1);

    default IntPredicate and(IntPredicate other) {
        Objects.requireNonNull(other);
        return (value) -> {
            return this.test(value) && other.test(value);
        };
    }

    default IntPredicate negate() {
        return (value) -> {
            return !this.test(value);
        };
    }

    default IntPredicate or(IntPredicate other) {
        Objects.requireNonNull(other);
        return (value) -> {
            return this.test(value) || other.test(value);
        };
    }
}
```

重點是練習寫出雛形，並成功簡化，`value%2 == 0` 可以是任何公式

```
printNum(new IntPredicate() {
            @Override
            public boolean test(int value) {
                return value % 2 == 0;
            }
        });
        
printNum((int value)->{
            return value % 2 == 0;
        });

printNum(value -> value % 2 == 0);
```

## 範例四

方法

```
import java.util.function.Function;

public static <R> R typeConver(Function<String, R> function) {
        String str = "12345";
        R result = function.apply(str);
        return result;
    }
```

簡化

```
Integer i = typeConver(new Function<String, Integer>() {
            @Override
            public Integer apply(String s) {
                return Integer.valueOf(s);
            }
        });

Integer i1 = typeConver((String s) -> {
            return Integer.valueOf(s);
        });

Integer i2 = typeConver(Integer::valueOf);
```

## 範例五

方法

```
import java.util.function.IntConsumer;

public static void foreachArr(IntConsumer consumer) {
        int[] arr = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
        for (int i : arr) {
            consumer.accept(i);
        }
    }
```

簡化

```
foreachArr(new IntConsumer() {
            @Override
            public void accept(int i) {
                System.out.println(i);
            }
        });

foreachArr((int i)->{
            System.out.println(i);
        });

foreachArr(System.out::println);
```
