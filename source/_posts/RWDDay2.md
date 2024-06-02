---
title: Day2 CSS em and rem explained
date: 2024-06-01 21:12:13
tags: [21DaysChallenge, Video]
categories: [HTML]
description: Kevin Powell Conquering Responsive Layout
---
## em
* 預設的瀏覽器字體尺寸為16px, 所以1em預設就是16px
* 父層若有具體設定font-size, 則1em的尺寸就會按照父層設定的font-size為主

<mark>父層若設定font-size為2em, 則代表所有子元素都會是以32px為1em</mark>

```html
  <div class="parent1">
    <h2>EM測試</h2>
  </div>
```
```css
.parent1{
  font-size:2em;
  /*代表父層預設為32px*/
}

.parent1 h2{
 font-size:2em;/* 32px*2 =64px*/
}
```
>rem 則不會因為父層元素的字體大小而會有任何的變化，因為rem的單位值為html根部的預設字體大小，相反的em單位值會因為父層的字體大小而影響

## 同一子元素的其他屬性（除字體大小外）的em值
* 若是用em為單位來定義其他屬性的長寬，則會依據同一子元素的font-size設定值為em基準單位值來定義

<mark>具體來說，若是.parent1 h2字體大小設定為64px,則要設定其他.parent1 h2的長寬就會變成1em為64px</mark>

```html
 <div class="parent1">
    <h2>EM測試</h2>
  </div>
```
```css
.parent1{
  font-size:2em;
  /*代表父層預設為32px*/
}

.parent1 h2{
 font-size:2em;/* 32px*2 =64px,要繼承父層預設的字體大小*/
 margin-bottom:1em;/*64px*1=64px,要繼承此子元素字體大小的64px為一單位em值*/
}
```

## em & rem
* em是比較類似相對值的概念，且要考慮的變數較多，但可以維持一個區塊<mark>例如:按鈕</mark>的固定比例（因為其他屬性的em單位值會隨著各元素的字體大小em值而進行調整）

* 相對來說，rem比較一致，因為其參考的基準值只有根部html的字體大小值

<span style="color:red">px是絕對值，所以通常會盡量避免使用在RWD中，有可能因此需要更多斷點(media queries)</span>