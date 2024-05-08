# JMeter 安裝 & 使用

透過 JMeter 對寫好的 api 進行流量測試，基本上跟 Postman 大同小異，只是需要各種手動設定

## 安裝

至官方網站下載主程式，解壓縮 (如未設置 JAVA_HOME，須先進行設置，不然無法啟動)

官網: https://www.apache.org/

## 啟動

1. 於 /bin 下找到 jmeter.bat 執行啟動
2. 上方快捷列 Options -> Change language 可更換繁體中文

## 使用

### 1. 對 Test plan 右鍵，新增 -> Threads - > 執行緒群組
   
   ![image](https://github.com/dacelo971130/learing/assets/83411220/623c9d19-f2e3-4810-afbe-f7ca5f1c893b)

   * 執行緒數量 - 可視作使用者數量
   
   * 啟動延遲 - 幾秒內到達設定的使用者數量，並非 loop 的間隔時間

### 2.  對 執行緒群組 右鍵，依序新增如下圖的選項
   
   ![image](https://github.com/dacelo971130/learing/assets/83411220/72320071-277a-419d-b9ab-f1251677d9d2)

   * HTTP 標頭管理員 - 設置 Header config 
     
   * HTTP 要求預設值 - 設定預設值、標頭類型細微設定
     
   * HTTP 要求 - 主要發送 Request 的設定地方
     
   * 檢視結果樹 - 所有 Request 結果細項
     
   * 檢視表格式結果 - 全部 Request 結果比對，包括 Latency、Byte、Connect Time(ms)等等相關資訊

### 3. 點擊綠色箭頭執行

## 參考

[Apache JMeter Doc](https://jmeter.apache.org/usermanual/component_reference.html#Thread_Group)

[Jmeter 基本介紹 - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天](https://ithelp.ithome.com.tw/articles/10186852)

[Day 20 Jmeter 壓力測試工具 - iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天](https://ithelp.ithome.com.tw/articles/10203900)

     
