## Javascript 高级教程

### 第一节

#### 数据类型

*分类

* 基本（值）数据类型
  * String :任意字符串
  * Number :任意的数字
  * boolean :true/false
  * undefined :undefined
  * null :null
* 对象（引用）类型
  * Object:任意对象
  * Function:一个特别的对象（可以执行）
  * Array:一种特别的对象（数值下标，内部数据是有序的）

#### 如何判断数据类型

* typeof  (可以判断undefined/数值类型/字符串/布尔值/function)(不能判断null 和Object  object与array)

* instanceof（判断对象的具体类型）

* ===（可以判断：undefined / null）为什么可以判断 因为undefined 和null只有一个值



***

### 第二节

#### 什么是实例对象 什么是类型对象

* ```javascript
  function Person(name,age){  构造函数  类型对象
    this.name=name;
    this.age=age
  }
  var p=new Person() //根据类型创建的实例对象
  
  ```

  

* undefined和null的区别

  undefined 代表定义未赋值

  null 定义并赋值了，只是值为null

#### 什么时候可以给变量赋值为null

* 初始赋值，表示将要赋值为对象  null 的类型是object

* 结束后，让对象成为垃圾对象（垃圾回收机制）

#### 严格区别变量类型与数据类型

* 数据类型
  * 对象的类型
  * 基本类型

* 变量类型
  * 基本类型（）保存的是基本类型的数据
  * 引用类型：保存的是地址值

***

### 第三节

#### 内存，数据，变量三者之间的关系

* 内存是用来存储数据的空间
* 变量是内存的标识

#### 什么是变量

* 可变化的量，由变量名和变量值组成
* 每个变量都对应的一块小内存，变量名用来查找对应的内存，变量值就是内存保存的数据。

#### 什么是内存

* 内存条通电后产生的可存储数据的空间（临时）
* 一块小内存的2个数据
  * 内部存储的数据
  * 地址值
* 内存的分类
  * 栈：全局变量/局部变量
  * 堆：对象

#### 什么是数据

* 存储在内存中代表特定信息的，本质上是01010...
* 数据的特点：可传递，可运算
* 一切皆数据
* 内存中所有操作的目标：数据
  * 算数运算
  * 逻辑运算
  * 赋值
  * 运算函数

#####  问题一：var  a=xxx ,a内存中到底保存的是什么？

* xxx 是数据，保存的就是这个数据
* xxx是对象，保存的就是对象的地址值
* xxx是一个变量 ，保存的xxx 的内存内容（可能是基本数据，也可能是地址值）

##### 问题二：关于引用变量赋值问题

* 2个引用变量指向同一个对象，通过一个变量修改对象内部数据吗，其他所有变量看到的是修改后的数据
* 2个引用变量指向同一个对象，让其中一个引用变量指向另一个对象，另一引用变量依然指向前一个对象

##### JS引擎如何管理内存

* 1.内存生命周期
  * 分配小内存空间，得到它的使用权
  * 存储数据，可以反复进行操作
  * 释放小内存空间
* 释放内存
  * 局部变量：函数执行完自动释放
  * 对象：成为垃圾对象==> 垃圾回收器回收

***

### 第四节

#### 什么是对象

* 多个数据的封装体
* 用来保存多个数据的容器
* 一个对象代表现实中的一个事物

#####  为什么要用对象

* 统一管理多个数据

##### 对象的组成

* 属性： 属性名（字符串）和属性值（任意类型）组成
* 方法：一种特别的属性（属性值是函数）

##### 如何访问对象内部的数据

* . 属性名
* ["属性名"] 
  * 什么时候必须使用["属性名"]
    * 属性名包含特殊字符： -  空格
    * 变量名不确定

```javascript
例子
1.给p对象添加一个属性：content type :text/json
// p.content-type='text/json'
p['context-type']='text/json'
console.log(p['context-type'])

2.属性名不确定
var propname = 'myAge'
p.propname=value // 不能用
var value = 18;
p['propname']=value
```



***

### 第五节

#### 什么是函数

* 实现特定功能的N条语句的封装体
* 只有函数是可以执行的，其它的类型的数据不能执行

#### 为什么要用函数

* 提高代码的复用
* 便于阅读交流

#### 如何定义函数

* 函数声明 

  ```javascript
  function fn(){} //函数声明
  ```

* 表达式

  ```
  var fn = function(){}
  ```

  

#### 如何调用（执行）函数

* 直接调用  

```javascript
text()
```

* 通过对象调用

```javascript
obj.text()
```

* new 调用

```
new text()
```

* 临时使用text() 成为obj方法进行调用

```javascript
var obj={}
function text2(){
  this.xxx='atguigu'
}
//调用
text2().call(obj)  // 可以让一个函数成为指定任意对象的方法进行调用
```

***

### 第六节

#### 什么是回调函数

* 你定义的
* 你没有调用
* 但是它最终执行了

#### 常见的回调函数

* dom 事件回调函数
* 定时器回调函数
* ajax 请求回调函数
* 生命周期回调函数

```javascript
document.getElementById(btn).onclick=function(){
  alert(this.innerHTML)
}
//
setTimeout(function(){
  alert(‘到点了’)
},200)
//典型的回调函数
```

***

### 第七节

#### IIFE函数（Immediately-Invoked Function Expression）

##### 匿名函数自调用

* 作用
  * 隐藏实现
  * 不会污染外部全局命名空间
  * 用它来编码JS模块

```javascript
//举例
（function(){ //匿名函数自调用
  var a=3
  console.log(a+3)
}）()；
// 举例二
(function(){
  var a=1;
  function test(){
    console.log(++a)
  }
 window.$=function(){ //向外暴露一个函数
   return{
     test:test
   }
 }
})()
$().test()  //输出结果是2 
//$是一个函数  2.$执行后是一个对象
```



