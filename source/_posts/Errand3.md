---
title: Errand3
date: 2024-07-02 20:01:37
tags: [HexSchool,Video]
categories: [HTML]
---
![Image](https://i.imgur.com/96hW8WI.png)

![Image](https://i.imgur.com/PV6umqW.png)

### 複習 container 的計算以及 container 的 RWD 設定

**桌機版 container：**

依照第一週計算 container 的方法，我們可以得知在桌機版的時候， container 會是以下設定：

```css
.container {
  max-width: 1296px;
  margin: 0 auto;
}
```
現在，有個重點來囉~ 

我們要請同學幫 container ，增加左右邊的一些留白。
讓裝置的螢幕比較窄的時候，網頁的內容比較不會太貼近邊緣。

左右邊的 padding 值通常會設定為 gutter 的一半。
也就是說，假如設計稿上 gutter 的數值為 24，那 container 的左右 padding 就可以設定 12px。