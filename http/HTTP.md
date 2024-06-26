# HTTP 介紹

## 什麼是 HTTP 協定

* 協定 - 電腦通訊網路中兩台電腦之間進行通訊所必須遵守的共同規範(意思就是你跟我打暗號前要講好遊戲規則拉，不然誰聽得懂)

* HTTP - 超文字傳輸協定(HyperText Transfer Protocl)，網際網路上最廣泛的網路通訊協定，允許將超文字標記語言(HTML)文件從 Web Server 傳送到用戶端的瀏覽器渲染

## 什麼是 URL

* URL - 統一資源定位器(Uniform Resource Locator)，用於完整描述網路上某一處資源的位址

## URL 格式

範例

```
http://www.mywebsite.com/tankxiao/test/test.aspx?name=sviergn&x=true#stuff
```

格式

```
schema://host[:port#]/path/../[?..query-string][#anchor]
```

| Key  | Value | Description |
| ------------- | ------------- | ------------- |
| schema | http  | 指定低層使用的協定 (例如: http，https，ftp) |
| host | www.mywebsite.com  | HTTP Server 的 Ip 位址或域名 |
| port#  | 8080，這裡沒有顯示而已，被包在 host 裡面  | HTTP Server 的預設通訊阜是 80 |
| path  | /tankxiao/test/test.aspx  | 存取資源的路徑 |
| query-string | name=sviergn&x=true  | 發送給 HTTP Server 的資料 |
| anchor | stuff  | 錨點 |

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
* User-Agent : 瀏覽器告訴 Server端，Client 端使用的作業系統版本、CPU、瀏覽器版本、瀏覽器繪製引擎、瀏覽器語言、外掛程式等 (可被修改，網站 >> 改成手機，就能登入手機板網頁)

* Refer : 伺服器判斷來源頁面，是從搜尋網頁還是書籤，或者其他網站連過來，以合理判斷定位網站，也被使用來防盜鏈，即判斷下載來源是否來自網站內部，否則不給下載

3. 得到 HTTP Code 200 ok! 回應判斷結果 

## HTTP 常用方法

| Method  | Description |
| ------------- | ------------- |
| GET | 請求資源  |
| POST | 修改資源  |
| PUT  | 全部修改  |
| PATH  | 部分修改  |
| DELETE | 刪除資源  |
| HEAD | 發送表頭資源  |

### GET & POST 差異

* 資料傳輸方式

  * GET 以 `?` 分割 URL 和傳輸資料 `user?userId=abc&pwd=123456`

  * POST 將傳送資料放進 HTTP 封包中的 Body

* 長度限制 

  * GET 有長度限制 (瀏覽器對 URL 有長度限制)

  * POST 沒有長度限制

* 取得方式

  * GET 使用 `Request.QueryString` 取得變數值

  * POST 使用 `Request.Form` 取得變數值

* GET 有安全問題，太容易暴露隱密資訊

## HTTP 為什麼不安全

瀏覽器發送給 Server 的內容非常容易被中間人攔截，許多工具(Fiddler)都可以攔截的到

```
username=tw123&password=tw123456
```

## Web 通訊如何做到安全

1. 只有瀏覽器和 Web Server 能看到真正內容，中間人(Proxy Server)也不行

2. HTTP 請求內容與回應內容，無法被篡改

### 那要如何實現?

 1. 使用加密演算法(非對稱加密、對稱加密、DES、RSA)，對內容做加密處理，並且對每個廠商使用不同種類加密演算法，且定期更新
 
 2. 使用 SSL/TLS (SSL 所有版本已不再安全，應該使用 TLS)

## HTTP 狀態碼

| Code  | state |
| ------------- | ------------- |
| 200 | OK! 請求成功  |
| 301/302 | Moved Permanently (重新導向) : 請求的 URL 已被移走。 Reponse 中的 `Location URL` 則提示資源所在位置  |
| 404  | Not Found : 未找到資源  |
| 500 | 伺服器錯誤  |

## 其他關鍵字

* Cookie、URL Encode、Cache、Base64、MD5、stamp(時間戳記)、sign(數位簽章)

## 工具

Fiddler、JMeter、Postman

## 參考

書籍 - 晉升成 HTTP 一代宗師 Java 實作 (吐槽: 根本沒有 Java 任何成分 lol)

[HTTP Method - mdn web docs](https://developer.mozilla.org/zh-TW/docs/Web/HTTP/Methods)

[MIME types](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_Types)
