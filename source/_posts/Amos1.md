---
title: 圖文滿版區塊 NO001
date: 2024-06-08 22:26:42
tags: [Youtube,Video,Book]
categories: [HTML]
description: Amos Youtube Video & CSS屬性第三章(背景)
---
[Codepen Example](https://codepen.io/gizelliang/pen/ExzvmBy)

## 如何設定多重背景?

```css
.banner{
  width: 100%;
  height:100vh;
  background-color: #ccc;
  /*此處設定為滿版高跟滿版寬*/
  background: linear-gradient(115deg,#7bf 50%,transparent 50%)center center/100% 100%,
    url(https://picsum.photos/seed/picsum/1200/600) right center / auto 100%;
}
```
```css
background-image: linear-gradient(to 目標方向, 起始色彩, 結束色彩);
```
* to top (下方漸層到上方)**0deg**
* to right (左方漸層到右方)**90deg**
* to bottom (上方漸層到下方)**180deg**
* to left (右方漸層到左方)**270deg**
* to top left (右下漸層到左上)**315deg**
* to top right (左下漸層到右上)**45deg**
* to bottom right (左上漸層到右下)**135deg**
* to bottom left (右上漸層到左下)**225deg**

```css
background-image: linear-gradient(角度, 起始色彩 起始色彩位置, 結束色彩 結束色彩位置);
```

## 3.1 background-color
[文章參考連結](https://csscoke.com/2015/01/01/rgb-hsl-hex/)

### RGB & RGBA
[RGB & RGBA](https://codepen.io/gizelliang/pen/gOJxJzG)

* 使用百分比
```css
color:rgba(100%,50%,0,.4)
```
* 使用0~255之間的數字
```css
color:rgba(255,123,0,.4)
```
* 第四個數字為alpha值<mark>不透明度</mark>

>alpha值介於0~1,越靠近1越不透明,<mark>alpha值也可改成用百分比</mark>

>各值之間不需逗號間隔,僅僅在alpha值前需要用/隔開

```css
color:rgba(255 123 0 /.4)
```

### HSL (Hue Saturation Lightness)
[Codepen Practice](https://codepen.io/gizelliang/pen/LYojoMR)
* Hue: 以角度來表示,<mark>撰寫時不需添加單位</mark>
    * 0 代表紅色
    * 120代表綠色
    * 240代表藍色

* Saturation:以百分比表示
    * 0%代表灰色，低飽和度
    * 100%代表正常飽和度

* Lightness: 以<mark>50%為預設值</mark>，越大就越白，越小就越黑,一樣只能用百分比來表示
    * 值越小代表黑色量越多
    * 值越大代表白色量越多

## background-color & background-image

* 漸層色是一種background-image, 而非background-color
* 同時設定background-color & background-image, 則背景圖片會蓋住背景色彩

* 背景色彩只能設定一個，背景圖片則可設定多重背景

```css
  background: linear-gradient(115deg,#7bf 50%,transparent 50%)center center/100% 100%,
    url(https://picsum.photos/seed/picsum/1200/600) right center / auto 100%;
}
```

><mark>background-image不會撐開容器本身,圖片超出區塊的地方不會顯示</mark>

## 多重背景
[Codepen](https://codepen.io/gizelliang/pen/ExzvBmZ)

* 多重背景時，會依序載入圖片，先寫的先顯示，後寫的顯示在後，需要設定background-repeat:no-repeat,才可以避免重複渲染,background-position也須錯開位置

## background-image:linear-gradient

[Codepen](https://codepen.io/gizelliang/pen/BaedXKy)

```css
.box3{
  background-image: linear-gradient(red 0%,40%,#FFF 100%);
}
```
* 第二個值僅設定色彩位置,就會是前後兩者的混合色
* 位置的趴數一定要小到大，才會有漸層效果
* 預設是180度,由上往下漸層
* 沒有設定色彩位置，就由幾個色彩等分所有位置

## background-position(定義的是background-image的位置)

* 