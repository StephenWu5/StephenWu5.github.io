##因为公司的项目中用到,所以要学习一下jstree

1. 首先,要引入资源文件,数量是3个:

  ```
  <link rel="stylesheet" href="../dist/themes/default/style.min.css" />
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/1.12.1/jquery.min.js"></script>
  <script src="dist/jstree.min.js"></script>
  ```

2. 
  ```
  $('#tree').jstree().get_checked(); //获取所有选中的节点ID
  $('#tree').jstree().get_checked(true); //获取所有选中的节点对象
  ```
3. html里面写上的代码是:

  ```
  //生成这个树
   <div id="jstree"></div>
  	$('#jstree').jstree()
  ```
4. **JSTree 默认展开 树节点默认展开**

  ```
  //红色部分
  $("#jstree_demo")
  .jstree({                                 
    "core" : {
        "animation" : 0,
        "check_callback" : true,
        'force_text' : true,
        "themes" : { "stripes" : true },
  // so that create works
    "check_callback" : true,
    'data' : function (obj, callback) {
                 var jsonstr="[]";
                 var jsonarray = eval('('+jsonstr+')')	        
                 $.ajax({
                     type: "POST",
                     url:url,
                     dataType:"json",
                     async: false,
                     success:function(result) {
                         var arrays= result;
                         for(var i=0 ; i<arrays.length; i++){
  console.log(Object.getOwnPropertyNames(arrays[i]).sort());
                             var arr = {
                                     "id":arrays[i].id,	                             "parent":arrays[i].pid==""?"#":arrays[i].pid,
                                     "text":arrays[i].name,
                                     "type":arrays[i].iconSkin,
                                     "state": {"opened" : true}
                                     //"state": {"selected":true}
                             }
                             jsonarray.push(arr);
                         }
                     }
                 });	               
                 callback.call(this, jsonarray);
             }
         },
         "plugins" : [ "search", "state", "types", "wholerow","checkbox" ]
     });
  ```