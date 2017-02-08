#第09課 使用call及apply函式


## (1) 使用call及apply函式建立物件


#####測試程式
```javascript
//=========================
// 用call函式生成物件s1
//=========================
var s1={};
//設定 this=s1, 並執行 Student()函式, 依序傳入其他參數
Student.call(s1, '10456001', '王小明'); 

console.log(s1.getStuNo());
console.log(s1.getStuName());
console.log(s1.dept());
console.log('--------------');


//=========================
// 用apply函式生成物件s2
//=========================
var s2={};
//設定 this=s2, 並執行 Student()函式, 其他參數放在一個陣列中
Student.apply(s2, ['10456002', '陳小華']);
console.log(s2.getStuNo());
console.log(s2.getStuName());
console.log(s2.dept());
console.log('--------------');



//=============
// 建構元函式
//=============
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



## (2) call函式及apply函式改變了this的指向


#####測試程式
```javascript
//===========================
// 用建構元函式生成物件s1
//===========================
var s1=new Student('10456001', '王小明', '張老師'); 

console.log(s1.getStuNo());
console.log(s1.getStuName());
console.log(s1.getTeacher());
console.log('--------------');


//===========================
// 用建構元函式生成物件s2
//===========================
var s2=new Student('10456002', '陳小華', '李老師');

console.log(s2.getStuNo());
console.log(s2.getStuName());
console.log(s2.getTeacher());
console.log('--------------');


//-----------------------------------
// 在s1.getTeacher()中, this改指向s2
//-----------------------------------
console.log(s1.getTeacher.call(s2));
console.log('--------------');


//-----------------------------------
// 在s2.getTeacher()中, this改指向s1
//-----------------------------------
console.log(s2.getTeacher.call(s1));
console.log('--------------');


//-----------------------------------
// 在s1.getTeacher()中, this改指向s2
//-----------------------------------
console.log(s1.getTeacher.apply(s2));
console.log('--------------');


//-----------------------------------
// 在s2.getTeacher()中, this改指向s1
//-----------------------------------
console.log(s2.getTeacher.apply(s1));
console.log('--------------');



//=============
// 建構元函式
//=============
function Student(stuNo, stuName, teacher){
    //------------------------
    // 建立物件內區域變數
    //------------------------    
    this.stuNo=stuNo;
    this.stuName=stuName;
    this.teacher=teacher;

    //------------------------
    // 建立物件內函式屬性
    //------------------------
    this.getStuNo=function(){return this.stuNo;}
    this.getStuName=function(){return this.stuName;}
    this.getTeacher=function(){return this.teacher;}
}
```



#####執行結果
```
10456001
王小明
張老師
--------------
10456002
陳小華
李老師
--------------
李老師
--------------
張老師
--------------
李老師
--------------
張老師
--------------
```
