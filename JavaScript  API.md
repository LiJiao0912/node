### 数据类型

#### String类型

- 字符串长度

```
str.length;
```

####转换成字符串类型

- 字符串拼接  +

```
当 + 两边一个操作符是字符串类型，一个操作符是其它类型的时候，会先把其它类型转换成字符串再进行字符串拼接，返回字符串
```

- [toSting()]()

```
var age = 11;
age.toString();  //"11"
var found = true;
found.toString();  //"true"

输出数值的基数：
var num = 10;
console.log(num.toString(2));   //"1010"
console.log(num.toString(8));   //"12"
console.log(num.toString(10));  //"10"
console.log(num.toString(16));  //"a"
console.log(num.toString());   //"10"
```

- [String()]()

```
obj.String(); 
var value1 = 10;
var value2 = true;
var value3 = null;
var value4;
console.log(String(value1));  // "10"
console.log(String(value2));  // "true"
console.log(String(value3));  // "null"
console.log(String(value4));  // "undefined"
```

​	有些值没有toString()方法的，可以使用String()。比如：		undefined和null

- [typeof]()    获取变量类型 （typeof 是一个操作符， 不是函数）

  - “undefined” -------- 如果这个值未定义
  - “boolean "----------  如果这个值是布尔值
  - “string"--------------如果这个值是字符串
  - “number”------------如果这个值是数值
  - “object”-------------如果这个值是对象 或 null
  - “function”-----------如果这个值是函数

  ```
  console.log(typeof 95);   //number
  console.log(typeof '123');  //string
  console.log(typeof true);  //boolean
  console.log(typeof null);  //object
  ```

### 数值类型

#### 转换成数值类型

- [Number()]()

  ```
  Number()可以把任意值转换成数值，如果要转换的字符串中有一个不是数值的字符，返回NaN

  console.log(Number('123abc'));   // NaN  如果字符串中带有非数字的字符，不能转成数字
  console.log(Number(true));   // 1  可以把布尔值变成数字（true变成1  false变成0）
  console.log(Number('123.5'));   // 123.5
  console.log(Number('abc123'));   // NaN  如果字符串中带有非数字的字符，不能转成数字
  ```
  + 如果字符串中带有非数字的字符，不能转成数字  ，  返回的是   NaN

  + 可以把布尔值变成数字  ( true ==>  1      false ==>  0 )

  + NaN ：特殊的数字

    + NaN 与任何值都不相等，包括他本身

    + [isNaN()]()  : 判断变量是不是一个数字  如果不是数字返回true， 如果是数字返回false

      ```
      console.log(isNaN('123abc'));    //  true   不是数字
      console.log(isNaN(3));       //  false	是数字
      ```

- [parseInt()]()

  ```
  parseInt("要转换的数据"); 
  //如果第一个字符是数字会解析直到遇到非数字结束
  //如果第一个字符不是数字或者符号就返回NaN

  console.log(parseInt('123abc'));  //  123
  console.log(parseInt('abc123'));  //  NaN
  ```

  - 在第一次看到数字时开始转换  到第一个非数字就停止
  - 第一个字符不是数字 直接返回 NaN

- [parseFloat()]()    把字符串转换成浮点数

  ```
  console.log(parseFloat('123abc'));  //  123
  console.log(parseFloat('abc123'));  // NaN
  console.log(parseFloat('123.5'));  //  123.5
  ```

  parseFloat遇到非数字结束，如果解析的内容里只有整数，解析成整数

- \+  ,  - 0

  - +obj     //  取正
  - -obj     //  取负
  - obj - 0

  ```
  var str = '500';

  console.log(+str);	//  500	
  console.log(-str);	//  -500	
  console.log(str - 0);  //  500
  ```

###布尔类型

- [Boolean()]()

  > 0   '(空字符串)'   null    undefined    NaN    会转换成false     其它都会转换成true

  ```
  Boolean();  //  false
  Boolean('');  //  false
  ```

### 数组

