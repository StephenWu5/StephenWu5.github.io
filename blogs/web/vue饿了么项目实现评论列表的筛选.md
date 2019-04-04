> 正如大家买东西都习惯看评论,评论好就买,评论不好就远离;所以评论对大家来说是很重要的,一个商品的评论往往数量挺多,所以评论列表的筛选这个功能也就需求大,在公司的项目中用的比较多。

问题是？如何来实现这个功能？

其实很简单：

#### 第一步：

先准备好数据按钮，如代码所示
```html
 <h1 class="title">商品评价</h1>
  <ul class="selects">
          <li v-for="(item,index) in classifyArr" :key="index" :class="item.active===true?'active':''" @click="classifyFn(index)">
              {{item.name}}{{item.count}}
          </li>
  </ul>
```

```
 classifyArr:[{
                name: '全部',
                count: this.food.ratings.length,
                active: true
            },{
                name: '推荐',
                count: this.food.ratings.filter((data)=>data.rateType === 0).length,
                active: false
            },{
                name: '吐槽',
                count: this.food.ratings.filter((data)=>data.rateType === 1).length,
                active: false
            },],
```

还有就是这个两个评论列表的数组数据：**newRatings**和 **food.ratings**

#### 第二步：

给页面上的各个按钮绑定点击事件，当不同的按钮被点击时就执行对应的函数，从`food.ratings`挑选出数组元素给到`newRatings`

```
getRatings(index){
     if(index===0){
    return this.food.ratings;
      }else if(index===1){
          return this.food.ratings.filter((data)=>data.rateType === 0);
      }else{
          return this.food.ratings.filter((data)=>data.rateType === 1);
      }
  },
```

#### 第三步：

在vue页面上用`v-for`列表渲染`newRatings` 就可以了；

```
<div class="rates-list">
   <ul>
          <li v-for="(item,index) in newRatings" :key="index" >
              <p><span class="time">{{item.rateTime}}</span> <span class="img">{{item.username}}<img :src="item.avatar" alt=""></span></p>
              <p><span class="icon-point-right"></span><span class="text">{{item.text}}</span></p>
          </li>
      </ul>
  </div>
```

#### 最后的效果：

![这里写图片描述](https://img-blog.csdn.net/20180621220021708?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)


喜欢我给我点个赞吧。