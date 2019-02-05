# 08-5 物件中的private member

```
在成員變數前加底線是私用成員的寫作規範, 它並沒有強制限制取存, 只是作為寫作的宣告.
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
    this._chi = chi;  //私用成員
    this._eng = eng;  //私用成員
    this._mat = mat;  //私用成員

    //getters
    this.getChi = function(){
        return this._chi;
    }
    
    this.getEng = function(){
        return this._eng;
    }

    this.getMat = function(){
        return this._mat;
    }

    //計算加權總分
    this.total = function(){
        return this._chi * 2 + this._eng * 1.5 + this._mat * 1.5;
    }
}

//-------------------------
// 測試
//-------------------------
var s = new score(60, 70, 80);
console.log(s._chi);       //仍可取用
console.log(s.getChi());
console.log(s.getEng());
console.log(s.getMat());
console.log(s.total());
```
