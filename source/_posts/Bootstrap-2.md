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

## 自定義通用類別（node_modules資料夾中將_utilities.scss複製後移到自己的stylesheets>helpers資料夾中）
```css
$utilities: (
  "opacity": (
    /* 此處會對應到最後輸出的class名稱首字*/
    property: opacity,
    /*此處會對應到大括號中的屬性*/
    values: (
      0: 0,
      25: .25,
      50: .5,
      75: .75,
      100: 1,
    /*此處會對應到屬性的值及class名稱的結尾*/
    )
  )
);
```
```css
.opacity-0 { opacity: 0; }
.opacity-25 { opacity: .25; }
.opacity-50 { opacity: .5; }
.opacity-75 { opacity: .75; }
.opacity-100 { opacity: 1; }
```
### 運用class屬性來縮寫

```css
$utilities: (
  "opacity": (
    property: opacity,
    class: o,
    values: (
      0: 0,
      25: .25,
      50: .5,
      75: .75,
      100: 1,
    )
  )
);
```
```css
.o-0 { opacity: 0 !important; }
.o-25 { opacity: .25 !important; }
.o-50 { opacity: .5 !important; }
.o-75 { opacity: .75 !important; }
.o-100 { opacity: 1 !important; }
```
### 運用responsive:true來將中斷點加入

```css
$utilities: (
  "opacity": (
    property: opacity,
    responsive: true,
    values: (
      0: 0,
      25: .25,
      50: .5,
      75: .75,
      100: 1,
    )
  )
);
```
```css
.opacity-0 { opacity: 0 !important; }
.opacity-25 { opacity: .25 !important; }
.opacity-50 { opacity: .5 !important; }
.opacity-75 { opacity: .75 !important; }
.opacity-100 { opacity: 1 !important; }

@media (min-width: 576px) {
  .opacity-sm-0 { opacity: 0 !important; }
  .opacity-sm-25 { opacity: .25 !important; }
  .opacity-sm-50 { opacity: .5 !important; }
  .opacity-sm-75 { opacity: .75 !important; }
  .opacity-sm-100 { opacity: 1 !important; }
}

@media (min-width: 768px) {
  .opacity-md-0 { opacity: 0 !important; }
  .opacity-md-25 { opacity: .25 !important; }
  .opacity-md-50 { opacity: .5 !important; }
  .opacity-md-75 { opacity: .75 !important; }
  .opacity-md-100 { opacity: 1 !important; }
}

@media (min-width: 992px) {
  .opacity-lg-0 { opacity: 0 !important; }
  .opacity-lg-25 { opacity: .25 !important; }
  .opacity-lg-50 { opacity: .5 !important; }
  .opacity-lg-75 { opacity: .75 !important; }
  .opacity-lg-100 { opacity: 1 !important; }
}

@media (min-width: 1200px) {
  .opacity-xl-0 { opacity: 0 !important; }
  .opacity-xl-25 { opacity: .25 !important; }
  .opacity-xl-50 { opacity: .5 !important; }
  .opacity-xl-75 { opacity: .75 !important; }
  .opacity-xl-100 { opacity: 1 !important; }
}

@media (min-width: 1400px) {
  .opacity-xxl-0 { opacity: 0 !important; }
  .opacity-xxl-25 { opacity: .25 !important; }
  .opacity-xxl-50 { opacity: .5 !important; }
  .opacity-xxl-75 { opacity: .75 !important; }
  .opacity-xxl-100 { opacity: 1 !important; }
}
```

## 使用 Bootstrap 方法，產生獨立元件
### 若要透過變數來產生一個新的樣式的按鈕的話
1. 新增$theme-colors裡面的屬性跟值,可以套用到所有的地方

```css
$theme-colors: (
  "primary":    $primary,
  "secondary":  $secondary,
  "hex": #69F0AE,
  "success":    $success,
  "info":       $info,
  "warning":    $warning,
  "danger":     $danger,
  "light":      $light,
  "dark":       $dark
);
```
```html
<button type="button" class="btn btn-primary">這是按鈕</button>
<button type="button" class="btn btn-hex">這是按鈕</button>
```

2. 只想要在特定的元件使用客製化的屬性跟值(Buttons to Mixins)

* 需要在**stylesheets**中創建一個新的**components**資料夾來存放
**_customs-buttons.scss** (前方的下底線會讓scss不被編譯出來)
* 需要在**all.scss**中引入
```css
@import "./components/custom-buttons";
```
* **_customs-buttons.scss**中的@include寫法如下，才可以將色彩引入
```css
.btn-custom-hex{
  @include button-variant(#69F0AE,#69F0AE)
}

.btn-outline-hex{
    @include button-outline-variant(#69F0AE,#69F0AE)
}
```

#### 官網文件寫法參考
```css
 @each $color, $value in $theme-colors {
  .btn-#{$color} {
    @include button-variant($value, $value);
  }
}

@each $color, $value in $theme-colors {
  .btn-outline-#{$color} {
    @include button-outline-variant($value);
  }
}
```

## 在 Sass 中，自訂高可用性的元件

![Image](https://i.imgur.com/Nd7mLPN.png)
* **_utilities.scss & _variables.scss**為變數檔，主要放在stylesheets>helpers資料夾中

>定義元件時，需預期該元件是可以重複利用的

![Image](https://i.imgur.com/AaVBLIF.png)

>建立完元件後，需在**all.scss**資料中將其引入

![Image](https://i.imgur.com/3USjqgK.png)

* 在編寫元件的SCSS時，須避免過度巢狀 & 盡量多使用變數
* 各元件的SCSS中所編寫的變數只能在該元件的SCSS中使用，若要整個專案都能使用的話，就編寫在stylesheets>helpers>_variables.scss中

* 統一把狀態(hover, active)編寫在scss檔案中的最下方