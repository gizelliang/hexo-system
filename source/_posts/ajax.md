---
title: Ajax
date: 2024-05-24 11:10:43
tags:
description: 六角JS直播預錄 & JS直播第六週
---
## AJAX 基本介紹

![Image](https://i.imgur.com/FbUrT8y.png)
> AJAX 是一種<mark>非同步的JS技術</mark>, 主要用來與伺服器做資料交換


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

## Request 網址請求 （瀏覽器給伺服器)
* 網址請求裡面還會包含傳送的基本資訊，Request Header是網址請求的一些簡介
* 網址請求通常會揭露使用者的身份，使伺服器能驗證其身份

## Response 網址回應 (伺服器給瀏覽器)
* **Response**回傳字串給瀏覽器
* **Response Header**中的**content-type**決定資料的格式及編譯方式
* axios會將response作為then中函數的parameter

## HTTP Method

* GET: 獲取資料
* POST:新增資料
* DELETE: 刪除資料
* PUT/PATCH:修改資料,PUT修改整個,PATCH修改一部分

>每種axios寫法中塞的參數都不同

## Get & Post的區別
* **Get**是一種取得資料的方式，參數通常只有url
[AXIOS GET PRACTICE](https://codepen.io/gizelliang/pen/YzoNMqj)
```javascript
let ary = []

axios.get("https://hexschool.github.io/ajaxHomework/data.json").then(function(response){
  console.log("資料有回傳了");
  ary = response.data;
  renderData();
})
//將不同功能分離出來做成不同的函式，然後再將其包在then之後
function renderData(){
 const listName = document.querySelector(".name");

listName.textContent = ary[0].name;
}

console.log(ary);

//1. renderData先被註冊到瀏覽器的javascript裡去
//2. 程式碼繼續向下執行
//3. response回傳, 觸發then中的函數
```
```html
<ul class="list">
  <li class="name"></li>
  <li></li>
  <li></li>
</ul>
```

* **Post**會傳送資料，參數通常會有兩個, 第二個值是一個物件，要把對應的屬性跟值去做傳送
* 用**Post**方法傳送的網路請求，第二個參數的物件資料一定要遵循伺服器要求的格式
* 伺服器會去跟資料庫核對資料，若帳號已經被註冊則會回傳Error Message

```javascript
// axios post 範例

axios.post('/user', {
    firstName: 'Fred',
    lastName: 'Flintstone'
  })
  .then(function (response) {
    console.log(response);
  })

  //response回傳成功
  .catch(function (error) {
    console.log(error);
  });
  //response回傳失敗
```
## content-type（網路請求的資料格式名稱)
1. application/x-www-form-urlencoded **較常見**
2. application/json **axios預設方式，但也支援其他方式**
3. multipart/form-data **較常見**
4. text/plain

>content-type包含在網路請求的Header中, **Header**是呈現response & request資訊的區塊

![Image](https://i.imgur.com/KAGjOiQ.png)
![Image](https://i.imgur.com/4cXF04V.png)