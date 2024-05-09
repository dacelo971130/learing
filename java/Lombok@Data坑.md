# 關於 Lombok @Data 的 equals & hashCode 稅費

使用 Lombok 時，有些需要注意的地方，以下說明

## 情境

使用 `@Data` 的 Class，如果用途單純，不會被繼承，那還不會發生什麼事，但被繼承且還設置不當，那就準備繳稅吧

## 範例

Animal.java
```
@Data
public class Animal {
    private int age;
    private String name;
}
```

Bird.java
```
@Getter
@Setter
public class Bird extends Animal {
    private String type;
}
```

Test.java
```
public static void main(String[] args) {
        Bird b1 = new Bird();
        Bird b2 = new Bird();

        // 1. 直接比對
        System.out.println(b1.equals(b2)); //true

        // 2. 對子類設置參數
        b1.setType("sky");
        b2.setType("sea");
        System.out.println(b1.equals(b2)); //true

        // 3. 對父類設置參數
        b1.setName("www");
        b2.setName("www");
        System.out.println(b1.equals(b2)); //true

        b1.setAge(1);
        b1.setAge(2);
        System.out.println(b1.equals(b2)); //false
    }
```

看到 2. 是不是已經發現不太對了!!

從 2. 來看 "sky" 和 "sea" 怎麼看都不可能相同，怎會是 true 呢?

## 問題點

**原因在於 `equals()` & `hashCode()` 上面，並沒有針對子類屬性的比對，Lombok `@Data` 並沒有幫我們做這件事**

如果我們對 `equals()` 案 ctrl + 滑鼠左鍵，點過去會發現它導向 Animal 的 `equals()` 去

接下來，我們來看一下反編譯後的 Animal.class 的 `equals()` & `hashCode()`

先從 `hashCode()` 開始看，這裡 `hashCode()` 只對 `name` 和 `age` 做處理，並沒有對子類的 `type` 做處理

```
 public int hashCode() {
        int PRIME = true;
        int result = 1;
        result = result * 59 + this.getAge();
        Object $name = this.getName();
        result = result * 59 + ($name == null ? 43 : $name.hashCode());
        return result;
    }
```

我們再看看 `equals` 是不是一樣

```
public boolean equals(final Object o) {
        if (o == this) { // 比對位址的值
            return true;
        } else if (!(o instanceof Animal)) { // 非 Animal 類或 Animal 子類，回 false
            return false;
        } else {
            Animal other = (Animal)o;
            if (!other.canEqual(this)) {
                return false;
            } else if (this.getAge() != other.getAge()) { // 答案在這裡，這只比對父類的所有屬性，未檢查子類的屬性
                return false;
            } else {
                Object this$name = this.getName();
                Object other$name = other.getName();
                if (this$name == null) {
                    if (other$name != null) {
                        return false;
                    }
                } else if (!this$name.equals(other$name)) {
                    return false;
                }

                return true;
            }
        }
    }
```

而好玩的是，如果用 `@Data` 取代 Bird 的 `@Getter`、`@Setter`，也會有一樣的問題，而且還反過來XD

並且 `@Data` 在新版本中，IDE 還可能提醒你，會有一段錯誤訊息要求你更改加上 `@EqualsAndHashCode(callSuper = true)`

但如果你是用 `@Getter`、`@Setter` 那就刺激了，可以過編譯還不會提醒你，真的讚

## 解決辦法

1. 自己 `override` `equals()` & `hashCode()`
2. 子類加上 `@EqualsAndHashCode(callSuper = true)`
3. 放棄使用 `@Data`
4. 直上 Kotlin 簡單、粗暴

個人選擇是 3. 

回報給團隊和其他在使用的人，明令禁止使用 `@Data`，直接略過這個坑，節省別人的時間和減少學習成本

## 推薦套件

SonarLint - 免費 coding 檢查工具，這種問題它也有檢核到
