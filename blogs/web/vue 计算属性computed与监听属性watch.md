> 有时在工作用用到计算属性和监听属性,可以写少很多行的代码,对开发效率有很大的提高;

## 计算属性
`computed` 

计算属性时根据实例的数据项计算而来的结果

优点是可以使用缓存,性能高

使用实例,属性`fullName`是由`firstName,lastName`计算而来的

```
computed:{
   fullName:function(){
          return this.firstName + ' ' + this.lastName;
      }
  },
```


## 监听属性
`watch`

作用就是监听某一个数据发生变化时,就去执行对应的代码

```
 watch:{
     //方式1
     // firstName: function(){
     //     this.count++;
     // },
     // lastName: function(){
     //     this.count++;
     // }

     //方式2
     fullName: function(){
         this.count++;
         
     }
 }
```
对比一下上图的两个方式,方式二比方式一省好多代码，简洁。