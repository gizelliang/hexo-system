---
title: 第二週補充知識
date: 2024-06-04 22:31:26
tags: [HexSchool,Video]
categories: [HTML]
description: background的用法 & 圖片種類介紹
---
## background-image:url()

```css
.intro-content{
  width:50%;
  background-image:url(../image/Screenshot1.png);
}
/*../代表回到根目錄後，再進入image資料夾中找相對應的檔案*/
```
```html
            <img src="image/facebook-logo.webp" alt="Facebook" srcset="">
/* index.html本來就在root directory, 所以就不需要回到上一層../ */
```
### 資料夾結構
![Image](https://i.imgur.com/KaWU84t.png)
>因為是相對於css stylesheet的image位置，所以跟原本與index.html的相對位置不同，與html的相對位置是直接從根目錄出發，就無需../(回到根目錄)

>瀏覽器預設會將background-image重複渲染出來，除非父層容器大小與image一樣大<mark>(VScode右下角會顯示出單張圖片大小)</mark>

## background-repeat 

* 有些圖片要是整張用<mark>background-image</mark>載入的話，會太大導致網頁載入速度變慢

>這時候就可以使用Photoshop**切片選取工具**,截取部分區塊然後用background-repeat將部分區塊沿著x軸延伸
```css
background-repeat:no-repeat;
```
* 不重複背景

```css
background-repeat:repeat-x;
```
* 沿著x軸重複

```css
background-repeat:repeat-y;
```
* 沿著y軸重複

>background-image會同時延著x軸和y軸一起延伸，若加上<mark>background-repeat:repeat-x or background-repeat:repeat-y</mark>的話就會限制延伸到單一軸上

><mark>background-color</mark>有時候會跟background-repeat & background-image一起連用，background-color是被壓在background-image的下面

## background-position 調整background-image的位置
```html
 <div class="container">
        <div class="intro-content">
            <h1>Lorem ipsum dolor sit.</h1>
            <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quod unde rerum, deleniti ea obcaecati sint hic
                odit dicta tenetur qui ut dolorum provident sit, atque, reprehenderit nulla voluptate! Officiis,
                consectetur?</p>
            <p>Iste ipsa enim delectus porro, ullam repellendus maiores quis rem debitis cum, necessitatibus architecto
                dolor? Velit, ad quaerat blanditiis veritatis expedita totam vel voluptatem officiis officia ab modi
                voluptatibus obcaecati.</p>
            <p>Accusantium minima iusto nobis fuga hic explicabo unde illum, perferendis et animi aperiam quaerat, eaque
                deleniti alias blanditiis exercitationem commodi repudiandae ullam consequatur incidunt reiciendis
                repellat officia laboriosam. Esse, modi.</p>
            <p>Expedita cupiditate iure odit, delectus placeat optio magnam assumenda mollitia aspernatur at saepe nisi
                commodi natus excepturi voluptate. Recusandae nisi dolorem, necessitatibus optio aliquam repellat.
                Adipisci, incidunt. Consequuntur, natus nulla.</p>
                <p>Expedita cupiditate iure odit, delectus placeat optio magnam assumenda mollitia aspernatur at saepe nisi
                    commodi natus excepturi voluptate. Recusandae nisi dolorem, necessitatibus optio aliquam repellat.
                    Adipisci, incidunt. Consequuntur, natus nulla.</p>
        </div>
    </div>
```
```css
.intro-content{
  height:100vh;
  background-image:url(../image/facebook-logo.webp);
  background-color: #ffec00;
  background-repeat:no-repeat;
  background-position:right bottom;
  
}
```
![Image](https://i.imgur.com/u9KRxeV.png)

```css
background-position:left top;
```
* 此為預設位置

### background-position的不同寫法   
```css
background-position: 30px 30px;
/*向左推30px,向上推30px*/
```
```css
background-position:50% 50%;
/*向左推50%, 向上推50%*/
```

## background 縮寫教學

>background是一種複合background-image, background-position, background-color & background-repeat的寫法

```css
 background-image:url(../image/facebook-logo.webp);
  background-color: #ffec00;
  background-repeat:no-repeat;
  background-position:right bottom;
```
* 將上述四個CSS屬性可以合併成下方的程式碼,先後順序可以顛倒，但是每個值中間都要有空格

```css
background: url(../image/facebook-logo.webp) #ffec00 no-repeat right bottom;
```
## 圖片取代文字技巧 

```html
<div class="header">
        <h1>
            <a href="#">Hex School</a>
        </h1>
        <ul>
            <li>1</li>
            <li>2</li>
            <li>3</li>
        </ul>
</div>

```
```css
.header h1 a{
     background-image:url();
     /*將a從inline轉成block後才可以設定寬高,background-image也才有辦法顯示出來*/
     /*此處的width & height都設定為background-image logo的寬高*/
     width: 200px;
     height:200px;
     display:block;
     /*為了SEO, a連結內必須要有字,將其中的文字縮排且不換行到父層容器外，再將其隱藏*/
    text-indent:101%;
    white-space:nowrap;
    overflow:hidden;
}
```
## 圖片種類介紹 ( gif、jpg、png )

* gif
1. 有動畫的圖片
2. 有支援透明的背景
3. 與png-8一樣，僅支援256色

* jpg
1. 沒有動畫效果
2. 沒有支援透明的背景(無法設定background-color)

* png-24 & png-8
1. png-8僅支援256色 png-24支援的顏色較豐富
2. 有支援透明效果(可以設定background-color)
