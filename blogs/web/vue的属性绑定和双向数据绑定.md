#### 属性绑定
`v-bind` 属性绑定,使用如下,为`div`绑定了一个`title`属性

```javascript
<div v-bind:title="'dell lee'+title">hello world!</div>
```

`v-bind:` 可以缩写为`:`

```javascript
<div :title="'dell lee'+title">hello world!</div>
```


#### 双向数据绑定
`v-model`  一般用于input等表单元素,实例里的数据改变,input里的数据也改变;相同,input里的数据改变,实例里的数据也改变;

实现如下:
```javascript
	<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>属性绑定和双向数据绑定</title>
    <script src="https://cdn.bootcss.com/vue/2.5.8/vue.min.js"></script>
</head>
<body>
    <div id="root">
        <!-- v-model 双向数据绑定 -->
        <input type="text" v-model="content">
        <div>{{content}}</div>
    </div>
</body>
<script>
    new Vue({
        el: '#root',
        data:{
            title: 'this is hello world',
            content: 'this is content'
        }
    })
</script>
</html>
```