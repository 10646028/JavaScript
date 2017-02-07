#第12課 使用prototype(2)


## (1) 使用prototype繼承某個物件


#####測試程式
```javascript
//=====================
// 共用變數
//=====================
var Common = {
    payPerHour:150,
    rank_A_salary:50000,
    rank_B_salary:45000,
    rank_others_salary:40000
}


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
        return Common.payPerHour*this.hoursThisWeek;
    }
}


//======================================
// 建構元函式，用來生成月薪員工物件
//======================================
function MonthlyEmployee(empNo, empName, rank){
    //------------------------
    // 建立物件內區域變數
    //------------------------    
    this.empNo=empNo;
    this.empName=empName;
    this.rank=rank;

    //------------------------
    // 建立物件內函式屬性
    //------------------------
    this.setRank=function(rank){this.rank=rank;}
    this.getRank=function(){return this.rank;}

    this.salary=function(){
        var salaryThisMonth=0;
    	
        if(this.rank=='A'){
            salaryThisMonth=Common.rank_A_salary;  		
        }else if(this.rank=='B'){
            salaryThisMonth=Common.rank_B_salary;
        }else{
            salaryThisMonth=Common.rank_others_salary;
        }
    	
        return salaryThisMonth;
    }
}


//========================================
// 將所有類型員工的原型指向employee物件
//========================================
HourlyEmployee.prototype=employee;
MonthlyEmployee.prototype=employee;


//===========================
// 用建構元函式生成物件s1
//===========================
var s1=new HourlyEmployee('A001', '王小明', 40);

console.log(s1.getEmpNo());
console.log(s1.getEmpName());
console.log(s1.getHoursThisWeek());
console.log(s1.salary());
console.log('--------------');


//===========================
// 用建構元函式生成物件s2
//===========================
var s2=new HourlyEmployee('A002', '陳小華', 35);

console.log(s2.getEmpNo());
console.log(s2.getEmpName());
console.log(s2.getHoursThisWeek());
console.log(s2.salary());
console.log('--------------');


//===========================
// 用建構元函式生成物件s3
//===========================
var s3=new MonthlyEmployee('B001', '李小強', 'A');

console.log(s3.getEmpNo());
console.log(s3.getEmpName());
console.log(s3.getRank());
console.log(s3.salary());
console.log('--------------');


//===========================
// 用建構元函式生成物件s4
//===========================
var s4=new MonthlyEmployee('B002', '張小文', 'B');

console.log(s4.getEmpNo());
console.log(s4.getEmpName());
console.log(s4.getRank());
console.log(s4.salary());
console.log('--------------');
```



#####執行結果
```
A001
王小明
40
6000
--------------
A002
陳小華
35
5250
--------------
B001
李小強
A
50000
--------------
B002
張小文
B
45000
--------------
```



## (2) 測試物件的原型


#####測試程式
```javascript
//=====================
// 共用變數
//=====================
var Common = {
	payPerHour:150,
	rank_A_salary:50000,
	rank_B_salary:45000,
	rank_others_salary:40000
}


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
    	return Common.payPerHour*this.hoursThisWeek;
    }
}


//======================================
// 建構元函式，用來生成月薪員工物件
//======================================
function MonthlyEmployee(empNo, empName, rank){
    //------------------------
    // 建立物件內區域變數
    //------------------------    
    this.empNo=empNo;
    this.empName=empName;
    this.rank=rank;

    //------------------------
    // 建立物件內函式屬性
    //------------------------
    this.setRank=function(rank){this.rank=rank;}
    this.getRank=function(){return this.rank;}

    this.salary=function(){
    	var salaryThisMonth=0;
    	
    	if(this.rank=='A'){
			salaryThisMonth=Common.rank_A_salary;  		
    	}else if(this.rank=='B'){
    		salaryThisMonth=Common.rank_B_salary;
    	}else{
    		salaryThisMonth=Common.rank_others_salary;
    	}
    	
    	return salaryThisMonth;
    }
}


//==========================================
// 將所有類型員工的原型指向employee物件
//==========================================
HourlyEmployee.prototype=employee;
MonthlyEmployee.prototype=employee;


//==============================
// 用建構元函式生成物件s1, s2
//==============================
var s1=new HourlyEmployee('A001', '王小明', 40);
var s2=new HourlyEmployee('A002', '陳小華', 35);


//==============================
// 用建構元函式生成物件s3, s4
//==============================
var s3=new MonthlyEmployee('B001', '李小強', 'A');
var s4=new MonthlyEmployee('B002', '張小文', 'B');


//==============================
// 測試物件的原型
//==============================
console.log(s1.__proto__);
console.log('--------------');

console.log(HourlyEmployee.prototype);
console.log('--------------');

console.log(s1.__proto__===HourlyEmployee.prototype);
console.log('--------------');
```



#####執行結果
```
{ setEmpNo: [Function: setEmpNo],
  setEmpName: [Function: setEmpName],
  getEmpNo: [Function: getEmpNo],
  getEmpName: [Function: getEmpName] }
--------------
{ setEmpNo: [Function: setEmpNo],
  setEmpName: [Function: setEmpName],
  getEmpNo: [Function: getEmpNo],
  getEmpName: [Function: getEmpName] }
--------------
true
--------------
```
