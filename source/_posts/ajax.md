---
title: ajax
date: 2024-05-24 11:10:43
tags:
description: 六角JS直播預錄
---
## AJAX 基本介紹

![Image](https://i.imgur.com/FbUrT8y.png)
> AJAX 是一種<mark>非同步的JS技術</mark>

>網頁載入時，<mark>只向資料庫要求指定區塊的資料</mark>，並不是傳統的整頁資料回傳，提升網頁回傳的速度及使用者體驗

>使用者提出請求時，會根據HTML架構陸陸續續從資料庫撈資料，一開始優先傳回的一定是HTML架構(document),這樣才能開始解析HTML後決定接下來要撈什麼資料

![Image](https://i.imgur.com/jQ95WL8.png)

>Network 中可以檢視出有幾個網路請求，Waterfall則可以看出網路請求的執行順序，<mark>最優先被載入的應該是HTML架構.解析HTML時,再依程式碼中的先後順序分批向伺服器請求載入缺失的資訊</mark>



## 網頁請求狀態碼

>網路請求並非只能透過Browser送出，使用<mark>Javascript原生寫法 or 套件axios的寫法也可以</mark>也可以

* 404 <span style="color:#B03A2E">**找不到請求資源**</span>
* 304 用Browser暫存的file把網頁&圖片顯示, 從未被編輯過，不會向伺服器提出任何請求（重定向)
* 500 程式有error


[Axios連結](https://github.com/axios/axios)