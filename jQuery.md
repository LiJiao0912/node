# jQuery

### 一、jQuery的基本概念

#### 1. 什么是jQuery

 `jQuery`是一个轻量级的`JavaScript`的类库,直白的说: `jQuery`就是封装好的js文件

	库: 辅助性的工具文件,能够帮助提高开发效率    库为辅 
	框架: 提供一个整体的基础的解决方案,你需要在它的规则上进行开发  框架为主
	
	库分为两种  
	  1. 类库：（代码的组织形式不一样,采用面向对象的形式组织代码  ）  
	  2. 函数库:（采用面向过程的代码组织形式）   
##### `jQuery`特点(区别于js):

1. 强大的DOM选择器
2. 封装了大量丰富且实用的方法
3. 丰富的动画效果
4. 灵活的ajax
5. 完整的事件机制
6. 已经处理好兼容性问题  不再需要考虑兼容性
7. 操作非常简单和方便  

#### 2. 学习jQuery 学什么、该如何学

- 学习`jQuery`就是在学它已经封装好的一大堆方法
- 该如何学?
  - 官网学习
  - github学习
  - 其他相关网站和论坛
  - 离线文档和书籍 (电子书 锋利的jQuery)     js (js高级程序设计  js权威指南)

#### 3. 如何下载jQuery

- 去官网下载

- github下载

- 其他相关网站和论坛

- 通过包管理器安装`npm`  、`bower` 、`yarn` (后面会学)    

  `node` 通过`npm  install  jquery`   通过命令安装

- 通过在线cdn使用: `jquery`的`cdn`

  **cdn概念**: 网络资源分发节点

####  4. jQuery的版本

- **大的版本**

  - 1.x.x   兼容了IE 6 7 8 ，所以更加适合**pc端**开发使用 

    jquery.1.6.2.js、jquery.1.10.5.js、 jquery.1.12.4.js

    ##### 咱们使用1版本里面的最高版本 1.12.4

  - 2.x.x   没有兼容IE 6 7 8 一般 在**移动端**使用

  - 3.0.0   添加了很多新的特性和功能，摈弃了很多旧的特性  是未来 jQuery 的发展趋势，适合**移动端**使用

- **版本中 分为**

  - 压缩版  1.12.4.min.js

    适合生产阶段使用，运行在线上  (将代码进行压缩  体积更小  传输速度更快)

  - 未压缩版   1.12.4.js

    适合开发阶段使用  (适合参考学习)

> jQuery的开发者发起者 约翰·莱西阁   john resig

###  二 、使用jQuery

> 想要用jQuery? 怎么办  花钱  花什么钱  花美元  **$**

1. 引包

   常见错误: 1）引包路径错误；2 ）把 jq 引到使用它的后面 或者忘记引包

2. 使用的 jq 的步骤

   1）引包、2）编写入口函数 、3）具体代码实现

3. 入口函数

   - js 中   `window.onload = function(){}`
   - jQuery 中   `$(function(){});` 、`$(document).ready(function(){要做事情})`

   **JS 与 JQ的入口函数的区别**：

   	js：当整个浏览器程序全部加载完毕(html、css以及外部引入图片和其他资源)之后，触发该事件，执行里面的代码 相当于一个入口函数
   	jQuery：当整个浏览器程序全部加载完毕(html和css渲染树生成，不需要考虑外部的资源的引入)之后触发

   **jQuery 和 js的对比**

   	1  入口函数   
   		js 多个入口函数 后者覆盖前者
   		jq 多个入口函数 不会发生覆盖
   	2  js 代码有错误 会报错  直接停止
   	   jq 有错误 不报错  后面代码仍然可以继续执行
   	3  兼容性方面 : innerText (老版火狐浏览器 不支持 textContent) 说明有兼容性
   		   js  有很多兼容性问题 需要考虑 
   		   jq  text() 已经处理了兼容性问题       js  ev = ev || event;    jq ev 
   	4 js操作繁琐  jq操作简便

### 三、jQuery的中的$ 符号

`/$();`  $本质上是一个函数  可以接收参数

- 如果你传入了一个匿名函数  那 意味着 是入口函数    
- 如果你传入的是一个字符串  那么它的意思就要 划分了
  - `#div` 意思是获取id名为div的元素
  - `.div` 意思是获取类名div的元素   
  - `div`  意思是获取标签名为div的元素

