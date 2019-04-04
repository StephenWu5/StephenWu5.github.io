# 用CSS3的border-radius来"画"一个杯子

今天是我在黑马创智博客学习快满2个月的一天,是学习HTML5和CSS3的第一天,学习了一个用border-radius来画一个杯子,实现起来也挺简单的,仅仅用了两个div.

![图像 001](C:\Users\98107\Desktop\截图\博客\10-16\图像 001.png)

## 1 先定义两个div   div.cup和div.handle

`

 <div class="cup">

​        <div class="handle"></div>

​    </div>

`

## 2给这两个div设置样式,特别是border-radius的样式

`

  .cup{

​            width: 150px;

​            height: 240px;

​            /* background-color: yellowgreen; */

​            margin:0 auto;

​            margin-top:150px;

​            position: relative;

​           

​            border: 3px solid black;

​            /* 设置盒子模型 */

​            box-sizing:border-box;

​            border-top:none;

​            border-bottom:none;

​        }

​        .handle{

​            width: 90px;

​            height: 150px;

​            /* background-color: yellowgreen; */

​            position: absolute;

​            left: -90px;

​            top:40px;

​            /* 设置圆角 */

​            border-radius:60px 40px 0px 90px/70px 30px 0px 90px;

​            border: 3px solid black;

​             /* 设置盒子模型 */

​             box-sizing:border-box;

​        }

`

## 3 利用before和after 伪元素给类名为cup的div设置两个伪元素,border-radius,给杯子设置顶部和底部.

`

 /* 伪元素 */

​        .cup::before{

​            /* content和display必须设置 */

​            content:"";

​            display: block;

​            width: 150px;

​            height: 30px;

​            /* background-color: yellowgreen; */

​            margin-top:-15px;

​            left:-3px;

​            position: absolute;

​            border: 3px solid black;

​            /* 设置盒子模型 */

​            box-sizing:border-box;

​            /* 设置圆角 */

​            border-radius:75px/15px;

​        }

​        .cup::after{

​            /* content和display必须设置 */

​            content:"";

​            display: block;

​            width: 150px;

​            height: 30px;

​            /* background-color: yellowgreen; */

​            bottom:-15px;

​            left:-3px;

​            position: absolute;

​            border: 3px solid black;

​            /* 设置盒子模型 */

​            box-sizing:border-box;

​            /* 设置圆角 */

​            border-radius:75px/15px;

​            /* 去掉border-top */

​            border-top:none;

​        }

`

要点1,after和before 内要写上 content:"";和float:block;  否则after和before不能显示;

要点2 div的盒子模型设置为box-sizing: border-box;这样后来添加border后, 宽度就不会变大.

要点3 出现粗的边框时,写上 "margin-left:-3px" "margin-top:-3px",可以让边框变细.

要点4 设置绝度定位时,父相子绝出现的情况挺多的.