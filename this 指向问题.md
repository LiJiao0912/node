### this 指向问题

```
function fn() {
  console.log(this);
}
fn();

// 1   函数的直接调用,函数内部的 this 指向window  ,相当于 window 在调用函数

var fn1 = new fn();  

//2  通过 new 的方式调用函数,this 是一个隐式对象虚拟的对象,可以理解为是一个初始化的模型,this  指向当前的构造函数
		
var obj = {
  fn:function () {
    console.log(this);
  }
}
obj.fn(); 

//3  obj 这个对象在调用它的方法，this 指向当前的对象
		
oBox.onclick = fn; 
//4  通过一个事件来触发这个函数，那么这个函数里面的this指向触发该事件的前面的那个元素对象
```

