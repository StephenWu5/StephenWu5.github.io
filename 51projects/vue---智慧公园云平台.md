1. 可能会用到动态表单验证 步道弹窗

   ```javascript
   $("input[name = 'coin_count']").rules('add', {number: true, required: true});
   
   $("input[name = 'strong_voltage']").rules('add', {number: true, required: true});
   
   $("input[name = 'strong_time']").rules('add', {number: true, required: true});
   
   $("input[name = 'weak_voltage']").rules('add', {number: true, required: true});
   
   $("input[name = 'award_probability']").rules('add', {number: true, required: true});
   
   ```

2. map是js中的预留字; map.vue踩的坑;

3. 步道围栏清除不能保存;(已搞好)

4. 项目中的样式是 admin1- material,不要浪费那么多的时间![1542700522407](C:\Users\wande007\AppData\Roaming\Typora\typora-user-images\1542700522407.png)

5. 设置字体大小一定要设置到这个div标签(亲力亲为)

   ```scss
   <style type="text/css" scoped>
   	.portlet .portlet-body .note-info p{
   		text-indent:2em;
   		color: #a0a9b4;
   		font-size: 16px!important;
   	}
   </style>
   ```

6. 地图的线如何设置的粗一点,打的点还不行,表单验证;

7. 添加/判断模式用id判断,不要用奇奇怪怪的字段;

8. form表单中有form标签,jquery验证会不起来;

9. ```js
   //修复百度地图不显示全部的线的Bug;
   this.map.panBy(0,0);
   ```


10.   下载html标签的图片到浏览器上，一开始遇到的bug：1、下载的图是一半一半的，没有全部，原因是他的html，body的高度限制了，或者目标标签的父元素的高度限制了，用样式“放开”高度。2、图片清晰度不够，尝试过博友的方法，但是图片有偏远，不好处理，公司方面又没有要求，所以没有深研。

    ```javascript
     downLoadCanvasImg(){
         //不要限制html标签的高度
         $('html').css({
             overflow: "scroll!important",
             height: "3600px"
         });
         html2canvas(document.querySelector('#img'), {
    
         }).then(function (canvas) {
             let imgUrl = canvas.toDataURL();
             let dlLink = document.createElement('a');
             dlLink.download = window.document.title;
             dlLink.href = imgUrl;
             dlLink.dataset.downloadurl = [dlLink.download, dlLink.href].join(':');
             document.body.appendChild(dlLink);
             dlLink.click();
             document.body.removeChild(dlLink);
    
             // 图片处理完后限制html标签的高度
             $('html').css({
                 overflow: "scroll!important",
                 height: "auto"
             });
         })
     }
    ```