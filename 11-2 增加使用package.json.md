# 11-2 增加使用package.json

```
<測試資料夾>
    |
    |__ main.js
    |
    |__ <utility>
            |__ package.json
            |__ connection.js
```

### (1) 模組, connection.js

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

### (2) package.json

```javascript
{
    "name" : "connection",
    "main" : "./connection.js"
}
```


### (3) 程式範例, main.js

```javascript
//-------------------
// 使用嚴格模式
//-------------------
'use strict';

//-------------------
// 引用需要的模組
//-------------------
const con = require('./utility');

//-------------------
// 測試
//-------------------
console.log(con);
console.log(con.url);
console.log(con.user);
console.log(con.password);
```
