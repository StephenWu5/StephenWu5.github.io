##前言
最近公司老大要我们前端入一下react的门,就学起react来了

##路由传参的实现步奏:

1. 在路由表中

  ```
   <Router>
     <div>
         <div className='headerStyle'>
               <p><Link to="/">电影</Link></p>
           <p><input type='text' placeholder='请输入搜索的内容'></input><img src={searchImg} alt='111'/></p>
         </div>
  
         <Route exact path="/" component={Index} />
       <Route exact path="/more/:url" component={More} /> //这里写上url参数
       </div>
  </Router>
  ```
2. 路由式导航与编程式导航
   2.1 html的**Link**标签中
   ```
   return  <span><Link to={"/more/"+ props.url}>更多></Link></span>;
   ```
   2.2 编程式导航
   ```
   this.props.history.push('path'+参数);
   ```

	   注意： 编程时导航不是在页面上的任意地方都可以实现的，如果组件中不是包在`Router`(即路由表中),它的this.props没有history这个属性,不能实现编程式导航,这时候可以通过`Link`路由式导航来实现;

1. 在跳转后页面通过this.props.match.params.url来获取该参数
   ```
      console.log(this.props.match.params.url,"1111props");
   
   ```
   ![这里写图片描述](https://img-blog.csdn.net/20180525155120560?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

##附加:

刚开始接触react,不太熟悉,发现打印react组件的this.props里面有很多东西,感觉是个大发现,哈哈
![这里写图片描述](https://img-blog.csdn.net/20180525155421705?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)