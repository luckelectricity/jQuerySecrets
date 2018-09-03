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

jQuery.prototype.init.prototype = jQuery.prototype

jQuery().css()
```
