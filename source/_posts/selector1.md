---
title: Amos_Basic Selector
date: 2024-05-21 15:24:43
tags: [Amos,Book]
categories: [HTML/CSS]
description: 金魚都能懂的CSS選取器第一章+第二章 & 六角 div 與後代選擇器運用
---
## 擬態選取器 :hover, :active
* :hover是滑鼠滑過去的效果,:active是滑鼠按著不放的效果

## 後代選取器
```html
<div class="style1">
        <a href="#">1</a>
        <a href="#">2</a>
        <a href="#">3</a>
        <p class = "content">這是段落</p>
        <p></p>
</div>
```
>父層的class(style1)可以將每個區塊內的子元素都指定為同一樣式，

```css
.style1 a{
    color:red;
}

.style1 .content{
    font-weight:bold;
}

```