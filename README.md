# bind、call、apply的区别

```
javaScript权威指南上的解释是： call() 、apply()可以看作是某个对象的方法，
通过调用方法的形式来间接调用函数。
bind() 就是将某个函数绑定到某个对象上。
var obj = {};
 
function foo(a, b, c) {
  console.log(b);
}
 
foo.call(obj, 1, 2, 3)   //打印结果： 2;
var obj = {};
 
function foo(a, b, c) {
  console.log(b);
}
 
foo.apply(obj, [1, 2, 3])   打印结果： 2;
bind() 方法和前两者不同在于： bind() 方法会返回执行上下文被改变的函数而不会立即执行，
而前两者是直接执行该函数。他的参数和call()相同。
```
```
var name='小王',age=17;
var obj={
    name:'小张',
    objAge:this.age,
    myFun:function(){
        console.log(this.name+"年龄"+this.age);
    }
}
var db={
    name:'德玛',
    age:99
}
obj.myFun.call(db)；　　　　//德玛年龄9
 obj.myFun.apply(db);　　　 //德玛年龄
 obj.myFun.bind(db)();　　　//德玛年龄9
　以上出了bind 方法后面多了个 () 外 ，结果返回都一致！
　　由此得出结论，bind 返回的是一个新的函数，你必须调用它才会被执行
```