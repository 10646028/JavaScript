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


### (2) 程式範例, 繼承

```javascript
//---------------------------------------
// 使用嚴格模式
//---------------------------------------
'use strict';

//---------------------------------------
// 一個父類別
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
// 一個子類別
//---------------------------------------
class TechScore extends Score{
    //建構元    
    constructor(chi, eng, mat, tech){
        super(chi, eng, mat);
        this._tech = tech;
    }

    //getter
    get tech(){return this._tech;}

    //setter
    set tech(tech){this._tech = tech;}

    //方法
    total(){
        return super.total() + this._tech * 3;
    }
}

//---------------------------------------
// 測試
//---------------------------------------
//產生一個Score物件
var s1 = new Score(60, 80, 60);  
console.log('國文:' + s1.chi);
console.log('英文:' + s1.eng);
console.log('數學:' + s1.mat);
console.log('加權總分:' + s1.total());

//產生一個TechScore物件
var s2 = new TechScore(65, 85, 65, 75);  
console.log('國文:' + s2.chi);
console.log('英文:' + s2.eng);
console.log('數學:' + s2.mat);
console.log('技藝:' + s2.tech);
console.log('加權總分:' + s2.total());
```