### 四、jQuery和JS的区别

jQuery对象: 就是通过`$`符号获取页面中的元素 就是jq对象

DOM对象: 就是通过js获取页面中的元素 称为dom对象


	jQuery对象 才可以用jq的方法 
	原生js的DOM对象 可以使用js的方法

- jq对象如何转成  => js的DOM对象

  ~~~
  $("#box")[0].style.background = "red";
  $("#box").get(0).style.background = "blue";
  ~~~

- js的DOM对象 => jq对象

  ~~~
  var oBox = document.getElementById("box");
  $(oBox).css("background","purple");		
  ~~~

### 选择器

#### 基本选择器

- ID选择器

  `$("#box").css("background","blue");`

- 类选择器

  `$(".aa").css("background","green");`

- 标签选择器

  `$('p').css("background","purple");`

- 并集选择器  兄弟关系选择器

  `$("#box,.aa,a").css("border","3px aqua solid");`

- 交集选择器

  ` $("span.aa").css("background","yellow")`

#### 层级选择器

- 子代选择器

  `$("#oUl>li").css("border","4px solid pink");`

- 后代选择器

  `$("#oUl li").css("border","4px solid greenyellow");`

#### 过滤选择器

- `:eq（index）`

  `$("ul li:eq(3)").css("background","red");`

- `:odd （奇数）`、`:even  (偶数)`

  ~~~
  $("ul li:odd").css("background","blue");
  $("ul li:even").css("background","deepskyblue");
  ~~~

- `:first ` 、`:last`

   $('ul li:last').css('background', 'orange')
   	$('ul li:first').css('border', '3px solid black')

#### 筛选选择器

> 筛选选择器都是方法  都有()

- 子类选择器  `children(selector)`

  - 相当于 `$("ul>li")`
  - 括号中 可以写 参数，参数是可选的   筛选的意思

  ~~~
  $("#box>span")   // box的下面的所有的直接子元素

  $("#box").children("span").css("background","red");
  ~~~

- 后代选择器  `find(selector)`

  - 相当于 `$("ul li")`

  `$("#box").find("span").css("border","2px solid green");`

- 兄弟选择器  `A.siblings()`

  - A 的其他兄弟们
  - 参数可选   用来筛选具体的兄弟们

  `$("#oSpan").siblings().css("backgroundColor","yellow");`

- 父级选择器   `A.parent()`

  - 找到A的父级 (结构上的父级)

  `$("#oSpan").parent().css("border","4px dashed purple");`

  > `A.parents()`   A的所有的直接父辈们 

- `eq(index)`   选中所有元素中第几个 

  ~~~
  $("#box>span").eq(2).css("color","white");
  $("#box>span:eq(2)").css("color","white");
  ~~~

  > `next()`  下一个兄弟
  >
  > `prev()`  上一个兄弟节点
  >
  > `index()`  直接可以获取索引    （相当于原生中 你建立索引   aBtn[i].index = i;）
  >
  >   **注意：**它指的是 在当前的并列兄弟们之间 排行第几 索引就是几
  >
  > `A.index()`  A 在并列兄弟们之间排行老几

### jQuery中常用的方法

#### html()   可以读取或者设置 某个元素中的内容

~~~
$("#box").html("<strong>哈哈哈哈<strong>");
$("#box").text("<strong>哈哈哈哈<strong>");
~~~

#### text()

#### css()   用来设置或者读取样式的

- 读取

  `$("#box").css("backgroundColor")`

- 设置

  - 设置单条样式

    ~~~
    $("#box").css("backgroundColor","green");
    $("#box").css("background-color","green");
    $("#box").css("border","3px solid purple");
    $("#box").css("fontSize","50px");
    ~~~

  - 设置多条样式

    ~~~
    $("#box").css({
        "background-color":"green",
        "border":"3px solid purple",
        "fontSize":"50px"
    })
    $("#box").css({
        backgroundColor:"green",
        border:"3px solid purple",
        fontSize:"50px"
    })

    //json格式  键名加不加引号都行  
    //但是后端服务器返回的json数据  键名必须加引号 而且是双引号
    ~~~

#### 操作类

案例：tab栏切换案例、选项卡

- 添加类的方法   `addClass(需要加的类名)`

  ~~~
  $("#box").addClass("lei abc");
  $("ul li").addClass("lei abc");
  ~~~

