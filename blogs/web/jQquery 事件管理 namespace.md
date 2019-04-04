 > 为了方便jquery的事件管理，1.4版本开始引入了这个namespace命名空间这个概念，说白了就是把事件分类，和css的className 方便管理

## 介绍 
添加事件命名空间，便于管理

## 示例 
示例1
```javascript
$p.bind('click.plugin', handler);
$p.bind('mouseover.plugin', function (event) {
     $('body').append('<p>mouseover event</p>');
 })
 $p.unbind('.plugin'); //一行代码就把两个事件解绑了
```

示例2
```javascript
$p.bind('click.plugin', handler);
$p.bind('click.foo', function (event) {
     $('body').append('<p>mouseover event</p>');
 })
 $p.unbind('.plugin'); //这行代码只把.plugin的单击事件解绑，.foo的事件依然可以执行
```

## 遇到的BUG
一开始，看了文档，我就这样来拿`namespace`
```
 function handler1(event){
      console.log(event.namespace,'1111');
   }
```
搞了老半天，`event.handleObj.namespace`这样拿才是正确的
```
function handler(event){
      console.log(event.handleObj.namespace,'1111');
   }
```
原来有的文档也不是全对的，要有自己的学习能力。