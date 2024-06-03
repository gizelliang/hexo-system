---
title: FlexBox
date: 2024-06-01 22:44:10
tags: [WesBos,Video]
categories: [HTML]
description: What the Flexbox?
---
## display:flex & display:inline-flex (On the Container)
[Codepen Example](https://codepen.io/gizelliang/pen/qBGmBGG)

```css
display:flex;
```
* 此一CSS屬性會將原本<mark>子層中</mark>垂直排列的區塊元素變成水平排列,且仍保有原本父層原本的區塊元素本性(佔滿整行的空間)

![Image](https://i.imgur.com/AJNtFYj.png)

```css
display:inline-flex;
```
* <mark>子層中區塊元素</mark>變成水平排列以外，改變父層container的block本性，變成inline，不會佔滿整行空間

![Image](https://i.imgur.com/7Kj7WoS.png)
********************************************************
## flex-direction (On the Container)
[Codepen Example](https://codepen.io/gizelliang/pen/gOJWbmW)
```css
 flex-direction:row;
```
* <mark>預設值為此一CSS屬性</mark>，代表主軸為左到右，交叉軸為上到下，不會對子層區塊元素產生任何影響
![Image](https://i.imgur.com/VJXd1B2.png)

```css
flex-direction:row-reverse;
```
* 代表主軸從右到左

![Image](https://i.imgur.com/plSpxhC.png)

```css
flex-direction:column;
```
* <mark>主軸變成上到下，交叉軸變成左到右</mark>，子層區塊元素變成垂直的狀態
![Image](https://i.imgur.com/xTW6iqB.png)

```css
flex-direction:column-reverse;
```
* <mark>主軸變成下到上</mark>

![Image](https://i.imgur.com/Y4co5yg.png)

*****************************
## flex-wrap （On the Container）

[Codepen](https://codepen.io/gizelliang/pen/gOJWbKG)

>父層container下display:flex,使得子層的區塊元素皆具有flex特性，就算寬度超過父層container，也不換行，反而會壓縮每個子元素來塞進container中(<mark>代表預設都是父層上下flex-wrap:nowrap</mark>)

>預設的情況下，具備flex特性的子元素高度都會延伸到充滿整個父層container，但若是有下flex-wrap:wrap的情況下，高度就會依照每行總共有幾個子元素來進行調整跟分配

>每個語言有自己的書寫習慣，若是英語系國家的話，習慣從左到右書寫，所以瀏覽器的主軸為左到右

```css
flex-wrap:wrap;
```
* 主軸從左到右，子元素都會依照寬度來換行

![Image](https://i.imgur.com/Ez6Yz4i.png)

```css
flex-wrap:wrap-reverse;
```

* 主軸從左到右，但交叉軸會變成下到上，子元素一樣會換行

![Image](https://i.imgur.com/b9XekZd.png)
*********************
## Flex Ordering

[Codepen Example](https://codepen.io/gizelliang/pen/MWdmwQK)

```css
.box{
  flex:1;
  order:1;
}

.box3{
  order:0;
}

.box7{
  order:2;
}
```
* 越往右的子元素, order的值越大
* 最左邊的子元素, order的值會是最小值
![Image](https://i.imgur.com/B7IlzY5.png)


```css
.box{
  flex:1;
  order:1;
}

.box3{
  order:2;
}

.box7{
  order:2;
}
```
![Image](https://i.imgur.com/jEd0ebW.png)

* 兩個子元素同樣的order值時,會依照css中寫的先後順序，從左到右排列

>***order***的值可以為負數

****************************

## justify-content

[Codepen Example](https://codepen.io/gizelliang/pen/VwObLOG)