- 移除类的方法   `removeClass(需要移除的类)`

  - 不写参数：会将元素的所有的类 都移除
  - 写上类：可以移除它身上的特定的类

  ~~~
  $("#box").removeClass();         // 移除所有类
  $("#box").removeClass("abc");    // 移除abc的类
  ~~~

- 判断是否有类  `hasClass(需要判断的类)`

  - 返回值是布尔类型的值

- 切换类   `toggleClass()`

#### 动画系列

- 显示与隐藏

  - `show()`      显示
  - `hide() `       隐藏
  - `toggle() `   在显示与隐藏之间切换

  **参数：**

  - 无参数：相当于直接显示和隐藏
  - 第一个参数： 动画执行时间，单位是毫秒。时间越大，效果越慢。时间不但可以写具体数值，还可以接收一些固定的字符串：
    - `fast`  快  （200ms）
    - `slow`  慢   （600ms）
    - `normal`   正常   （400ms）   默认
    - 如果写其他字符串 默认是`normal`  
  - 第二个参数 : 回调函数 ，当前动画执行完毕 之后 要执行的函数

  > **这两个方法 其实改变的是元素的宽和高 以及透明度**

  ~~~
  $("input:eq(0)").click(function(){		
  	$("#box").show(500,function(){
  		alert("显示出来了")
  	});		
  })
  		
  $("input:eq(1)").click(function(){		
  	$("#box").hide(1000,function(){
  		alert("已经隐藏啦")
  	});		
  })

  $("input:eq(2)").click(function(){
  	$("#box").toggle(1000);
  })
  ~~~

- 滑入滑出

  - `slideDown() `       滑入
  - `slideUp()`          滑出
  - `slideToggle()`   在滑入滑出之间切换

  **参数：**

  - 第一个参数： 动画执行时间，单位是毫秒。一些固定的字符串
  - 第二个参数 : 回调函数 ，当前动画执行完毕 之后 要执行的函数

  > **内部改变的是元素的高(height)**

  ~~~
  $(function(){
  	$("input:eq(0)").click(function(){
  		// 让div滑入
  		$("#box").slideDown(1000);
  	})
  	
  	$("input:eq(1)").click(function(){
  		// 让div滑入
  		$("#box").slideUp(1000,function(){
  			alert("滑出啦")
  		});
  	})
  	
  	$("input:eq(2)").click(function(){
  		// 让div切换滑入滑出
  		$("#box").slideToggle(2000);
  	})
  })
  ~~~

  案例：修改下拉菜单为滑动效果

- 淡入淡出

  - `fadeIn()`       淡入
  - `fadeOut()`     淡出    
  - `fadeToggle()`   在淡入淡出之间切换 
  - `fadeTo()`        变化到指定透明度

  **参数：**

  - 第一个参数： 动画执行时间，单位是毫秒。一些固定的字符串
  - 第二个参数（可选） : 回调函数 ，当前动画执行完毕 之后 要执行的函数 

  变化到指定透明度的参数：

  - 第一个参数：动画执行时间  这个参数必须写
  - 第二参数：指定透明度
  - 第三个参数：回调函数

  ~~~
  $(function(){
  	$("input:eq(0)").click(function(){
  		$("#box").fadeIn(1000);
  	})
  	
  	$("input:eq(1)").click(function(){
  		$("#box").fadeOut(1000);
  	})
  				
  	$("input:eq(2)").click(function(){
  		$("#box").fadeToggle(1000);
  	})
  	
  	$("input:eq(3)").click(function(){
  		$("#box").fadeTo(1000,0.3,function(){
  			alert("当前动画已经执行完了")
  		});
  	})
  })
  ~~~

  案例： 京剧小人淡入淡出 、 淡入淡出轮播图 

