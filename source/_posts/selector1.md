---
title: CSS優先權 & 基本類型CSS選取器
date: 2024-05-21 15:24:43
tags: [Amos,Book]
categories: [HTML/CSS]
description: 金魚都能懂的CSS選取器第一章+第二章 & 六角 div 與後代選擇器運用
---
## CSS優先權

1. 選取器之間的優先權
2. 屬性之間的優先權 (@keyframes)

>重複性狀況發生時，最終要套用的是哪個的機制與準則

* 相同選取器下，**後者優於前者**

<mark>inline style >ID>class>tag</mark>

### 父層繼承而來的屬性
* 某些CSS屬性也是可以藉由父層繼承而來，例如:文字樣式，通常這樣**繼承而來的屬性**優先權是最低的

### !important 屬性後方的選取器
* 盡量避免使用，因為優先權遠高於其他選取器，維護上會有很多困擾

### * 號通用選取器
* *號通用選取器的優先權也僅僅高於繼承而來的屬性，是倒數第二低的

### 屬性選取器與類別選取器
* 兩者為同樣優先權,以先後順序來決定
```css
[class]{
    color:"red";
}

[class="info"]{
    color:"blue";
}

.info {
    color:gray;
}
```

### @keyframes 動畫執行期間的優先權

* 關鍵影格(@keyframes)中的動畫在執行期間具有絕對的優先權（僅次於!important), 執行完畢後會退到下一階的優先權

<mark>!important > @keyframes > inlines style > ID > class & 屬性選取器 > tag選取器 > * 通用選取器 > 繼承的屬性</mark>

## Tag 選取器
>CSS reset 是透過tag選取器來將各家瀏覽器的樣式統一

>通常CSS reset會跟網站基礎樣式一起寫在CSS的最前面，Tag選取器通常就是用來寫網站的基本視覺外觀
## Class 選取器
### 命名原則
1. 首字不能是數字
2. 首字可以是中線，或是下底線，除此之外都不行
3. 相同字母大小寫不同，則區分為不同命名

>藉由有系統的分類命名方式，來達到只看class名稱就能理解該物件的用途
>(OOCSS, SMACSS)

## ID選取器
>ID選取器命名規則與Class選取器相同

* 同個ID名稱在同個頁面只能出現一次, 但就算有相同ID名稱的物件出現在同一個網頁上，也都會正常的對畫面做處理

* 同個物件不能放兩個ID名稱

>使用上較class選取器自由度低，所以不太常用

```html
<div id= "amos">Where are you?</div>
```
```css
#amos{
    color:red;
}
```
## CSS群組式宣告(使用半型逗號來隔開)
>運用半形逗號將不同的選取器隔開，來達到共用CSS樣式的目的，以減少太多重複的原始碼

```css
.news-list,
.event-list{
    border:10px;
    padding:20px;
}
```
>最後一個選取器的右側不可出現逗號，會導致選取器失效

## CSS組合式宣告

>將同一個目標對象的多個選取器一起選取，且中間沒有空格,代表只有同時符合的物件才會被選到
```html
<p clas="amos" id="handsome"></p>
```
```css
p.amos#handsome{

}
```

## 擬態選取器 :hover, :active
* :hover是滑鼠滑過去的效果,:active是滑鼠按著不放的效果

## 後代選取器 (Descendant Selector)

>與組合式宣告不同，每個選取器中間要有空格，同一組選取器前後的關係為選到被某一父層所包覆的子物件，而非組合式宣告為選到有多個選取器的同一物件
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
/*被.style1所包覆的a*/
.style1 .content{
    font-weight:bold;
}

```
<mark>後代選取器最多不可寫超過兩層, 不然效能會被認為太差</mark>

## CSS屬性選取器
>選取到擁有特定HTML屬性的物件

1. **[屬性=值]**, 此種寫法需要HTML中<mark>對應屬性的值</mark>與此選取器的值完全一致才可以選得到
```css
img[alt="Pretty Lady"]{
    ...
}
``` 
2. **[屬性^=值]**, 此種寫法只要HTML中<mark>對應屬性的開頭</mark>與此選取器中的值相同即可

3. **[屬性$=值]**, 此種寫法是選取HTML中結尾等於特定文字/字串的物件
```css
a[href$=".png"]{
    background-image:url("icon-png.png");
}
```
<mark>若要不分檔名大小寫皆可選到，需要多加一個i</mark>

```css
a[href$=".png" i]{
    background-image:url("icon-png.png");
}
```
4. **[屬性*=值]**, 代表只要HTML中對應屬性的值有包含特定文字即可，不用管到底是開頭還是結尾

```html
<img src="" alt="我的貓">
```
```css
img[alt*="我"][alt*="貓"]{
    display:none;
}
```
5. **[屬性~=值]**, 此選取器針對英文，代表包含特定單字而非字串

[文章參考連結](https://www.thisweb.dev/post/css-specificity)