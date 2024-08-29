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

## 文字運用
### h1~h6作為語意化標籤及單純樣式

>若不想要套用h1~h6的語意，單純只想要用樣式，就可以將其用作class來帶入

```html
<div class="demo">
  <p class="h1">h1. Bootstrap heading</p>
  <p class="h2">h2. Bootstrap heading</p>
  <p class="h6">h3. Bootstrap heading</p>
  <p class="h4">h4. Bootstrap heading</p>
  <p class="h3">h5. Bootstrap heading</p>
  <p class="h3">h6. Bootstrap heading</p>
</div>
```
### 將文字<small>變小</small>
```html
<small></small>
```
### display-1~display-6作為class來帶入
```html
<div class="demo">
  <h1 class="display-6">Display 1</h1>
  <h1 class="h6">Display 2</h1>
  <h1 class="display-5">Display 3</h1>
  <h1 class="h5">Display 4</h1>
  <h1 class="display-3">Display 5</h1>
  <h1 class="h3">Display 6</h1>
</div>
```
![Image](https://i.imgur.com/DheuSAk.png)

### 前導文本
```html
<div class="demo">
  <p>
    <span class="lead">
    This is a lead paragraph. It stands out from regular paragraphs.
  </span>
  Lorem ipsum dolor, sit amet consectetur adipisicing elit. Vel, quasi omnis eos magnam perspiciatis cupiditate iusto aspernatur harum deleniti mollitia libero, ab repudiandae maiores? Nisi atque ex alias impedit laboriosam.
</p>
</div>
```
![Image](https://i.imgur.com/FO3bXbE.png)

### 行內<del>文本</del><ins>元素</ins>
```html
<div class="demo">
  <p>You can use the mark tag to <mark>highlight</mark> text.</p>
  <p><del>This line of text is meant to be treated as deleted text.</del></p>
  <!--線從文字上橫槓-->
  <p><ins>This line of text is meant to be treated as an addition to the document.</ins></p>
 <!--文字下底線-->
  <p><small>This line of text is meant to be treated as fine print.</small></p>
  <p><strong>This line rendered as bold text.</strong></p>
  <p><em>This line rendered as italicized text.</em></p>
  <!--<s></s> & <u></u> 已經不太常使用-->
</div>
```
### <abbr>縮寫標籤</abbr>
#### title ="" 表示鼠標停留時顯示出的內容
#### class="initialism"表示字比縮寫更小

```html
<div class="demo">
  <p><abbr title="attribute">attr</abbr></p>
  <p><abbr title="HyperText Markup Language" class="initialism">加入 initialism</abbr></p> 
</div>
```

### 引用 & 引用細節

```html
<div class="demo">
  <figure>
    <blockquote class="blockquote">
      <p>A well-known quote, contained in a blockquote element.</p>
    </blockquote>
    <figcaption class="blockquote-footer">
      Someone famous in <cite title="Source Title">Source Title</cite>
    </figcaption>
  </figure>
</div>
```
### list-inline & list-inline-item 帶入class

>將列表轉成行內元素

### class="text-start" or "text-end" 對齊(start 左邊，end 右邊)
```html
<div class="demo">
  <figure class="text-start">
    <blockquote class="blockquote">
      <p>A well-known quote, contained in a blockquote element.</p>
    </blockquote>
    <figcaption class="blockquote-footer text-end">
      Someone famous in <cite title="Source Title">Source Title</cite>
    </figcaption>
  </figure>
</div>
```
![Image](https://i.imgur.com/XrZMIwZ.png)

### class="text-truncate" 
>將過長的文字截斷

## 圖片運用
### class="img-fluid"

>使圖片能夠自適應裝置大小

### class="rounded"

>圖片有圓角

### class="img-thumbnail"

>有1px 邊框的圖片縮略圖

[Codepen Example](https://codepen.io/gizelliang/pen/MWMoZda)

### class="clearfix"下在父層，class="float-start" & "float-end"在子層的連用
[Codepen](https://codepen.io/gizelliang/pen/gONRZVQ)

### 圖片本身加class="d-block mx-auto" 水平置中
[Codepen](https://codepen.io/gizelliang/pen/eYwRxYz)

>image預設的屬性為**display:inline-block**, 可以用**text-center**加在父層來置中
[Codepen](https://codepen.io/gizelliang/pen/jOjwdPE)

## 圖片區 (figure & figcaption)

```html
<figure class="text-end figure">
  <img src="https://picsum.photos/900/700/" >
  <figcaption class="figure-caption">Deep Blue Sea</figcaption>
  </figure>
```
