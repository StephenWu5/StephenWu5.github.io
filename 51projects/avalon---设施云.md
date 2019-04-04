#### 截止时间

下周三



#### 需求



### 项目业务逻辑

1. 系统总管下的二维码管理状态为出厂扫码时是不存在的,只有使用状态才有东西;



#### 问题

1. 如何改变process.env.NODE_ENV

   ```
   process.env.NODE_ENV = 'development';
   ```

   在base的js里面加两个同名的debugUrl字段，提交代码是手动切换；

2. ios下video标签下的大于640px的视频是不能播放的，上传视频是要注意提示；

3. 之前一个面包霄的bug 

   ```js
     //下面的代码是防止三级菜单时找不到第一个菜单
                   $subMenu = $curMenu.closest('.sub-menu').parent().closest('.sub-menu'); //closest是从当前元素开始查找的，所以第一个closet之后要加上一个parent;
                   if ($subMenu.length > 0) {
                       tmpPath.push($subMenu.siblings('a'));
                   }
   ```







