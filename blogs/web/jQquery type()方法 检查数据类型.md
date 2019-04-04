> 以前在工作项目中用到的数据类型的检测,都是用百度上别人的js段,今天刚好看到这个函数,以后用的地方就多了,为什么用jquery,不用自己的代码段,因为jquery的兼容性比较好。

## 描述

检测obj的数据类型。

## 参数

obj   用于检测类型的对象

## 示例 

```javascript
jQuery.type(true) === "boolean"
      
jQuery.type(3) === "number"
        
jQuery.type("test") === "string"
      
jQuery.type(function(){}) === "function"
        
jQuery.type([]) === "array"
      
jQuery.type(new Date()) === "date"
        
jQuery.type(/test/) === "regexp"
```

大家看出来什么区别了吗？　使用`$.type`能够返回更准确的对象类型，而`typeof`则返回`object`，所以如果你使用`jQuery`来编码的时候，使用`$.type` 将更加方便。