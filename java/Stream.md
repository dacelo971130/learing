# Stream

## 概述

## 範例

題目: 查詢未成年作家的評分在70以上的書籍，但作家和書籍可能出現重複，需要進行篩選

銜接上篇 [lambda](../java/lambda.md) ，我們先複習一下未簡化之寫法

```
getAuthors()
                .stream() // 把集合轉成流
                .distinct() // 去除重複
                .filter(author -> author.getAge() < 18) // 過濾 author 年齡小於 18
                .forEach(new Consumer<Author>() { // 迭代所有 author.toString 查看流裡面的 author 內容
                    @Override
                    public void accept(Author author) {
                        System.out.println(author);
                    }
                });
```

再看看簡化後

```
getAuthors()
                .stream()
                .distinct()
                .filter(author -> author.getAge() < 18)
                .forEach(author -> System.out.println(author)); // 可省略成 .forEach(System.out::println);
```

## 創建 Stream 流

### List: `集合對象.stream()`創建

```
List<Author> authors = getAuthors();
Stream<Author> stream = authors.stream();
```

### Arrays: `Arrays.stream(陣列)`或者使用`Stream.of();`創建

```
Integer[] arr = {1,2,3,4,5};
Stream<Integer> stream1 = Arrays.stream(arr);
Stream<Integer> stream2 = Stream.of(arr);
```

### Map: 轉換成

```
Map<String, Integer> map = new HashMap<>();
        map.put("a", 19);
        map.put("b", 20);
        map.put("c", 21);

Stream<Map.Entry<String, Integer>> stream3 = map.entrySet().stream();
```

## Filter()

## Peek()

## distinct()

## foreach()

## sorted()

## limit()

## skip()

## flatMap()

## count()

## min() & max()

## collect()

## anyMatch()

## allMatch()

## findAny()

## findFrist()

## reduce()
