> 现在国内vue非常火,所以学习vue,给大伙讲解一下吧.

## 一个vue实例

```html
   <div id="root">
        <!-- 插值表达式 -->
        <!-- <h1>hello{{msg}}{{number}}</h1> -->
        <h1 v-text="number"></h1>
        <!-- v-html会转义 -->
        <h1 v-html="content" @click="handleClick"></h1>
    </div>
```

```javascript
// el元素
    new Vue({
        //挂载点,模版,实例之间的关系
        el:"#root",
        template:"<h1>hello{{msg}}</h1>",
        // vue数组
        data:{
            msg: "hello world",
            number: 123,
            content:'<h1>hello</h1>'
        },
        // vue实例的方法
        methods:{
            handleClick:function(){
                //方便之处就是不用管Dom
                this.content = 'world';
            }
        }
    })
```
#### 挂载点
`el`就是挂载点，element元素的意思，它的就是告诉实例要找页面上节点id为root的元素来插入替换；

#### 模板
`template` ,模板，就是插入到页面的内容，就是准备好的页面内容；
一般在工作中template是不写在实例里面，因为不好写；
页面上id为`root`的div包含的内容默认就是`template`;

#### 实例
`new Vue()` 创建出来一个实例，就是一个vue的组件；

大家可以看到挂载点，模板是写在实例里面，是实例的属性；

`data`,实例上的一些数据；

`methods` 实例上的方法；
改变`data `里的数据项this.xxx


`vue`的好处就是可以不要管dom,开发者可以把精力放在业务逻辑上面；

喜欢我给我点个赞把