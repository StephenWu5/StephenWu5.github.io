#### 问题markdown版

1. 首页的地图的点换星星;
2. 账单的状态是不是还有待确认啊;
3. 有时间写一下注释；


​    

#### 新需求

订单管理增加筛选：输入订单编号或手机号，选择预定时间，订单金额范围，选择支付方式，选择订单状态，订单时间  done
体育馆管理增加筛选项：输入体育馆编号或名称  done
场馆增加筛选项：输入场馆编号或名称，选择场馆种类，预定类型 done
活动占场增加筛选：活动时间 done 
门禁管理增加筛选项：输入设备编号或场馆编号或场地/场馆名称，选择设备状态。 done 
门禁管理设备前面加个状态图标。 done
如果有新订单，预约管理和订单管理显示红点。

用户管理增加筛选项：输入昵称或者编号或者手机号，选择性别 done
支付记录增加筛选项：输入订单编号或者支付订单号或者支付人或者手机号，选择支付方式，选择订单时间  done
开锁记录增加筛选项：输入订单编码或者设备编号或者序列号，选择时间。  done
[@吴土福(吴土福)](app://desktop.dingtalk.com/web_content/chatbox.html#) [@刘艺(刘艺)](app://desktop.dingtalk.com/web_content/chatbox.html#) 再加上面这几个筛选



#### 一个bug: 添加时点的上的勾,编辑时点不上

```javascript
//还是由于 JavaScript 的限制，Vue 不能检测对象属性的添加或删除  (大佬给我解决)
//确定时间块的勾选状态
onChoosePriceOne(index,index1){
    var isChoose = !this.data.data[index].list[index1].isChoose;
    this.$set(this.data.data[index].list[index1], "isChoose",isChoose);
},

```



#### 传很复杂的json应该设置一下header

```javascript
一、setting参数 headers

$.ajax({

    headers: {
        Accept: "application/json; charset=utf-8"
    },
    type: "get",
    success: function (data) {
    }
});


--------------------- 
作者：shjavadown 
来源：CSDN 
原文：https://blog.csdn.net/shjavadown/article/details/51213342 
版权声明：本文为博主原创文章，转载请附上博文链接！
```



##### layui框架，时间控件一闪而过

```javascript

<span class="input-inline ml5">
					<input type="search" id="orderTime"  placeholder="请选择订单时间"
						   class="form-control input-inline w250" lay-key="1" v-model="orderTime">
				  </span>
				  <span class="input-inline ml5">
					<input type="search" id="preTime"  placeholder="请选择预定时间"
						   class="form-control input-inline w250" lay-key="2" v-model="preTime">
				  </span>
```

**解决方法:** 把lay-key去掉



```
$('select[name^="lev"]').rules('remove');
```

