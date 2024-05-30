# Lambda

## 為什麼使用 lambda?

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
(參數) -> {代碼}
```
