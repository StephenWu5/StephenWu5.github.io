# es6的学习

1. 含义
async函数,使得异步操作变的方便;
内置了执行器;
返回值是Promis对象;

1. 用法:
返回值是Promist对象,可以给使用then函数来添加回调函数;
	```
	function timeout(ms) {
	        return new Promise((resolve)=>{
	            setTimeout(resolve,ms);
	        })
	    }
	
	    async function asyncPrint(value,ms){
	        await timeout(ms);
	        console.log(value);
	    }
	
	    asyncPrint('hello world', 2000);
	```

1. 多种形式:

	```
	//函数声明
	async function foo(){}
	//函数表达式
	const foo = async function (){}
	//对象的方法
	let  obj = { async foo(){}};
	obj.foo.then(...);
	
	//Class的方法
	class Storage  {
	
	}
	//箭头韩式
	const foo = async () => {};
	```

## await命令

正常情况下,await命令后面是一个Promise对象.如果不是,会被转成一个立即resolve的Promise对象;

最简单的asnyc

```
async function f(){
await 123;
}
f().then(v=>console.log(v))
 .catch(e=>console.log(e));
```

如果await后面是Promise或者fetch之类的请求,可以不写return,当然也可以写;

## 错误处理

如果await后面的异步操作出错,那么等同于async函数返回Promise对象被reject;

```
 async function f2(){
        await new Promise(function(resolve, reject){
            throw new Error('出错了');
        });
    }
    f2().then(v=>{
        //出错了这里不会执行
        console.log(v,'vvv');
    })
    .catch(e=>console.log(e,'e'));
```



