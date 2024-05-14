# HTTP 介紹

## 什麼是 HTTP 協定

* 協定 - 電腦通訊網路中兩台電腦之間進行通訊所必須遵守的共同規範(意思就是你跟我打暗號前要講好遊戲規則拉，不然誰聽得懂)

* HTTP - 超文字傳輸協定(HyperText Transfer Protocl)，網際網路上最廣泛的網路通訊協定，允許將超文字標記語言(HTML)文件從 Web Server 傳送到用戶端的瀏覽器渲染

## 什麼是 URL

* URL - 統一資源定位器(Uniform Resource Locator)，用於完整描述網路上某一處資源的位址

* URL 格式

```
schema://host[:port#]/path/../[?..query-string][#anchor]
```

* URL 格式對應說明

  * schema - 指定低層使用的協定 (例如: http，https，ftp)

  * host - HTTP Server 的 Ip 位址或域名

  * port# - HTTP Server 的預設通訊阜是 80

  * path - 存取資源的路徑

  * query-string - 發送給 HTTP Server 的資料

  * anchor - 錨點

* 範例

```
http://www.mywebsite.com/tankxiao/test/test.aspx?name=sviergn&x=true#stuff
```

* 範例對應說明

   * schema - http
  
  * host - www.mywebsite.com

  * port# - 8080，這裡沒有顯示而已，被包在 host 裡面

  * path - /tankxiao/test/test.aspx

  * query-string - name=sviergn&x=true

  *  anchor - stuff

## 送出一張包含 form 的 html 會發生什麼事

1.於瀏覽器按下 submit 後

uploadFile.html

```
<form
  action="http://localhost:8000/"
  method="post"
  enctype="multipart/form-data">
  <label>Name: <input name="myTextField" value="Test" /></label>
  <label><input type="checkbox" name="myCheckBox" /> Check</label>
  <label>
    Upload file: <input type="file" name="myFile" value="test.txt" />
  </label>
  <button>Send the file</button>
</form>

```

2.form 會以下方封包結構方式送出

```
POST / HTTP/1.1
Host: localhost:8000
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:50.0) Gecko/20100101 Firefox/50.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Connection: keep-alive
Upgrade-Insecure-Requests: 1
Content-Type: multipart/form-data; boundary=---------------------------8721656041911415653955004498
Content-Length: 465

-----------------------------8721656041911415653955004498
Content-Disposition: form-data; name="myTextField"

Test
-----------------------------8721656041911415653955004498
Content-Disposition: form-data; name="myCheckBox"

on
-----------------------------8721656041911415653955004498
Content-Disposition: form-data; name="myFile"; filename="test.txt"
Content-Type: text/plain

Simple file.
-----------------------------8721656041911415653955004498--

```


### 回應封包



## HTTP 常用方法

| Method  | Description |
| ------------- | ------------- |
| GET | 請求資源  |
| POST | 修改資源  |
| PUT  | 全部修改  |
| PATH  | 部分修改  |
| DELETE | 刪除資源  |
| HEAD | 發送表頭資源  |

## HTTP 狀態碼

| Code  | state |
| ------------- | ------------- |
| 200 | 請求資源  |
| 400 | 修改資源  |
| 403  | 全部修改  |
| 406  | 部分修改  |
| 500 | 刪除資源  |
| HEAD | 發送表頭資源  |

## HTTP Header

## HTTP Cache

## URL Encode

## Cookie

## HTTP 基本認證

## HTTP 為什麼不安全

瀏覽器發送給 Server 的內容非常容易被中間人攔截，許多工具都可以攔截的到

```
username=tw123&password=tw123456
```

## Web 通訊如何做到安全

## 工具

Fiddler、JMeter、Postman

## 參考

書籍 - 晉升成 HTTP 一代宗師 Java 實作

[HTTP Method - mdn web docs](https://developer.mozilla.org/zh-TW/docs/Web/HTTP/Methods)

[MIME types](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_Types)
