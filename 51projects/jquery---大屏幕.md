### 财贸北村智能步道

1. 财贸北村步道   swiper轮播图有第一张图一闪而过		

   ```js
     setTimeout(function(){   //等到html骨架生成后才生成轮播图  用setTimeOUT延时处理
               if(videoSwiper == undefined){
                   var videoSwiper = new Swiper('.video-swiper-container', {  //视频区的轮播图
                       autoplay: 5000,//可选选项，自动滑动
                       loop: true,//可选选项，开启循环
                       speed: 300,
                       initialSlide : 0
                   })
               }
           },1000)
   ```

2. 财贸北村换广告	`type`决定文件类型还是 `acceptFileTypes`决定文件类型

   可以判断文件后缀来修改文件类型;

   ```
   
   ```



### 劳动公园智能步道

1.  今天在公司里，做的东西都简单，所以就想做一个js代码丑化的处理，为了不让其他公司的程序员盗   我们的代码；

    uglify只能做到逻辑压缩跟变量压缩，做混淆应该不行；

    混淆JavaScript代码的gulp插件：gulp-obfuscate；

   花了半天时间搞好的bug，用了gulp-obfuscate之后，代码丑化的确实看不出来了，alert(9)也没有运行了；

   **正确的解决方法:** 

   ```js
   gulp.src('./src/oldJs/*.js')
           .pipe(uglify({
                   sourceMap: false,
                   compress: {
                       warnings: false,
                       drop_console: true,
                       drop_debugger: true,
                   },
                   mangle: {except: ['$super', '$', 'exports', 'require','avalon']} //排除关键字
               })).pipe(gulp.dest('./src/js'));
   ```

   同时把gulp的版本回退;

   可以参考vue-cli脚手架gulpfile.js文件;

