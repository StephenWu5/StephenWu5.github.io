> 自从jquery1.7以来，on事件添加到这个版本，使得事件的绑定变的十分简单，用过jquery的人都说好，相信对off，on方法爱不释手。下面是我总结出来的on,off的使用语法，希望对小伙伴有帮助。

#### on() 使用场景最多

1. 最简单的写法

  ```
   $("ul li").on("click",function(){  
    alert("不响应事件!");  
   })  
  ```
2. 同时给多个元素绑定一样的事件

  ```
   $("ul li,div").on("click",function(){  
    alert("不响应事件!");  
   }) 
  ```
3. 同时给元素绑定多个事件

  ```
  $(".demonstrate").on({  
    mouseover:function(){  
    $(this).addClass("over");  
    },  
    mouseout:function(){  
    $(this).removeClass("over");  
    }  
  },"ul li")  
  ```
4. 实现事件委托 
  父元素`ul li` 给目标元素`.demostrate`添加事件,事件委托的好处是,目标元素可以是之前页面不存在到,后来加上去的也可以。
  只需要考虑一个父元素就可以，给父元素添加委托事件，不用考虑子元素的数量什么的。

  ```
   $("ul li").on({
          click:function(){
              console.log('click','1111');
          },
          mouseover: function () {
              console.log('mouseover','1111');
              $(this).addClass("over");
          },
          mouseout: function () {
              $(this).removeClass("over");
          }
      },".demostrate");
  
  ```
#### off() 解绑事件

1. 最简单的写法

  ```
   $("ul li").off("click")  
  ```
2. 同时给多个元素解绑一样的事件

  ```
   $("ul li,div").off("click") 
  ```
3. 同时给元素解绑多个事件

  ```
  $(".demonstrate").off("mouseover mouseout","ul li")  
  ```
4. 实现事件委托的解绑
  父元素`ul li` 给目标元素`.demostrate`移除事件,事件委托的好处是,目标元素可以是之前页面不存在到,后来加上去的也可以。
  只需要考虑一个父元素就可以，给父元素移除委托事件，不用考虑子元素的数量什么的。

  ```
   $("ul li").off("click mouseover mouseout",".demostrate");
  
  ```