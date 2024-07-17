---
title: Hex-Bootstrap-W5
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

## Base & Reset的差別

>Base是針對網站進行全站調整，至於reset則是清空瀏覽器樣式

## 通用類別 Utils
* 通用類別增加一個CSS檔案的維護性及重複使用性

>Bootstrap是支援ＲＷＤ的，所以做完PC版後，就毋需再另外做手機版

## 元件 components

>語意命名會導致元件無法在另一頁面使用, 所以實務上並不重要, 除非該元件只會使用一次

## 互動式視窗 Modal
* data-bs-toggle 所帶入的值代表要用什麼功能
* data-bs-target 對應到所要展開區域的ID

```html
<!-- Button trigger modal -->
<button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#staticBackdrop">
  Launch static backdrop modal
</button>

<!-- Modal -->
<div class="modal fade" id="staticBackdrop" data-bs-backdrop="static" data-bs-keyboard="false" tabindex="-1" aria-labelledby="staticBackdropLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="staticBackdropLabel">Modal title</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
        ...
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary">Understood</button>
      </div>
    </div>
  </div>
</div>
```