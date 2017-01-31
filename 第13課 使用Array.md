#第13課 使用Array

## (1) 宣告一個Array物件


#####測試程式
```javascript
var array = [10, 20, 30, 40, 'tom', 'mary', 'judy'];

for(var i=0; i<array.length; i++){
    console.log(array[i]);
} 
```

執行結果
```
10
20
30
40
tom
mary
judy
```



## (2) 用push()加入元件

#####測試程式
```javascript
var array = [10, 20, 30, 40, 'tom', 'mary', 'judy'];

for(var i=0; i<array.length; i++){
    console.log(array[i]);
} 

console.log('-----------------');


//=====================
// 加入元件
//=====================
array.push('smith');

for(var i=0; i<array.length; i++){
    console.log(array[i]);
}

console.log('-----------------');
```

執行結果
```
10
20
30
40
tom
mary
judy
-----------------
10
20
30
40
tom
mary
judy
smith
-----------------
```



## (3) 用pop()取出元件

#####測試程式
```javascript
var array = [10, 20, 30, 40, 'tom', 'mary', 'judy'];

for(var i=0; i<array.length; i++){
    console.log(array[i]);
} 

console.log('-----------------');


//=====================
// 取出元件
//=====================
var k=array.pop();

console.log(k);
console.log('-----------------');


for(var i=0; i<array.length; i++){
    console.log(array[i]);
}

console.log('-----------------');
```

執行結果
```
10
20
30
40
tom
mary
judy
-----------------
judy
-----------------
10
20
30
40
tom
mary
-----------------
```



## (4) 用shift()取出元件

#####測試程式
```javascript
var array = [10, 20, 30, 40, 'tom', 'mary', 'judy'];

for(var i=0; i<array.length; i++){
    console.log(array[i]);
} 

console.log('-----------------');


//=====================
// 取出元件
//=====================
var k=array.shift();

console.log(k);
console.log('-----------------');


for(var i=0; i<array.length; i++){
    console.log(array[i]);
}

console.log('-----------------');
```

執行結果
```
10
20
30
40
tom
mary
judy
-----------------
10
-----------------
20
30
40
tom
mary
judy
-----------------
```



## (5) 用unshift()加入元件

#####測試程式
```javascript
var array = [10, 20, 30, 40, 'tom', 'mary', 'judy'];

for(var i=0; i<array.length; i++){
    console.log(array[i]);
} 

console.log('-----------------');


//=====================
// 加入元件
//=====================
array.unshift(5);


for(var i=0; i<array.length; i++){
    console.log(array[i]);
}

console.log('-----------------');
```

執行結果
```
10
20
30
40
tom
mary
judy
-----------------
5
10
20
30
40
tom
mary
judy
-----------------
```
