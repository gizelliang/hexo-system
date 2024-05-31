---
title: Day 1 Using Percentages & Avoiding Heights
date: 2024-05-31 10:19:04
tags: [21DaysChallenge, Video]
categories: [HTML]
description: Kevin Powell Conquering Responsive Layout
---
## Percentages vs Fixed widths

>區塊元素若不設定具體寬度的話，通常就會佔滿整個畫面(代表預設寬度就是100%的父層元素)

>運用百分比來設定寬度的話，就會讓其中的區塊元素一直隨著父層寬度來調整

```html
<div class="parent">
  <div class="child"></div>
</div>
```
```css
.parent{
  background:#23424A;
  padding:50px;/*內推才可以看得得出父層元素*/
  /*width:500px; 設定固定寬度的話，就不會隨著畫面的縮放而縮放*/
  width:50%;/*responsive*/
  margin: 0 auto;
}

.child{
  background:#38CFD9;
  height:250px;

}
```
