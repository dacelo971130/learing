# Java SE

## 基礎

### classpath

在系統環境變數中所設的 CLASSPATH，其提供 java 程式(jdk8..etc)在執行環境中，尋找類別與其他相關資源的路徑。

對於一些命令工具，例如 : `java`、`javac`、`javadoc`也提供 `-classpth`(-cp) 等指令。

### -cp

設定 classpth 在 xxx 目錄下，這樣就不用一路 cd 進去到 xxx 目錄裡在執行其他指令。

```
java -cp C:\prg\classes book.java7.chapter.water.Fish
```

### jar -cvf

可將目錄 xxx 下所有 class 打包在 sample.jar 裡面，再將 xxx 所有子目錄刪除，剩下 sample.jar

```
jar -cvf sample.jar
```

### 存取修飾字(Modifier)

* public : 皆可存取。

* private : 同一個 class 下才可存取。

* default : 同一個 package 下的 classes 皆可存取。

* protected : 同一個 package 下的 classes 皆可存取。若在不同 package 下的 classes 要有繼承關係才可存取。

### import 是否會影響效能?

不會，只會增加編譯時間。

## 流程控制

## OOP

## Exception

## Collection
