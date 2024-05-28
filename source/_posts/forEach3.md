---
title: Hex_forEach題型
date: 2024-05-19 17:02:41
tags: [HexSchool,Video]
categories: [Javascript]
description: 六角學院JS直播forEach練習
---
# 網頁預想呈現畫面
![image](https://i.imgur.com/usFRj1I.png)

## 每日任務 Day25 forEach補充
```js
let data = ["a", "b", "c"];

// 參數 item 代表陣列中目前正在被處理的那個元素
// 參數 index 代表陣列中目前正在被處理的那個元素的索引值
// 參數 array 代表被處理的陣列本身，在此為 data
data.forEach(function(item, index, array){
  console.log(item, index, array);
})
```
![Image](https://i.imgur.com/1gjNwl0.png)
>這邊需要特別提醒，在 forEach() 函式內用 return 無法停止函式進行下一個 item。除非程式碼有誤，否則並沒有中止 forEach() 的辦法
>

## 決定資料格式(HTML)
```html
<ul class="list">
    <li></li>
</ul>
```
```html
    <h2>新增資料</h2>
    <input type="text" class="stationName" placeholder="充電站名稱">
    <input type="text" class="stationCharge" placeholder="免費 or 付費"></br>
</br>
    <input type="button" value="Save" class="btn">
```
## 初始化一個空字串，再塞入ul.list 的innerHTML
## 初始化一個空物件，再塞入相對應屬性的值
```js
let data=[
  {
    Charge:"Free",
    name: "Kathy Charge Station"
  },
  {
    Charge:"Coin",
    name: "Sophie Charge Station"
  },
  {
    Charge:"Free",
    name: "Cecilia Charge Station"
  },
  {
    Charge:"Coin",
    name: "George Charge Station"
  },
]
const list = document.querySelector(".list");
let str = "";
data.forEach(function(item, index){
    let content = `<li>${item.name}, ${item.Charge}</li>`;// 組好list.innerHTML指定的HTML樣式
    str += content
   
})
list.innerHTML = str;
```
```js
 const stationName = document.querySelector('.stationName');
const stationCharge = document.querySelector('.stationCharge');
const btn = document.querySelector('.btn');

btn.addEventListener("click",function(e){
  console.log(stationName.value);
  console.log(stationCharge.value);
  let obj ={};
  obj.name = stationName.value;
  obj.Charge = stationCharge.value;
  data.push(obj);//此行程式碼只是將新增的資料先放入data中
  init();//沒有新增的那一筆，因為需要一開始初始化的資料結構
  stationName.value="";//清空欄位
  stationCharge.value="";//清空欄位
})
```
## 將要抓資料的forEach部分用function包覆，才可以一開始就在網頁上呈現需要的HTML樣式

```js
const list = document.querySelector(".list");
function init(){

let str = "";
data.forEach(function(item, index){
    let content = `<li>${item.name}, ${item.Charge}</li>`;// 組好list.innerHTML指定的HTML樣式
    str += content
   
})
list.innerHTML = str;
};

init();
```

## 插入兩個按鈕去做相對應的資料篩選, 監聽區塊為div.filter區塊

```html
 <div class="filter">
        <input type="button" value ="Free">
        <input type="button" value ="Coin">
    </div>
```

```js
const stationFilter = document.querySelector('.filter');
console.log(stationFilter);
stationFilter.addEventListener("click",function(e){
  console.log(e);
  console.log(e.target);
  console.log(e.target.value);
  console.log(e.target.nodeName);
}
)
```
![Image](https://i.imgur.com/lKXbMRE.png)


>stationFilter的區塊中並非所有區塊都有value, 只有點到按鈕才會觸發事件,才可以console.log(e.target.value), **e.target.value**在點擊到非按鈕的stationFilter區塊時，會因為沒有value而使e.target.value為**undefined**
```js
const stationFilter = document.querySelector('.filter');
stationFilter.addEventListener("click",function(e){
  if(e.target.value == undefined){
    console.log("Where you click is empty space");
    return
  }
  let str = ""
  data.forEach(function(item,index){
    if (item.Charge == e.target.value){
      str+=`<li>${item.name},${item.Charge}</li>`
    }
  })
  list.innerHTML = str;
}
)
```

+ **之所以使用e.target.value而非e.target.nodeName是因為兩顆按鈕篩選出來的資料不一樣，若使用e.target.nodeName通常就是只有一顆按鈕**

  + **e** 會把事件觸發時的物件狀態快照起來,event通常在大括號中存活,Function結束時就會消失,**e.target** 會呈現出當下點擊到的HTML架構

   + **e.target.nodeName**則會呈現出當下的ＨＴＭＬ標籤(例如~INPUT,LI)

>innerHTML會將其中的HTML全部清空後再帶入要塞入的內容

>**const list** 有被重複使用到,所以可以拉到最外層, init()上方，作為全域變數