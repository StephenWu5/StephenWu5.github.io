##gulp 是一个自动化工具,前端开发者常用它来完成任务:

1. 创建一个gulpfile.js的文件

  ```
  var gulp = require('gulp');
  //gulp.task('task-name', function() {
  // Stuff here
  //});
  gulp.task('hello', function() {
    console.log('Hello World!');
  });
  ```
  gulp hello 运行
  那么将会输出Hello World!。

2. 用gulp做移动开发的真机测试,要注意的地方
  ```
  //配置代理服务器
  var connect = require('gulp-connect');
  var proxy = require('http-proxy-middleware');
  
  gulp.task('connect', function () {
      connect.server({
          root: './src',
          //如何8080不行,就3000吧
          port: 3000,
          //本电脑的ip cmd -> ipconfig
          host:"192.168.1.149",
          livereload: true,
          middleware: function (connect, opt) {
              return [
                  proxy('/api', {
                      target: 'http://www.tiyouholdings.com/',
                      changeOrigin: true
                  })
              ]
          }
      })
  });
  ```