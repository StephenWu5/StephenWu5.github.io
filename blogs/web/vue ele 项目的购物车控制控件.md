说说最近在工作很闲的时候,在GITHUB找了一个关于VUE2.0的饿了么项目来练手,然后在遇到的一个bug;
有点诡异:
是同一个购物车的控件组件,分别位于不同的商品列表上，其中一个点击+ ，能选择商品，其数量加一，但另外一个点击+， 没有前者的反应；
笔者找了好久，才发现是这个代码做的怪：

```
 // if (!event._constructed) {
 //     return
 // }
```
`event._constructed` 是better-scroll的一个属性,防止非vue事件,它适合对于一些better-scroll处理过的商品列表,所以为了让后一个列表上的控件有效,要不就是把上面的三行代码注释掉或者后一个商品列表也用better-scroll处理一下;


```
addCar(event){
    console.log(this.food, "1111");
       console.log("add",'1111');
       // if (!event._constructed) {
       //     return
       // }
       if(!this.food.count){
           Vue.set(this.food,'count',0);
       }
       this.food.count++;
       console.log(this.food.count, "1111count");

     //兄弟组件的一个函数调用
       this.$root.eventHub.$emit('cart.add',event.target);
   },
   decreaseCar(){
       if(!event._constructed || !this.food.count){
           return
       }
       this.food.count--;
   }
```