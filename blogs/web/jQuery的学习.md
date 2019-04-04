## 第一章 ajax 
####**ajax** 

	```
	 $('.button').click(function(){
	         $.ajax({
	            type: "GET",
	            url: "https://www.apiopen.top/weatherApi?city=成都",
	            dataType: "json",
	            async: true,
	            // false ajax不再缓存此页面
	            cache: false,
	            success: function (msg, code, jqXHR, xx) {
	                console.log(msg, '1111msg');
	                console.log(code, '1111code');
	                console.log(jqXHR,'1111');
	            },
	            statusCode: {
	                200: function () {
	                    console.log('请求成功了','1111');;
	                }
	            }
	        });
	    });
	```
#### **ajaxComplete** 
 **这里ducument是范围,监听document范围内的ajax发起**

	```
	 $(document).ajaxStart(function () {
	        $('#txt').show();
	    });
	    $(document).ajaxComplete(function(event){
	        $('#txt').hide();
	    })
	```
#### **ajaxSetup**
利用ajax查询数据，在谷歌浏览器下可以获取到最新数据，而在IE中获得是旧数据，无法获得最新的数据，经 查资料，才发现时IE缓存再作怪。
发现此ajax请求用的get方式，每次请求的URL一模一样，IE浏览器有个特殊的地方，如果每次请求的URL一样时，就会拿出缓存中已有的数据显示在页面上，并不会再次去查询数据库，所以每次显示的都是旧数据。

	```
	$.ajaxSetup({ cache: false })       //不设置ajax缓存
	```
ajaxSetup还有一个好处：在下面的栗子中,都设置了beforeSend函数,这两个函数是互不影响的，对不同的单击事件各自儿对立执行。

	```
	<!DOCTYPE html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <meta name="viewport" content="width=device-width, initial-scale=1.0">
	    <meta http-equiv="X-UA-Compatible" content="ie=edge">
	    <title>AJAX</title>
	</head>
	<body>
	    <div id="d" name="id" style="width:200px; height:100px;">bbb</div>
	    <button id="ii">加载</button>
	    <button id="jj">加载2</button>
	</body>
	<script src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
	<script type="text/javascript">
	    $(document).ready(
	        function () {
	            $("#ii").click(function () {
	                $.ajaxSetup({ cache: false, url: "jx.html", beforeSend: function () { alert("post请求之前"); }, success: function (result) { alert(result); } });
	                $.post("jx.asp");
	            });
	            $("#jj").click(function () {
	                $.ajaxSetup({ cache: false, url: "jx.html", beforeSend: function () { alert("get请求之前"); }, success: function (result) { alert(result); } });
	                $.get();
	            });
	        })
	</script>
	</html>
	```
####  load
load()方法从服务器加载数据，把返回的数据放入被选的元素中。
有些情况下,用load方法就是快。
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>load</title>
    <script src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
</head>
<body>
    <input type="text" id="UserName" value="admin" />
    <input type="button" id="btn" value="校验用户名" />
    <br/>
    <div id="message"></div>
</body>
<script type="text/javascript">  
    $(document).ready(function () {
        $("#btn").click(function () {
            //从文本框中获取内容  
            var userName = document.getElementById("UserName").value;

            //load()方法从服务器加载数据，并把返回的数据放入被选元素中。  
            //GET方式  
            // $('#message').load("AJAX?name=" + userName);
            // $('#message').load("https://www.apiopen.top/weatherApi?city=北京");
            $('#message').load("https://www.apiopen.top/weatherApi",{city: '北京'});
            //POST方式  
            //$('#message').load("AJAX?name=" + userName,{"Content-type":"application/x-www-form-urlencoded"});  
        });
    });  
</script>
</html>
```
####  serialize
介绍：
>作用：序列表单内容为字符串。
>    参数： 无
>    返回值：表单内容的字符串格式

栗子： 
```
> <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>serialize</title>
    <script src="https://cdn.bootcss.com/jquery/3.3.1/jquery.min.js"></script>
</head>
<body>
    <p id="results">
        <b>Results: </b>
    </p>
    <form>
        <select name="single">
            <option>Single</option>
            <option>Single2</option>
        </select>
        <select name="multiple" multiple="multiple">
            <option selected="selected">Multiple</option>
            <option>Multiple2</option>
            <option selected="selected">Multiple3</option>
        </select>
        <br/>
        <input type="checkbox" name="check" value="check1" /> check1
        <input type="checkbox" name="check" value="check2" checked="checked" /> check2
        <input type="radio" name="radio" value="radio1" checked="checked" /> radio1
        <input type="radio" name="radio" value="radio2" /> radio2
    </form>
