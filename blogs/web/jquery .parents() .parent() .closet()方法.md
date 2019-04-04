parent是找当前元素的第一个父节点，parents是找当前元素的所有父节点 
parent()、parents()与closest()方法两两之间有类似又有不同，本篇简短的区分一下这三个方法。通过本篇内容，大家将会在以后使用.parent()、parents()和closest()时不会显得无从下手。

我们直接看例子来来说明一下这三个方法的使用区别：

```
 <ul id="menu" style="width:100px;">
        <li>
            <ul>
                <li>
                    <a href="#">Home</a>
                </li>
            </ul>
        </li>
        <li>End</li>
    </ul>
```

接下来，分别看看这三个方法：

```
<script>    
    $("#menu a").click(function () {
        // $(this).parent("ul").css("background", "yellow");
        // $(this).parent("li").parent("ul").css("background", "yellow");
        // $(this).parents("ul").css("background", "yellow");
        $(this).closest("ul").css("background", "yellow");
        return false;
    }); 
</script>
```

1.parent()方法从指定类型的直接父节点开始查找，在"0"中，`<a>`的直接父节点是`<li>`所以在这里找不到`<ul>`父节点。在"2"中先找到了`<li>`，接着找到`<ul>`，并将它的背景色设置为yellow。parent()返回一个节点。

2.parents()方法查找方式同parent()方法类似，不同的一点在于，当它找到第一的父节点时并没有停止查找，而是继续查找，最后返回多个父节点，如在"2"中，使得id为menu的`ul`整个背景色变成了yellow。

3.closest()方法查找时从包含自身的节点找起，它同parents()很类似，不同点就在于它只返回一个节点如在"3"中，实现的功能同1相同。但它使得代码量减小，同"2"相比又只返回单一的一个节点。可见，closest()方法在项目中的使用频率是比较大的。