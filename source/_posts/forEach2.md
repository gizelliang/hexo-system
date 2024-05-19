---
title: forEach2
date: 2024-05-19 15:19:21
tags: [HexSchool,Video]
categories: [Javascript]
---

## forEach 搭配 DOM做整合

### 決定資料格式(HTML)
```html
<ul class="list">
    <li></li>
</ul>
```
### 初始化一個空字串，再塞入ul.list 的innerHTML
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
### 將要抓資料的forEach部分用function包覆，才可以一開始就在網頁上呈現需要的HTML樣式

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

function init(){
const list = document.querySelector(".list");
let str = "";
data.forEach(function(item, index){
    let content = `<li>${item.name}, ${item.Charge}</li>`;// 組好list.innerHTML指定的HTML樣式
    str += content
   
})
list.innerHTML = str;
};

init();
```
### init()後網頁呈現的畫面
<blockquote class="imgur-embed-pub" lang="en" data-id="r69I6PY"><a href="//imgur.com/r69I6PY"></a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script>

### 插入兩個按鈕去做相對應的資料篩選, 監聽區塊為div.filter區塊

```html
 <div class="filter">
        <input type="button" value ="免費">
        <input type="button" value ="投幣式">
    </div>
```