---
title: Bootstrap 環境建置
date: 2024-07-15 14:54:55
tags: [HexSchool,Video]
categories: [HTML]
description: 六角學院預錄
---
## Bootstrap基本介紹

* **Bootstrap 5**可以與Bootstrap 5 分離導入

* **Utilities 通用類別** & **Helpers 工具** 是針對元件的一些擴增

[官方原文 Bootstrap](https://getbootstrap.com/)

[六角學院繁體中文版本](https://bootstrap5.hexschool.com/)

[VS Code 參考套件](https://www.casper.tw/development/2020/12/13/vscode-extension/)

## 語系設置與 Bootstrap CDN

![Image](https://i.imgur.com/RadQKcv.png)
[語系設置的英文代碼](https://www.iana.org/assignments/language-subtag-registry/language-subtag-registry)

```html
<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.1/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-F3w7mX95PdgyTmZZMECAngseQB83DfGTowi0iMjiWaeVhAn4FJkqJByhZMI3AhiU" crossorigin="anonymous">
</head>
<body>
<p lang="zh-Hant-TW">骨花學崎雨</p>
<p lang="zh-Hant-HK">骨花學崎雨</p>
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.1/dist/js/bootstrap.bundle.min.js" integrity="sha384-/bQdsTh/da6pkI1MST/rWKFNjaCP5gBSY4sEBT38Q/9RBh9AH40zEOg7Hlq2THRZ" crossorigin="anonymous"></script>
</body>
</html>

```

## data-bs & 切換 & 方法

* 出現這些字眼時，通常都與Javascript有關

## Bootstrap Javascript 的CDN
* Bundle 的CDN:直接整合了popper
```html
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.1/dist/js/bootstrap.bundle.min.js" integrity="sha384-/bQdsTh/da6pkI1MST/rWKFNjaCP5gBSY4sEBT38Q/9RBh9AH40zEOg7Hlq2THRZ" crossorigin="anonymous"></script>
```
* Separate的CDN:未整合popper

```html
<script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.10.1/dist/umd/popper.min.js" integrity="sha384-W8fXfP3gkOKtndU4JGtKDvXbO53Wy8SZCQHczT5FMiiqmQfUpWbYdTil/SxwZgAN" crossorigin="anonymous"></script>
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.1/dist/js/bootstrap.min.js" integrity="sha384-skAcpIdS7UcVUC05LJ9Dxay8AXcDYfBJqt1CJ85S/CFujBsIzCIv+l9liuYLaMQ/" crossorigin="anonymous"></script>
```
## box-sizing:border-box

* **padding** 原本是外距，但加上**box-sizing:border-box** 後就變成內距

* **margin** 自始至終都維持向外推，不影響到容器本身的寬度

* Bootstrap中原本就有預設**box-sizing:border-box**, 即padding & margin不會影響到容器的整體寬度

## CSS Variables

* CSS Variables通常會定義在根部，根部上也通常只會定義變數，不會撰寫其他的CSS

```css
:root{
    --primary:#69F0AE;
}

.bg-primary{
    background-color:var(--primary);
}
```
>定義在根部時(:root),就代表是定義在全域上,不管在父層或子層的元素都可以直接套用, 變數寫法開頭為--, 用var()代入

### 區域變數重新定義CSS Variables來截斷全域變數的效果

>用local重新定義同一個背景色的變數來覆蓋原本根部的變數

```html
<div class="local">
   <div class="box bg-primary"></div>
  </div>
```
```css
:root{
    --primary:#D2D2D2 !important;
}

.box{
    width:200px;
    height:200px;
    padding:20px;
    margin-bottom: 30px;
    box-sizing:border-box;
}

.bg-primary{
    background-color: var(--primary);
}

.local{
   --primary: orange;
}
```
![Image](https://i.imgur.com/Q3P8hzn.png)
>導入Bootstrap時，無法利用這種寫法來直接覆蓋在Bootstrap中預設的primary顏色

## rem & em 的比較

* rem從頭到尾都以網頁預設的16px為基數
* em則會子層繼承父層的基數
```html
    <div class="em2">
        How are you?
        <strong class="em2">lorem</strong>
    </div>

    <div class="rem2">
        Who are you?
        <strong class="rem2">Lorem</strong>
    </div>
    <!--父層子層皆為32px-->
```
>rem2 父層子層皆為32px

>em2 父層為32px, 子層為16px x 2 x 2 = 64px
![Image](https://i.imgur.com/NaBZBP4.png)

* 若要更改網頁預設的16px, 可以用:root or html 來改寫

```css
html{
            font-size: 20px;
        }
```

```css
:root{
    font-size:20px;
}
```

> 使用body來定義最外層的文字大小時，只有em才會採計，rem不會，rem只參考:root & html的文字大小

>結論：rem相較em來得穩定，所以比較常使用在實務上
## 系統預設字體
![Image](https://i.imgur.com/LKJBlao.png)

>Bootstrap字體以英文字體為主，中文字體要手動載入

![Image](https://i.imgur.com/zQvOU7F.png)

## Bootstrap Reboot & CSS Reset

* **Bootstrap Reboot** 即Bootstrap CSS的預設樣式
    * 預設字體，字體大小，行間距
    * 套用box-sizing:border-box
    * 套用list的Normalize Reset樣式
    * 可以在Google開發者工具中的:root 尋找變數色彩