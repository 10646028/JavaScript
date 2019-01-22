# 06 使用const宣告常數

```
用const宣告一個常數後, 該常數的內容即不可再被更改.
```
### (1) 未使用const的程式

```javascript
//--------------------------------------
// 使用嚴格模式, 使用的變數一定要事前宣告
//--------------------------------------
'use strict';

//----------------------------------------- 
// 一個計算bmi的函式
// 傳入: 身高(cm), 體重(kg)
// 回傳: bmi
//----------------------------------------- 
function bmi(height, weight){
    return weight / Math.pow(height/100, 2);     
}
   
//----------------------------------------- 
// 一個評估bmi的函式
// 傳入: 身高(cm), 體重(kg)
// 回傳: bmi評語
//-----------------------------------------  
function evaluation(height, weight){
    var b = bmi(height, weight);

    if(b < 18.5){
        return "過輕";
    }else if(b >= 18.5 && b < 24){
        return "正常體重";
    }else if(b >= 24 && b < 27){
        return "過重";
    }else{
        return "肥胖";
    }
}

//------------------------------
// 主程式
//------------------------------
console.log(bmi(170, 60));          //20.7612...
console.log(evaluation(170, 60));   //正常體重
```


### (2) 在函式中宣告const常數

```javascript
//--------------------------------------
// 使用嚴格模式, 使用的變數一定要事前宣告
//--------------------------------------
'use strict';

//----------------------------------------- 
// 一個計算bmi的函式
// 傳入: 身高(cm), 體重(kg)
// 回傳: bmi
//----------------------------------------- 
function bmi(height, weight){
    return weight / Math.pow(height/100, 2);     
}
   
//----------------------------------------- 
// 一個評估bmi的函式
// 傳入: 身高(cm), 體重(kg)
// 回傳: bmi評語
//-----------------------------------------  
function evaluation(height, weight){
    const tooSlim = "過輕";     //不可更改內容值的常數
    const normal = "正常體重";  //不可更改內容值的常數
    const tooHeavy = "過重";   //不可更改內容值的常數
    const obesity = "肥胖";    //不可更改內容值的常數

    var b = bmi(height, weight);

    if(b < 18.5){
        return tooSlim;
    }else if(b >= 18.5 && b < 24){
        return normal;
    }else if(b >= 24 && b < 27){
        return tooHeavy;
    }else{
        return obesity;
    }
}

//------------------------------
// 主程式
//------------------------------
console.log(bmi(170, 60));          //20.7612...
console.log(evaluation(170, 60));   //正常體重
```


### (3) 宣告廣域的const常數

```javascript
//--------------------------------------
// 使用嚴格模式, 使用的變數一定要事前宣告
//--------------------------------------
'use strict';

//--------------------------------------
// 廣域使用的函式
//--------------------------------------
const tooSlim = "過輕";
const normal = "正常體重";
const tooHeavy = "過重";
const obesity = "肥胖";

//----------------------------------------- 
// 一個計算bmi的靜態方法
// 傳入: 身高(cm), 體重(kg)
// 回傳: bmi
//----------------------------------------- 
function bmi(height, weight){
    return weight / Math.pow(height/100, 2);     
}
   
//----------------------------------------- 
// 一個評估bmi的函式
// 傳入: 身高(cm), 體重(kg)
// 回傳: bmi評語
//-----------------------------------------  
function evaluation(height, weight){
    var b = bmi(height, weight);

    if(b < 18.5){
        return tooSlim;
    }else if(b >= 18.5 && b < 24){
        return normal;
    }else if(b >= 24 && b < 27){
        return tooHeavy;
    }else{
        return obesity;
    }
}

//------------------------------
// 主程式
//------------------------------
console.log(bmi(170, 60));          //20.7612...
console.log(evaluation(170, 60));   //正常體重
```
