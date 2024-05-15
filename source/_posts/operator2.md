---
title: Day 1 & Day 2
date: 2024-05-14 11:58:33
tags: [008Days,Book]
categories: [Javascript]
---

# 變數命名原則

* 變數的命名的首尾可以為`英文字母,底線,或是$`
* Javascript 可以用中文命名,但有可能會亂碼
* 不可以是`Reserved Words 保留字` or `關鍵字 keyword`
* Javascript的語法是有`區分大小寫`的
* Javascript是一個`弱型別`的語言, 宣告時無需指定型別,型別的資訊只在`值` 或 `物件` 本身才有型別的資訊,**變數沒有型別,值才有**

# 變數的宣告
* 未經宣告只賦予值,造成`全域變數`
```js
m=1;
console.log(m);//print 1
```
* 有宣告但未賦予值, 變數預設為`undefined`
```js
var m;
console.log(m);//undefined
```
* 未經宣告但就要去使用時，出現`ReferenceError` 的錯誤

* **var**可以`重複宣告`同一變數，但**let**不能
```js
var m = 1;
var m = 2;

let n =3;
let n=4;//Uncaught Syntax Error
```
# 變數的型別簡介及例外
## 基本型別 (Primitives)

* String
* Number
* Boolean
* Null
* Undefined
* Symbol `After ES6`

## 基本型別的例外
```js
  typeof {}; //object
  typeof []; //object
  typeof null;//object
  typeof window.alert; //function
```
*************************
### String 字串
* 不可單引號包單引號，也不可雙引號包雙引號, 若真的有這樣的情況，可以使用跳脫字元`\`**Escape Character**
* 多組的字串,可以用`+`連接

```js
var str = 'Let\'s go!';

var hello = "Hello"+"World";
```
### 樣板字面值 (Template Literal)
* ***`${}`*** 可以直接置入運算式 & 變數

```js
var a =5;
var b=15;

console.log(`Fifteen is ${a+b} and not ${2*a + b}`)
```
### 數字 (Number)
* JS只有一種數值的型別,就是number, 不管是整數或帶有小數點的浮點數字皆屬於這一類
* Infinity (無限大), -Infinity（負無限大), NaN(不是數值,Not a Number)
1. 正數除以0 => `Infinity 無限大`
2. 負數除以0 => `-Infinity 負無限大`
3. 0/0, Infinity/Infinity, -Infinity/-Infinity =>`NaN`

#### NaN 
```js
typeof(NaN); //'number'
```
* `NaN`與任何數字作運算，結果都是`NaN`,也就是說,`NaN`並不等於任何的數字，甚至是自己
```js
NaN === NaN //false
isNaN("123") //false String 會透過隱含的Number()轉型成數字
isNaN("NaN")//true 因為字串"NaN"無法轉型成數字
```
* 十進位的小數無法完美的用`二進位`的方式表示，只能用無限循環的位數來趨近於十進位的小數
```js
0.1+0.2 === 0.3 //false
```
* 要數字精準的話，可將小數點在運算錢轉成整數，計算後再調整回來

### 布林值 (True & False)
* 通常用在`判斷式`,作為控制`程式流程`的用途

### null & undefined
> null 與 undefined的共通點就是, null只有一種值就是`null`, undefined 也只有一種值就是`undefined`
* 此兩者透過`Boolean()`強制轉型成Boolean時，都會代表`false`
```js
Number(null);//0
Number(undefined); //NaN
```
>undefined 代表`尚未給值, 未定義`, null則表示`此變數沒有值`

## 物件 (Object)
>所有基本型別(Primitives)以外的值都是物件, `零至多種屬性的集合`