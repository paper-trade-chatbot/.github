# paper trade chatbot 模擬股票交易系統 - by Josh Tsai

Paper trade chatbot 是一個模擬股票交易的系統，使用golang撰寫與kubernetes架設，利用microservice架構結合mysql, redis, rabbitmq等資源架設，使用者可以註冊會員、檢視股票票價與走勢、出入金、開倉平倉等。k8s配合redis具有便於水平擴展的特性。

### 簡介
本系統為用來練習`k8s`,`grpc`,`rabbitmq`的side project，商業邏輯部份由Josh獨立開發完成，目前僅開發後端部份。

### 微服務

Paper trade chatbot 包含以下微服務：

* `api` 提供統一api接口（目前想把API分散到各個service各自開API，因此暫時刪掉api service）
* `member` 用戶註冊、用戶資料、用戶群組
* `quote` 股票票價即時報價
* `candle` K線紀錄
* `product` 股票產品資料
* `position` 用戶持倉資料
* `order` 下單開倉、平倉
* `match` 即時撮合訂單
* `wallet` 用戶錢包資料

### 其他repo

Paper trade chatbot 除以上微服務外，也包含相關repo

* `k8s` kubernetes設定檔、架設腳本
* `proto` 所有microservice共用的protobuf與產生的golang package
* `pubsub` 所有microservice共用的rabbitmq串接與傳輸格式

### 資源

* `mysql` 各microservice各自有其schema，便於拆分db使用量
* `redis` 儲存暫存資料與處理水平擴展的service間溝通
* `rabbitmq` 擺放資料的queue，應付大量訂單情形

### 流程

![image](https://github.com/paper-trade-chatbot/.github/blob/main/profile/order%20process.jpg?raw=true)

---

## 開發者
以上程式商業邏輯與相關工具開發來自 [Josh](https://github.com/lisyaoran51), 系統設計架構參考101投資平台, 重新撰寫並優化訂單處理流程