- 自定义动画   `animate`    时间版

  这个动画方法可以支持大部分属性运行，但是一些特殊的属性不支持，因此需要额外处理 ，比如：颜色不能运动，去官网载一个颜色插件，引入进来 就可以实现颜色运动变化。

  > jquery中的运动算法和flash中的运动是一样的算法（tween算法），tween.js （外部动画库文件）
  >
  > 补间动画  `startMove`     速度版动画     startMove.js
  >
  > ​	谁运动  运动什么属性json    速率    回调函数
  >
  > `startMove(obj,{},8,function(){})`

  **参数：**

  - 第一个参数：需要运动什么属性    json格式  

  - 第二个参数：运动需要的时间 ，单位毫秒。也支持固定字符串 ：`slow`、`fast `、`normal`

  - 第三个参数（可选）：运动形式，jQuery中默认有两种运动形式：`swing` 慢快慢（默认）、`linear` 匀速

    **注意：**可以在这里 引入一个基于jQuery的一个动画库，实现多种运动形式，运动形式取决于运动的速度算法

  - 第四个参数 ：回调函数

  ~~~
  $(function(){
  	$("#box").animate({
  		width:300,
  		height:400,
  		left:500,
  		top:200
  	},2000,"linear");
  })
  ~~~

#### 动画队列的问题

>  **动画队列**，一个物体 触发一个动画时间  由于动画需要时间播放，但是你多次快速触发了多次动画事件，它就会积累很多动画。这些动画会放入一个动画队列中，按照先后顺序，等待 依次执行，这就是**动画队列问题**。

解决方法：`stop()`方法

**`stop()`方法  ：  专门用来停止动画队列     最常用的**

参数：

- 无参数: 第一个参数 是false  第二参数 也是false 
- 第一个参数：是否清除队列
- 第二个参数：是否跳转到最终效果

~~~
stop()：相当于stop(false,false)，不清除动画队列、不跳转到最终效果，将当前的动画停止，继续执行后续动画
		
stop(true)：相当于stop(true,false)，清除动画队列、不跳转到最后效果，将当前的动画停止，后续动画队列已经清除了，所以不执行
		
stop(true,true)：清除动画队列，将当前动画停止，直接跳转到当前的动画的最终效果
		
stop(false,true)：不会清除动画队列，直接跳转到当前的动画的最终效果，然后继续执行后面动画
	
finish()：完成方法，将所有的动画队列全部清除、停止当前动画，直接跳转到所有的动画的最后的最终效果
		
stop() 一般用的最多
~~~

### jQuery中的DOM节点操作

#### 创建节点

- `$("<div>")`

  ~~~
  var oStrong =  $("<div>");
  //var oStrong =  $("<div>这是内容可以加</div>");
  $("body").append(oStrong);

  $("body").append("<span>哈哈哈</span>");		
  ~~~

- `html()`

  ~~~
  html("<div></div>")
  html("<strong>加粗</strong>")
  ~~~

  ##### `html` 与 `text` 方法的异同：

  - 不同点：

    ~~~
    html方法   能识别标签   和原生js中的  innerHTML 相同
    text方法   不识别标签   和原生js中的  innerText 相同
    ~~~

  - 相同点：

    - 设置

      ~~~
      $("#box").html("<strong>加粗标签</strong>");
      $("#box").text("<strong>加粗标签</strong>");
      ~~~

    - 读取

      ~~~
      $("#box").html()
      $("#box").text()
      ~~~

#### 添加节点

- `A.prepend(B)`  将B放在A里面的最前面
- `A.append(B)`    将B放在A里面的最后面
- `A.after(B) `      将B放在A的后面
- `A.before(B)`    将B放在A的前面

> 如果要是将页面上的元素节点 位置发生操作之后 ，类似于剪切功能 ，原来的位置不存在了

#### 节点清空

- `A.empty()`   把A里面的内容全部清空

- `html()`

  ~~~
  $("#box").html("");  // 相当于 innerHTML= "";
  ~~~

- `remove()`      移除方法

  ~~~
  $("#box").remove();  // 和 empty 方法有一个区别：它会自杀
  ~~~

#### 克隆节点    `clone()`

- 无参数：只拷贝当前的节点

  ~~~
  $("p").clone();
  ~~~

- 有参数`true` 时：会把之前节点的身上的事件也拷贝过来

  ~~~
  $("#box").clone(true); // 加上参数 true  会把之前节点的身上的事件复制过来
  ~~~

### jQuery的属性操作

#### `attr()`  ：设置或者获取html属性

- 读取 ：`$().attr(需要读取的html属性名)`

  ​             如果没有这个属性 那么则获取的是undefined

