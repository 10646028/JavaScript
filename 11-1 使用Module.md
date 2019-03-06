# 11-1 使用Module

## (1)
```
<測試資料夾>
    |
    |__ main.js
    |
    |__ <utility>
            |__ connection.js
```

### (1-1) 模組, connection.js

```javascript
//--------------------------
// 一個供其他程式引入的模組
//--------------------------
var connection = {
    'url' : 'www.ntub.edu.tw',
    'user' : 'tomlin',
    'password' : '123456'
}

module.exports = connection;
```


### (1-2) 程式範例, main.js

```javascript
//-------------------
// 使用嚴格模式
//-------------------
'use strict';

//-------------------
// 引用外部模組
//-------------------
const con = require('./utility/connection');

//-------------------
// 測試
//-------------------
console.log(con);
console.log(con.url);
console.log(con.user);
console.log(con.password);
```


## (2)
```
<測試資料夾>
    |
    |__ main.js
    |
    |__ <utility>
            |__ adder.js
```

### (2-1) 模組, adder.js

```javascript
//-------------------
// 使用嚴格模式
//-------------------
'use strict';

//--------------------------
// 一個供其他程式引入的模組
//--------------------------
function adder(x, y){
    var z = x + y;
    return z;
}

module.exports = adder;
```


### (2-2) 程式範例, main.js

```javascript
//-------------------
// 使用嚴格模式
//-------------------
'use strict';

//-------------------
// 引用外部模組
//-------------------
const add = require('./utility/adder');

//-------------------
// 測試
//-------------------
var z = 100;

console.log(add(10, 20));   //30
console.log(z);             //100
```


## (3)
```
<測試資料夾>
    |
    |__ main.js
    |
    |__ <utility>
            |__ adder.js
```

### (3-1) 模組, adder.js

```javascript
//--------------------------
// 一個供其他程式引入的模組
//--------------------------
function adder(x, y){
    z = x + y;
    return z;
}

module.exports = adder;
```


### (3-2) 程式範例, main.js

```javascript
//-------------------
// 使用嚴格模式
//-------------------
'use strict';

//-------------------
// 引用外部模組
//-------------------
const add = require('./utility/adder');

//-------------------
// 測試
//-------------------
console.log(add(10, 20));  //30
console.log(z);            //30 
```
