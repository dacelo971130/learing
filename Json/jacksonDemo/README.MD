# Spring-boot API 使用 Jackson 接收多階層 JSON 

## 概述

在專案中，常常會有撰寫 API 接收 JSON 的情況，有時候階層數一多，Key 又都是大寫，真的是很頭痛

因此，藉由 spring-boot 內建的 Jackson 我們可以輕鬆的將 Json 賦值到所有對應的 Field 上，

不管它有幾層 Map 只要準備好相對應的 Class 即可

## 範例

JSON

```
{
    "QAZ": {
        "FUNCTION": {
            "FUNNAME": "qazPayment",
            "VERSION": "v1"
        },
        "DOC": {
            "HEADER": {
                "UUID": "188b6ac0-fa34-4fa0-a59d-49e3f7e9c3c0",
                "TX_DATETIME": "20240422063943",
                "MERCHANT": "85930815",
                "UNIQUE_ID": "48515"
            },
            "BODY": {
                "MEMBER_NO": "41905599930723",
            }
        },
        "ENCODE": {
            "DIG": "ABCEFG",
            "SIGNATURE": "QAZWSX",
            "MAC": "QAZWSXEDC"
        }
    }
}
```

## 添加依賴

使用 Lombok 省略 Sample Code 

```
compileOnly 'org.projectlombok:lombok'
annotationProcessor 'org.projectlombok:lombok'
```

## 準備類別

@JsonProperty("") : 是 Jackson 中的一個註釋類別，會辨識 JSON 中的 key，支援大小寫區別

### QazApiRequest

```
@Getter
@Setter
@ToString
@NoArgsConstructor
@AllArgsConstructor
public class QazApiRequest {

    @JsonProperty("QAZ")
    private Qaz qaz;
}
```

### Qaz

```
@Getter 
// 略..
public class Qaz {

    @JsonProperty("FUNCTION")
    private Function function;

    @JsonProperty("DOC")
    private Doc doc;

    @JsonProperty("ENCODE")
    private Encode encode;
}
```

### Function

```
@Getter 
// 略..
public class Function {

    @JsonProperty("FUNNAME")
    private String funName;

    @JsonProperty("VERSION")
    private String version;
}
```

### Doc

```
@Getter 
// 略..
public class Doc {

    @JsonProperty("HEADER")
    private Header header;

    @JsonProperty("BODY")
    private Body body;
}
```

### Header

```
@Getter
// 略..
public class Header {

    @JsonProperty("UUID")
    private String uuid;

    @JsonProperty("TX_DATETIME")
    private String txDatetime;

    @JsonProperty("MERCHANT")
    private String merchant;

    @JsonProperty("UNIQUE_ID")
    private String uniqueId;
}
```

### Body

```
@Getter
// 略..
public class Body {

    @JsonProperty("MEMBER_NO")
    private String memberNo;
}
```

### Encode

```
@Getter
// 略..
public class Encode {

    @JsonProperty("DIG")
    private String dig;

    @JsonProperty("MAC")
    private String mac;

    @JsonProperty("SIGNATURE")
    private String signature;
}
```

## 使用方式

接下來我們要藉由 Jacnkson 的 objectMapper.readValue() 來轉化我們收到的 JSON 成為所需物件

```
// objectMapper 建議以 @Autowired 的方式使用， new 的開銷比較大
 QazApiRequest rq = objectMapper.readValue(dto.getJson(), QazApiRequest.class);
```

之後變大功告成~

## 額外補充

有許多 Developer Tools 也支援將 JSON 轉換為 Class 自行建立，完全不需要手動一個個設置