- 设置 ：`attr(需要设置的属性名，设置的值)`

  - 设置单条属性

    ~~~
    $("#box").attr("class","aa")
    $("#box").attr("title","哈哈标题")
    $("#box").attr("alt","说明文字") 
    ~~~

  - 设置多条属性  用`json`格式 

    ~~~
    $("#box").attr({
    	class:"abc",
    	title:"哈哈",
    	alt:"呵呵",
    	style:"color:red;background-color:blue;"
    })
    ~~~

  > `oBox.getAttribute("haha")`     //  js中可以获取自定义属性的方法

#### `prop() ` ：设置或者获取表单属性

> 像 `disabled` 、 `checked` 、`selected` 类似于属性值为**布尔值**这样的属性 

- 读取：

  ~~~
  $("input:eq(1)").prop("checked")  //  true     false
  $("input:eq(1)").attr("checked")  //  checked  undefined
  ~~~

- 设置：

  ~~~
  $("input:eq(0)").prop("disabled",true);
  $("input:eq(1)").prop("checked",false);
  ~~~

#### `val()` ：专门用来获取 表单中，类似于 `input`文本框中的值，或者 `textarea`文本域中的值 

- 获取 ： 

  ~~~
  $("input[type=text]").val()

  $("input[type=text]").attr("value")  
    // 这个方法获取的只能是初始化设定的那个value值
  ~~~

- 设置：

  ~~~
  $("input[type=text]").val("这是我设置的内容")
  ~~~

### jQuery中尺寸方法

#### `width()` ：宽

~~~
读取：
	console.log( $("#box").width() ); // 样式中定义的宽 100
设置：
	$("#box").width(200)
~~~

#### `innerWidth()` ：宽 + 左右padding

~~~
读取：
	console.log( $("#box").innerWidth() ); // 样式中定义的宽 100  + 左右的padding
设置：
	$("#box").innerWidth(300); // 100+ 50*2   宽200
~~~

#### `outerWidth()`  ：宽 + 左右padding + 左右border

~~~ 
读取：
	console.log( $("#box").outerWidth() );  // 样式中定义的宽 100 + 左右的padding + 左右border
设置：
	$("#box").outerWidth(450);  // 100宽+50*2左右padding + 左右border 5*2  = 210  240+100==340
~~~

#### `outerWidth(true)` ：宽 + 左右padding + 左右border + 左右margin 

~~~
读取：
	console.log( $("#box").outerWidth(true) );  // 样式中定义的宽 100  + 左右的padding + 左右border + 左右margin
设置：
	$("#box").outerWidth(550,true);  // 这个方法如果设置  需要先写数值 再写true
~~~



### jQuery中坐标值的方法

#### `offset()`  ：返回一个json对象，里面有left值 和top值，设置或者获取元素相对于文档document的位置。 

- 读取 ：参考的永远是 `document`文档页面，返回的是一个 json 对象，里面会存上它的 `left` 值(实际偏移量)和 `top` 值  (实际偏移量)，有定位则获取定位的`left + margin` ，没有定位则将它转换成**相对定位**，然后获取相对于文档的实际偏移 。

  ~~~
  $("#box").offset()  //  left:150    top:150
  ~~~

- 设置 ：按照写的设置的值进行设置 ，但是如果有`margin`会减去`margin` 实际得到一个值，这个值作为实际`left` 和 `top` 。

  ~~~
  $("#box").offset({
  	left:300,  // left:250 + margin:50 = 300
  	top:400   // 50+ box转换成相对定位，给它加上top 350
  })
  ~~~

  `A.offsetParent`  ：找的是距离 a 最近的具有定位属性的父级，如果没有定位的父级 ，直接指向`body`

#### `postion()` 

`position`方法只能获取不能设置，不算自身`margin`值，它返回`json`格式 ：{left: ,top:}

	console.log( $("#box2").position() ); // {left:50,top:50}
	console.log( $("#box2").offset() );   // 直接参考的是document文档页面

#### `scrollTop()`  ：设置或者获取垂直滚动条在垂直方向上滚动过的距离（卷去的距离）的位置

- 读取：

  ~~~
  $("html").scrollTop()  // 没有兼容性问题

  // JS中的 scrollTop 有兼容问题 ：
  var scrollT = document.documentElement.scrollTop || document.body.scrollTop;
  console.log(scrollT);
  ~~~

- 设置：

  ~~~
  $("html").scrollTop(300);
  ~~~

