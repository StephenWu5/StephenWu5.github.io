1. **让每个vue实例都可以通过this.store取得store对象**
  在一个storeInit.js中写上如下的代码
  ```
  import Vue from 'vue';
  
  // 共享的数据
  let store = {
      pageTitle: '',
      user: {},
      privileges: [],
      menus: {},
      parkList: [],
      adminStatusSelect: [],
      parkDataList: [],
      debug: 0,    //0开发模式 1测试模式 2正式模式
  };
  
  export default {
      store: store,
      init: function() {
          // 让每个vue实例都可以通过this.store取得store对象
          Vue.mixin({
              data: function() {
                  return {
                      store: store
                  }
              },
              data1:"data1"
          });
      },
      getStore: function() {
          return store;
      }
  };
  ```
2. **vue.mixin与vue.extend**
   vue.mixin 全局注册一个混合,影响注册之后所有创建的每一个Vue实例.谨慎使用全局混合对象，因为会影响到每个单独创建的 Vue 实例（包括第三方模板）。大多数情况下，只应当应用于自定义选项，就像上面示例一样。 也可以将其用作 Plugins 以避免产生重复应用
   	vue.extend对单个实例进行扩展，项目中可以在main.js中使用来扩展根组件
3. 
  ```javascript
  	//子组件中使用$emit发射函数
  	this.$emit('search', $.extend({}, this.params));
  	//父组件中使用@search监听
  	<list @search="onSearch"></list> 
  	//不一定要$on,这也是一种监听
    
  ```
4. 

  ```
  vm.$ref  一个对象,持有注册过的所有子组件
  ref  给  元素或子组件注册引用信息
  vm.$set(target,key,value)   设置值
  ```
5. vue组件的使用

  ```
  <pager ref = 'pager'  :config='pagerConfig'>
  	<list @search="onSearch"></list>
  </pager>
  ```

6. 比如每次登陆获取到个人信息后, 把个人信息放进vuex里存储,  然后做了开通vip等等操作都需要及时更新个人信息,   像从后台调用接口获取个人信息, 然后把请求回的数据存进vuex里,  像这类包含异步求情操作需要经常用到, 所以放进action里,  如果vuex的操作中没有异步代码直接mutation就行了
   ![这里写图片描述](https://img-blog.csdn.net/20180528103715298?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

7. `props` 和 `data`数据的默认值写法：

  ```javascript
  goods: {
  type: Array,
  default: []
  },
  //写在props;
  goods: [] 
  //写在data
  ```
8. `span`的宽高不能设置，除非设置`display:inline-block`;

9. 在vue项目中style部分引入scss文件，非js部分；

10. 一个潘大神帮我解决的BUG，可以去掉一些子组件的一些报错的吧

  ```
  	<Header :seller="seller" v-if="Object.keys(seller).length"></Header>
  ```