</body>
<script>
    $("#results").append("<tt>" + $("form").serialize() + "</tt>");
</script>
</html
```
例子运行效果：

![这里写图片描述](https://img-blog.csdn.net/20180608104733693?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

serialize就是把表单的值拼接成下图的字符串一般用于post表单提交数据，用的还是比较多的。

![这里写图片描述](https://img-blog.csdn.net/20180608104801255?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

####  serializeArray

serializeArray和serialize的方法名称差不多，用法也是大相接近，他俩的返回值不同，serializeArray返回的是数组，se'rialize返回的是字符串,如图所示： 

![这里写图片描述](https://img-blog.csdn.net/20180608105629417?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

## 第二章 属性property

attr removeAttr 操作一般标签的属性

prop removeProp 操作表单标签的属性

addClass removeClass  toggleClass  操作一般标签的类名

 html text val 操作匹配元素的内容


## 第三章 css

#### css() 
1. 取得第一个段落的color样式属性的值。
  ```
  $("p").css("color");
  ```

2. 赋值
  ```
  $("p").css({ "color": "#ff0011", "background": "blue" });
  ```
3. 利用回调函数改变div的宽高,这个在工作中用的少,但是有些情况下真的很有用。

  ```
  $("div").click(function() {
    $(this).css({
  	    width: function(index, value) {
  	      return parseFloat(value) * 1.2;
  	    }, 
  	    height: function(index, value) {
  	      return parseFloat(value) * 1.2;
  	    }
    });
  });
  ```
#### innerHeight()    innerWidth()
1. 注意参数不加的区别
  ```
  //outerHeight如果不写参数true,是不算margin在内的哦
  var outerHeight = $('div').outerHeight(true);
  var outerHeight = $('div').outerHeight();
  console.log(outerHeight, '1111outerHeight');
  
  //同理,outerWidth的用法和outerHeight的差不多
  ```
  如需了解更多请参考[这里](https://blog.csdn.net/Stephen__Wu/article/details/80623283)
  <br>
## 第四章 文档处理
<br>
## 第五章 筛选
<br>
## 第六章 事件

<br>
#### ready(fn) 

1. 当DOM载入就绪可以查询及操纵时绑定一个要执行的函数。
  这是事件模型中最重要的一个函数，因为它可以极大地提高Web应用程序的响应速度。
  99.99%的函数都需要在那一刻执行。
  ready方法只是window.load方法的一个替代方法而已。

  ```
  $(function($) {
    // 你可以在这里继续使用$作为别名...
  });
  ```

#### on() 使用场景最多

1. 最简单的写法

  ```
   $("ul li").on("click",function(){  
    alert("不响应事件!");  
   })  
  ```
2. 同时给多个元素绑定一样的事件

  ```
   $("ul li,div").on("click",function(){  
    alert("不响应事件!");  
   }) 
  ```
3. 同时给元素绑定多个事件

  ```
  $(".demonstrate").on({  
    mouseover:function(){  
    $(this).addClass("over");  
    },  
    mouseout:function(){  
    $(this).removeClass("over");  
    }  
  },"ul li")  
  ```
4. 实现事件委托 
  父元素`ul li` 给目标元素`.demostrate`添加事件,事件委托的好处是,目标元素可以是之前页面不存在到,后来加上去的也可以。
  只需要考虑一个父元素就可以，给父元素添加委托事件，不用考虑子元素的数量什么的。

  ```
   $("ul li").on({
          click:function(){
              console.log('click','1111');
          },
          mouseover: function () {
              console.log('mouseover','1111');
              $(this).addClass("over");
          },
          mouseout: function () {
              $(this).removeClass("over");
          }
      },".demostrate");
  
  ```
  <br/>
#### off() 解绑事件

1. 最简单的写法

  ```
   $("ul li").off("click")  
  ```
2. 同时给多个元素解绑一样的事件

  ```
   $("ul li,div").off("click") 
  ```
3. 同时给元素解绑多个事件

  ```
  $(".demonstrate").off("mouseover mouseout","ul li")  
  ```
4. 实现事件委托的解绑
  父元素`ul li` 给目标元素`.demostrate`移除事件,事件委托的好处是,目标元素可以是之前页面不存在到,后来加上去的也可以。
  只需要考虑一个父元素就可以，给父元素移除委托事件，不用考虑子元素的数量什么的。

  ```
   $("ul li").off("click mouseover mouseout",".demostrate");
  
  ```
  <br/>
#### one  一次性绑定事件
1. 介绍
  type:添加到元素的一个或多个事件。由空格分隔多个事件。必须是有效的事件。
  data:将要传递给事件处理函数的数据映射
   fn:每当事件触发时执行的函数。

  ```
  $("p").one("click", function(){
    alert( $(this).text() );
  });
  ```
  <br/>
#### 自动触发事件trigger使用
1. trigger 的好处是你可以不通过trigger就可以触发单击事件；

  ```
  $('a').first().trigger("click");
  ```
2. 触发自定义事件

  ```
  //定义事件
  $('#btn').bind("myEvent", function(){ 
      alert("自定义事件");
  });
  //触发事件
  $('#btn').trigger("myEvent");
  ```
3. 传递数据

  ```
  $('#btn').bind("myEvent", function(event,message1,message2){ 
      alert(message1 + "," + message2);
  });
  $('#btn').trigger("myEvent", ["Hello","World!"]);
  ```

<br />
#### triggerHandler 
1.   triggerHandler() 
  这个方法的行为表现与trigger类似，但有以下三个主要区别：
  第一，他不会触发浏览器的默认事件。
  第二，只触发jquery对象集合中的第一个元素的事件处理函数。
  第三，之歌方法返回值时事件处理函数的返回值，而不是具有可链性的jQquery对象。
```
$('#btn').bind("myEvent", function (event, message1, message2) {
          console.log(message1,'1111');
           console.log(message2,'1111');
           // alert(message1 + "," + message2);
       });
   $('#btn').trigger("myEvent", ["Hello", "World!"]);

