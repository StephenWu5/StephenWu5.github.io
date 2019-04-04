## 成长知识点(BUG版)
1. **z-index**

  -  父元素的`z-index`和子元素的`z-index`优先级很不同哦;

  -  两个兄弟元素比较`z-index`时,最好是position的类型一样的情况下比较: 例如一个是`absolute`,另一个也是`absolute`;

2. 
  ```
   < a href=" ">< img src="img/logo.png" alt="logo" class="logo-default" style="margin: 16px 0 0 28px!important;"></ a>
   // ../../无论多少个../只能退到服务器域名那里
  ```

3. css span宽度高度成功设置解决篇 span 要设置display:block,才能设置好宽高的

4. 有时候样式设置不对,就是浏览器缓存的问题
   上线后的样式缓存,jquery请求的问题,为什么请求不到,都是谷歌浏览器的缓存问题 

5. 记住一点,自个的web测试,要清除浏览器的缓存

6. 不要轻易说别人的代码没什么用,这是不好的习惯;

7. 谷歌浏览器的最小字体,为12px;

8. jquery插件 jquery.nav.js 的使用: $("#back-to-top").onePageNav(),这个ul的li必须要用2个,而且href的值要对的上;

9. js的debugger相当与添加断点;

10. 二倍图三倍图的使用的样式的书写

  ```
   [data-dpr='2'] div{
  			fontsive:24px;
  }
  ```
11. 项目中使用gulp代理可以解决跨域的问题

   ```
     connect.server({
     root:'./src',
     port:8010,
     livereload:true,
     middleware:""
     })
   ```
12. 不能给退出全屏的F11添加事件; 改 resign 函数中的

   ```
    var $window = $('.row');
    //on() off()  取消单击事件
   ```
13. 当项目中的宽度不够时,要注意是否缩放了;注意:    回调中的回调,体游控股后台列表的排序;
14. 一个无缘无故的bug:  html{  overflow-x:hidden}
15. ueditor 不能上传图片,因为需要后台的配置;
16. 页面的缓存控制

   ```
    <meta http-equiv='cache-control'/>
     <meta http-equiv='expires'/>
   ```
17. 
   项目中的login与网络中的login,ie登录不上,谷歌却可以;
     远程视频管理 ie11的浏览器设置为默认;
18. 来自成哥的建议：
     不要浪费时间；学习新的知识点要看视频，同事之间讨论，刷题等等；8小时的睡眠；与产品多沟通，预测，提前解决bug;   
19. 如果是在 windows 下用 git bash，那么应该是 ssh-add 没有正确添加 key。改用 Git GUI 创建 key 而不是 ssh-keygen 命令，就能解决这个问题。
   Github Windows
20. ssh git提交免登陆 fatal: HttpRequestException encountered解决方法
   网上查了一下发现是Github 禁用了TLS v1.0 and v1.1，必须更新Windows的git凭证管理器，才行。 
   [https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/tag/v1.14.0](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/tag/v1.14.0)
21. 
   ```
   if(projectData.name){
     // 一个bug  一定要全用同步的好处
     fs.mkdirSync(projectData.name);
   
     var fileData = projectData.fileData;
     if(fileData && fileData.forEach){
       fileData.forEach(function(f){
         f.path = projectData.name+'/'+f.name;
         f.content = f.content || '';
         switch (f.type) {
           case 'dir':
               fs.mkdirSync(f.path);
             break;
           case 'file':
               fs.writeFileSync(f.path,f.content);
             break;
           default:
             break;
         }
       })
     }
   }
   ```
22. **百度echart** 

   ```
   handleIcon:"",
   handleSize:"80%"
   ```
23. js**除掉字符串**的方法

   ```
    if(parkIds!=""){
   		parrkIds = parkIds.substr(0,parkIds.length - 1);
    }
       //除掉空的字符串
   ```
24. 一个没有解决的bug,为什么豆瓣有的图能请求到,有的就没法请求的到呢
    豆瓣内部的链

25. 一个mongodb的bug,--dbpath写成--path了
   ongoDB: shutting down with code:100
   	解决的方法是把mongod安装在非系统盘,在cmd中以系统管理员的身份运行配一个运行mongodb的服务,net start mongodb则可;

26. weui.js 的alert弹窗的字体太小是因为页面上没有加一个meta viewport的标签.

