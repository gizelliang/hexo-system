---
title: Hex-RWD-W4
date: 2024-07-03 07:32:50
tags: [HexSchool,Video]
categories: [HTML]
description: 六角學院切版直播第四堂+SCSS筆記+週三助教文字講解
---

## Layout

* 共通版型，出現在多個網頁上
![Image](https://i.imgur.com/UpRfJRC.png)
* ejs 版型控制語言
    * EJS檔案是可以自行新增的
### EJS引入方式
```html
    <%- include('./layout/header'); -%>

```
https://cacoo.com/diagrams/QHmZu18tdwZZG3qJ/CD531

![Image](https://i.imgur.com/b3XuPBn.png)

### index.html 中不能改動

```html
<script type="module" src="../main.js"></script>
```
### assets 靜態資源
>包含SCSS & Images

## SCSS
[投影片資源](https://docs.google.com/presentation/d/11-HFPxkmVj5b6WP50zkKB_GtccvynUu3GaDeALaLpd0/edit#slide=id.p152)

* @import時,variables必須要寫在最上面，因為要符合SCSS的編譯順序,接著是reset, layout & pages的scss檔案
* 有下底線的scss檔案，都不會被編譯出css
* Prepros是scss的編譯器，會將scss轉換成css

### SCSS常見巢狀寫法

```scss
.header{
    width:50px;
    height:50px;
    background:#000;
    ul{
        width:500px;
    }
    li{
        height:30px;
        a{
            color:#000;
        }
    }
}
```
### 變數寫法
```scss
$linkcolor:#000;
$font-m:16px;
$font-l:$font-m*1.2;
$font-s:$font-m*0.8;
```
### @mixin: 將常用語法化簡為自己的知識庫

>@mixin幫助記住ＣＳＳ技巧，讓你不用再因回想原理而中斷思緒

```scss
@mixin hide-text{
    text-indent:110%;
    white-space:nowrap;
    overflow:hidden;
}
```
>@include 會將上述@mixin語法複製，然後貼在引用的地方
```scss
.header h1{
  @include hide-text;
}
```
### @mixin代入變數的寫法

```scss
@mixin circle($size,$bgcolor){
    border-radius:50%;
    height:$size;
    width:$size;
    font-size:$size/3;
    background:$bgcolor;
}

.white {
    @include circle(30px,#fff)
}
```
![Image](https://i.imgur.com/bR7Cf7z.png)

### @content簡化RWD的寫法

* ＠mixin有點像假設出一個media query的代名詞(pad, iphone,tablet......etc),這個media query的代名詞可以用@include代入，@content則是將media query中的內容帶入@mixin中

```scss
@mixin iphone5{
    @media (max-width:320px){
        @content;
    }
}

.header{
    width:100px;
    height:100px;
    @include iphone5(){
        height:30px;
    }
}
```
![Image](https://i.imgur.com/5GZ3Odl.png)

### Sass 7-1 Pattern 中的 7-1 代表著七個資料夾以及一個檔案，基本上就是為了方便區分 Sass。

* base
    * _reset.scss
    * _base.scss
    * _fontStyle.scss
* components
    * _button.scss
    * _dropdown.scss
    * _alert.scss
* layout
    * _header.scss
    * _footer.scss
    * _nav.scss
* pages
    * _index.scss
    * _content.scss
* themes
    * _theme.scss
    * _admin.scss
* utils: 通常都是放一些工具類型的檔案，例如 p-1、mt-10 這類的生成工具
* vendors
* 主要引入的檔案: all.scss or main.scss

