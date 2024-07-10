---
title: Jquery
date: 2024-07-06 16:11:44
tags: [HexSchool,Video]
categories: [HTML]
description: 六角學院每日任務Day23 Jquery Youtube
---
[每日任務](https://hackmd.io/ToeJ26VpRGy0ly7mHA3ljA)

* Jquery本身是一種Javascript, 瀏覽器兼容性強
* 在HTML中載入CSS & Jquery時，jquery一樣在CSS後面才載入
* 下載了Jquery壓縮的版本後將程式碼放在專案中的資料夾
* 連結到外部cdn引入jquery的話，則有可能因為突然沒有網路而導致jquery失效
![Image](https://i.imgur.com/NlxZ5dR.png)

```js
$(document).ready(function(){
    $('h1').hide();
    //選擇器
    //a, .header
});

```
[Jquery下載網址](https://jquery.com/download/)
[Jquery Cheatsheet](https://oscarotero.com/jquery/)

## toggle()

>將區塊打開或關上
```js
$(document).ready(function(){
  $('h1').click(function(event){$('p').toggle();})
    })
```
## slideToggle()
>滑落或滑出
```js
$(document).ready(function(){
  $('h1').click(function(event){
    $('p').slideToggle(5000);
    //時間的單位為毫秒
    });
  });
  ```
## fadeToggle()
* 淡入淡出
```js
$(document).ready(function(){
  $('h1').click(function(event){
    $('p').fadeToggle(5000);
    //時間的單位為毫秒
    });
  });
```

[Codepen](https://codepen.io/gizelliang/pen/MWPMGYb)

## Jquery鏈式寫法
### .slideUp().slideDown()
>滑上滑下
```js
$(document).ready(function(){
  $('h1').click(function(event){
    $('p').slideUp(4000).slideDown(2000);
    //時間的單位為毫秒
    $('div').hide();
  });
  });
```

## .addClass() .toggleClass()

* 加上CSS樣式是一種常見用來寫動畫效果的方式, 相比用Jquery來說, 用addClass or toggleClass 透過CSS來載入效果的方式效能較好

## .attr() 改變屬性

* 動態改變HTML屬性的值，第一個參數是HTML的屬性，第二個則是要代入的值

```js
$('a').attr('href', '屬性要代入的值')
```

## .html 動態載入

* 事件觸發後，動態載入的html檔不會存在原始碼中
