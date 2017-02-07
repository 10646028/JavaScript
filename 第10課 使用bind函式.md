#第10課 使用bind函式


## (1) 使用bind函式挷定this


#####測試程式
```javascript
//===========================
// 建立一個window層級的變數
//===========================
var teacher='林老師';


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


//===========================
// 此例的this指向window
//===========================
var gt1=s1.getTeacher;
console.log(gt1());
console.log('--------------');


//===========================
// 此例的this指向s2
//===========================
var gt2=s1.getTeacher.bind(s2);
console.log(gt2())
console.log('--------------');


//================================================
// 一建構元函式，用來生成物件, 建議以大寫字開頭
//================================================
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
林老師
--------------
李老師
--------------
```
