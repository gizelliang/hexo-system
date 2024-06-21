---
title: Hex_Arrow Function
date: 2024-05-22 00:29:24
tags: [HexSchool,Video]
categories: [Javascript]
description: JS直播箭頭函數預錄
---

## 函式表達式(Function Expression) & 函式陳述式 (Function Statement)

```js
//此為函式表達式
console.log(numB(6))
const numB = function(x){
    return x*x;
}

//Uncaught ReferenceError: numB is not defined
```
>函式陳述式有Hoisting的作用，不論在陳述式前或是陳述式後，都可以呼叫函式

```js
//此為函式陳述式

console.log(numA(25));//print 625
function numA(x){
    return x*x;
}
console.log(numA(4));//print 16
```
## 箭頭函式寫法

1. 如果函式搭配到Return **箭頭函式會自帶return**
```js
const numberA = function(x){
    return x*x;
}

//Arrow Function, Return 可省略
const numberA = (x)=>{ return x*x};
const numberB = (x)=> x*x*x;
```
2. 如果只有一個參數，可以省略括號
   多行程式碼的話，大括號就不可省略
```js
const numberA = x=>{ return x*x};
const numberB = x=> x*x*x;
```
3. 沒有參數，還是要有空括號
```js
const numberA = ()=>{ return x*x};
const numberB = ()=> x*x*x;
```
