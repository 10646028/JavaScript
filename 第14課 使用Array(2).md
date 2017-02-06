#第14課 使用Array(2)


## (1) 物件的陣列

#####測試程式
```javascript
//================================
// 宣告一個空陣列, 填入幾個物件
//================================
var array=[{stuNo:'10456001', stuName:'王小明', teacher:'張老師'}, 
           {stuNo:'10456002', stuName:'陳小華', teacher:'李老師'}, 
           {stuNo:'10456003', stuName:'張小文', teacher:'陳老師'}];


//=====================
// 將陣列內容依序取出
//=====================
for(var i=0; i<array.length; i++){
    var s = array[i];
    
    console.log(s.stuNo);
    console.log(s.stuName);
    console.log(s.teacher);   
    console.log('--------------');
}
```

執行結果
```
10456001
王小明
張老師
--------------
10456002
陳小華
李老師
--------------
10456003
張小文
陳老師
--------------
```



## (2) 物件的陣列與建構元函式

#####測試程式
```javascript
//================================
// 宣告一個空陣列, 填入幾個物件
//================================
var array=[];

array.push(new Student('10456001', '王小明', '張老師'));
array.push(new Student('10456002', '陳小華', '李老師'));
array.push(new Student('10456003', '張小文', '陳老師'));


//=====================
// 將陣列內容依序取出
//=====================
for(var i=0; i<array.length; i++){
    var s = array[i];
    
    console.log(s.getStuNo());
    console.log(s.getStuName());
    console.log(s.getTeacher());   
    console.log('--------------');
}


//===========================
// 一建構元函式，用來生成物件
//===========================
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

執行結果
```
10456001
王小明
張老師
--------------
10456002
陳小華
李老師
--------------
10456003
張小文
陳老師
--------------
```
