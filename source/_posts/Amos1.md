---
title: 圖文滿版區塊 NO001
date: 2024-06-08 22:26:42
tags:
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
* to top (下方漸層到上方)
* to right (左方漸層到右方)
* to bottom (上方漸層到下方)
* to left (右方漸層到左方)
* to top left (右下漸層到左上)
* to top right (左下漸層到右上)
* to bottom right (左上漸層到右下)
* to bottom left (右上漸層到左下)

```css
background-image: linear-gradient(角度, 起始色彩 起始色彩位置, 結束色彩 結束色彩位置);
```