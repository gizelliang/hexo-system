---
title: 偽類選取器
date: 2024-07-02 16:56:28
tags: [Amos,Book]
categories: [HTML/CSS]
description: 金魚都能懂的CSS選取器第四章
---

## :nth-child & :nth-last-child

>:nth-child(an+b),基本上就是在()塞入選取的條件，選取到第an＋b個子物件, an的a表示間隔幾個物件

>:nth-last-child, 表示從後往前選

### ()中塞入odd & even
[Codepen](https://codepen.io/gizelliang/pen/vYwogeV)

* 塞入odd, 則選到奇數的子物件
* 塞入even, 則選到偶數的子物件

### 選取特定單一物件時，則可以直接在()中塞入數字

### 間隔跳位選取物件時, 寫3n則表示第3n倍數的物件會被選取到，寫4n則表示4n倍數的物件會被選取到
[Codepen](https://codepen.io/gizelliang/pen/JjqgWPa)

[Codepen](https://codepen.io/gizelliang/pen/ExzqWVR)


