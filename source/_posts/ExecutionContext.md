---
title: 執行環境與作用域
date: 2024-08-22 23:14:59
tags: [HexSchool,Video]
categories: [Javascript]
description: Javascript 核心篇
---
## 直譯式語言 & 編譯式語言
![Image](https://i.imgur.com/YNaSM0w.png)
![Image](https://i.imgur.com/3lBDrcL.png)
>Javascript屬於一種直譯式語言, 而非編譯式語言
* 編譯式語言預先編譯的話就可以預先除錯
* 直譯式語言的彈性定義比較高，不用預先定義型別，有出錯就直接出現在console上（出錯就直接出現在環境中）
![Image](https://i.imgur.com/7gqBRnZ.png)

>語法基本單元化就是將JS中的標點符號跟詞彙一一的解析出來,抽象結構樹會將整個原始碼的結構定義出來, 最後才將代碼生成

>代碼生成後才會運行程式碼

## LHS & RHS


