# 11-1 使用Module

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
const con = require('./utility/connection.js');

//-------------------
// 測試
//-------------------
console.log(con);
console.log(con.url);
console.log(con.user);
console.log(con.password);
```
