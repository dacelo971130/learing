# Stream

## 概述

## 範例

題目: 查詢未成年作家的評分在70以上的書籍，但作家和書籍可能出現重複，需要進行篩選

銜接上篇 [lambda](../java/lambda.md) 未簡化之寫法

```
getAuthors()
                .stream() // 把集合轉成流
                .distinct() // 去除重複
                .filter(author -> author.getAge() < 18)
                .forEach(new Consumer<Author>() {
                    @Override
                    public void accept(Author author) {
                        System.out.println(author);
                    }
                });
```
