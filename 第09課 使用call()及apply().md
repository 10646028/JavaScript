#第09課 使用call()及apply()


## (1) 使用call()及apply()建立物件


#####測試程式
```javascript
//===========================
// 用call(...)生成物件s1
//===========================
var s1={};
//設定 this=s1, 並執行 Student()函式, 依序傳入其他參數
Student.call(s1, '10456001', '王小明');   //註1

console.log(s1.getStuNo());
console.log(s1.getStuName());
console.log(s1.dept());
console.log('--------------');


//-------------------------------
// 用apply(...)生成物件s2
//-------------------------------
var s2={};
//設定 this=s2, 並執行 Student()函式, 其他參數放在一個陣列中
Student.apply(s2, ['10456002', '陳小華']);
console.log(s2.getStuNo());
console.log(s2.getStuName());
console.log(s2.dept());
console.log('--------------');



//================================================
// 一建構元函式，用來生成物件, 建議以大寫字開頭
//================================================
function Student(stuNo, stuName){
    //------------------------
    // 判斷輸入參數個數及型態
    //------------------------
    if(arguments.length!=2){
        return null;
    }

    if(typeof(arguments[0])!='string'){
        return null;
    }

    if(arguments[0].length!=8){
        return null;
    }  

    //------------------------
    // 建立物件內區域變數
    //------------------------    
    var stuNo=stuNo;
    var stuName=stuName;

    //------------------------
    // 建立物件內函式屬性
    //------------------------
    this.getStuNo=function(){return stuNo;}
    this.getStuName=function(){return stuName;}

    this.dept=function(){
        var d='未知';

        var s=stuNo.charAt(3);
        if(s=='3'){
            d='二技';
        }else if(s=='4'){
            d='四技';
        }else if(s=='5'){
            d='五專';
        }

        return d;
    }
}
```



#####執行結果
```
10456001
王小明
五專
--------------
10456002
陳小華
五專
--------------
```

