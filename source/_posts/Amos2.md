---
title: 互動圖文卡片 NO002
date: 2024-06-10 11:45:17
tags: [Youtube,Video,Book]
categories: [HTML]
description: Amos Youtube Video & CSS屬性第七章(定位) & 第九章(其他重點)
---
[Codepen Example](https://codepen.io/gizelliang/pen/NWOaaad)

## 如何消除image下方與區塊元素的空白間隔？
[Image設定Vertical-align:middle](https://qoo8857300.medium.com/css-%E5%A6%82%E4%BD%95%E8%A7%A3%E6%B1%BAimg%E7%9A%84%E5%9E%82%E7%9B%B4%E5%B0%8D%E9%BD%8A-a3dcd6c47a4)

>Image本身為inline的特性，會讓他無法與下方的區塊元素貼齊,故須設定vertical-align:middle 或是display:block

## 定位

### position:static

＊ 此為預設樣式，不需特別設定
* 作用是將其他定位取消，回到最原始的狀態

### position:relative
* 不會將物件獨立一層，仍會參考原始的資料流位置，搭配top,bottom,left, right來達到顯示位置的偏移
* 也可搭配z-index來做使用，z-index越大者就可以覆蓋在z-index較小者之上

### position:absolute
* 獨立一層，不會參考原始的資料流位置
* 也可搭配top,bottom,left,right來做顯示位置的偏移，但會根據最靠近的containing block來做偏移，預設的containing block為viewport
* containing block通常是代表在父層上設定除了position:static以外的定位值（有時候不是直接父層，甚至是包裹在最外層的container)

* 除非在RWD中，不然盡量避免使用position:absolute


## Opacity
## Transition