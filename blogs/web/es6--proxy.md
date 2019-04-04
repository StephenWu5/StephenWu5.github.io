### es 6的学习

##### es6 proxy对象的学习

> 有时候,我们在代码中需要对自己定义的对象的有一些属性进行保护,不能让用户进行修改,最常见的就是人类的性别;



##### 具体写法

首先定义一个对象

```javascript
let obj = {
    name: 'stephen chow',
    age: 15,
    sex: 'male'
}
```



##### 理解Proxy(参考了阮一峰的博客)

Proxy 用于修改某些操作的默认行为，等同于在语言层面做出修改，所以属于一种“元编程”（meta programming），即对编程语言进行编程。

Proxy 可以理解成，在目标对象之前架设一层“拦截”，外界对该对象的访问，都必须先通过这层拦截，因此提供了一种机制，可以对外界的访问进行过滤和改写。Proxy 这个词的原意是代理，用在这里表示由它来“代理”某些操作，可以译为“代理器”。



例子代码:

```javascript
let person = new Proxy(obj,{
    get: function(tartet,key){
        return target[key];
    }
    set: function(tartet,key,value){
    	if(key !== 'sex'){
         	target[key]  = value
    	}
 	}
})
```

这个例子保护了person对象中的sex,不让别人随意修改,写法简单,可见es6的强大;



在严格模式下`use strict` ,

```javascript
person.name = 'stephenWu5' //没有问题,能正常赋值
person.sex = 'female' //就会报错提示
```