# 定义函数jQuery
```
	jQuery = function (selector, context) {   // 定义函数jQuery  jQuery = function () {}
		// The jQuery object is actually just the init constructor 'enhanced'
		return new jQuery.fn.init( selector, context, rootjQuery );
	},
```
## 普通面向对象方法
```
function Obj() {

}
Obj.prototype.init = function () {

}
Obj.prototype.css = function () {

}
var a = new Obj()
a.init()
a.css()
```

## jQuery面向对象写法
```
function jQuery(){
  return new jQuery.prototype.init()
}
jQuery.prototype.init = function () {

}
jQuery.prototype.css = function () {

}

// 更美小哥哥面试的时候问的我这个问题，终于有了一个完善的答案了，其实就是把jQuery的原型挂在new出来的jQuery.prototype.init的原型上，所以每次new出来的都可以访问jQuery原型上的方法。
jQuery.prototype.init.prototype = jQuery.prototype

jQuery().css()
```
### 无new对象
这样就无new创建了对象，如果函数这样写
```
function jQuery(){
  return new jQuery()
}
```
就是死循环了，每次new 就会创建一个new jQuery 然后又创建一个。。。。。

根据上面的代码,就能得到以下等式
```
jQuery().__proto__ === jQuery.prototype.init.prototype
```
