1. 步道小程序详情页的问题，弹窗切换样式有问题。![img](file:///C:/Users/wande007/AppData/Roaming/Typora/typora-user-images/1546497239586.png?lastModify=1546500130)

   问题1： 点击切换，样式没法缓过来，比如省略号一直有。解决如下： 多写一个标签 <cover-view class="text text2 {{text2_visiblity_Class}}">{{trailsData.wayDesc}}</cover-view>,y样式的切换只是简单的控制显示和隐藏，不会涉及过多复杂的样式，因为小程序才出来没有几年，没有过多的能力支持复杂的样式切换。

   <cover-view class="introduction {{introductionClass}} {{text1_visiblity_Class}}">

   <cover-view class="text text2 {{text2_visiblity_Class}}">{{trailsData.wayDesc}}</cover-view>

   <cover-view class="text text1 {{text1_visiblity_Class}}">{{trailsData.wayDesc}}</cover-view>

   <cover-view class="hat" bindtap="onSwitchIntroduction">

   <cover-image class="hat-icon" src="<https://parkapp.wandetech.com/image/trailsInfo/hat.png>"></cover-image>

   </cover-view>

   </cover-view>

   问题2： z-index没有让帽子图标在文字之上，解决：让帽子所在的标签在文字标签之后，改变一下标签的顺序，正常情况下，z-index改一下值的大小就可以，看来小程序对css支持有缺陷。以后要用心理准备慢慢踩小程序的雷吧，一般人玩小程序就开心，前端写小程序就流泪。😅