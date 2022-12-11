# paper trade chatbot

Paper trade chatbot 是一個模擬股票交易的系統，使用golang撰寫與kubernetes架設，利用micro service架構結合mysql, redis, rabbitmq等資源架設，使用者可以註冊會員、檢視股票票價與走勢、出入金、開倉平倉等。

### 微服務

Paper trade chatbot 包含以下微服務：

* `member` 用戶註冊、用戶資料、用戶群組
* `auth` 用戶群組權限、登入登出
* `quote` 股票票價即時報價
* `candle` K線紀錄
* `product` 股票產品資料
* `position` 用戶持倉資料
* `order` 下單開倉、平倉
* `match` 即時撮合訂單
* `wallet` 用戶錢包資料
* `api` 提供RESTful API供外部使用

### 其他repo

Paper trade chatbot 除以上微服務外，也包含相關repo

* `k8s` kubernetes設定檔、架設腳本
* `common` 所有microservice共用的golang程式碼
* ``
