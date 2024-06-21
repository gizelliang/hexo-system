---
title: Errand2
date: 2024-06-19 11:30:55
tags: [HexSchool,Video]
categories: [HTML]

---

>同時要調整 4 張卡片的寬度，讓卡片能齊寬。
>可以使用 width 屬性的 `calc` 來自動計算卡片的寬度。

>卡片的寬度會是父層元素的一半，再減掉 gutter 的 24px / 2，也就是 `calc(50% - 12px);` 
>所以我們可以將卡片的寬度設定為 `width: calc(50% - 12px);`  ，再加上灰色 border 邊框以及 padding 數值：

```css
.card {
  border: 1px solid #e3e3e3;
  padding: 16px;
  width: calc(50% - 12px);
}
```
![Image](https://i.imgur.com/YNYAC0d.png)
```css
.contact .image {
  /* object-fit: cover; 讓圖維持設定好的寬高，並且圖片會自動裁切掉邊緣，防止圖片被壓縮變形 */
  /* 可參考文章 https://www.casper.tw/development/2020/10/11/img-cover/ */
  object-fit: cover;
  /* 加入圓角 */
  border-radius: 40px;
  width: 162px;
  height: 162px;
}
```