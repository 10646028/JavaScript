# 11-2 使用Module

## (1)
```
<測試資料夾>
    |
    |__ main.js
    |
    |__ <utility>
            |__ score.js
```

### (1-1) 模組, score.js

```javascript
'use strict';

//計算成績總分
var total = function(chi, eng, mat){
    const sum = chi*2 + eng*1.5 + mat*1;

    return sum;
}

//計算成績等第
var rank = function(chi, eng, mat){
    const sum = chi*2 + eng*1.5 + mat*1;
    
    if(sum>400){
        return 'High';
    }else if(sum<=400 && sum>300){
        return 'Medium';
    }else{
        return 'Low';
    }
}

module.exports = {total, rank};
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
const {total, rank} = require('./utility/score.js');

//-------------------
// 測試
//-------------------
console.log(rank(80, 70, 90));
console.log(rank(86, 50, 50));
console.log(rank(90, 90, 90));

console.log(total(80, 70, 90));
console.log(total(86, 50, 50));
console.log(total(90, 90, 90));
```