- 获取数组长度

  ```
  arr.length
  ```

- 遍历数组 (  [for]() )

  ```
  for(var i = 0; i < arr.length; i++) { // 数组遍历的固定结构 }
  ```

- 新增元素

  ```
  数组名[下标/索引] = 值;
  ```

### 函数

- 函数声明

  ```
  function 函数名(){ // 函数体 }
  ```

- 函数表达式

  ```
   var fn = function() { // 函数体 }
  ```

- 函数自调用

  ```
  (function() {})();
  ```

### 对象

> 字面量 ：11   'abc'    true    []   {}  等
>
> 对象字面量 ：var o = {
>
>   				name: 'zs,
>
>  				 age: 18,
>
>  				 sex: true,
>
>  				 sayHi: function () {
>
> ​    					console.log(this.name);
>
>   				}
>
> ​			};

##### 对象的创建方式

- 对象字面量

- new  Object ()  创建对象

  ```
  var person = new Object();
    person.name = 'lisi';
    person.age = 35;
    person.job = 'actor';
    person.sayHi = function(){
    	console.log('Hello,everyBody');
  }
  ```

- 工厂函数创建对象

  ```
  function createPerson(name, age, job) {
    var person = new Object();
    person.name = name;
    person.age = age;
    person.job = job;
    person.sayHi = function(){
      console.log('Hello,everyBody');
    }
    return person;
  }
  var p1 = createPerson('张三', 22, 'actor');
  ```

- 自定义构造函数

  ```
  function Person(name,age,job){
    this.name = name;
    this.age = age;
    this.job = job;
    this.sayHi = function(){
    	console.log('Hello,everyBody');
    }
  }
  var p1 = new Person('张三', 22, 'actor');
  ```

  new 在执行时会做四件事：

  1. new会在内存中创建一个新的空对象
  2. new 会让this指向这个新的对象
  3. 执行构造函数  目的：给这个新对象加属性和方法
  4. new会返回这个新对象

#####  this 详解

1. 函数在定义的时候this是不确定的，只有在调用的时候才可以确定
2. 一般函数直接执行，内部this指向全局window
3. 函数作为一个对象的方法，被该对象所调用，那么this指向的是该对象
4. 构造函数中的this其实是一个隐式对象，类似一个初始化的模型，所有方法和属性都挂载到了这个隐式对象身上，后续通过new关键字来调用，从而实现实例化

##### 对象的使用

- 遍历对象 （  [for ··· in]() ）

  ```
  for ( var key in obj ) { }
  ```

- 删除对象

  ```
  delete obj.name;
  ```

### Math 对象

- 圆周率  [Math.PI]()

- 生成随机数  [Math.random()]()

- 向下取整 [Math.floor() ]() / 向上取整 [Math.ceil()]()

  ```
  console.log(Math.random());   // 0.6381113651544794
  Math.ceil(Math.random() * 20);  // 13
  Math.floor(Math.random() * 20);  // 
  ```

- 取整，四舍五入 [Math.round()]()

- 绝对值 [Math.abs()]()

- 求最大值 [Math.max()]() 和最小值 [Math.min()]()

  ```
  console.log(Math.max(16,32,21,15,2));  //  32
  console.log(Math.min(16,32,21,15,2));  //  2

  console.log(Math.max());  // -Infinity
  当max没有进行参数的传递 返回 -infinity

  console.log(Math.min());  //  Infinity
  当min没有进行参数的传递 返回 infinity
  ```

- 正弦/余弦  [Math.sin() / Math.cos()](Math.sin()/Math.cos())

- 求指数次幂/求平方根 [Math.pow() / Math.sqrt()](Math.pow()/Math.sqrt())


### Date对象

