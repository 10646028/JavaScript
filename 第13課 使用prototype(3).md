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
