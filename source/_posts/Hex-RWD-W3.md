---
title: Hex_RWD第三週直播
date: 2024-06-11 08:05:51
tags: [HexSchool,Video]
categories: [HTML]
description: 六角學院切版直播第三堂
---
```css
  <!--手機螢幕解析度 reset,讓解析度等同於載具的寬度,建立手機版的環境-->
  <meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
```
>以ＣＳＳ中的順序來決定吃到的樣式，<mark>權重高的選取器</mark>會優先被吃到 **先看權重，再看先後**

* HTML 選擇器 **1分**
* 類別選擇器   **10分**
* ID 選擇器   **100分**
>不要用ID選擇器寫樣式, 因為權重太高樣式很難覆蓋
* inline style 選擇器 **1000分**
* ！important **10000分**

## Can I use?

[Can I use?](https://caniuse.com/)

>過新的技術或是冷門的用法，需要先用Can I use?網站確定是否該瀏覽器有支援

![Image](https://i.imgur.com/dBO7AwA.png)

>市占率要大於<mark>90%</mark>才比較建議使用

## 為何要max-width?
* 若父層空間足夠,才會固定寬度
* 若父層空間不足,max-width會跟隨父層的寬度自適應伸縮（能夠避免出現x軸)
* 通常用在最外層的container, 其他被包裹在其中的子元素較少用到
* 被container包裹在其中的子元素通常是用%來寫寬度,有些小的子元素則可以使用px來寫死寬度

## image為何需要max-width?
```css
img{
    max-width:100%;
    height:auto;

}
```
>width:100%有可能會讓圖片變模糊（隨著螢幕解析度放大),max-width:100%則不會（根據原圖大小的最大值)

* height: auto
Automatically adjusts an element's height based on its content, expanding or contracting to accommodate its size

* max-width
Sets the maximum width of an element, preventing the width property from becoming larger than the specified value. For example, setting max-width to 100% will shrink an image of 500px to fit within a space of 360px.

* setting an image's max-width to 100% and its height to auto can make it responsive and scale down to fit within its container while maintaining its aspect ratio.

<mark>Image的尺寸不一定要照PC版的UI設計稿設計，可以稍微設計大張一點，因為有時候平板是兩張圖一欄呈現，到PC則變成三張圖一欄</mark>

## @media 斷點
```css
@media (max-width:992px) {
	.container{
		padding: 0 15px;
	}
	.news li {
		width: 48%
	}
}
@media (max-width:767px) {
	.news li {
		width: 100%
	}
}

```

>992px以下就開啟其中的樣式，到767px以下就轉換到新的樣式

>改動時，斷點中只要放其中唯一要更動的關鍵語法，不用重複放與PC版相同的語法（意味著code量只會增加10%~30%就算有ipad & 手機的樣式)

>斷點不建議設太多個，大概3~4個算是正常的範圍

![Image](https://i.imgur.com/4vH0kAB.png)

* 桌機    >= 992px（視設計稿而定，有時可能要用到最大的：>= 1400px）
* 平板    768px ～ 991px
* 手機    <= 767px（視設計稿而定，有時可能要用到最小的：< 576px）

```css
.container{
		padding: 0 15px;
	}
```
* 此段語法是因為手機跟平板的版型絕對不能貼齊viewport兩邊，需要有一定寬度的留白（Bootstrap也是會預留15px的留白)

* 透過container來增加留白比較方便，就不用一一針對子元素去做設定

