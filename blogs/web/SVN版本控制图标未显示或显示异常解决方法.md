在工作中大伙不是用svn就是用git管理代码,对于用小乌龟svn的公司来说,svn的图标真的很重要,因为它显示我们是否在项目中修改了代码,问题来吗,如果有一天SVN版本控制图标未显示或显示异常,你会很着急的。

不幸的是，我遇到了，百度啊；

## 步骤

1. win+r 打开注册表 ,展开

  ```
  计算机\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\ShellIconOverlayIdentifiers\
  ```
  ![这里写图片描述](https://img-blog.csdn.net/2018061514321121?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

  把图中的Tortorise共九项提到前面，如图所需，往前提的方法就是重命名，在原来的名称前加一个或多个空格；

2. ctrl+shift+ESc 打开任务管理器，找到windows资源管理器，点击重启；

3. 到svn找到setting页，

  ![这里写图片描述](https://img-blog.csdn.net/20180615143715948?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

  把上图的`status cache`改为`default`**或者**`shell`,在这里是或者啊,注意,我在百度找了很多帮助,都是叫我改为`shell`项,但是图标依然显示异常,最后我改回`default`,终于显示正常了,妈妈再也不要担心我改了代码忘了提交了哈哈;


**喜欢我给我点个赞吧.**