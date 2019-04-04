1、 微信端不是支持线性渐变

```css
    /*css线性渐变实现不同的背景色,无奈微信端不支持5555*/
    /*background: linear-gradient(to bottom, #62ABEF, #62ABEF 47.5%,  #F4F4F247.5%, #F4F4F2);*/
    height: 400px;
    background-color: #F4F4F2;
```

2、 vue 中替换或者绑定图片，用es5的require和es6的import

```js
// 状态图片
let imgArr = [require('../../images/status0.png'),require('../../images/status1.png'),require('../../images/status2.png')],
    defaultImg = require('../../images/status0.png')
function statusImg(value) {
    value = value || defaultImg;
    if(value === '偏低'){
        value = imgArr[0];
    }else if(value === '正常'){
        value = imgArr[1];
    }else if(value === '偏高'){
        value = imgArr[2];
    }
    return value;
}
```

3、 es6 includes函数的使用,判断一个字符串和数组是否包含一个对象

```html
<div class="item2" v-if="!['收缩压', '舒张压' ,'安静心率'].includes(subObj.name)">
</div>
```

4、img图片下方2px缝隙方法：

- 可以设置img的父级div的line-height:0 或者font-size：0；   第一个方法亲测有效
- 设置img为display：block 或者设置vertical-align：middle;
- 也可以设置img父元素为浮动

 5、ios微信端下软键盘出现页面会上滑一下段而一直没有下来

```js
 // input失去焦点事件   解决移动端微信下页面上滑不自动下滑
inputBlur(){
    let scrollTop = $('body').scrollTop();
    if(scrollTop < 10){
        //当软键盘弹出，在这里面操作
        // alert('弹出')
    }else{
        //当软键盘收起，在此处操作
        // alert($('body').scrollTop())
        // 页面自动下滑
        $('body').scrollTop(0)
    }
}
```