> `scroll` 当整个浏览器窗口 滚动条发生滚动的时候 触发该事件



###  jquery中的事件机制

####  简单的事件绑定机制，如：`click`、 `mouseover`、`mouseout  (mouseenter、mouseleave) ` 、` contextmenu`、`dbclick`

- 语法：`jQuery对象 . 事件名称类型 (事件处理函数)`

- 缺点: 不能一次性绑定多个事件  (当然分开写多次写 不会覆盖)

  ~~~
  $("#box").click(function(){  // jquery内部不会发生事件覆盖，绑定形式addEventListener、attachEvent
  	alert(123)
  })

  //  发生事件覆盖
  $("#box").mouseover(function(){
  	alert(123)
  })
  $("#box").click(function(){
  	alert(456)
  })
  ~~~

- 解绑：`off()`

  ~~~
  $("#box").off("mouseover")

  $("#box").off()
  ~~~

  ​

#### bind 绑定方式

- 语法 ：

  ~~~
  jq对象.bind("事件名称1  事件名称2  ……",事件处理函数);

  jq对象.bind({
  	"事件名称1":事件处理函数1,
  	"事件名称2":事件处理函数2,
  	……
  });
  ~~~

- 缺点：不支持动态创建出来的元素绑定事件，不支持事件委托

  > 事件委托：将一个子元素身上的事件，委托给父级元素来添加，有父级元素触发该事件，利用的是事件冒泡机制

  ~~~
  $("#box").bind("click mouseover",function(){
  	console.log("哈哈");
  })

  $("#box").bind({
  	"click":function(){
  		console.log("你单击了");
  	},
  	"mouseover":function(){
  		console.log("你移上了");
  	}
  })
  ~~~

- 解绑 ：`unbind()`

  ~~~
  $("#box").unbind("mouseout");

  $("#box").unbind();  // 如果不写参数  可以取消这个元素身上的所有的事件
  ~~~

  ​

#### delegate事件绑定

- 语法 ：`jq对象.delegate(被委托的元素,事件类型,事件处理函数)`

- 有点 ： 支持动态绑定事件  实现事件委托

  ~~~
  /*原生js的写法*/
  var oUl = document.getElementById("oUl");
  oUl.onclick = function(e) {
  	e = e || event;
  	// 通过事件对象下面 去找 事件源 需要处理一下事件源的兼容性
  	var target = e.srcElement || e.target ;
  	// 通过找事件源的节点名称  如果是A  说明你单击了ul里面的a标签元素
  	if(target.nodeName == "A") {
  		// 让ul 去移除里面的 当前你单击的那个a 的父级li
  		this.removeChild(target.parentNode);
  	}
  }

  /*jQuery 写法*/
  $("#oUl").delegate("a","click",function(e){
  	//e jq中的e事件对象已经兼容好了 你直接使用
  	console.log( e.target ); // jq中的事件源 也不用做兼容
  	//通过事件源　找到它的父级li  让li执行remove()
  	$(e.target).parent().remove();
  })
  ~~~

- 解绑 ：`undelegate()`

  ~~~
  $("#box").undelegate("click")

  $("#box").undelegate()
  ~~~

  ​

#### on的绑定方式

- 参数 ：
  - 第一个参数 ：事件类型 `click`
  - 第二个参数 （可选）：需要被委托的内部的元素 `a` ，如果不需要事件委托，这个参数 可以省略不写
  - 第三个参数（可选） ：可以传入一些数据
  - 第四个参数 : 事件处理函数

  ~~~
  $("#box").on("click mouseover mouseout",function(){
  	console.log(123);
  })

  $("#box").on("click",function(){
  	alert(123)
  })

  $("#oUl").on("click","a",person,function(e){
  	$(e.target).parent().remove();
  	console.log("当前的li已经删除了");
  	console.log("从外面接收到了一个数据："+"姓名:"+e.data.name + "年龄："+e.data.age );
  })
  ~~~

- 参数为 json 格式

  ~~~
  $("#box").on({
  	"click":function(e){
  		console.log("这是一个"+e.type+"事件");
  		console.log(e.data[1]);
  	},
  	"mouseover":function(e){
  		console.log("鼠标移上了，这是一个"+e.type+"事件");
  		console.log(e.data[0]);
  	},
  	"mouseout":function(e){
  		console.log("鼠标移出啦， 这是一个"+e.type+"事件");
  		console.log(e.data[2]);
  	}
  },"p",["red","green","orange"])
  ~~~

