##webstrom 3.3.3的使用
1. 这是一个恶心的BUG:vue中关闭eslint,太严格太多报错不好,所以要关掉.
2. 在.idea的文件夹下加上 

   ```
   
   ```

		<excludeFolder url="file://$MODULE_DIR$/build" />
	  <excludeFolder url="file://$MODULE_DIR$/node_modules" />
	  <excludeFolder url="file://$MODULE_DIR$/src/static" />
		```
		就不会卡;