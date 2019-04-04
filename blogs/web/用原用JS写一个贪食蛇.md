1. 第一步，写好一个盒子（让蛇在里面走），宽 800 p x,高 600 p x;

2. 第二步,写一个食特的构造函数 Function food(){
   this.width = width || 20;
        this.height = height || 20;
        this.backgroundColor = bgc || "green";
        this.left = 0;
        this.bottom = 0;
   }

	![这里写图片描述](http://img.blog.csdn.net/20170921211803873?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
	 一开始在这里写错js的名字 一看我就是新手啦啊,的确进来这个行业不多.
	
	![这里写图片描述](http://img.blog.csdn.net/20170921211915379?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
	
	还有这个"box"错写为".box",真的是醉了.
	
	![这里写图片描述](http://img.blog.csdn.net/20170921212237345?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)


	![这里写图片描述](http://img.blog.csdn.net/20170921212927563?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
	效果图随机食物出来了
1. 第三步,写一个生成蛇的构造函数.
  ![这里写图片描述](http://img.blog.csdn.net/20170921214042516?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
  先借助画图软件写出刚渲染出的蛇的身段,然后得出位置.

  ![这里写图片描述](http://img.blog.csdn.net/20170921215853290?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

  蛇有三节,所以定义body是一个包有三个数的数组

  ![这里写图片描述](http://img.blog.csdn.net/20170921223532180?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

  这个上下文调用模式很关键,不然找不到Snake对象中的direction

  ![这里写图片描述](http://img.blog.csdn.net/20170921223622148?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

  用一个数组保存蛇身体的原来的位置![这里写图片描述](http://img.blog.csdn.net/20170921223840496?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

  问题来了,再次走时,蛇原来的身体还在????怎么办呢?![这里写图片描述](http://img.blog.csdn.net/20170921235615697?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)


	传入这个参数很重要,让它能找到那个对象.this.snake;
	
	![这里写图片描述](http://img.blog.csdn.net/20170924111119466?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
	
	给window添加键盘按下事件,让蛇可以四个方法移动.
	
	![这里写图片描述](http://img.blog.csdn.net/20170924111202627?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
	
	易错点,删蛇身时,要从后往前删,要不删不干净.
	![这里写图片描述](http://img.blog.csdn.net/20170924111346371?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
	
	顺序很重要,要不两个蛇身会走在一处的.
	![这里写图片描述](http://img.blog.csdn.net/20170924111425992?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
	
	有BUG如下图
	![这里写图片描述](http://img.blog.csdn.net/20170924111520359?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
	解决的方法如下:
	![这里写图片描述](http://img.blog.csdn.net/20170924111654290?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
	
	蛇吃进食物后加在尾部;好关键的一部
	![这里写图片描述](http://img.blog.csdn.net/20170924111739818?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
	不能少写一个减1
	![这里写图片描述](http://img.blog.csdn.net/20170924111830678?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
	![这里写图片描述](http://img.blog.csdn.net/20170924111843449?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
	
	//让food这个量变全局变量,当蛇吃了食物时,食物的位置发生了变化.
	![这里写图片描述](http://img.blog.csdn.net/20170924111913455?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
	![这里写图片描述](http://img.blog.csdn.net/20170924112037975?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
	//加入这些条件是让蛇只能左右转,前进,不能后退;
	
	![这里写图片描述](http://img.blog.csdn.net/20170924112000288?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
	
	这是一个易错点,还没有改过来的.
	
	![这里写图片描述](http://img.blog.csdn.net/20170924112100334?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
	
	//两个判断条件,但是出现了下面的BUG
	
	![这里写图片描述](http://img.blog.csdn.net/20170924112142139?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
	
	这里没写好.汗汗
	
	![这里写图片描述](http://img.blog.csdn.net/20170924112213633?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

----------


##阶段2
1. 总的来说,一个完整的贪食蛇写出来了,但是一个完好的贪食蛇是有等级的,怎么写的呢,比如等级越高,速度就越快.
  定义 this.duration

  ![这里写图片描述](http://img.blog.csdn.net/20170924124411098?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

2. 有个BUG如上图所示

  ![这里写图片描述](http://img.blog.csdn.net/20170924124653151?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

3. 更改语名1,,2的位置则可

![这里写图片描述](http://img.blog.csdn.net/20170924144955113?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU3RlcGhlbl9fV3U=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
大功告成,除了进入下一关时,不能好好的按自已想的延时,其它的一切都好了.

小伙伴们可以看我的原码[代码](http://pan.baidu.com/s/1gf8auor)