![Image](https://i.imgur.com/Znqaj4B.png)

## 更改軸線(flex-direction) or 超過100%推擠到下一行(flex-wrap:wrap)
[滿版](https://codepen.io/gizelliang/pen/vYwexgM)
[不規則](https://codepen.io/gizelliang/pen/PovJpKw)
### 更改軸線(flex-direction)主要用在不規則的形狀（不像接近滿版的版型)
```css
.header{
	display: flex;
	justify-content: space-between;
	align-items: flex-start;
	padding-top: 20px;
	margin-bottom: 24px;
}
@media(max-width: 992px){
	.header{
		flex-direction: column;
		align-items: center;
	}
}
```
![Image](https://i.imgur.com/Df7mSWP.png)
![Image](https://i.imgur.com/WTN3RZJ.png)

### 超過100%推擠到下一行(flex-wrap:wrap)則用在接近滿版的版型


```html
<div class="main container">
    <div class="content">
      <h2>新聞標題</h2>
      <p>六角學院新聞 (2016-06-21 09:06)</p>
      <p>生藝本技得童總信。上能表有能已位字高企斷他？神些的司……特了又他的，了象大初小研車對加、間四比，想年訴選年：三車寫教。他成濟位像知他氣程表事。聽制起又雲師山，重不能界使我傷！溫統接視情期事……況無沒指超及世。</p>
      <p>
        列文一有愛的空金代電一前卻歡電個魚天讀狀各童流處開起那朋。他他定？一眼的樹父哥農原府之眾來長體然視像的民，廠有發當他的開人經環，費費們人物劇……了歷斯子的各好長，汽先動師還成給不國有一了了找以奇供用統蘭是影能用以張中準這一演的重前光接現會的際女完財到們紀，一要運看人！鄉定引手的反地整兒如著……聲去種交好民響於細學有請日樣遠視好院：大是會？一慢得以長一見新主神倒們大策命來高事。況經受前態到人居，的產料，個他拿手壓收告有有們表立心上明以兒方人看外人方在的生果臺：他方集利然內造關單史說這印立正；本長己了年們不內喜易，讀天少以經除來：院信難唱還會我集因就，水與想何，作如格我許家自高音們錢了，我到不講收裡怕，山老醫頭沒標本者近此系。
      </p>
    </div>
    <div class="sidebar">
      <img src="images/1.jpg" alt="">
      <img src="images/1.jpg" alt="">
      <img src="images/1.jpg" alt="">
    </div>
  </div>
```
![Image](https://i.imgur.com/jZ8X7zZ.png)

```css
.main{
	display: flex;
	flex-wrap: wrap;
	justify-content: space-between;
}
.content{
	width: 75%;
	border:2px solid #000;
	padding: 10px
}
.content h2{
	font-weight: bold;
	font-size: 20px;
	line-height: 1.2;
	margin-bottom: 24px;
}
.content p{
	line-height: 1.5;
	font-size: 16px;
	margin-bottom: 24px;
}
.sidebar{
	width: 20%;
	border:2px solid #000;
	padding: 5px;
}
.sidebar img{
	margin-bottom:10px;
}
 @media(max-width: 992px) {
	.content,.sidebar{
		width: 100%; /* 百分比呈現寬度 */
	}
	.content{
		margin-bottom: 20px;
	}
	.sidebar{
		display: flex;	
		flex-direction: column;
		align-items: center;
	}
	.sidebar img{
		margin-bottom: 10px;
	}
}
```
## 動線設計：並非所有內容都要全部塞到網頁內容

* PC版的內容不用全部都塞到手機版中, 篩選必要的留在手機版中即可

* 這邊額外補充一下，中文內文單行字元 30～40 會比較好閱讀，英文則是 32～80 個字元數

更詳細一點的規範與說明，可以看以下參考連結唷

https://www.ibm.com/design/language/typography/type-basics/

https://www.ibm.com/...ography/type-basics/

## 點擊範圍：設計讓人好點選的元素

* 手指點擊範圍約44px, 所以各個欄位的點選範圍高度都需要至少44px

## 少即是多：避免資訊量爆炸

### PC版
＊ 縮圖
＊ 標題
＊ 局部內文
＊ 其他說明

### 手機版
* 縮圖
* 標題

## 斷點元素：只有手機才會顯示的功能與Layout切換

![Image](https://i.imgur.com/taYekWM.png)

* 768px Ipad直式的解析度