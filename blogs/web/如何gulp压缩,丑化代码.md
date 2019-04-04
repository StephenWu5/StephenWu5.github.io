#### 为什么使用

最近在迭代公司的项目,发现项目有如下缺点: 

1. 代码没有压缩,js文件，内存大，放在服务器上占空间；
2. 源代码没有混淆或者丑化处理，本公司的程序员写出来的代码和高质量逻辑容易被其他公司的程序员盗用；
3. js,css 文件数量多，浏览器加载起来会“手忙脚乱”和“生气”。

这个小项目使用gulp构建工具写的，所以很自然用gulp下的一系列插件来完成。其中用到的插件有：`gulp-concat`整合数量大的文件为一个文件，`gulp-uglify`丑化代码，不让别人轻易得到你的源码，`gulp-uglify`重新命名文件名称等等

#### 实现

运行`cnpm i   gulp-concat  gulp-uglify gulp-rename --save-dev` 安装这三个包 `--save-dev`的意思就是在开发环境；

这几个插件使用起来还好，容易，比较曲折一点的就是`gulp-uglify:` 我一开始是上npm官网安装了一个最新版的uglify可是没有用，我百度，谷歌折腾了一会，同事和我说vue-cli项目就有这个gulp功能，让我去参考如何使用。原来是uglify的版本不一样，我把版本从最新版降级到2.0.0就可以了。

```json
"gulp-uglify": "^2.0.0",
```

其中使用代码如下：（js部分）

```js
//丑化js代码
gulp.task('compress', function () {
    gulp.src('./src/oldJs/*.js')    //注意路径的写法
        .pipe(concat('main.js'))    //合并所有js到main.js
        .pipe(rename({suffix: '.min'}))   //rename压缩后的文件名
        .pipe(uglify({              //丑化js代码，相当加密
            sourceMap: false,
            compress: {
                warnings: false,
                drop_console: true,
                drop_debugger: true,
            },
            mangle: {except: ['$super', '$', 'exports', 'require','avalon']} //排除关键字
        }))
        .pipe(gulp.dest('./src/js'));  //注意路径的写法
});
//😀😀😀😀😀😀
```

其中源文件夹和输出文件夹的路径要看具体项目而言。

最后,运用这个知识点,你会发现代码简洁，内存变小，js文件的数量也控制在1了，不是挺好的吗，嘿嘿。