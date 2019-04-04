1. http://localhost:3666/#/app/login这样子访问首页是不对的，应该这样访问 http://localhost:3666/#/login; 代码上还有优化;

2. 这个项目不能只清cookie，应该和localstorage一块清除掉；

3. 手机打开页面调到wap移动端这个项目

   ```
    //跳转到移动端
           function browserRedirect() {
               var sUserAgent = navigator.userAgent.toLowerCase();
               var bIsIpad = sUserAgent.match(/ipad/i) == "ipad";
               var bIsIphoneOs = sUserAgent.match(/iphone os/i) == "iphone os";
               var bIsMidp = sUserAgent.match(/midp/i) == "midp";
               var bIsUc7 = sUserAgent.match(/rv:1.2.3.4/i) == "rv:1.2.3.4";
               var bIsUc = sUserAgent.match(/ucweb/i) == "ucweb";
               var bIsAndroid = sUserAgent.match(/android/i) == "android";
               var bIsCE = sUserAgent.match(/windows ce/i) == "windows ce";
               var bIsWM = sUserAgent.match(/windows mobile/i) == "windows mobile";
               if (!(bIsIpad || bIsIphoneOs || bIsMidp || bIsUc7 || bIsUc || bIsAndroid || bIsCE || bIsWM) ){
   
               } else {
                   window.location.href="http://parkreport.wandetech.com/wap/#/login";
               }
           }
           browserRedirect();
   ```


4. cookie路径的问题, / 和 /wap 、 登录页面清空所以的localStorage的问题；
5. cookie的domain属性应该和PC端的一致都为".wandetech.com"


