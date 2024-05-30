---
title: Hex_W4_Function
date: 2024-05-14 12:13:16
tags: [HexSchool,Video]
categories: [Javascript]
description: 六角學院JS直播第四堂 & JS核心函數對應高階課程
---
## 函式的特性及使用時機
* 函式可以重複呼叫
* 封裝重複的程式碼
* 事件處理
* 非同步操作
* 參數只能存活在函數中
* 函式的參數是有順序的
><mark>console.log()</mark>只用來印出資料，而無法將值傳到函數之外，return才可以, <mark>console.log()</mark> 專門用在debug

## 物件縮寫範例
```javascript
let data = [];
function add (name, gender){
    const obj = {};
    obj.name = name;
    obj.gender = gender;
    data.push(obj);
    return data;
}

//物件中屬性和值為一樣的名稱，就可省略其中之一
let data = [];
function add (name, gender){
  data.push({name, gender});
    return data;
}

```
