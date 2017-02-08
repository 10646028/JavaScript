#第13課 使用prototype(3)


## (1) 使用apply函式建立物件的prototype


#####測試程式
```javascript
//====================
// 員工的原型物件
//====================
var employee = {
    //------------------------
    // setters
    //------------------------
    setEmpNo:function(empNo){
        this.empNo=empNo;
    },
    setEmpName:function(empName){
        this.empName=empName;
    },

    //------------------------
    // getters
    //------------------------  
    getEmpNo:function(){
        return this.empNo;
    },
    getEmpName:function(){
        return this.empName;
    }
}


//======================================
// 建構元函式，用來生成時薪員工物件
//======================================
function HourlyEmployee(empNo, empName, hoursThisWeek){
    //------------------------
    // 建立物件內區域變數
    //------------------------    
    this.empNo=empNo;
    this.empName=empName;
    this.hoursThisWeek=hoursThisWeek;

    //------------------------
    // 建立物件內函式屬性
    //------------------------
    this.setHoursThisWeek=function(hoursThisWeek){this.hoursThisWeek=hoursThisWeek;}
    this.getHoursThisWeek=function(){return this.hoursThisWeek;}

    this.salary=function(){
        return 300*this.hoursThisWeek;
    }
}


//======================================
// 建立一個prototype為employee的物件
//======================================
var s1=Object.create(employee);


//============================
// 使用apply函式建立物件內容
//============================
HourlyEmployee.apply(s1, ['A001', '王小明', 40]);


//=================
// 列出物件內容
//=================
console.log(s1.getEmpNo());
console.log(s1.getEmpName());
console.log(s1.getHoursThisWeek());
console.log(s1.salary());
console.log('------------');


//=================
// 列出物件的原型
//=================
console.log(s1.__proto__);
console.log('------------');


//=================
// 判斷物件的原型
//=================
console.log(employee.isPrototypeOf(s1));
console.log('------------');
```


#####執行結果
```
A001
王小明
40
12000
------------
{ setEmpNo: [Function: setEmpNo],
  setEmpName: [Function: setEmpName],
  getEmpNo: [Function: getEmpNo],
  getEmpName: [Function: getEmpName] }
------------
true
------------
```



## (2) 使用Object.create函式建立prototype


#####測試程式
```javascript
//====================
// 員工的建構元函式
//====================
function Employee(empNo, empName, department){
	this.empNo=empNo;
	this.empName=empName;
	this.department=department;
}


//==========================
// 時薪員工的建構元函式
//==========================
function HourlyEmployee(hoursThisWeek){
    //------------------------
    // 建立物件內區域變數
    //------------------------    
    this.hoursThisWeek=hoursThisWeek;

    //------------------------
    // 建立物件內函式屬性
    //------------------------
    this.salary=function(){
        return 300*this.hoursThisWeek;
    };
}


//==========================================
// 建立s1, 它的prototype 為 Employee物件
//==========================================
var s1=Object.create(new Employee('A001', '王小明', '財務部'));


//====================
// 設定 s1 的屬性
//====================
HourlyEmployee.apply(s1, [35]);


//===============
// 列出屬性值
//===============
console.log(s1.empNo);
console.log(s1.empName);
console.log(s1.department);
console.log(s1.hoursThisWeek);
console.log(s1.salary());
console.log('------------');


//====================
// 列出屬性名稱及值
//====================
for(var property in s1){
    console.log(property + ":" + s1[property]);
}

console.log('------------');
```


#####執行結果
```
A001
王小明
財務部
35
10500
------------
hoursThisWeek:35
salary:function () {
        return 300 * this.hoursThisWeek;
    }
empNo:A001
empName:王小明
department:財務部
------------
```



## (3) 使用函式建立父子關係


#####測試程式
```javascript
//====================
// 員工的建構元函式
//====================
function Employee(empNo, empName, department){
	this.empNo=empNo;
	this.empName=empName;
	this.department=department;
}


//==========================
// 時薪員工的建構元函式
//==========================
function HourlyEmployee(hoursThisWeek){
    //------------------------
    // 建立物件內區域變數
    //------------------------    
    this.hoursThisWeek=hoursThisWeek;

    //------------------------
    // 建立物件內函式屬性
    //------------------------
    this.salary=function(){
        return 300*this.hoursThisWeek;
    };
}



//=========================
// 以函式建立物件的繼承
//=========================
function inherit(parent){
    if(parent===null){
        throw TypeError();
    }

    if(Object.create(parent)){
        return Object.create(parent);
    }

    function child(){}
    child.prototype=parent;
    return new child();
} 


//==========================================
// 建立s1, 它的prototype 為 Employee物件
//==========================================
var s1=inherit(new Employee('A001', '王小明', '財務部'));


//====================
// 設定 s1 的屬性
//====================
HourlyEmployee.apply(s1, [35]);


//===============
// 列出屬性值
//===============
console.log(s1.empNo);
console.log(s1.empName);
console.log(s1.department);
console.log(s1.hoursThisWeek);
console.log(s1.salary());
console.log('------------');
```


#####執行結果
```
A001
王小明
財務部
35
10500
------------
```
