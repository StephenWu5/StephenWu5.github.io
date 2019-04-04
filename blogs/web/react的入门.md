##react的入门
1. react组件的使用,必须大写字母开头 如

  ```html
  <App/>
  ```
2. 组件中的样式,不能以双引号开头,要写成 {}  ,内部带上一个对象

3. render 函数中的return 必须返回一个东西,最好带上一个括号()

4. import  './static/test1.css' 导入css资源时的注意点,不能省略**./** 不然会报错找不到资源的哦

5. react 组件中的div的className=""是带双引号,不是带{}

6. react 的脚手架,是react-creact-app,npm run object 可以让隐藏的项目文件显示出来.

7. **react 渲染组件的四个过程**

  ```javascript
  四个过程:
  我们对<Welcome name="Sara" />元素调用了ReactDOM.render()方法。
  React将{name: 'Sara'}作为props传入并调用Welcome组件。
  Welcome组件将<h1>Hello, Sara</h1>元素作为结果返回。
  React DOM将DOM更新为<h1>Hello, Sara</h1>。
  ```
8. react 初始化state的值要给好数据结构(豆瓣几小时的bug);

9. ```
   text-align: center;
   display: inline-block;
   //豆瓣的文件title水平居中了	 
   ```

10. react-create-app 的项目文件夹的名称不能改,否则项目跑起来会报错.

11. 当一个脚手架需要一个功能时,应该从这个脚手架的npm包开始研究,不应该从别的npm包;

12. 一个react的组件中一定要写上一个 render函数 (来自react的语法)
   ![这里写图片描述](https://img-blog.csdn.net/20180531172414593?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

13. 一个尚未解决的BUG: (莫名奇妙的bug)    
   ![这里写图片描述](https://img-blog.csdn.net/20180604164332362?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
   解决方法: 删掉node_modules,用npm i重新安装,不要用CNPM,因为npm 的包才是最干净的;