# jQuery outerHeight()的用法

近来公司没事,有时间,有研究一下jquery的api,碰到outerHeight()获取不到外边距,搞了一小时,原来是没有在outerHeight()写上一个参数。

#### 没有写上该参数

![这里写图片描述](https://img-blog.csdn.net/20180608144807790?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

####  加上该参数

![这里写图片描述](https://img-blog.csdn.net/20180608145040297?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)


## 介绍
>$(selector).outerHeight(options)
| 参数    |  值   |             作用 |
| ------- | :---: | ---------------: |
| options | true  |     边距计算在内 |
|         | false | 包括内边距和边框 |
|         |  空   | 包括内边距和边框 |

同理，outerWidth的用法一样的。

####demo的代码如下：
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>css的学习2</title>
    <script src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
    <style>
        *{
            padding: 0;
            margin: 0;
        }
        body{
            position: relative;
        }
        div{
            width: 100px;
            height: 100px;
            padding: 10px;
            margin: 10px;
            border: 5px solid red;
            background-color: skyblue;
            position: absolute;
            display: inline-block;
            top: 10px;
            left: 10px;
        }
    </style>
</head>
<body>
    <div></div>
</body>
<script>
    //css 还能以function的形式来使用
    // $("div").click(function () {
    //     $(this).css({
    //         width: function (index, value) {
    //             console.log(value,'1111');
    //             return parseFloat(value) * 1.2;
    //         },
    //         height: function (index, value) {
    //             console.log(index, '1111');
    //             return parseFloat(value) * 1.2;
    //         }
    //     });
    // });

    //设置匹配元素在当前视口的相对偏移
    //获取匹配元素在当前视口的相对偏移
    // var offset = $('div').offset({top: 10,left: 30});
    // var offset = $('div').offset();
    // console.log(offset,'1111');

    //获取匹配元素相对父元素的偏移
    // var position = $('div').position();
    // console.log(position,'1111');

    //获取匹配元素相对滚动条顶部的偏移
    //此方法对可见和隐藏元素均有效。
    //scrollLeft scrollTop 已弃用了
    // var position = $('div').scrollLeft();
    // console.log(scrollTop,'1111scrollTop');

    // var height = $('div').height(function(index,value){
    //     // return value+100;
    // });
    // console.log(height,'1111');

    var innerHeight = $('div').innerHeight();
    console.log(innerHeight,'1111');
    
    var outerHeight = $('div').outerHeight(true);  // 写上参数true
    // var outerHeight = $('div').outerHeight();   // 不要参数true
    console.log(outerHeight, '1111outerHeight');
</script>
</html>
```

**喜欢我，给我点个赞哦**