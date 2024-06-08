---
title: 字體設定全攻略
date: 2024-06-05 11:51:31
tags: [HexSchool,Video]
categories: [HTML]
description: font-family, font-weight & Google 雲端字體
---
## Win、Mac 內建字體介紹
* Windows
    * 中文：新細明體(Default), 微軟正黑體,標楷體
    >業界開發比較少使用新細明體，通常比較常使用微軟正黑體
    * 英文: Segoe UI（Default）
* Ｍac
    * 中文: 蘋方繁(Default)
    >切版時，就算該作業系統沒有UI設計稿指定的字體，也可以直接切換用預設的，不用特地安裝該字體
## font-family 載入內建字體
```css
h1{
    color:blue;
    font-family:Apple LiGothic, Apple LiSung;
}
```
* font-family可以設定多於一個的字體，若第一個沒吃到就會載入第二個

* 載入外部字體時，可以用“”或是''包覆

## font-weight的數值對照

* font-weight:400 相當於 font-weight:normal

* 寫數字比較好調整，相較於英文單字

* font-weight最大值為900, font-weight:700為標準定義的font-weight:bold

* 微軟正黑體只有三種設定值，Light(300), Regular(400) & Bold(700)

## 如何安裝字體到本地端的字體簿？
[字體下載網站]（https://developer.apple.com/fonts/）

* Ｍac電腦上，下載到本地端後可以在字體簿<mark>Font Book App</mark>中找到

* 中文字體的話，就有包含數字/英文/中文
* 英文字體的話，只有包含英數

## 如何載入Google雲端資料庫的字體？

[思源中文黑體Google雲端免費商業授權](https://fonts.google.com/noto/specimen/Noto+Sans+TC)
[Roboto＿英文雲端字體](https://developer.apple.com/fonts/)

```SCSS
<style>
/*SCSS導入*/
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+TC:wght@100..900&display=swap');
</style>
/*載入font-weight:100~900的字體*/
```
```html
<!--放置在<head></head>中-->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Noto+Sans+TC:wght@100..900&display=swap" rel="stylesheet">
```

## 如何規劃字體配置？
>除了針對Mac以外，也要同時設定預設的字體給Microsoft作業系統
```css
body{
    font-family:"SF Pro Text", "Microsoft JhengHei";/*微軟正黑體*/
}
```

## 系統預設文字統一設定

```css
body {
    font-family: -apple-system, BlinkMacSystemFont,
    /* Mac字體*/
    "Segoe UI", /*Windows預設英文字體*/
    "Microsoft JhengHei",
    /* Windows預設中文字體*/
    Roboto
    /*Android內建字體*/
    , "Helvetica Neue",
    /*IOS內建字體*/
    Arial, sans-serif;
    /*通用字體*/
}
```
## 補充資源
[font-family用法解說](https://www.oxxostudio.tw/articles/201811/css-font-family.html)

[Google Font 文字版筆記](https://hackmd.io/@YmcMgo-NSKOqgTGAjl_5tg/HJpJk8ABU/https%3A%2F%2Fhackmd.io%2F2nenMilfR7WSJSDI4WzcWA%3Fview)

[卡斯柏＿系統字體介紹](https://www.casper.tw/design/2018/10/25/fonts/)