```

<br>
#### resize(） 调整窗口的函数
```
 var x =0;
    // $(window).resize(function () {
    //         $('span').text(x += 1);
    // });
    $(window).scroll(function () {
        $("span").text(x += 1);
    });
```

<br>

#### select() 
当textarea或者文本类型的input元素中的文本被选择是，会发生select事件
```
 $("input").select();
 $("input").select(
      function(){
          console.log('select','1111');
      }
  );
```

<br>
#### submit  表单提交 
`return false` 防止表单的默认事件

```
 $('form').submit();
 $('form').submit(function(){
      return false;
  });
```

<br>
## 第七章  效果

#### show()  控制元素的显示
```
$("p").show('slow',function(){
    console.log('显示完成了','1111');
})
```
<br>
####  fadeOut 淡出效果

```
$("p").fadeOut("slow");
```
<br>
#### animate
一个强大的动画函数

1. 模式A
  ```
  	// 模式1
      $("#block").animate({
         width: "90%",
        fontSize: "10em",
        opacity: 0.6,
       borderWidth: 10
      }, 2000);
  ```

2. 模式B,如代码所示
  注意:可以利用animate每走一步都要执行一下step函数的特点,可以实现和rotate，translate函数的一模一样的动画效果
  ```javascript
   //  模式2  可以写rotate，translate函数的动画效果
      $("#block").animate({
          width: "300px",
          height: '100px'
      },{
          duration: 2000,
          start: function(){
              // console.log('start','1111');
          },
          step:function(now,fx){
              // console.log(now,'1111');
              if(now >= 102){
                  //.finish()方法和.stop(true, true)很相似，
                  //.stop(true, true)将清除队列，并且目前的动画跳转到其最终值。
                  // $("#block").stop(true);
                  // $("#block").finish();
                  // console.log("jQuery.fx.off",'1111');
                  // jQuery.fx.off = true;
              }
              // jQuery.fx 原型对象的一个引用,其中包含了多项属性,比如 fx
              // console.log(fx,'1111fx');
              // console.log('step','1111');
          },
          complete:function(){
              // console.log('complete','1111');
          }
      });
  ```
  <br>
## 第八章 工具
<br>
####  each
通用遍历方法，可用于遍历对象和数组。
不同于遍历 jQuery 对象的 $().each() 方法，此方法可用于遍历任何对象。
三种用法如下所示:
```javascript
   //用法1 遍历数组
   $.each([0,1,2],function(i,n){
    console.log(i,n,'1111');
   })
   //用法2 遍历数组
  $([0, 1, 2]).each(function(i,n){
      console.log(i,n,'1111');
  })
  //用法3 遍历对象
  $.each({name:'john',lang:'js'}, function (i, n) {
      console.log(i, n, '1111');
  })
```