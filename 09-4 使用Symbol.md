# 09-4 使用Symbol

```
一個Symbol()產生一個不同於其他Symbol()產生的值.
```

### 程式範例, 繼承

```javascript
//---------------------------------------
// 使用嚴格模式
//---------------------------------------
'use strict';

//---------------------------------------
// 一個類別
//---------------------------------------
let student = {
    no: '110001',
    name: '王小明',
    age: 20,

    [Symbol('record')] : '丙級檢定及格',
    [Symbol('record')] : '乙級檢定及格',
    [Symbol('record')] : '甲級檢定及格',
}

//---------------------------------------
// Symbol('record')和
// 另一個Symbol('record')一定有不同值
//---------------------------------------
console.log(student);

//---------------------------------------
// 列出物件中所有的Symbol屬性值
//---------------------------------------
const symbolKeys = Object.getOwnPropertySymbols(student);
for(let value of symbolKeys) {
    console.log(student[value]) 
}
```
