首先:
    要在网上查得三个资料
    // 免费天气接口
    // http://wthrcdn.etouch.cn/WeatherApi?city=
    // 方法 :get
    // 地址:就这个
    // key:city
    
第二,要有ajax get 资料的知识
    有五步:
    1创建一个xml对象;
    2设置请求行
    3请求头(get方法下可以省略)
    4设置回设函数
    5发送请求主体
这五步知识点一定要操作几遍,得熟.

最后,根据在回调函数返回的数据得到responseXML,
    在控制台打印这个数据,取其中的数据得到有用的数据,生成表格;
    
    

本人已成功做出来,并不顺利,有几个易错点吧,与大家分享这个经历,希望大家不要走这个弯路.

 var html = "";
            html += "<tbody>";
            for (var i = 0; i < weather.length; i++) {
                html += "<tr>";
                html += "<td>"+weather[i].querySelectorAll("date")[0].innerHTML+"</td>";
                html += "<td>"+weather[i].querySelectorAll("high")[0].innerHTML+"</td>";
                html += "<td>"+weather[i].querySelectorAll("low")[0].innerHTML+"</td>";
                html += "<td>"+weather[i].querySelectorAll("type")[0].innerHTML+"</td>";
                html += "<td>"+weather[i].querySelectorAll("fengxiang")[0].innerHTML+"</td>";
                html += "</tr>";
            }
            html += "</tbody>";
            
"weather[i].querySelectorAll("date")[0].innerHTML" 这一句其中的下标[0]不能省,因为前面的querySelecterAll得到的数是数组,或者你们可以不要下标,但是要把querySelectorALL改为querySelectoer。







最后的最后，我复制上所有的代码





    <h2>请输入你要查的城市名(天气查询)</h2>
    <input type="text">
    <input type="button" value="搜索">
    <table>
    </table>

    // 免费天气接口
    // http://wthrcdn.etouch.cn/WeatherApi?city=
    // 方法 :get
    // 地址:就这个
    // key:city

    document.querySelector("input[type='button']").onclick = function () {
        //创建一个对象
        var value = document.querySelector("input").value;
        var xhr = new XMLHttpRequest();
        //请求行
        xhr.open("get", "http://wthrcdn.etouch.cn/WeatherApi?city=" + value);
        //请求头

        //回调函数
        xhr.onload = function () {
            var result = xhr.responseXML;

            
            var weather = result.querySelectorAll("weather");            
            var html = "";
            html += "<tbody>";
            for (var i = 0; i < weather.length; i++) {
                html += "<tr>";
                html += "<td>"+weather[i].querySelectorAll("date")[0].innerHTML+"</td>";
                html += "<td>"+weather[i].querySelectorAll("high")[0].innerHTML+"</td>";
                html += "<td>"+weather[i].querySelectorAll("low")[0].innerHTML+"</td>";
                html += "<td>"+weather[i].querySelectorAll("type")[0].innerHTML+"</td>";
                html += "<td>"+weather[i].querySelectorAll("fengxiang")[0].innerHTML+"</td>";
                html += "</tr>";
            }
            html += "</tbody>";
            
            document.querySelector("table").innerHTML = html;

        }
        //请求主体
        xhr.send(null);
    }






