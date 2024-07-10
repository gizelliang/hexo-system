---
title: Hex-RWD-W5
date: 2024-07-08 10:38:09
tags: [HexSchool,Video]
categories: [HTML]
description: 六角學院切版直播第五堂+週三助教文字講解
---
## 表單的應用

* action的值為資料要送往的地方
* 用get傳送資料的話，網址會顯示出傳送資料的內容
* 比較常用post傳送資料，網址不會揭露出資料內容

```html
<form action="index.html" method="get">

</form>
```
* input的value為元件中顯示的文字初始值
```html
<input type="submit" value=“送出“>
```
* id作為錨點使用,可以使使用者點擊label時直接聚焦到input欄位上

```html
<label for = "myName">姓名:</label>
<input id="myName" type="text" name="myName">
```
* 
## <input type="date"> 不要使用

* 無法改動行事曆的樣式
* 若要取出裡面的日期時，各個瀏覽器格式不同,傳送到後端的資料會怪怪的

### 替代方案
[Jquery Datepicker](https://jqueryui.com/datepicker/)
[Javascript FullCalendar](https://fullcalendar.io/)

## readonly & disabled

* readonly 使input的值無法改動，只能閱讀

```html
<label for="myName">姓名:</label>
<input id="myName" type="text" name="myName" value="Sophie" readonly>
```
* disabled使input的值凍結

```html
<label for="myName">姓名:</label>
<input id="myName" type="text" name="myName" value="Sophie" disabled>
```

>select option所做出的下拉選單，在手機上的樣式是內建的，無法隨之更改

## Normalize Reset & CSS Reset

* CSS Reset就是把所有樣式都清空，重新歸零
* Normalize Reset則是保有樣式，Bootstrap就是用這套