- 获取当前时间

  ```
  Date构造函数的参数
  1. 毫秒数 1498099000356		new Date(1498099000356)
  2. 日期格式字符串  '2015-5-1'	 new Date('2015-5-1')
  3. 年、月、日……				  new Date(2015, 4, 1)   // 月份从0开始
  ```

  - [var now = new Date(); ](Math.pow()/Math.sqrt())

    ```
    var date = new Date();
    console.log(date);  //  Thu Nov 23 2017 08:59:57 GMT+0800 (中国标准时间)
    console.log(date.valueOf());  //  1511398797854
    ```

  - [var now = Date.now();](Math.pow()/Math.sqrt())

    ```
    var now = Date.now();console.log(now);  // 1511399147000

    //H5 提供的
    ```

  - [var now = + new Date();](Math.pow()/Math.sqrt())

    ```
    var now = + new Date();console.log(now);  // 1511399214085

    //不支持 H5的浏览器
    ```

- 日期格式化

  - 转换成字符串 [toString()](Math.pow()/Math.sqrt())

    ```
    console.log(date.toString());  // Thu Nov 23 2017 08:59:57 GMT+0800 (中国标准时间)
    ```

  - 获取毫秒值  [valueOf()](Math.pow()/Math.sqrt())

    ```
    var date = new Date();
    console.log(date);  //  Thu Nov 23 2017 08:59:57 GMT+0800 (中国标准时间)
    console.log(date.valueOf());  //  1511398797854

    // valueOf用于获取对象的原始值，valueOf()内部调用的getTime()
    ```

- 获取日期指定部分

  + [getTime()](Math.pow()/Math.sqrt()) 毫秒数  （和[valueOf ()]() 结果一样）

    ```
    var date = new Date();
    console.log(date.getTime());  //  1511399725733
    ```

  + [getSeconds()](Math.pow()/Math.sqrt())  秒   0-59

    ```
    var date = new Date();
    console.log(date.getSeconds());  //  20
    ```

  + [getMinutes()](Math.pow()/Math.sqrt()) 分钟  0-59

    ```
    var date = new Date();
    console.log(date.getMinutes());  // 17
    ```

  + [getHours() ](Math.pow()/Math.sqrt()) 返回小时  0-23

    ```
    var date = new Date();
    console.log(date.getHours() );  //  9
    ```

  + [getDay()](Math.pow()/Math.sqrt()) 返回星期几  （ 0周日）

    ```
    var date = new Date();
    console.log(date.getDay());  // 4
    ```

  + [getDate() ](Math.pow()/Math.sqrt()) 返回当前月的第几天

    ```
    var date = new Date();
    console.log(date.getDate() );  // 23
    ```

  + [getMonth()](Math.pow()/Math.sqrt()) 返回月份，***从0开始***

    ```
    var date = new Date();
    console.log(date.getMonth() );  // 10
    ```

  + [getFullYear()](Math.pow()/Math.sqrt()) 返回4位的年份  如 2016

    ```
    var date = new Date();
    console.log(date.getFullYear() );  // 2017
    ```


### Array 对象

- 创建数组

  + 字面量

    ```
    ex:var arr = [1, 2, 3];
    ```

  + [new Array ()]()

    ```
    var arr = new Array(); 
    var arr = new Array('zs', 'ls', 'ww');
    var arr = new Array(1, 2, 3, 4);
    ```

- 检测一个对象是否是数组

  - [instanceof]()

    ```
    var array = new Array(1,2,4,'a','b');
    console.log(array instanceof Array);  //  true
    ```

  - [Array.isArray()]()  

    ```
    Array.isArray() 是 HTML5中提供的方法，有兼容性问题

     var array = new Array(1,2,4,'a','b');
     var result= Array.isArray(array);
     console.log(result);  //  true
    ```

    函数的参数，如果要求是一个数组的话，可以用这种方式来进行判断

- toString()/valueOf()

  - [toString()]()   把数组转换成字符串，逗号分隔每一项

    ```
    var array = [1,2,3,4,5];
    var result = array.toString();
    console.log(result);  //  1,2,3,4,5
    ```

  - [valueOf()](/valueOf())   返回数组对象本身

