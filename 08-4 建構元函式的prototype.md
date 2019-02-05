# 08-4 建構元函式的prototype

```
用建構元函式產生不同物件時, 這些物件透過建構元函式的prototype宣告而共同某些物件.
```


### 程式範例

```javascript
//-------------------------
// 使用嚴格模式
//-------------------------
'use strict';

//-------------------------
// 一個建構元函式
//-------------------------
function score(chi, eng, mat){
    this.chi = chi;
    this.eng = eng;
    this.mat = mat;
    
    this.total = function(){
        return this.chi * 2 + this.eng * 1.5 + this.mat * 1.5;
    }
}

//-------------------------
// 建構元函式的prototype
//-------------------------
score.prototype.printInfo = function(){
    console.log('國文:' + this.chi);
    console.log('英文:' + this.eng);
    console.log('數學:' + this.mat);        

    console.log('加權總分:' + this.total());
    console.log();    
}

//-------------------------
// 由建構元函式產生物件
//-------------------------
var s1 = new score(60, 80, 60);
s1.printInfo();

var s2 = new score(60, 80, 60);
s2.printInfo();

//-------------------------
// 物件的測試
//-------------------------
console.log('s1和s2是否同一物件?' + (s1 === s2));  //false
console.log('s1和s2的printInfo是否同一物件?' + (s1.printInfo === s2.printInfo));  //true
```
