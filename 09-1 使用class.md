# 09-1 使用class

```
class的本質是function, 在不影響javaScript本質而使用的語法糖, 可以用比較簡單的語法完成物件及繼承.
```

### (1) 程式範例

```javascript
//---------------------------------------
// 使用嚴格模式
//---------------------------------------
'use strict';

//---------------------------------------
// 一個類別
// function可以寫在使用它的指令之前或之後,
// 但class必須寫在使用它的指令之前.
//---------------------------------------
class Score{
    //建構元
    constructor(chi, eng, mat){
        this._chi = chi;
        this._eng = eng;
        this._mat = mat;
    }    
    
    //getter
    get chi(){return this._chi;}
    get eng(){return this._eng;}
    get mat(){return this._mat;}

    //setter
    set chi(chi){this._chi = chi;}
    set eng(eng){this._eng = eng;}
    set mat(mat){this._mat = mat;}

    //方法
    total(){
        return this._chi * 2 + this._eng * 1.5 + this._mat * 1.5;
    }
}

//---------------------------------------
// 測試
//---------------------------------------
//產生物件s, 再呼叫Score的建構元, 其中的this是指s
var s = new Score(60, 80, 60);  

s.chi = 90;  //呼叫setter

console.log('國文:' + s.chi);  //呼叫getter
console.log('英文:' + s.eng);  //呼叫getter
console.log('數學:' + s.mat);  //呼叫getter
console.log('加權總分:' + s.total());  //呼叫方法
```
