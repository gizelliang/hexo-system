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
* 此一CSS屬性會將原本垂直排列的子元素變成水平排列,且仍保有原本父層container原本的區塊元素本性(佔滿整行的空間)

![Image](https://i.imgur.com/AJNtFYj.png)

```css
display:inline-flex;
```
* 子元素變成水平排列以外，改變父層container的block本性，<mark>變成inline</mark>，不會佔滿整行空間

![Image](https://i.imgur.com/7Kj7WoS.png)
********************************************************

## flex-direction (On the Container)
[Codepen Example](https://codepen.io/gizelliang/pen/gOJWbmW)
```css
 flex-direction:row;
```
* <mark>預設值為此一CSS屬性</mark>，代表主軸為左到右，交叉軸為上到下，不會對子層區塊元素產生任何影響(因為是預設值)

![Image](https://i.imgur.com/VJXd1B2.png)

```css
flex-direction:row-reverse;
```
* <mark>代表主軸從右到左</mark>

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
* 主軸從左到右，<mark>子元素都會依照寬度來換行</mark>

![Image](https://i.imgur.com/Ez6Yz4i.png)

```css
flex-wrap:wrap-reverse;
```

* 主軸從左到右，<mark>但交叉軸會變成下到上</mark>，子元素一樣會換行

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
* 越往右的子元素, <mark>order的值越大</mark>
* 最左邊的子元素, <mark>order的值會是最小值</mark>

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

* 兩個子元素同樣的order值時,會<mark>依照css中寫的先後順序</mark>，從左到右排列

>***order***的值可以為<mark>負數</mark>

****************************

## justify-content (On the container)

[Codepen Example](https://codepen.io/gizelliang/pen/VwObLOG)

>justify-content 定義子元素如何在<mark>主軸上</mark>排列

```css
justify-content:flex-start;
/*預設*/
/*主軸起點*/
```
```css
justify-content:flex-end;

/*主軸終點*/
```
```css
justify-content:center;

/*主軸中間*/
```

>space-around在主軸起點跟終點的最左邊跟最右邊一樣會有空間，space-between則完全都是子元素之間將所有空間分配
![Image](https://i.imgur.com/XbFMvjc.png)

```css
justify-content:space-between;
```

![Image](https://i.imgur.com/BCg1Spo.png)
```css
justify-content:space-around;
```

## align-items(On the container)

>align-items:stretch是<mark>預設</mark>,代表每個子元素都會將父層容器的高度塞滿（若父層容器有設定高度的話）

>align-items的值與justify-content大致相同,但其代表的是<mark>交叉軸的位置</mark>

![Image](https://i.imgur.com/BIw6A47.png)

```css
align-items:baseline;
/*內文的baseline會對齊, 不論字體大小*/
```
[Codepen Example](https://codepen.io/gizelliang/pen/KKLmvYb)

## align-content (On the container)

>相對於justify-content, align-content代表的是交叉軸的位置,預設的值一樣是stretch

><mark>align-content & align-items</mark>通常與flex-wrap:wrap一起搭配使用，因為若是沒有<mark>flex-wrap:wrap</mark>的話，每個flex的子物件都不會顯示出其真實寬度，而只會自適應調整成父層的container寬度
[Codepen Example](https://codepen.io/gizelliang/pen/wvbdqLX)

## align-self (On the child element)

>專門用在子元素上，使子元素的flex屬性取代父層的flex屬性
***********************************
## flex (On the child element)

```css
.container{
  display:flex;  
}

.box{
  flex:1;
}
```

```css
flex:1;
```
* 子層元素沒有<mark>flex:1</flex>時，子層元素不會充滿整個父層的container，只會依照內文的寬度跟高度來呈現
* 依照css寫的順序，若後續有其他子層元素被下了flex:2，則一開始寫的<mark>flex:1就會被覆寫</mark>

[Codepen Example](https://codepen.io/gizelliang/pen/OJYmzPb)

><mark>flex其實是flex-grow & flex-shrink的簡寫</mark>

```css
flex:1 5 400px;
```
* flex有三個值時，依序為grow,shrink,basis

## Flexbox flex-grow, flex-shrink and flex-basis(On the child element)

[Codepen Example](https://codepen.io/gizelliang/pen/WNBjdxX)

```css
flex-basis:400px;
```

>flex-basis是每個子元素的基準值

![Image](https://i.imgur.com/GLf6PEk.png)

![Image](https://i.imgur.com/ZcA6NRX.png)

```css
flex-grow:1;
```
>網頁預設的flex-grow為0,當有額外空間時，會將空間分配給那些flex-grow值越大的子元素,按照flex-grow值等比例分配多的空間

```css
flex-shrink:1;
```
>flex-shrink代表當視窗不夠大時，一個子元素收縮的倍率

>flex-shrink的預設值為1,代表當網頁不夠所有子元素的flex-basis長度時，會自動縮小每個子元素所佔的空間

## Nesting Flexbox
[Codepen Example](https://codepen.io/gizelliang/pen/bGyrBxm)
