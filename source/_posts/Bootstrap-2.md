---
title: Bootstrap-2
date: 2024-08-26 19:35:19
tags: [HexSchool,Video]
categories: [HTML]
description: Bootstrap 與神奇的 Sass
---
## Bootstrap 與 Sass 的關係
* Bootstrap本身就是使用Sass預處理器來進行開發的
* Sass or Scss 皆屬於Sass預處理器可以編譯的
* Bootstrap 這麼大框架的原始檔案是由許多小元件組成, Sass編譯器才能將這些小元件組成CSS,並且能夠在瀏覽器上運行

### CSS是否需要前綴詞？-webkit-,-moz-,-o-,-ms-
>Ｓass可搭配PostCSS 自動自動修正前綴詞
### 變數的調整去客製化各個網站樣式的色彩及款式
### 相同結構去重複利用

## 在 VSCode 中加入 Sass 環境

1. 先安裝Live Sass Compiler
2. 安裝完後下方應該會出現**Watch Sass**, 若沒有則就是沒有Sass
3. 編輯CSS都是在scss檔案中撰寫,再透過**Watch Sass**編譯成CSS

##  匯入 Bootstrap 並調整樣式
1. 直接使用下載的方式將Bootstrap加入專案中(將**原始檔案**載入到專案中)
2. 運用npm的方式去下載(**npm init + npm install bootstrap**)
 * 下載完後，用下方程式碼引入專案中
 ```scss
@import "../node_modules/bootstrap/scss/bootstrap";
 ```
 * 到node_modules資料夾中去找**bootstrap>scss>_variables.scss**, 找到
 **_variables.scss**後將其給複製到專案中的stylesheets資料夾中

![Image](https://i.imgur.com/yUJWnQe.png)

* 接著一樣需要將**variables**引入，但通常是在引入**functions**之後

## 如何只載入Bootstrap中的部分元件 (Optimize)
[官方文件連結](https://getbootstrap.com/docs/5.2/customize/optimize/)
* 官方文件中,Optimize的Configuration為必須要載入的

```scss
// Configuration
@import "functions";
@import "variables";
@import "maps";
@import "mixins";
@import "utilities";
```
* 可以刪去部分元件，但前三個需要保留，因為這三個為Bootstrap的預設值

> 以下為Bootstrap中比較常用到的部分

```scss
// Layout & components
@import "root";
@import "reboot";
@import "type";
@import "images";
@import "containers";
@import "grid";
@import "tables";
@import "forms";
@import "buttons";
// Helpers
@import "helpers";

// Utilities
@import "utilities/api";
```
##  修改特定的元件的變數 (Layout to Grid to Sass Variables)
[官方文件連結](https://getbootstrap.com/docs/5.2/layout/grid/#variables)

1. 在Bootstrap **_variables.scss**中搜尋radius就可更改圓角的值
2. 在Bootstrap **_variables.scss**中搜尋特定模組/元件去調整其設定值

```scss
$grid-columns:      12;
//預設就是12欄，通常不會修改這個值
$grid-gutter-width: 1.5rem;
$grid-row-columns:  6;
```
>若有動到預設值的話，不將預設值移除，用//預設值隱藏後，用**custom**這個單字代表有做客製化的設定, 之後若要調整回來的話，就搜尋**custom**

```scss
$border-radius: 1rem; //0.25rem !default ; custom
```

>按鈕 & input要視為一個群組，所以radius值要調整成一樣

### 修改$spacer來增加新的間鉅值

```scss
$spacer: 1rem;
$spacers: (
  0: 0,
  1: $spacer * .25,
  2: $spacer * .5,
  3: $spacer,
  4: $spacer * 1.5,
  5: $spacer * 3,
  //預設值最大就是5, 空間就是$spacer*3
);
```
```html
<a href="#" class="btn btn-primary me-5">我是按鈕</a>
<a href="#" class="btn btn-primary">我是按鈕</a>
```
## Bootstrap 隱藏功能開關！(Customize to Options)
>有很多隱藏的功能開關都在Customize to Options的官方文件中,列出所有可修改的變數
### Background Gradient (Utilities to Background) 漸層背景色
* 需將 **_variables.scss** 中 **$enable-gradients的值改成true**

### 陰影效果
* 需將 **_variables.scss** 中 **$enable-shadows的值改成true**

### 漸變的視覺效果
* 需將 **_variables.scss** 中 **$enable-transition的值改成true**

### 負值的margin
* 需將 **_variables.scss** 中 **$enable-negative-margins的值改成true**

## RFS 響應式文字縮放 
* 需將 **_variables.scss** 中 **$enable-negative-margins的值改成false**來關掉功能

```css

.title {
  @include font-size(4rem);
}

.title {
  font-size: calc(1.525rem + 3.3vw);
}

@media (min-width: 1200px) {
  .title {
    font-size: 4rem;
  }
}
```

>使文字大小隨著視窗縮放來放大縮小

## 自定義通用類別
