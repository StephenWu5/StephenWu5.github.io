1. 高级的svn解决冲突的方法： 

   选择正在冲突的文件，右键，选择Edit confilicts，这时候出现一个弹框，

   - [ ] ![1546570814986](C:\Users\wande007\AppData\Roaming\Typora\typora-user-images\1546570814986.png)

     看你实际的需要用自己的代码，还是用同事的代码，或者合并起来。最后点击`Mark as resolved`标记冲突已经解决。这时候，冲突文件下的三个文件就会显示。

     比起我之前解决的方法高级多了：到编辑器里找到重复的代码，一个个代码块的删，最后还有手动删掉那三个文件。

2. ```
   video.type === 0 ? '智能器材' : '敏捷训练'  // 1 敏捷训练 0智能器材
   
   api/device/list  status参数 是干什么的。
   `status` int(11) NOT NULL DEFAULT '0' COMMENT '设备状态 1激活 2运行 3 休眠',
   `is_activation` int(11) NOT NULL DEFAULT '2' COMMENT '是否激活(上电) 1已上电 2未上电',
   `operate_status` int(11) DEFAULT '2' COMMENT '录入操作状态 0待审批 1通过 2未通过',
   ```

3. 如果让后台数据查询列表添加更多的搜索条件，查询速度会比较慢。

   可以通过这样jquery插件select2select2的来解决。效果如下： 

​        select2官网​ https://select2.org/ 

4. 业务理解:  

   1、 添加智能器材，敏捷训练等等的器材，这些器材是有设备类型分类的，有场地的。添加器材的时候一定是要有组织和场地的。

   2、 系统管理： 添加系统管理员要指定是哪种角色。添加每一种角色要制定一个组织，特定的权限。组织要指定地址，组织和场地应该没有什么关联。权限管理就是管理具体权限的。

   3、device表 父类型字段名称是type  deviceZn表 父类型字段名称是type_id 别搞错了，详情：

   ​      device_type是父类表，  他有两种类型，  `type` int(11) DEFAULT '0' COMMENT '设备类型 1 敏捷训练 0 智能器材', 

   ​	device是敏捷训练表，  `type` int(11) NOT NULL DEFAULT '1' COMMENT '父设备类型',

   ​	device_zn是智能器材表  `type_id` int(11) DEFAULT NULL COMMENT '父设备类型id',

​       4、未注册设备列表就是小程序连接设备的时候传一个设备ID给后台，后台去判断，然后添加到未注册设备列表里面。

 	5、角色，场地都是属于不同的组织。所以切换组织会有所不同。器材属于不同的场地。超级管理员生成一个指定组织的用户，再让用户自己生产一些用户，应为orgId都是和第一个用户一样，所以都是一样的。

​	6、 权限控制的一些说明：未注册设备，设备设置，新增设备，设备类型管理不可以分配给客户。组织管理和权限管理都是不能暴露给客户的。