- 解绑 ：`off()`

  ~~~
  $("#box").off("click");
  $("#box").off("mouseover mouseout");

  $("#box").off();
  ~~~

  ​



### jQuery的链式编程

链式编程原理 ：在jq方法调用之后，在方法内部会 `return this`  （就是将当前的对象返回出去）

**注意 ：**必须是设置方法，不能使读取方法

~~~
var obj = {
	name: "",
	setName : function(name){
		this.name = name;
		return this;// jq中一般设置方法  将设置操作设置完毕之后 可以返回当前的对象  this
	},
	getName:function(){
		return this.name;//jq中 读取 方法 一般会将读取的结果返回 所以就不能返回当前对象啦  
	}
}
~~~



### 隐式迭代

隐式迭代 ：通过jq的`$`符号获取的元素为jq对象，那么这个对象如果有多个元素，它会内部自动遍历，不需要你在外面手动循环

### jQuery的遍历方法

`each()` ：接收一个匿名函数，匿名函数里有两个形参

形参：

- 第一个形参 ：默认是每一次循环的索引
- 第二个形参 ：是每一次循环的元素

~~~
$("p").each(function(i,ele){
	console.log(i);每一次循环的索引
	console.log(ele);是每一次循环的元素		
	$(ele).html((i+1)+":哈哈哈");
});
~~~



### jQuery的多库共存机制

- 释放`$` 的控制权，赋值给自定义的变量

  ~~~
  var ABC = $.noConflict()  //  将$身上的全部功能给了ABC  将$控制权释放出来
  ~~~

- `$` === `jQuery`

  ~~~
  console.log( $("#box") );
  console.log( jQuery("#box") );

  console.log( $==jQuery );
  ~~~

  ​

> **插件:**是要依托于某一个软件(或者硬件)平台，辅助性提供或者增强某一种功能，一般针对性较强、功能比较单一
>
> **组件:** 组件的概念要比插件大，包含插件，更像多个插件的有机整体，可以实现多种功能   (控件)
>
> **库：**辅助性的工具  (被动) ，一定是有一个主体的开发语言或者框架，在整个基础上 引入库，可以提高开发效率
>
> **框架：**提供一个整体的基础性的解决方案，一套标准和规则，脱离了原生，根据对应的设计规则进行开发就可以啦  (主动)



### jQuery对象方法的扩展

- 开发工具方法，给`$`函数直接挂载和添加方法  (静态方法) (不常用)

  `$.extend()`：（这是jq内部提供的一个 api 接口，这个接口可以实现静态工具方法的开发）进行添加即可

  ~~~
  $.extend() 还有一个功能，就是可以将对象的属性进行遍历并且赋值
  实现步骤：建立一个新的json对象，将默认对象配置参数和用户传入的配置参数，统一进行属性遍历，赋给新的json对象

  (function($){
  	$.fn.extend({
  		changeStyle:function(options){
  			// 给一个默认的配置参数项  是一个json数据格式
  			var defaultSettings = {
  				color:"white",
  				backgroundColor : "orange",
  				fontSize:20
  			}
  			var settings = {};
  			$.extend(settings,defaultSettings,options);
  				console.log(options);
  				console.log(defaultSettings);
  				console.log(settings);
  				this.css({
  					color:settings.color,
  					backgroundColor:settings.backgroundColor,
  					fontSize: settings.fontSize
  				})
  			}
  	})
  })(jQuery);
  jQuery("#box").changeStyle();   // 如果用户懒的传参  最好里面有一个默认值
  jQuery("#box2").changeStyle({
  	color:"black",
  	backgroundColor:"red",
  	fontSize:30
  });
  jQuery("#box3").changeStyle({
  	fontSize:40
  })
  ~~~

- 直接给jq对象扩展方法（一般开发者就是基于这种形式实现）

  `$.fn.extend()` ：通过这个接口可以实现给jq对象扩展方法

  ~~~
  $.fn.extend({
  	abc:function(){
  		......
  	},
  	cc:function(){
  		......			
  	}		
  })

  $.fn.abc = function() {
  	......			
  }
  $.fn.cc = function(){
  	......			
  }
  ~~~

  ​