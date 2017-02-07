#第16課 關於closure


## (1) 廣域變數的內容會被函式外指令改變

#####測試程式
```javascript
//===================================================
// 宣告一廣域變數cnt, 雖由add()使用, 但其他函式也可取用它
//===================================================
var cnt=0;

function add(){
    cnt++;
    return cnt;
}


//===================
// 執行累加
//===================
console.log(add());
console.log(add());
console.log(add());
```

執行結果
```
1
2
3
```



## (2) 將變數包在function中, 只能由add()函式取用

#####測試程式
```javascript
//===========================================================
// 宣告一區域變數cnt, 只由add()使用, 其值不會因每次呼叫函數而被清除
//===========================================================
function myfunction(){
    var cnt=0;
    
    function add(){
        cnt++;
        return cnt;
    }
    
    return add;
}


//===================
// 執行累加
//===================
var add=myfunction();
console.log(add());
console.log(add());
console.log(add());
```

執行結果
```
1
2
3
```



## (3) 改寫程式(2)

#####測試程式

```javascript
//===========================================================
// 宣告一區域變數cnt, 只由add()使用, 其值不會因每次呼叫函數而被清除
//===========================================================
var myfunction=function(){
    var cnt=0;
    
    return (function(){
        cnt++;
        return cnt;
    });
};


//===================
// 執行累加
//===================
var add=myfunction();
console.log(add());
console.log(add());
console.log(add());
```

執行結果
```
1
2
3
```



## (4) 另一個例子, 用closure儲存已知質數


#####測試程式

```javascript
//=========================================
// 宣告一區域陣列變數p, 只由isPrime()使用
//=========================================
function myfunction(){
    var p=[2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37];

    return (function (num){
        var flag=true;

        for(var i=0; i<p.length; i++){
            if(num%p[i]===0){
                flag=false;
                break;
            }
        }

        if(flag){
            for(var j=3; j<Math.sqrt(num); j+=2){
                if(num%j===0){
                    flag=false;
                    break;
                }
            }
        }

        if(flag){
            p.push(num);
            return true;
        }else{
            return false;
        }
    });
}


//===================
// 執行判斷質數
//===================
var isPrime=myfunction();
console.log(isPrime(1231));
console.log(isPrime(123451)); 
```

執行結果
```
true
false
```

