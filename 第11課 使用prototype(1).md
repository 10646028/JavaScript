#第11課 使用prototype(1)


## (1) 使用prototype繼承某個物件


#####測試程式
```javascript
//====================================================
// 產生一個Student物件 並將NTUBStudent原型指向前述物件
//====================================================
var student=new Student();
NTUBStudent.prototype=student;


//=============================
// 建構元函式, 產生原型物件
//=============================
function Student(){
    this.getDept=function(){
        var d='未知';
        
        //------------------------
        // this指向Student物件
        //------------------------
        var s=this.stuNo.charAt(3);
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


//=========================================
// 一建構元函式，用來生成NTUBStudent物件
//=========================================
function NTUBStudent(stuNo, stuName){
    //------------------------
    // 建立物件內區域變數
    //------------------------    
    this.stuNo=stuNo;
    this.stuName=stuName;

    //------------------------
    // 建立物件內函式屬性
    //------------------------
    this.getStuNo=function(){return this.stuNo;}
    this.getStuName=function(){return this.stuName;}
}



//===========================
// 用建構元函式生成物件s1
//===========================
var s1=new NTUBStudent('10456001', '王小明');

console.log(s1.getStuNo());
console.log(s1.getStuName());
console.log(s1.getDept());
console.log('--------------');


//===========================
// 用建構元函式生成物件s2
//===========================
var s2=new NTUBStudent('10446002', '陳小華');
console.log(s2.getStuNo());
console.log(s2.getStuName());
console.log(s2.getDept());
console.log('--------------');
```



#####執行結果
```
10456001
王小明
五專
--------------
10446002
陳小華
四技
--------------
```



## (2) prototype指向一個物件或是指向null


#####測試程式
```javascript
//========================================
// 一個物件, 將作為NTUBStudent物件的原型
//========================================
var student = {
    getDept:function(){
        var d='未知';

        //--------------------------
        // this指向NTUBStudent物件
        //--------------------------
        var s=this.stuNo.charAt(3);
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


//========================================
// 一建構元函式，用來生成NTUBStudent物件
//========================================
function NTUBStudent(stuNo, stuName){
    //------------------------
    // 建立物件內區域變數
    //------------------------    
    this.stuNo=stuNo;
    this.stuName=stuName;

    //------------------------
    // 建立物件內函式屬性
    //------------------------
    this.getStuNo=function(){return this.stuNo;}
    this.getStuName=function(){return this.stuName;}
}


//======================================
// 將NTUBStudent原型指向student物件
//======================================
NTUBStudent.prototype=student;


//===========================
// 用建構元函式生成物件s1
//===========================
var s1=new NTUBStudent('10456001', '王小明');

console.log(s1.getStuNo());
console.log(s1.getStuName());
console.log(s1.getDept());
console.log('--------------');


//===========================
// 用建構元函式生成物件s2
//===========================
var s2=new NTUBStudent('10446002', '陳小華');
console.log(s2.getStuNo());
console.log(s2.getStuName());
console.log(s2.getDept());
console.log('--------------');
```



#####執行結果
```
10456001
王小明
五專
--------------
10446002
陳小華
四技
--------------
```
