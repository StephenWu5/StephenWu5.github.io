# jquery给input赋值,val的三种用法


## val()方法
####  定义和用法
val() 方法返回或设置被选元素的值。
元素的值是通过 value 属性设置的。该方法大多用于 input 元素。
如果该方法未设置参数，则返回被选元素的当前值。

```
<input type="text" class="input1">
$('.input1').val('value567'); // 用法1 给input赋值value567
$('.input1').val(''); // 用法2 给input清空
$('.input1').val('');  //  用法3 返回val的值
```

#### 更多
想了解更多请点击[点击](http://www.w3school.com.cn/jquery/attributes_val.asp)