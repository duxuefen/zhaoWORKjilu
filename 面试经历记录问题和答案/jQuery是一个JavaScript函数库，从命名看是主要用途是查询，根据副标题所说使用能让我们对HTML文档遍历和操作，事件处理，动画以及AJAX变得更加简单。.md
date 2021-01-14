jQuery是一个JavaScript函数库，从命名看是主要用途是查询，根据副标题所说使用能让我们对HTML文档遍历和操作，事件处理，动画以及AJAX变得更加简单。

jQuery是一个轻量级的"写的少，做的多"的JavaScript库。

jQuery库包含以下功能：

- HTML 元素选取
- HTML 元素操作
- CSS 操作
- HTML 事件函数
- JavaScript 特效和动画
- HTML DOM 遍历和修改
- AJAX
- Utilities



基础

原理

ajax



开发中使用未压缩版本

上线后使用压缩版





**window.onload()** 方法用于在网页加载完毕后立刻执行的操作，即当 HTML 文档加载完毕后，立刻执行某个方法。



```
$(document).ready(function(){.... })
jQuery(doucument).ready()
```

**这个函数是用来取代页面中的window.onload;**

而$(document).ready()所要执行的代码是在DOM元素被加载完成的情况下执行，所以，使用document.ready()方法的执行速度比onload()的方法要快。



js如果编写了多个入口函数。后面的编写会覆盖前面编写的

 加载会等到DOM元素加载完毕，并且图片也加载完毕才执行



JQuery 如果编写了多个入口函数。后面的编写会覆盖前面编写的

等到DOM元素加载完毕，但不会等到图片也加载完毕就会执行



$()就代表调用JQuery的核心函数

接受的参数：1.接收一个函数（相当于一个入口函数） 2.--一个字符串2.1字符串选择器var dd=$(".box") ，返回了Jquery对象，保存了对应的DOM元素   用于查找DOM元素 2.2 代码片段 var p=$("<p>我是段落<p>")  返回了Jquery对象 保存了创建对应的dom元素     3.接受一个DOM元素，会被包装成一个

Jquery对象是一个伪数组

**静态方法和实例方法：**

静态方法通过类调用 Aclass.staticMethid=function(){

}

实例方法：//定义一个静态方法
		AClass.staticMethod=function(){
			alert("Jingtai");
		}
		AClass.staticMethod();

//定义一个实例方法
		AClass.prototype.instanceMethod=function(){
			alert("shili");
		}
		var a=new AClass();
		a.instanceMethod();



##  静态方法



Jquery当中的一些静态方法

原生JS forEach方法只能遍历数组

each方法：可以遍历伪数组 ，和数组    返回值遍历谁，返回谁

不支持在回调函数中对遍历的数组进行处理

map方法：可以遍历伪数组 ，和数组    返回值是一个空数组

支持在回调函数中通过return对遍历的数组进行处理，然后生成一个新的数组返回

trim（字符串） 去掉字符串两端的空格 ，返回一个新的字符串

isArray（） 判断传入的对象是否为真数组 返回

isFunction() 判断传入的对象是否为一个函数 JQuery框架本质是一个函数

isWindow()   判断传入的对象是否是window 返回值true false

holdReady (true) 暂停入口函数的执行  ，false代表回复入口函数的执行 指示是否暂停或恢复被请求的ready事件

##  选择器

###  基本选择器

#id 

element  根据给定的元素标签名匹配所有元素

.class 类选择

*匹配所有元素，多用于结合上下文来搜索

selector1,selector2,selectorN  将每一个选择器匹配到的元素合并后一起返回

### 层级选择器

### 基本选择器

###  内容选择器

$("div:内容")  empty 找到既没有文本内容也没有子元素的指定元素

​                        parent找到文本内容和子元素的指定元素

​                         contains （‘我是div’）找到包含指定文本内容的指定元素

​                         has（‘span’）包含指定子元素的指定元素

###  子元素

###  表单

###  表单对象属性

###  混淆选择器



##   属性的相关操作  attribute  属性

什么是属性节点  在标签添加属性 就是属性节点

###  属性节点的方法

 attr (name|pro|key,val|fn)  设置或返回被选元素的属性值。

可以传递一个参数，也可以传递两个参数

注意无论找到多少个元素，都只会返回第一个元素指定的属性的值

设置，找到多少属性，设置多少 ，没有的话会创建

removeAttr(name)  会删除所有找到元素指定的属性节点  多个属性 节点  用空格分开

###  属性的方法

