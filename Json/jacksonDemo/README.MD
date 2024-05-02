# Spring-boot API 使用 Jackson 接收多階層 JSON 

## 概述

在專案中，常常會有撰寫 API 接受 JSON 的情況，有時候階層數一多，一個個賦值非常的耗時又容易出錯

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

## 情境要求

1. 加密 - JSON 整體資訊做為重要參數
2. 變動式 Body - 因為功能而提供不同的 Body

## 添加依賴

使用 Lombok 省略樣本 Code 

```
compileOnly 'org.projectlombok:lombok'
annotationProcessor 'org.projectlombok:lombok'
```

## 使用方式

接下來我們要藉由 Jacnkson 的 objectMapper.readValue() 來轉化我們收到的 Json 成為所需物件

```
 QazApiRequest rq = objectMapper.readValue(dto.getJson(), QazApiRequest.class);
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

### QAZ

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

### FUNCTION

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

### DOC

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

### HEADER

```

```

## 參考




