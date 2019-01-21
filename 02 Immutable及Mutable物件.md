# 02 Immutable及Mutable物件

```
資料來源: https://developer.mozilla.org/zh-TW/docs/Glossary/Primitive

所有的基本型別都是不可變的（immutable），即不可修改的。
```

### (1) string是immutable物件

```javascript
var m1 = 'Hello';
var m2 = m1;

console.log(m1);
console.log(m2);
console.log();

//-----------------------------------------
// m1物件(string)是一個immutable物件,
// 不可更改其原有內容;
// 當設定m1新值時, 事實上是生成一個新物件.
//-----------------------------------------
m1 = 'Hi';

console.log(m1);
console.log(m2);
```

### (2) Array是mutable物件

```javascript
var m1 = ['Hello'];
var m2 = m1;

console.log(m1);
console.log(m2);
console.log();

//-------------------------------------------------
// m1物件(Array)是一個mutable物件,
// 其內容可以更改; 
// 當操作新增內容的指令時, 不因內容更改而生成新物件,
// 而是更改在原物件中.
//-------------------------------------------------
m1.push('Hi');

console.log(m1);
console.log(m2);
```
