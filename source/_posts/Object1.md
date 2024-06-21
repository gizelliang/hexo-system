---
title: 物件與陣列(淺拷貝/深拷貝 & 傳址/傳值)
date: 2024-06-17 16:10:38
tags: [HexSchool,Video]
categories: [Javascript]
description: 第四周核心（By value, by reference or by sharing + Shallow Copy/Deep Copy）
---

[淺/深拷貝]https://www.thisweb.dev/post/js-deep-clone
## Pass by reference & Pass by value
* 物件與陣列不屬於基本型別，所以不是傳值（Pass by value）是傳參考(Pass by reference)

## 物件如何使用陣列方法？
```js
const family = {
    Ming:{
        name:"小明",
    },
    Jay:{
        name:"杰倫",
    },
    Auntie:{
        name:"漂亮阿姨",
    }
};

console.log(Object.keys(family));
console.log(Object.values(family));
```
![Image](https://i.imgur.com/cuq5xWN.png)

![Image](https://i.imgur.com/Vz4ce9e.png)

```js
Object.values(family).forEach(item =>{console.log(item);})
```
![Image](https://i.imgur.com/HkJ8Tz5.png)

```js
Object.keys(family).forEach(
    key=>{
        console.log(key);
        console.log(family[key]);
    }
)
```
![Image](https://i.imgur.com/PeBWk1u.png)

