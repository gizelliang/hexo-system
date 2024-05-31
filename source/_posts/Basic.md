---
title: Basic HTML & CSS
date: 2024-05-28 16:42:55
tags: [HexSchool,Video]
categories: [HTML]
description: 盒模型, inline & block 及CSS初步設定
---
## 建立HTML環境
 ```html
<head></head>
```
主要有網頁的細部資訊，例如:
```html 
<title></title>
```
會呈現出網頁頁面的名稱

```html 
<body></body>
``` 
則會呈現出網頁畫面的HTML架構

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
//網頁瀏覽器改成UTF-8的編碼，打中文才不會有亂碼
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
//針對網頁螢幕解析度的優化
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```
![Image](https://i.imgur.com/uVIVTVM.png)
## a連結特殊用法

```html
<a href="" target="_blank" title="連到Google"></a>

//target="_blank"會另開新的頁面連結到網站
//title的內容會呈現出一個小小的彈跳視窗
```
![Image](https://i.imgur.com/N1Du1WW.png)

## CSS 簡介

>***link:css*** 插入css的熱鍵,放在head裡

```html
 <link rel="stylesheet" href="style.css">
```
>***CSS Reset***是一種清除瀏覽器預設樣式的初始化設定

## 行內元素 & 區塊元素

[Codepen Example]()
* 區塊元素 **Block Element**
    * 預設佔滿整個版面，會依照父層元素自適應延伸佔滿
    * 寬度跟高度可以設定
    * 另起一行，無法跟其他元素並列
* 行內元素 **Inline Element**
    ```html
    <span></span>
    ```
    是常見的排版用的行內元素，沒有任何語意
    * 在一個區塊中，不希望某個元素另起一行，就可以用行內元素包覆
    * 行內元素是不能夠被設定寬高的，用**display:block**可以改行內元素的特性

## margin & padding
* margin 向外推
* padding 向內推

## margin:auto & text-align:center

[Codepen Example](https://codepen.io/gizelliang/pen/mdYRYBa)

```css
margin:auto;
``` 
* 依照父元素的寬度來做平均分配,水平置中

```css
text-align:center;
```
* 區塊內的文字段落要靠左，中，還是右

```html
<div class="wrap">
  <div class="header"></div>
  <div class="content"></div>
  <div class="footer"></div>
</div>
```
```css
.wrap{
  width:100px;
  height:100px;
  background:green;
  margin-left:auto;
  margin-right:auto;
}

.header{
  height:20px;
  background:blue;
}

.content{
  height:30px;
  background:gray;
}

.footer{
  background:yellow;
  height:10px;
}
```

![Image](https://i.imgur.com/dcVFCKr.png)

>區塊元素會自適應父層的寬度，不寫死高度的話，區塊元素會隨著內文延伸

>網頁預設字體大小是16px,傾向不要寫死高度，都讓內文來撐高
