---
title: 互動圖文卡片 NO002
date: 2024-06-10 11:45:17
tags: [Youtube,Video,Book]
categories: [HTML]
description: Amos Youtube Video & CSS屬性第七章(定位) & 第九章(其他重點)
---
[Codepen Example](https://codepen.io/gizelliang/pen/NWOaaad)

## 如何消除image下方與區塊元素的空白間隔？
[Image設定Vertical-align:middle](https://qoo8857300.medium.com/css-%E5%A6%82%E4%BD%95%E8%A7%A3%E6%B1%BAimg%E7%9A%84%E5%9E%82%E7%9B%B4%E5%B0%8D%E9%BD%8A-a3dcd6c47a4)

>Image本身為inline的特性，會讓他無法與下方的區塊元素貼齊,故須設定vertical-align:middle 或是display:block

## 定位
>定位就是控制物件在畫面當中要依據誰來做對齊，或者說要依據誰來做位置的排列
### position:static

* 此為預設樣式，不需特別設定,該元素z-index層級不會因此提高
* 作用是將<mark>其他定位取消，回到最原始的狀態</mark>

### position:relative

* 不會將物件獨立一層，仍會<mark>參考原始的資料流位置，搭配top,bottom,left, right來達到顯示位置的偏移</mark>

>相對定位可以被視為一種偏移顯示

* 也可搭配z-index來做使用，z-index越大者就可以覆蓋在z-index較小者之上,所有元素的z-index皆預設為0

>單純設定position:relative就會使該元素z-index值較高（而會覆蓋其他元素)

>前後物件都有設定position:relative時，原始碼中後方的物件會覆蓋前方的物件

[Position:Relative](https://codepen.io/gizelliang/pen/eYaVYQq)

### position:absolute
* 獨立一層，不會參考原始的資料流位置,<mark>會因為卷軸捲動而消失</mark>
* 也可搭配top,bottom,left,right來做顯示位置的偏移，但會根據最靠近的containing block來做偏移，預設的containing block為viewport(若外層沒有任何元素設定position的話)

> containing block通常是代表在父層上設定除了position:static以外的定位值<mark>有時候不是直接父層，甚至是包裹在最外層的container</mark>

>containing block就等同於position:absolute的父層，所以有設定position:absolute的子層也會以containing block作為寬度的基準

* 除非在RWD中，不然盡量避免使用position:absolute

### position:fixed 
* position:fixed通常用在header, 使該區塊固定在viewport最上方，不會因為卷軸捲動而消失

* 被設定的position:fixed元素一樣會獨立一層且永遠固定在視窗範圍內

>position:fixed的containing block會一直都是<mark>viewport</mark>

[position:fixed](https://codepen.io/gizelliang/pen/GRaQgXP)
>position:fixed也可達到垂直置中，且會一直出現在viewport的正中央

### 補充垂直置中
[absolute + margin auto](https://ithelp.ithome.com.tw/articles/10202245)

### position:sticky
* 預設定位在資料流中
* 捲動到position:sticky物件時, 才會根據其設定的top值來呈現
* 呈現fixed效果時，所能fixed的僅僅為該物件的父層空間
* 超過父層空間時，就會被捲軸捲走
[position:sticky](https://codepen.io/gizelliang/pen/zYQRvPg)
<!--position:sticky若是被position:flex包覆時，效果會消失（主要是因為預設為align-items:stretch)，因為無法定位在該containing block的最上方，除非自身下align-self:start,讓position:sticky的高度縮小到與內文一樣-->

![Image](https://i.imgur.com/ALuxDN7.png)

## 水平置中 & 垂直置中的原理（position:absolute & position:fixed)
[水平置中](https://codepen.io/gizelliang/pen/GRaQomB)

* position:absolute & position:fixed會獨立一層,在尚未設定top,right,bottom,left以前,無法預測有多少空間可以供<mark>margin:auto</mark>自由分配, 一旦設定了,<mark>就可做到水平/垂直置中</mark>
## 沒有設定寬高時，利用width:auto, height:auto & position來做到蓋板廣告/燈箱效果
```css
div{
    position:absolute;
    background:red;
    top:30px;
    left:30px;
    bottom:30px;
    right:30px;
}
```
[蓋板廣告](https://codepen.io/gizelliang/pen/OJYQMOr)

## z-index
## Opacity
## Transition