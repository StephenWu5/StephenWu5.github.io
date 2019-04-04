



##为什么学习
> nodejsNode.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境。 
> Node.js 使用了一个事件驱动、非阻塞式 I/O 的模型，使其轻量又高效。 
> Node.js 的包管理器 npm，是全球最大的开源库生态系统。
> MongoDB 是一个基于分布式文件存储的数据库。由 C++ 语言编写。旨在为 WEB 应用提供可扩展的高性能数据存储解决方案。

目前,nodejs,比较火,作用挺大的,nodejs可以用来搭建一个前端项目脚手架,可以搭建服务器,可以作为后台语言操作数据库写业务逻辑;都说做后台的,一定懂一点前端,当前端不一定懂后台,所以,我觉得前端有必要学一下后台,至少要入一下门;

## 需要的知识点

1. html,css,jquery(这个是必备的)

2. nodejs

  nodejs使得javascript可以写后台的逻辑;nodejs前几年就火起来了,发展快,据公司的一个大佬已经成为一个规模相当大的生态圈;[nodejs的官网](http://nodejs.cn/)

3. express(nodejs)的一个框架

4. MongoDB 数据库 
  ![这里写图片描述](https://img-blog.csdn.net/20180524173942626?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
  其中mongodb的安装我是踩过好几次坑,得到了'血'的教训,长了经验:
  1. MongoDB最好安装在非Program Files的目录下,最好是这样的安装路径: E:\MongoDB\Server\3.2;
  2. 把mongodb的启动做成window的服务,然后net start mongodb, 这样关掉powershell,服务照样启动,方便好用;具体怎么实现这个服务可以看我的[博客](https://blog.csdn.net/Stephen__Wu/article/details/79451891)的35条看过程.

5. mongoose的一些操作MongoDB的API,如图所示
  [mongoose的官网](http://mongoosejs.com/docs/api.html#Model)
  ![这里写图片描述](https://img-blog.csdn.net/20180524173601759?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

## 在哪里学习

我是在网易云课堂上找到妙味课堂的[Node.js 实战开发：博客系统](http://study.163.com/note/noteIndex.htm?id=1003675016&type=0)安照老师的步奏来学习,从2018年的4月3号开始,陆陆续续的看视频,敲代码,知道现在5月24号(),差不多弄了大半了才觉得有必要写一个博客记录这个blog前后端的项目的学习过程;所以有开始写博客;中间也有时断开去打一小阵游戏(我有点贪玩);

#前端部分

- **写好blog的首页** 如图所示

   ![这里写图片描述](https://img-blog.csdn.net/20180524095542722?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

 ```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="/public/css/main.css">
    <script src="/public/js/jquery.min.js"></script>
    <script src="/public/js/index.js"></script>
    <title>我的博客</title>
</head>
<body>
    <header>
        <a href="./" class="logo"></a>
    </header>
    <nav class="navigation">
        <ul>
            <li class="active"><a href="">首页</a></li>
            <li><a href="">HTMLS</a></li>
            <li><a href="">CSS</a></li>
            <li><a href="">JAVASCRIPT</a></li>
            <li><a href="">PHP</a></li>
            <li><a href="">JAVA</a></li>
            <li><a href="">Express</a></li>
        </ul>
    </nav>
     <nav class="total">
         <nav class="wenzhang">
             <ul>
                 <li>
                     <p>symfony2</p>
                     <p>作者：<span class="author">admin</span> - 时间：<span class="time">2016年7月19日</span> - 阅读：<span class="preview">231</span> - 评论：<span class="commit">10</span></p>
                     <p>php框架 - symfony2</p>
                     <p>阅读全文</p>
                 </li>
                 <li>
                     <p>symfony2</p>
                     <p>作者：<span class="author">admin</span> - 时间：<span class="time">2016年7月19日</span> - 阅读：<span class="preview">231</span> - 评论：<span class="commit">10</span></p>
                     <p>php框架 - symfony2</p>
                     <p>阅读全文</p>
                 </li>
                 <li>
                     <p>symfony2</p>
                     <p>作者：<span class="author">admin</span> - 时间：<span class="time">2016年7月19日</span> - 阅读：<span class="preview">231</span> - 评论：<span class="commit">10</span></p>
                     <p>php框架 - symfony2</p>
                     <p>阅读全文</p>
                 </li>
             </ul>
         </nav>
         <nav class="user">
             <ul>
                 {% if userInfo._id %}
                <li id="userInfo">
                     <div class="title">用户信息</div>
                     <div class="body">
                         <p class="username">{{userInfo.username}}</p>
                         {% if userInfo.isAdmin %}
                         <p class="red info">
                             <span>你好,管理员!</span>
                             <a href="/admin">进入管理</a>
                         </p>
                         {% else %}
                         <p class="red info">你好,欢迎光临我的博客!</p>
                         {% endif %}
                         <p><a href="javascript:;" id="logout">退出</a></span></p>
                     </div>
                 </li>
                 {% else %}
                 <li id='loginBox'  style="display:none">
                     <div class="title">登录</div>
                     <div class="body">
                         <p>用户名: <input type="text" name="username"></p>
                         <p>密码:  <input type="password" name="password"></p>
                         <p><input type="button" value="登陆" class="denglu"></p>
                         <p>还没有注册？<a href="javascript:;" class="colMint">马上注册</a></p>
                         <p class="colWarning" style="color:black;text-align: center"></p>
                     </div>
                 </li>
                 <li id='registerBox'>
                     <div class="title">注册</div>
                     <div class="body">
                         <p>用户名: <input name='username' type="text"></p>
                         <p>密码:  <input name='password' type="password"></p>
                         <p>确认:  <input name='repassword' type="password"></p>
                         <p><input type="button" value="注册" class="denglu"></p>
                         <p>已经注册？<a href="javascript:;" class="colMint">马上登陆</a></p>
                         <p class="colWarning" style="color:black;text-align: center"></p>
                     </div>
                 </li>
                 {% endif %}
                 <li id='community'>
                     <div class="title">社区</div>
                     <div class="body">
                          <p><a href="">妙味课堂</a></p>
                          <p><a href="">妙味课堂2</a></p>
                     </div>
                 </li>
             </ul>
         </nav>
     </nav>
</body>
</html>

 ```
- **blog的管理首页**

     ![这里写图片描述](https://img-blog.csdn.net/20180524100809663?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
     
       实现这个blog的管理首页用的技术是boostrap的导航条组件，巨幕组件，功能单一，但是完全可以慢慢加；还有就是后端服务器渲染的知识点模板的语法；
     
       项目中用到的模板知识点：
     
      ```
       {% extends 'layout.html' %} //模板字符串的继承
       {% block main %}         //主模板
       <div class="jumbotron">
          <h1>Hello, {{userInfo.username}}!</h1>
          <p>欢迎进入我的博客后台管理!</p>
       </div>
       {% endblock %}
      ```

  - **blog的用户管理首页**
      ![这里写图片描述](https://img-blog.csdn.net/20180524102735438?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

      实现这个blog的管理首页用的技术是boostrap的导航条组件，路径导航组件，表格组件(用于展示用户列表),分页组件(点击实现页数的跳转);还有就是后端服务器渲染的知识点模板的语法；

      ```
      {%include 'page.html'%}   //服务端渲染子字符串模版(页数跳转页面)
       
      {% for user in users %}    //循环渲染
          <tr>
              <td>{{user._id.toString()}}</td>
              <td>{{user.username}}</td>
              <td>{{user.password}}</td>
              <td>{%if user.isAdmin%}是{%endif%}</td>
          </tr>
      {% endfor %}
      ```
      其中我来说说页数跳转的功能实现: 

   - page.html

  	   ```
  	   <nav aria-label="...">
  			    <ul class="pager">
  			        <li class="previous"><a href="/admin/user?page={{page-1}}"><span aria-hidden="true">&larr;</span> 上一页</a></li>
  			        <li> 一共有{{count}}条数据，每页显示{{limit}}条数据，一共{{pages}}页，当前{{page}}页</li>
  			        <li class="next"><a href="/admin/user?page={{page+1}}">下一页<span aria-hidden="true">&rarr;</span></a></li>
  			    </ul>
  			</nav>
  	```

   - page 后台逻辑的实现 express();

  	```
  	/*
  	* 从数据库中读取所有的用户的数据
  	* limit(Number) : 限制获取的数据的条数
  	*
  	* 每页显示2页
  	* skip(2): 忽略的条数
  	* 1: 1-2 skip: 0 ->(当前也-1) * limit
  	* 2: 3-4 skip: 2
  	 */
  	 var page = Number(req.query.page || 1);  //当前页
  	 var limit = 2;   // 一个显示的个数
  	 var pages = 0;   // 总页数
  	
  	User.count().then(function(count){   //count为总的用户的个数
  	
  	    var skip;    //忽略的页数
  	    //总页数
  	    pages = Math.ceil(count / limit);
  	    // 取值不能大于pages
  	    page = Math.min(page,pages);
  	    // 取值不能小于1
  	    page = Math.max(page,1);
  	
  	    skip = (page - 1) * limit
  	    User.find().limit(limit).skip(skip).then(function(users){
  	        res.render('admin/user_index',{
  	            userInfo: req.userInfo,
  	            users: users,
  	
  	            count: count,
  	            pages: pages,
  	            limit: limit,
  	            page: page
  	        })
  	    })
  	})
  	```
  - **分类管理/分类添加页面** 
    ![这里写图片描述](https://img-blog.csdn.net/20180524105514609?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
    这个页面用到的技术是boostrap的导航条组件,路径导航组件,表单组件(用来提交)
    表单中的点击提交后,会自动向服务器提交一个和当前页面路径加上jquery的一样的post请求;所以只需要在后台添加一个post请求的接口就可以了,前端部分并不需要太多的处理,简单方便,真是前端工程师的一大福音;

  - **分类的删除**

    ![这里写图片描述](https://img-blog.csdn.net/20180524172311512?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
    	该删除页面用到的技术是bootstrap的导航条组件,路径导航组件,警告框组件,表单组件;同理,该页面的表单提交后,会默认的向服务器提交一个和当前页面路径一样的post请求,前端部分同样不需要太多的处理
    	
        
    #后台部分

    ## blog的首页
    - **用户注册**
      - 注册查询
        - 用户名不能为空

          ```
          if(username === ''){
                responseData.code = 1;
                responseData.message = '用户名不能为空';
                res.json(responseData);
                return;
            }
          ```
        - 密码不能为空
          		
          ```
          if(password === ''){
                responseData.code = 2;
                responseData.message = '密码不能为空';
                res.json(responseData);
                return;
            }
          ```
        - 两次的密码不能不一致

          ```
          if(repassword !== password){
              responseData.code = 2;
              responseData.message = '密码不能为不一致';
              res.json(responseData);
              return;
          }
          ```
      - 数据库查询
        - 数据库中是否已存在这个用户名
        - 存在   返回提示用户名已存在
        - 不存在    返回提示注册成功

          ```
              User.findOne({
                username: username
              }).then(function(userInfo){
                  console.log(userInfo, "1111");
                  if(userInfo ){
                      //数据库已存在
                      responseData.code = 4;
                      responseData.message = '数据库已存在';
                      res.json(responseData);
                      return ;
                  }
                  // 保存用户注册的信息到数据库中
                  var user = new User({
                      username: username,
                      password: password
                  });
                  return user.save();
              }).then(function(newUserInfo){
                  console.log(newUserInfo, "1111");
                  responseData.message = '注册成功';
                  res.json(responseData);
              });
          ```

    - **用户登录**  
      - 登录查询
        -  用户名不能为空

        ```
        if(username === ''){
              responseData.code = 1;
              responseData.message = '用户名不能为空';
              res.json(responseData);
              return;
          }
        ```
        - 密码不能为空

        ```
        if(password === ''){
              responseData.code = 2;
              responseData.message = '密码不能为空';
              res.json(responseData);
              return;
          }
        ```
       - 数据库查询
           - 用户名和密码同时存在  返回登录成功
           - 用户名和密码不同时存在 返回登录失败

           ```
                User.findOne({
                   password: password,
                   username: username
               }).then(function(userInfo){
                   if(userInfo){
                       responseData.message = '登录成功!';
                       responseData.userInfo = {
                           _id: userInfo._id,
                           username: userInfo.username
                       }
                       req.cookies.set('userInfo',JSON.stringify({
                           _id: userInfo._id,
                           username: userInfo.username
                       }));
                       res.json(responseData);
                       return;
                   }else{
                       responseData.code = 3;
                       responseData.message = '用户名或者密码错误!';
                       res.json(responseData);
                       return;
                   }
               })
           ```

           - 登录成功的时候 记得从服务器设置发送一个cookies到浏览器这边,代码如下:
           ```
                req.cookies.set('userInfo',JSON.stringify({
                    _id: userInfo._id,
                    username: userInfo.username
                }));
           ```
    - **退出功能** 点击一个html上的退出按钮,发送/user/logout接口请求

      - 前端代码如下:

        ```
        $('#logout').on('click',function(){
            $.ajax({
                url:'/api/user/logout',
                success:function(result){
                    if(!result.code){
                        window.location.reload();
                    }
                }
            })
        })
        ```
      - 后台代码

        ```
        router.get('/user/logout',function(req,res){
            req.cookies.set('userInfo',null);
            res.json(responseData);
        })
        ```

    ## blog管理页面

    ### 用户管理

    ### 分类首页
    - **分类的编辑**
      - 分类编辑框的展示
        同样是两个分支,根据_id查询服务器 id 在服务器中存在,正常渲染category_edit.html

        ```
        res.render('admin/category_edit',{
        	userInfo: req.userInfo,
        	 category: category
             });
        ```

        如果不存在,渲染error.html

        ```
        res.render('admin/error',{
             userInfo: req.userInfo,
             message: '分类信息不存在'
        });
        return Promise.reject();
        		
        ```
      - 分类编辑的修改

        - 新修改后的类名不能为空

        ```
        if(name === ''){
              res.render('admin/error',{
                  userInfo: req.userInfo,
                  message: '类名不能为空'
              });
              return;
          }
        ```
        - 数据库查询 
          - 新取的类名是否在类名列表中存在
            这个时候有两种情况 1.和自已相同;2.和别人相同

            ```
            if(morename._id == id){
                     res.render('admin/error',{
                         userInfo: req.userInfo,
                         message: '修改不成功,类名不能和上一次相同'
                     });
                     return;
                 }else{
                     res.render('admin/error',{
                         userInfo: req.userInfo,
                         message: '修改不成功,类名已存在'
                     });
                     return;
               }
            ```
          - 新取的类名是否在类名列表中不存在
            提示类名修改成功

            ```
             Category.findByIdAndUpdate(id,{
                        name: name
                    }).then(function(newName){
                        if(!newName){
                            res.render('admin/error',{
                                userInfo: req.userInfo,
                                message: '修改不成功'
                            });
                            return;
                        }else{
                            res.render('admin/success.html',{
                                userInfo: req.userInfo,
                                message: '修改类名成功',
                                url:'/admin/category'
                            })
                            return;
                        }
                    })
            ```
    - **分类的删除**
      - 删除页面的展示

         数据库查询ID,存在,展示category_delete页面,

       ```
       res.render('admin/category_delete',{
                   userInfo: req.userInfo,
                   category: category
               })
       ```
       如果不存在,跳到error.html页面
       ```
        res.render('admin/error',{
            userInfo: req.userInfo,
                message: '分类信息不存在'
            })
       ```
      - 利用删除页面上的post按钮,发送一个post请求到服务器; 服务器后台的业务逻辑如下:

        	```
          	router.post('/category/delete',function(req,res,next){
          	    var id = req.query.id;
          	    Category.findByIdAndDelete(id).then(function(success){
          	        if(!success){
          	            res.render('admin/error',{
          	                userInfo: req.userInfo,
          	                message: '删除失败'
          	            })
          	        }else{
          	            res.render('admin/success',{
          	                userInfo: req.userInfo,
          	                message: '删除成功',
          	                url:'/admin/category'
          	            })
          	        }
          	    })
          	})
        ```

        ### 分类添加

        - 分类保存的查询
           - 分类名不能为空

              ```
              var name = req.body.name || '';
               if(name === ''){
                   res.render('admin/error',{
                       userInfo: req.userInfo,
                       message: '名称不能为空'
                   });
                   return;
               }
              ```
           - 数据库是否已存在这个分类名
              - 存在,跳到一个error.html页面
              - 不存在,保存分类名到数据库内,之后跳到一个success.html的页面,代码如下:

              ```
                   //数据库中是否已存在这个分类名
               Category.findOne({
                   name: name
               }).then(function(rs){
                   if(rs){
                       //该数据库中1已存在
                       res.render('admin/error',{
                           userInfo: req.userInfo,
                           message: '分类中已存在',
                           url: '/admin/category/add'
                       });
                       return;
                   }else{
                       //数据库中不存在该分类
                       return new Category({name: name}).save();
                   }
               }).then(function(newCategory){
                   if(newCategory){
                       res.render('admin/success',{
                           userInfo: req.userInfo,
                           message: '分类保存成功',
                           url: '/admin/category'
                       })
                   }
                   return;
               })
              ```


##为什么学习
> nodejsNode.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境。 
> Node.js 使用了一个事件驱动、非阻塞式 I/O 的模型，使其轻量又高效。 
> Node.js 的包管理器 npm，是全球最大的开源库生态系统。
> MongoDB 是一个基于分布式文件存储的数据库。由 C++ 语言编写。旨在为 WEB 应用提供可扩展的高性能数据存储解决方案。

目前,nodejs,比较火,作用挺大的,nodejs可以用来搭建一个前端项目脚手架,可以搭建服务器,可以作为后台语言操作数据库写业务逻辑;都说做后台的,一定懂一点前端,当前端不一定懂后台,所以,我觉得前端有必要学一下后台,至少要入一下门;

## 需要的知识点

1. html,css,jquery(这个是必备的)

2. nodejs

  nodejs使得javascript可以写后台的逻辑;nodejs前几年就火起来了,发展快,据公司的一个大佬已经成为一个规模相当大的生态圈;[nodejs的官网](http://nodejs.cn/)

3. express(nodejs)的一个框架

4. MongoDB 数据库 
  ![这里写图片描述](https://img-blog.csdn.net/20180524173942626?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
  其中mongodb的安装我是踩过好几次坑,得到了'血'的教训,长了经验:
  1. MongoDB最好安装在非Program Files的目录下,最好是这样的安装路径: E:\MongoDB\Server\3.2;
  2. 把mongodb的启动做成window的服务,然后net start mongodb, 这样关掉powershell,服务照样启动,方便好用;具体怎么实现这个服务可以看我的[博客](https://blog.csdn.net/Stephen__Wu/article/details/79451891)的35条看过程.

5. mongoose的一些操作MongoDB的API,如图所示
  [mongoose的官网](http://mongoosejs.com/docs/api.html#Model)
  ![这里写图片描述](https://img-blog.csdn.net/20180524173601759?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

## 在哪里学习

我是在网易云课堂上找到妙味课堂的[Node.js 实战开发：博客系统](http://study.163.com/note/noteIndex.htm?id=1003675016&type=0)安照老师的步奏来学习,从2018年的4月3号开始,陆陆续续的看视频,敲代码,知道现在5月24号(),差不多弄了大半了才觉得有必要写一个博客记录这个blog前后端的项目的学习过程;所以有开始写博客;中间也有时断开去打一小阵游戏(我有点贪玩);


#前端部分


- **写好blog的首页** 如图所示

   ![这里写图片描述](https://img-blog.csdn.net/20180524095542722?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

 ```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="/public/css/main.css">
    <script src="/public/js/jquery.min.js"></script>
    <script src="/public/js/index.js"></script>
    <title>我的博客</title>
</head>
<body>
    <header>
        <a href="./" class="logo"></a>
    </header>
    <nav class="navigation">
        <ul>
            <li class="active"><a href="">首页</a></li>
            <li><a href="">HTMLS</a></li>
            <li><a href="">CSS</a></li>
            <li><a href="">JAVASCRIPT</a></li>
            <li><a href="">PHP</a></li>
            <li><a href="">JAVA</a></li>
            <li><a href="">Express</a></li>
        </ul>
    </nav>
     <nav class="total">
         <nav class="wenzhang">
             <ul>
                 <li>
                     <p>symfony2</p>
                     <p>作者：<span class="author">admin</span> - 时间：<span class="time">2016年7月19日</span> - 阅读：<span class="preview">231</span> - 评论：<span class="commit">10</span></p>
                     <p>php框架 - symfony2</p>
                     <p>阅读全文</p>
                 </li>
                 <li>
                     <p>symfony2</p>
                     <p>作者：<span class="author">admin</span> - 时间：<span class="time">2016年7月19日</span> - 阅读：<span class="preview">231</span> - 评论：<span class="commit">10</span></p>
                     <p>php框架 - symfony2</p>
                     <p>阅读全文</p>
                 </li>
                 <li>
                     <p>symfony2</p>
                     <p>作者：<span class="author">admin</span> - 时间：<span class="time">2016年7月19日</span> - 阅读：<span class="preview">231</span> - 评论：<span class="commit">10</span></p>
                     <p>php框架 - symfony2</p>
                     <p>阅读全文</p>
                 </li>
             </ul>
         </nav>
         <nav class="user">
             <ul>
                 {% if userInfo._id %}
                <li id="userInfo">
                     <div class="title">用户信息</div>
                     <div class="body">
                         <p class="username">{{userInfo.username}}</p>
                         {% if userInfo.isAdmin %}
                         <p class="red info">
                             <span>你好,管理员!</span>
                             <a href="/admin">进入管理</a>
                         </p>
                         {% else %}
                         <p class="red info">你好,欢迎光临我的博客!</p>
                         {% endif %}
                         <p><a href="javascript:;" id="logout">退出</a></span></p>
                     </div>
                 </li>
                 {% else %}
                 <li id='loginBox'  style="display:none">
                     <div class="title">登录</div>
                     <div class="body">
                         <p>用户名: <input type="text" name="username"></p>
                         <p>密码:  <input type="password" name="password"></p>
                         <p><input type="button" value="登陆" class="denglu"></p>
                         <p>还没有注册？<a href="javascript:;" class="colMint">马上注册</a></p>
                         <p class="colWarning" style="color:black;text-align: center"></p>
                     </div>
                 </li>
                 <li id='registerBox'>
                     <div class="title">注册</div>
                     <div class="body">
                         <p>用户名: <input name='username' type="text"></p>
                         <p>密码:  <input name='password' type="password"></p>
                         <p>确认:  <input name='repassword' type="password"></p>
                         <p><input type="button" value="注册" class="denglu"></p>
                         <p>已经注册？<a href="javascript:;" class="colMint">马上登陆</a></p>
                         <p class="colWarning" style="color:black;text-align: center"></p>
                     </div>
                 </li>
                 {% endif %}
                 <li id='community'>
                     <div class="title">社区</div>
                     <div class="body">
                          <p><a href="">妙味课堂</a></p>
                          <p><a href="">妙味课堂2</a></p>
                     </div>
                 </li>
             </ul>
         </nav>
     </nav>
</body>
</html>

 ```
































> nodejsNode.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境。 
> Node.js 使用了一个事件驱动、非阻塞式 I/O 的模型，使其轻量又高效。 
> Node.js 的包管理器 npm，是全球最大的开源库生态系统。
> MongoDB 是一个基于分布式文件存储的数据库。由 C++ 语言编写。旨在为 WEB 应用提供可扩展的高性能数据存储解决方案。

##为什么学习

目前,nodejs,比较火,作用挺大的,nodejs可以用来搭建一个前端项目脚手架,可以搭建服务器,可以作为后台语言操作数据库写业务逻辑;都说做后台的,一定懂一点前端,当前端不一定懂后台,所以,我觉得前端有必要学一下后台,至少要入一下门;

## 需要的知识点

1. html,css,jquery(这个是必备的)

2. nodejs

  nodejs使得javascript可以写后台的逻辑;nodejs前几年就火起来了,发展快,据公司的一个大佬已经成为一个规模相当大的生态圈;[nodejs的官网](http://nodejs.cn/)

3. express(nodejs)的一个框架

4. MongoDB 数据库 
  ![这里写图片描述](https://img-blog.csdn.net/20180524173942626?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
  其中mongodb的安装我是踩过好几次坑,得到了'血'的教训,长了经验:
  1. MongoDB最好安装在非Program Files的目录下,最好是这样的安装路径: E:\MongoDB\Server\3.2;
  2. 把mongodb的启动做成window的服务,然后net start mongodb, 这样关掉powershell,服务照样启动,方便好用;具体怎么实现这个服务可以看我的[博客](https://blog.csdn.net/Stephen__Wu/article/details/79451891)的35条看过程.

5. mongoose的一些操作MongoDB的API,如图所示
  [mongoose的官网](http://mongoosejs.com/docs/api.html#Model)
  ![这里写图片描述](https://img-blog.csdn.net/20180524173601759?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

## 在哪里学习

我是在网易云课堂上找到妙味课堂的[Node.js 实战开发：博客系统](http://study.163.com/note/noteIndex.htm?id=1003675016&type=0)安照老师的步奏来学习,从2018年的4月3号开始,陆陆续续的看视频,敲代码,知道现在5月24号(),差不多弄了大半了才觉得有必要写一个博客记录这个blog前后端的项目的学习过程;所以有开始写博客;中间也有时断开去打一小阵游戏(我有点贪玩);


#前端部分

- **写好blog的首页** 如图所示

   ![这里写图片描述](https://img-blog.csdn.net/20180524095542722?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

 ``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="/public/css/main.css">
    <script src="/public/js/jquery.min.js"></script>
    <script src="/public/js/index.js"></script>
    <title>我的博客</title>
</head>
<body>
    <header>
        <a href="./" class="logo"></a>
    </header>
    <nav class="navigation">
        <ul>
            <li class="active"><a href="">首页</a></li>
            <li><a href="">HTMLS</a></li>
            <li><a href="">CSS</a></li>
            <li><a href="">JAVASCRIPT</a></li>
            <li><a href="">PHP</a></li>
            <li><a href="">JAVA</a></li>
            <li><a href="">Express</a></li>
        </ul>
    </nav>
     <nav class="total">
         <nav class="wenzhang">
             <ul>
                 <li>
                     <p>symfony2</p>
                     <p>作者：<span class="author">admin</span> - 时间：<span class="time">2016年7月19日</span> - 阅读：<span class="preview">231</span> - 评论：<span class="commit">10</span></p>
                     <p>php框架 - symfony2</p>
                     <p>阅读全文</p>
                 </li>
                 <li>
                     <p>symfony2</p>
                     <p>作者：<span class="author">admin</span> - 时间：<span class="time">2016年7月19日</span> - 阅读：<span class="preview">231</span> - 评论：<span class="commit">10</span></p>
                     <p>php框架 - symfony2</p>
                     <p>阅读全文</p>
                 </li>
                 <li>
                     <p>symfony2</p>
                     <p>作者：<span class="author">admin</span> - 时间：<span class="time">2016年7月19日</span> - 阅读：<span class="preview">231</span> - 评论：<span class="commit">10</span></p>
                     <p>php框架 - symfony2</p>
                     <p>阅读全文</p>
                 </li>
             </ul>
         </nav>
         <nav class="user">
             <ul>
                 {% if userInfo._id %}
                <li id="userInfo">
                     <div class="title">用户信息</div>
                     <div class="body">
                         <p class="username">{{userInfo.username}}</p>
                         {% if userInfo.isAdmin %}
                         <p class="red info">
                             <span>你好,管理员!</span>
                             <a href="/admin">进入管理</a>
                         </p>
                         {% else %}
                         <p class="red info">你好,欢迎光临我的博客!</p>
                         {% endif %}
                         <p><a href="javascript:;" id="logout">退出</a></span></p>
                     </div>
                 </li>
                 {% else %}
                 <li id='loginBox'  style="display:none">
                     <div class="title">登录</div>
                     <div class="body">
                         <p>用户名: <input type="text" name="username"></p>
                         <p>密码:  <input type="password" name="password"></p>
                         <p><input type="button" value="登陆" class="denglu"></p>
                         <p>还没有注册？<a href="javascript:;" class="colMint">马上注册</a></p>
                         <p class="colWarning" style="color:black;text-align: center"></p>
                     </div>
                 </li>
                 <li id='registerBox'>
                     <div class="title">注册</div>
                     <div class="body">
                         <p>用户名: <input name='username' type="text"></p>
                         <p>密码:  <input name='password' type="password"></p>
                         <p>确认:  <input name='repassword' type="password"></p>
                         <p><input type="button" value="注册" class="denglu"></p>
                         <p>已经注册？<a href="javascript:;" class="colMint">马上登陆</a></p>
                         <p class="colWarning" style="color:black;text-align: center"></p>
                     </div>
                 </li>
                 {% endif %}
                 <li id='community'>
                     <div class="title">社区</div>
                     <div class="body">
                          <p><a href="">妙味课堂</a></p>
                          <p><a href="">妙味课堂2</a></p>
                     </div>
                 </li>
             </ul>
         </nav>
     </nav>
</body>
</html>

 ```