- 栈操作（先进后出）

  - [push()](/valueOf())   ：将一个或多个元素添加到数组的末尾,并返回新数组的长度

    ```
    var array = [1,2,3,4,5];
    var result = array.push('a',6,true);
    console.log(result);  //  8
    console.log(array);  //  (8) [1, 2, 3, 4, 5, "a", 6, true]
    ```

  - [pop](/valueOf())   :取出数组中的最后一项，返回被删除的项

    ```
    var array = [1,2,3,4,5];
    var result= array.pop()
    console.log(result);  //  5
    console.log(array);  //   (4) [1, 2, 3, 4]
    ```

-  队列操作(先进先出)   ：结合使用 shift() 和 push() 方法 ， 可以像使用队列一样使用数组

  - [unshift()](unshift() 	//在数组最前面插入项，返回数组的长度)     ：在数组最前面插入项，返回数组的新长度

    ```
    var array = [2,3,4,5];
    console.log(array.unshift(1));  //  5
    console.log(array);  //  (5) [1, 2, 3, 4, 5]
    ```

    - [shift()](shift()//取出数组中的第一个元素，修改length属性)        ：取出数组中的第一个元素，返回被删除的项

    ```
    var array = [1,2,3,4,5];
    console.log(array.shift()); //  1
    console.log(array);  //  (4) [2, 3, 4, 5]
    ```

- 排序方法

  - [reverse()]()  ：翻转数组，返回新数组

    ```
    var array = [2,3,4,5];
    console.log(array.reverse());  //  (4) [5, 4, 3, 2]
    console.log(array);  //  (4) [5, 4, 3, 2]
    ```

  - [sort()]() : sort()方法是根据字符，从小到大排序    此方法在适当的位置对数组的元素进行排序，并返回数组

    ```
    var array = [0,1,2,3,10,15];
    console.log(array.sort());  //  (6) [0, 1, 10, 15, 2, 3]
    console.log(array);  //  (6) [0, 1, 10, 15, 2, 3]
    ```

    **优化 ：接收一个比较函数作为参数  用于指定排序方式**

    > 比较函数接收两个参数，如果第一个参数应该位于第二个参数之前则返回一个负数，如果俩个参数相等则返回0，如果第一个参数应该位于第二个参数之后则返回一个正数，代码如下：

    ```
    function compare(value1,value2) {
      if(value1 < value2) {
        return -1;
      } else if (value1 > value2) {
        return 1;
      }  else {
        return 0;
      }
    }
    简化：
    function compare(value1,value2) {
       return value1 - value2;
    }

    var array = [0,1,2,3,10,15];
    console.log(array.sort(compare));  //  (6) [0, 1, 2, 3, 10, 15]
    console.log(array);  //  (6) [0, 1, 2, 3, 10, 15]
    ```

- 操作方法

  - [concat()](Math.pow()/Math.sqrt())   ：把参数拼接到当前数组，返回拼接后的新数组

    ```
    var array = [1,2,3];
    console.log(array.concat(array));  //  (6) [1, 2, 3, 1, 2, 3]
    console.log(array);  //  (3) [1, 2, 3]
    ```

  - [slice() ](Math.pow()/Math.sqrt())   ：从当前数组中截取一个新的数组，**不影响原来的数组** 

    - [一个参数](Math.pow()/Math.sqrt())：从指定位置起到数组末尾的所有
    - [两个参数](Math.pow()/Math.sqrt())：返回起始和结束位置之间的项，但不包括结束位置的项

    ```
    var array = [1,2,56,33,43,45,78,12];
    console.log(array.slice(3));  //  (5) [33, 43, 45, 78, 12]
    console.log(array.slice(2,5));  //  (3) [56, 33, 43]
    console.log(array);  //  (8) [1, 2, 56, 33, 43, 45, 78, 12]
    ```

    - 如果参数中有**负数**，则用数组的长度加上该数来确定相应的位置
    - 如果结束位置小于起始位置，则返回空数组

    ```
    var array = [1,2,56,33,43,45,78,12];
    console.log(array.slice(-3,-1));  //  (2) [45, 78]
    console.log(array.slice(5,7));  //  (2) [45, 78]

    console.log(array.slice(6,2));  //  []
    console.log(array);  //  (8) [1, 2, 56, 33, 43, 45, 78, 12]
    ```

  - [splice() ](Math.pow()/Math.sqrt())   ：主要用途是向数组的中部插入项

    - **删除**（可以删除任意数量的项）：[两个参数](Math.pow()/Math.sqrt()) ，要删除的第一项的位置和要删除的项数

    ```
    var array = [1,2,56,33,43,45,78,12];
    console.log(array.splice(3,3));  //  (3) [33, 43, 45]
    console.log(array);  //  (5) [1, 2, 56, 78, 12]
    ```

    - **插入** （可以向指定位置插入任意数量的项）：[三个参数](Math.pow()/Math.sqrt()) ，起始位置、要删除的项数和要插入的任意数量的项（如果要插入多个项可以再传入第四、第五，以至任意个项）

    ```
    console.log(array.splice(2,3,7,4,1,14));  //  (3) [56, 78, 12]
    console.log(array);  //  (9) [1, 2, 7, 4, 1, 14, 45, 78, 12]
    ```

    + **替换** （可以向指定位置插入任意数量的项）： [三个参数](Math.pow()/Math.sqrt()) ，起始位置、要删除的项数和要插入的任意数量的项，插入的项不必与删除的项数相等

    ```
    console.log(array.splice(0,2,24,23,22));  //  (2) [1, 2]
    console.log(array);  //  (7) [24, 23, 22, 7, 4, 1, 14]
    ```

- 位置方法（只找第一个匹配的）

  - [indexOf()](Math.pow()/Math.sqrt()) ：（要查找的项，查找起点位置的索引） 从数组的开头（位置0）开始向后查找，返回要查找的项在数组中的位置，没有找到返回 -1  ， 查找的项必须严格相等（===）

    ```
    var num = [1,2,3,4,5,4,3,2,1];
    console.log(num.indexOf(4));  //  3
    console.log(num.indexOf(4,4));  //  5
    console.log(num.indexOf(6));  //  -1
    ```

  - [lastIndexOf()](Math.pow()/Math.sqrt()) ：（要查找的项，查找起点位置的索引）从数组的末尾开始向前查找，返回要查找的项在数组中的位置，没有找到返回 -1  ， 查找的项必须严格相等（===）

    ````
    var num = [1,2,3,4,5,4,3,2,1];
    console.log(num.lastIndexOf(4));  //  5
    console.log(num.lastIndexOf(4,4));  //  3
    console.log(num.lastIndexOf(6));  //  -1
    ````

- 迭代方法 （不会修改数组中包含的值）

  - [every()]() ：对数组中的每一项运行给定的函数，如果该函数对每一项都返回 true ，则返回true ， 否则返回 false 。**用于查询数组中的项是否满足某个条件**

  - [some()]() ：对数组中的每一项运行给定的函数，如果该函数对任一项返回 true ，则返回 true 。**用于查询数组中的项是否满足某个条件**

    ```
    var num = [1,2,3,4,5,4,3,2,1];
    var numBool1 = num.every(function(item,index,num) {
    	return item > 3;
    });
    console.log(numBool);  //  false
    var numBool2 = num.some(function(item,index,num) {
    	return item > 3;
    });
    console.log(numBool2);  //  true
    ```

  - [filter()]() ：对数组中的每一项运行给定的函数，返回该函数会返回 true 的项组成的数组 。**用于查询数组中满足某个条件的所有项** 

    ```
    var num = [1,2,3,4,5,4,3,2,1];
    var numBool = num.filter(function(item,index,num) {
    	return item > 3;
    });
    console.log(numBool);  //  (3) [4, 5, 4]
    ```

  - [forEach()]() ：对数组中的每一项运行给定的函数，没有返回值 。该方法与 for 方法相似

    ```
    var num = [1,2,3,4,5];
    var result = num.forEach(function(item,index,num) {
    	console.log(item);
    });
    // 1 2 3 4 5
    ```

  - [map()]() ：对数组中的每一项运行给定的函数，返回每次函数调用的结果组成的数组

    ```
    var num = [1,2,3,4,5,4,3,2,1];
    var result = num.map(function(item,index,num) {
    	return item + 3;
    });
    console.log(result);  //  (9) [4, 5, 6, 7, 8, 7, 6, 5, 4]
    console.log(num);  //   (9) [1, 2, 3, 4, 5, 4, 3, 2, 1]
    ```

- 归并方法

  - [reduce()]() ：从数组的第一项开始，逐个遍历到最后

    ```
    //求数组中所有值的和

    var values = [1,2,3,4,5];
    var sum = values.reduce(function(prev, cur, index, array) {
    	console.log(prev,cur);  // 1 2   3 3   6 4   10 5
    	return prev + cur;
    });
    console.log(sum);  //  15
    ```

  - [reduceRight()]() ：从数组的最后一项开始，向前遍历到第一项

- 转换方法 [join()]() 

  - 只能接收一个参数，用作分隔符的字符串，返回包含所有数组项的字符串
  - 没有传入参数 或者 传入了 undefined ，则使用逗号作为分隔符

  ```
  var colors = ['red', 'green', 'blue'];
  console.log(colors.join(','));  //  red,green,blue
  console.log(colors.join('|'));  //  red|green|blue
  console.log(colors.join());  //  red,green,blue
  console.log(colors.join(undefined));  //  red,green,blue
  ```

- 清空数组

  - [arr = []]() 
  - [arr.length = 0 ]()
  - [arr.splice(0, arr.length) ]() 

- 案例

  - 将一个字符串数组输出为|分割的形式，比如“刘备|张飞|关羽”。使用两种方式实现

    ```
    方法一（join） ：
    var array = ["刘备","张飞","关羽"];
    console.log(array.join('|'));  //  刘备|张飞|关羽

    方法二（遍历数组） ：
    var array = ["刘备","张飞","关羽"];

    1.forEach
    var str = [];
    array.forEach(function (item, index, array) {
    	if (index==0) {
    		str[0] = item;
    	} else {
    		str += '|' + item;
    	}
    });

    2.for
    var str = array[0];
    for (var i=1; i<array.length; i++) {
    	str += "|" + array[i];
    }
    console.log(str);

    3.分装函数
    function Join (array,symbol) {
    	array = array || '';
    	symbol = symbol || ',';
    	if (!array.length) {
    		return array = [];
    	}
    	var str = array[0];
    	for (var i=1; i<array.length; i++) {
    		str += symbol + array[i];
    	}
    	return str;
    }
    console.log(Join(array,"|"));
    ```

  - 将一个字符串数组的元素的顺序进行反转。["a", "b", "c", "d"] -> [ "d","c","b","a"]。使用两种种方式实现。提示：第i个和第length-i-1个进行交换

    ```
    var arr = ["a", "b", "c", "d"];

    方法一 ：
    console.log(arr.reverse(1));

    方法二 ：
    var str = [];
    for (var i = arr.length; i > 0; i--) {
    	str[str.length] = arr[i-1] ;
    }
    console.log(str);
    ```

  - 工资的数组[1500, 1200, 2000, 2100, 1800],把工资超过2000的删除

    ```
    var array = [1500, 1200, 2000, 2100, 1800];
    方法一 :
    var str = array.filter(function(item,index,array) {
    	return item <= 2000;
    });
    console.log(str);

    方法二 ：
    var str = [];
    for (var i = 0; i < array.length; i++) {
    	if (array[i] <= 2000) {
     		str[str.length] = array[i];
     	}
     }
     console.log(str);
    ```

  - ["c", "a", "z", "a", "x", "a"]找到数组中每一个a出现的位置

    ```
    var array =  ['c', 'a', 'z', 'a', 'x', 'a'];
    do {
      var index = array.indexOf('a',index + 1);
      if (index != -1){
        console.log(index);
      }
    } while (index > 0);
    ```

  -  ["c", "a", "z", "a", "x", "a"] 编写一个方法去掉一个数组的重复元素

    ```
    var array =  ['c', 'a', 'z', 'a', 'x', 'a'];
    Array.prototype.delete = function() {
    	var str = [];
    	var json = {};
    	for (var i = 0; i < this.length; i++) {
    		if (!json[this[i]]) {
    			str[str.length] = this[i];
    			json[this[i]] = 1;
    		}	
    	}
    	return str;
    }
    console.log(array.delete());
    ```

### 字符串类型 

- 字符串不可变

- 字符串对象的常用方法

  - 字符方法

    - [charAt ()]()   获取字符串指定位置的字符

      ```
      var s = 'abcde';
      console.log(s.charAt(0));  //  a

      for (var i = 0; i < s.length; i++) {
      	console.log(s.charAt(i));  //  a  b  c  d  e
      }
      ```

    - [charCodeAt ()]() 获取指定位置的字符的 ASCII 码

      ```
      var s = 'abcde';
      console.log(s.charCodeAt(0));  //  97  98  99  100  101
      ```

    - [str [ 索引 ]]()  HTML5，IE8+支持 和 [charAt ()]()  等效

      ```
      var s = 'abcde';
      for (var i = 0; i < s.length; i++) {
      	console.log(s[i]);  //  a  b  c  d  e
      }
      ```

  - 字符串操作方法 

    - [concat ()]()  拼接字符串，等效于 +

      ```
      var s = 'abcde';
      var str = s.concat('12345','一二三'); 
      console.log(s);  //  abcde
      console.log(str);  //  abcde12345一二三
      ```

    - [slice ()]()  截取字符串     

      - 两个参数：第一个，起始位置 ；第二个：结束位置 （如果没有传入第二个参数，将字符串的长度作为结束位置）  **返回值不包含结束位置**

      ```
      var s = "hello world";
      console.log(s.slice(3));  //  lo world
      console.log(s.slice(3, 7));  //  lo w
      ```

      - 参数是负值  ：slice()方法会将传入的负值与字符串的长度相加

      ```
      var s = "hello world";
      console.log(s.slice(-3));  //  rld
      console.log(s.slice(-3, -1));  //  rl  相当于 slice(8, 10)
      ```

    - [substring ()]()    截取字符串     

      - 两个参数：第一个，起始位置 ；第二个：结束位置 （如果没有传入第二个参数，将字符串的长度作为结束位置）  **返回值不包含结束位置**

      ```
      var s = "hello world";
      console.log(s.substring (3));  //  lo world
      console.log(s.substring (3, 7));  //  lo w
      ```

      - substring()方法会把所有负值参数都转换为 0

      ```
      var s = "hello world";
      console.log(s.substring(-3));  //  hello world
      console.log(s.substring(-3, -1));  //  空字符串
      ```

    - [substr ()]() 

      - 两个参数：第一个，起始位置 ；第二个：返回的字符个数（结束位置的字符取不到）

      ```
      var s = "hello world";
      console.log(s.substr(3));  //  lo world
      console.log(s.substr(3, 7));  //  lo worl
      ```

      - 参数是负值 ： substr()方法将负的第一个参数加上字符串的长度，而将负的第二个参数转换为 0。


      ```
      var s = "hello world";
      console.log(s.substr(-3));  //  rld
      console.log(s.substr(-3, -7)); // 空字符串
      ```

- 位置方法 （从一个字符串中搜索给定的字符串，返回给定字符串的第一次出现的位置，如果没有则返回 -1）

  - [indexOf ()]()   ：从前向后搜索

    - 一个参数 ：要搜索的字符串
    - 两个参数 ：要搜索的字符串 ， 搜索的位置

  ```
  var s = "hello world";
  console.log(s.indexOf('l'));  //  2
  console.log(s.indexOf('l', 3));  //  3
  ```


  - [lastIndexOf ()]()  ：从后向前开始搜索

    - 一个参数 ： 要搜索的字符串 
    - 两个参数 ：要搜索的字符串 ， 搜索的位置

    ```
    var s = "hello world";
    console.log(s.lastIndexOf('l'));  //  9
    console.log(s.lastIndexOf('l', 3));  //  3
    ```

- 去除空白

  - [trim ()]()  ：去除字符串前后的空白

    ```
    var str = "  hello world  ";
    console.log(str.trim());  //  "hello world"
    console.log(str);  // "  hello world  "
    ```

  - [trimLeft ()]()   ：删除字符串左侧的空白

    ```
    var str = "  hello world  ";
    console.log(str.trimLeft ());  //  "hello world  "
    console.log(str);  //  "  hello world  "
    ```

  - [trimRight ()]() ：删除字符串右侧的空白

    ```
    var str = "  hello world  ";
    console.log(str.trimRight());  //  "  hello world"
    console.log(str);  //  "  hello world  "
    ```

- 大小写转换 （Locale 是针对特定地区的实现）

  - [to(Locale)UpperCase ()]() ：转换大写
  - [to(Locale)LowerCase ()]() ：转换小写

  ```
  var s = "hello world"; 
  console.log(s.toLocaleUpperCase());  //  HELLO WORLD
  console.log(s.toUpperCase());  //  HELLO WORLD
  console.log(s.toLocaleLowerCase());  //  hello world
  console.log(s.toLowerCase());  //  hello world
  ```

- 模式匹配

  - [search () ]() ：查找模式  ，参数：由字符串或 RegExp 对象指定的一个正则表达式 ；返回值：字符串中第一个匹配项的索引；如果没有找到匹配项，则返回-1

    ```
    var text = "cat, bat, sat, fat"; 
    var pos = text.search(/sat/); 
    console.log(pos);  //  10
    ```

  - [replace ()]() ：替换 ，参数：如果第一个参数是字符串，只会替换第一个子字符串；如果第一个参数是正则表达式（还要指定为全局（g）），会替换所有的子字符串。第二个参数可以使函数，实现更精细的替换操作

    ```
    var text = "cat, bat, sat, fat"; 
    var result = text.replace("at","ond"); 
    console.log(result);  //  cond, bat, sat, fat

    var result = text.replace(/at/,"ond"); 
    console.log(result);  //  cond, bat, sat, fat  委表示全局 g

    var result = text.replace(/at/g,"ond"); 
    console.log(result);  //  cond, bond, sond, fond
    ```

  - [split ()]() ：按照指定的分隔符分割字符串，参数：第一个参数可以是字符串也可以是正则表达式；可选择接受第二个参数，用于指定数组大小。返回分割分割后的字符串

    ```
    var colorText = "red,blue,green,yellow"; 
    colorText.split(",");  // (4) ["red", "blue", "green", "yellow"]

    colorText.split(",", 2);  //  (2) ["red", "blue"]

    colorText.split(/[^\,]+/);  // (5) ["", ",", ",", ",", ""]
    ```

  - [fromCharCode ()]() ：接收一个或多个字符编码，然后将他们转换成一个字符串。与 `charCodeAt ()` 执行的是相反的操作  



##### 案例

- 截取字符串“我爱中华人名共和国”，中的“中华”

  ```
  1.substr方法：
  var s = '我爱中华人民共和国'; 
  var str = s.substr(2,2);
  console.log(str);  //  中华

  2.substring 方法：
  var str = s.substring(2,4);
  console.log(str);  //  中华

  3.slice 方法
  var str = s.slice(2,4);
  console.log(str);  //  中华
  ```

  ​









































































































































### 基本包装类型

> 为了方便操作基本数据类型，JavaScript还提供了三个特殊的引用类型：String/Number/Boolean ，都具有与各自的基本类型相应的特殊行为。