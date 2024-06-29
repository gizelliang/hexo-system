---
title: 常見陣列處理方法
date: 2024-06-17 16:20:49
tags: [HexSchool,Video]
categories: [Javascript]
description: 第四週核心課程Casper提供Youtube連結
---
[陣列方法參考]（https://hackmd.io/@Heidi-Liu/javascript-for-loop）
[陣列方法參考](https://hackmd.io/@Heidi-Liu/javascript-native-array)
![Image](https://i.imgur.com/TnUDAXU.png)
## map 與 forEach 比較

> map 一定會回傳結果, ForEach並不回傳任何東西 

> map 可帶入的參數與 forEach相同

```js
const people = [
  {
    name: '卡斯伯',
    order: '鍋燒意麵',
    price: 80
  },
  {
    name: '小明',
    order: '牛肉麵',
    price: 120
  },
  {
    name: '漂亮阿姨',
    order: '滷味切盤',
    price: 40
  },
  {
    name: 'Ray',
    order: '大麻醬乾麵',
    price: 60
  },
];
```

### forEach

```js
// 取出所有值（要一一列出每個人的訂單）
people.forEach((item, key, arr) => {
  console.log(item, key, arr);
});
```
* forEach會讓函數執行四次,且不能跳出迴圈

### map & forEach比較
#### 陣列內的值調整（大家看到活動期間，價格 八折）

```js
const newOrders=[];
people.forEach(function(obj,key){
    newOrders[key]={
        ...obj,
        newPrice:obj.price * 0.8
    }
})

console.log(newOrders);
```
```js
const people2 = people.map((item) => {
  return {
    ...item,
    price: item.price * 0.8,
  };
});
console.log('map:', people2);
```

### filter
#### 過濾情境：老闆說 80 元以上加送滷蛋
```js
 const newOrders2=[];
 people.forEach(function(item,index){
    if(item.price>=80){
        newOrders2.push(item);
    }
 });
```
```js
//filter+Arrow Function
const filterPeople = people.filter((item) => item.price >= 80);
//將判斷式放入filter中
console.log('過濾:', filterPeople);
```
```js
//filter

const newOrder2 = people.filter(function(item,index){ return item.price >=80;})
//將判斷式放入filter中
```


### findIndex
#### 情境：找出特定位置的索引位置，老闆說牛肉沒了,要改牛肉麵變成牛肉湯麵

>最終只會找到一個索引位置

```js
let orderIndex = 0;
people.forEach((item, index) => {
  if (item.order === '牛肉麵') {
    orderIndex = index
  }
});
people[orderIndex].order = '牛肉湯麵'
console.log('索引位置:', orderIndex);
console.log(people);
```

```js
//filter+傳統函數
const index = people.findIndex(function(item,index){
  return item.order === "牛肉麵";
})
people[index].order ="牛肉湯麵";
console.log(people[index]);
```
```js
//filter＋arrow function
const index = people.findIndex((item)=>(item.order ==="牛肉麵"))
people[index].order = "牛肉湯麵";
console.log(people[index]);

```

### map & forEach
#### 情境：組成 li 結構：老闆說 POS 機壞了，需要印發票，請幫忙組出 li 結構

>map就會進行return, 且回傳的結果也為陣列，陣列多長，map回傳的結果就會多長

```js
let htmlTemplate = '';
people.forEach((item) => {
  htmlTemplate = htmlTemplate + `<li>
    ${item.order} 共 ${item.price} 元
    </li>`
});
console.log(htmlTemplate);
```

>map通常會搭配**join**方法一起使用, join可以協助map將產出的結果轉成字串
```js
const htmlTemplate = people.map(function(obj,key){
  return `<li>${obj.order},${obj.price}</li>` }
)
```

![Image](https://i.imgur.com/q49eCsL.png)

>利用join將陣列中的逗號替換成空字串（就是把逗號從陣列中移除）
[join MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join)

```js
const htmlTemplate = people.map(function(obj,key){
  return `<li>${obj.order},${obj.price}</li>` }
).join('');
```
![Image](https://i.imgur.com/4vfpWXO.png)

```js
//map搭配Arrow Function
const htmlTemplate = people.map((obj,key)=>`<li>${obj.order},${obj.price}</li>`
).join('');
```

### reduce & forEach
#### 情境:老闆要收錢啦

>reduce當中帶入的參數並非為物件本身與索引位置

```js
let total = 0;//起始值
people.forEach(function(obj,key){
  total +=obj.price;
});
```
```js
let total = people.reduce(function(acc,cur){
  console.log(`Total:${acc}`)
  console.log(`Item:${cur.price}`)
  console.log(acc,cur);
  return acc + 1;
},0)

/* acc為累計值，cur為當前值＊/
/* 0 為起始值 */
```
```js
let total = people.reduce((acc,cur) => acc + cur.price
,0)
```
![Image](https://i.imgur.com/qYt2yvm.png)

#### 利用reduce來分類
```js
const people = [
  {name:"Kyle",age:26},
  {name:"John",age:31},
  {name:"Sally",age:42},
  {name:"Jill",age:42},
]

const result = people.reduce((groupedPeople,person)=>{
  const age = person.age
  if (groupedPeople[age]==null)
  groupedPeople[age]=[]
  groupedPeople[age].push(person)
  return groupedPeople
},{})

console.log(result);
```
![Image](https://i.imgur.com/oWEWUyk.png)

#### reduce的四個參數

```js
const numbers = [13,2,5];
const sum = numbers.reduce((total,number,index, array)=>{
  console.log(array);
  return total + number
},0)

console.log(sum);
```
![Image](https://i.imgur.com/AmhZntX.png)

>初始值可設可不設，但通常建議一定要設初始值，不然reduce就會將陣列中的第一個值當作total,若陣列為空陣列，則會出現error

>reduce的四個參數中通常只會用total, number(即累計值跟當前物件)

>初始值是指acc的起始值, cur不是指當前值，而是代表當前的物件

### sort
#### 排序
```js
const peopleSort = people.sort((a, b) => {
  return b.price - a.price;
});
console.log(peopleSort);
```
>sort會兩兩相互比較
>a & b 代表同一陣列中的兩個物件