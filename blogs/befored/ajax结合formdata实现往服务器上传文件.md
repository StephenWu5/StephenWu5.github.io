# ajax结合FormData对象实现服务器上传文件(初步认识)

## ajax的定义

Ajax是一种用于创建快速动态网页的技术，通过在后台与服务器进行少量数据交换，AJAX可以使网页实现异步更新。意味这可以再不重新加载整个网页的情况下，对网页的某部分进行更新。

## 全体代码

同学们,下面我来讲解js中的ajax来实现服务器上传文件的几个步骤:

` //给按钮添加单击事件

​    document.querySelector('input[type=button]').onclick = function(){

​	//定义一个变量记录上传进度的百分比

​        var percent;

​        //创建一个对象

​        var xhr  =new XMLHttpRequest();

​        xhr.open("post","./saveFiles.php");

​        //请求头可以省略

​        //回调函数

​        xhr.onload = function(){

​           console.log("9999");

​        }

​        //监控上传进度

​        xhr.upload.onprogress = function(e){

​            percent = e.loaded/e.total * 100 +"%";

​            document.querySelector(".step").style.width = percent;

​        }   

​        

​        //创建formdata对象

​        var formdata  = new FormData(document.querySelector("form"));

​        //发送请求主体

​        xhr.send(formdata);

​    };`

## 章节2  分几个步骤



### 1, //创建一个XHR对象 

​        var xhr  =new XMLHttpRequest();

### 2,//设置请求行,方法是post,请求地址是"./saveFile.php"

open()方法传入三参数

- method：请求的类型（GET/POST）
- url：文件在服务器上的位置
- async：布尔值，true表示异步，false表示同步（可选，默认为true）

​	xhr.open("post","./saveFiles.php");

### 3, //请求头可以省略

这里的请求头一定要省略,万一设置了,文件就发不出了.

### 4,//回调函数

​        xhr.onload = function(){

​           console.log("9999");

​	//在这里可以写一些程序员自己定义的功能

​	//得到数据后需要执行什么

​        }

### 5,//创建formdata对象 这个是协助input type="files"  发送文件

​	formdata是XMLHTTPREQUESTER 2.0之后的新加上去的

​	FormData类型其实是在XMLHttpRequest 2级定义的，它是为序列化表以及创建与表单格式相同的数据（当然是用于XHR传输）提供便利。

​        var formdata  = new FormData(document.querySelector("form"));

####      //利用xhr.upload.onprogress事件监控上传进度

​	e.loaded 是已上传的文件部分       e.total是全部的文件

​        xhr.upload.onprogress = function(e){

​            percent = e.loaded/e.total * 100 +"%";

​            document.querySelector(".step").style.width = percent;

​        }   

###    6,//发送主体

​	在send函数中发送formdata这个对象

​        xhr.send(formdata);



## 上面所写的是我在最近学习的前端,php知识点之一,看起来简单,但如果要用的熟练度高,深度深,还要多多努力才行。



