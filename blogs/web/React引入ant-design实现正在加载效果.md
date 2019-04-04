# React引入ant-design实现正在加载效果

## 1.安装

```
npm install antd --save
```

## 2.导入ant-design

```
// 导入ant design
import { Spin, Icon } from 'antd';
import 'antd/dist/antd.css';
const antIcon = <Icon type="loading" style={{ fontSize: 24 }} spin />;
```

## 3. react项目中使用(结合React的条件渲染,不懂条件渲染的可以看[官网](https://reactjs.org/docs/conditional-rendering.html))

```
render(){
        var detail = this.state.detail;
        if(this.state.isLoading){   // 
            return (
                <div>
                    <Spin indicator={antIcon} /> //在这里使用 正在加载效果
                </div>
            )
        }else{
	        return(
		         <div> // 其他内容
		         </div>
	        )
        }
   }
```

## 4.最后的效果
![这里写图片描述](https://img-blog.csdn.net/20180526165446239?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1N0ZXBoZW5fX1d1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)