27. 如何设置avalon组件的array的值,用的是es6的箭头函数.

   ```
    array: vm.array,
    onInit:function(){
          setInterval(()=>{
             this.array = vm.array;
              console.log(this.array, "11113");
         }, 7000);
     },
     onReady: function(){
         console.log('onReady',"1111");
     }
   ```
28. 当avalon和swiper结合使用时,swiper的初始化会切断avalon与数据的绑定,所以是不能再次更新数据列表,等这一经验于公司的赛事项目的大屏幕直播页面;最好的做法是去掉swiper这个插件,用原生的jquery写列表动画!

29. 当npm的插件记录不到pack.json中时,记得在npm中手动加上去;

30. 当访问放到服务器上的页面的时候,最好带上.html,哪怕是index.html,这样子确保一定访问的到;在ios上调试有问题的时候,最好用苹果的笔记本去调试;
31. 一段不重复显示的代码(微信端的报名页面):

   ```
   //不显示重复的日期
     NoShowRepeat(arr){
           let matchTime = -1;
           $(arr).each(function(index,ele){
               if(index === 0){
                  matchTime =  ele.matchTime;
                  ele.isShow = true;
              }else if(matchTime === ele.matchTime){
                  ele.isShow = false;
              }else if(matchTime !== ele.matchTime){
                  matchTime =  ele.matchTime;
                  ele.isShow = true;
              }
           })
   
           return arr;
       }
   ```
32. 当vue 渲染列表时需要一些特殊的属性时,在后台接口返回来的json数据加上需要的键值对,这样子渲染时就能方便拿得到;

33. 当页面的高度不够屏幕的高度时,用jQuery暴力赋予啦啦啦;
   ```
    //高度自适配
         height(){
               console.log(document.documentElement.clientWidth,"1111clientWidth");
               console.log(document.documentElement.clientHeight,"1111");
               var clientHeight = document.documentElement.clientHeight;
               if($('.active-list').height() < clientHeight){
                   $('html,body').css({
                       'height': clientHeight,
                       'background-color': '#252638'
                   });
               }
   
             }
   ```

34. 平时写接口是可以好好利用github上的这个接口

   ```
   https://api.github.com/users/StephenWu5    或者
   https://api.github.com/users/octocat/gists //这个是官网自己定义的
   ```

35. mongodb的安装问题

   ```javascript
     //安装：
     mongod --dbpath "C:\mongodb\db" --logpath "C:\mongodb\log.txt" --install --serviceName "MongoDB"
     //卸载：
   mongod.exe --remove --serviceName "MongoDB"
   启动服务报错100 的解决方法:具体操作方法：开始-》所有程序-》附件-》右键“命令行提示符”，选择以管理员身份运行，然后执行下面的命令：
   D:\mongodb-win32-i386-2.0.2\bin>mongod --install --serviceName MongoDB --serviceDisplayName MongoDB --logpath c:\MongoDB.Log --dbpath c:\MongoDB --directoryperdb  
   终于，Mongo服务安装成功啦！
   ```

36. class 预留字,不能作为css的类名,否则不会起到什么作用的哦。

37. 一个jQuery发送请求时应写好的模式:
   ```javascript
   	// done 
       // 当延迟成功时调用的一个函数
       // fail
       // 当延迟失败时调用的一个函数
       $.get("http://wthrcdn.etouch.cn/WeatherApi?ci5ty=深圳").done(function (e) {
           console.log(e,'1111');
       }).fail(function(e){
           console.log(e,'1111');
       })
   ```
38. 当后台的接口返回来的json格式不对时,
   `ajax`的`success`不会执行。 

39. 侧边栏的tab效果关键是利用window.location.pathname找到a标签；

40. 日期选择器的样式乱是因为没有已经对应的样式；百度地图和echart是可以结合使用的；

41. 用传统的方法写圆点的时候,移动端项目中有时会出现有的点不是全圆的点,这是因为px转rem的时候他不是完全对的,有四舍五入: 
   解决的方法有2:
   ```css
   <span class="circle">●</span>  //html的内容
   .circle{
   margin-right: 10px;
   color: #666bfe!important;
   font-size: 6pt;
   }
   ```
   或者
   ```css
   .circle{
   	width: 10px; /**px**/  //不让这个px值往rem那边转
   	height: 10px;  /**px**/
   }
   ```