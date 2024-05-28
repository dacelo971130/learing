# Lambda

語法結構

```
(parameters) -> expression

(parameters) -> {statements;}
```

跟 groovy 一樣 expression 調用

```
MathOperation addition = (a, b) -> a + b;
```

MathOperation 是一個 interface，他有一個 operation abstract method，labmbda 實現了這個方法，表示 (a, b) -> a + b;
```
int result = addition.operation(5, 3);
System.out.println("5 + 3 = " + result);
```

搭配集合操作
```
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
names.forEach(name -> System.out.println(name));
```
