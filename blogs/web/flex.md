今天学习了阮一峰大哥的flexbox布局的form篇；觉得可以，简单好用，就记录一下；

## demo的全部代码
### dom篇
```
<form>
		<input type='email' name="email">
		<button type="submit">
				send
		<button/>
</form>
```
### 样式篇
```
	form{
		display: flex;
	}
	input{
		flex-grow: 1;
		align-self: center;
	}
```

`form`的`display:flex`弹性布局的项目默认没有间隔,所以可以去掉控件之间的间隔;

`flex-grow:1 `: 该项目的宽度拉伸,占据该行的剩余宽度;

`align-self`: 有四个值: flex-start ,flex-end,center ,stretch 决定项目的高度拉伸与否;只可以应用于一个;

`align-items` 的意思与	`align-self`的用法类似, align-items的属性可以被该项目的子项目继承,可谓应用于多个;

由于时间关系，也没有写的过于详细。