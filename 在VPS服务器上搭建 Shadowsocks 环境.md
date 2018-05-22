# 在VPS服务器上搭建 Shadowsocks 环境

### 一、准备
* paypal

因为国外的大部分网站支付方式都可以用paypal ，绑定一张银行卡和支付宝，就可以随意的买买买了。

### 二、市场行情
#### 国内:(不详细介绍)
1. 阿里云服务器
2. 腾讯云
3. 景安快云

#### 国外:

1. [Vultr](https://www.vultr.com/)
简单介绍：Vultr作为全球最大的游戏主机提供商背景之一，上线之后以高质的性价比、15个数据中心，以及新注册账户赠送5美金的账户使用金优惠促销，吸引广大的用户。作为我们用户，日本、洛杉矶等数据中心速度较好，如果有需要海外其他机房也可以在其12个数据中心中选择到适合自己的。

2. [SugarHosts](https://www.sugarhosts.com/zh-cn/vps/ssd-vps-hosting)
简单介绍：提供Sata和SSD两种硬盘VPS，且有WINDOWS VPS方案，洛杉矶MC数据中心对国内线路优化过，平均PING在160左右，支持支付宝付款，有中文客服，如果是需要稳定建站的，这款机器还是不错的。

3. [BandwagonHost（搬瓦工VPS）](https://bwh1.net/vps-hosting.php)
IT7官方旗下的低价VPS主机产品，拥有速度较好的西岸亚利桑那州机房，最低年付仅需3.99美元（目前无货），我们可以用来学习、工作项目演示。拥有11个数据中心，而且可以自由切换IP，更换不同的IP，尤其是适合新手学习Linux系统和建站使用，初学者必备，

4. 其他
[RAKSmart](https://billing.raksmart.com/)
[linode](http://www.laozuo.org/go/linode.com)
[digitalocean](http://www.laozuo.org/digitalocean)

### 配置对比
|名字|最低配置|价格|
|-----|-----|-----|
|[vultr](https://www.vultr.com/)|25G SSD 1G内存 1CPU<br/> 1000G流量/月|5\$/月|
|[SugarHosts](https://www.sugarhosts.com/zh-cn/vps/ssd-vps-hosting)|10G SSD 768M内存 1CPU <br/> 1000G流量/月|46￥/月|
|[BandwagonHost（搬瓦工VPS）](https://bwh1.net/vps-hosting.php)|10G SSD 768M内存 1CPU<br/> 500G流量/月|19.99\$/年|

### 购买选择

从价格上看搬瓦工是最便宜的，但是如果只是看资料的话，那是够用的，如果想看youtobe，twitch等，不能看高清，也就480p - 720p 之间的水平。

推荐购买vultr 大厂，速度快，价格实惠，可以随时停掉。
 
### 节点选择

首选节点：香港 ，新加坡 ，日本 ，韩国 (ping值 150-220 之间) 
次选节点：美国，俄罗斯，澳大利亚，英国(ping值 220+)

美国节点实测 要要明显慢于香港，新加坡
### 三、安装

新用户在vultr 是有优惠的（可能失效）
[传送门](https://www.cnvultr.com/255.html)
1.注册
![](http://upload-images.jianshu.io/upload_images/1359048-2e602d235daeda03.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
2.支付
![](https://diycode.b0.upaiyun.com/photo/2017/80abb72bffcdf83be22bef389644cf6c.jpg)
3.创建Service
在Vultr Servers页面，点击右上角"+"按钮
![](http://upload-images.jianshu.io/upload_images/1359048-3e9b8ac0875280a9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
4.看国旗选节点(亚洲最快)图是我找的，你们按需求买
![](http://upload-images.jianshu.io/upload_images/1359048-79740ca62d3f0da4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
5.**CenterOS6(后边有用)**；按时收费，1CPU、1G Memory、1000G（2.5$能抢可以抢一波，抢不到就老老实实去买5\$的）
![](http://upload-images.jianshu.io/upload_images/1359048-c71ba6c94d57201a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
6.创建Server成功后，Servers界面会显示刚创建的Server，状态是Installing. 等几分钟，状态会变成Running。

#### windows

Putty是一个免费SSH客户端，可以到 Putty官网 下载putty客户端，下载页面：http://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html。SSH是一种安全协议，常用于连接服务器。

1.打开Putty，在Session页面填写VPS IP地址和Port（默认22）：
![](http://upload-images.jianshu.io/upload_images/1359048-d8bf777b154ac568.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
2.然后到Connection -> Data填写登录用户名（root）：
![](http://upload-images.jianshu.io/upload_images/1359048-6653d75c0e2d680d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
3.[](3.填写完后，顺手保存一下Session：)
![](http://upload-images.jianshu.io/upload_images/1359048-899eb8f4fd966b11.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
4.点击Open连接VPS，连接成功后，会提示输入Password，输入密码后（大小写敏感），如果出现[root@vultr ~]#表示成功登录。
5.[Shadowsocks 一键安装脚本](https://teddysun.com/486.html)
运行以下命令
```
wget --no-check-certificate -O shadowsocks-all.sh https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-all.sh
chmod +x shadowsocks-all.sh
./shadowsocks-all.sh 2>&1 | tee shadowsocks-all.log
```
选择脚本
```
Which Shadowsocks server you'd select:
1.Shadowsocks-Python
2.ShadowsocksR
3.Shadowsocks-Go
4.Shadowsocks-libev
Please enter a number (default 1):
```
需要哪个选数字即可：比如选Shadowsocks-Go 就是3 (据说选go 有buff 加成，我已经不记得我选的什么了，推荐Go)
默认密码：teddysun.com
默认端口:8989
```
You choose = Shadowsocks-Go
Please enter password for Shadowsocks-Go
(default password: teddysun.com):
password = teddysun.com
Please enter a port for Shadowsocks-Go [1-65535]
(default port: 8989):

port = 8989
Press any key to start...or Press Ctrl+C to cancel
```
安装成功后
```
Congratulations, Shadowsocks-Go server install completed!
Your Server IP        :  45.32.73.59
Your Server Port      :  8989
Your Password         :  teddysun.com
Your Encryption Method:  aes-256-cfb

Welcome to visit: https://teddysun.com/486.html
Enjoy it!
```
（安装失败，清换一个脚本，不要在一棵树上吊死）

[Shadowsocks客户端 下载](https://github.com/shadowsocks)
### 使用

![](http://upload-images.jianshu.io/upload_images/1359048-953d8d293c71f2ea.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### [VPS单边加速](https://www.wn789.com/9469.html)
Shadowsocks 使用过程中可能会发现连接速度有时不太稳定。这就是「锐速」发挥功能的时候了。锐速 ServerSpeeder 是一个 TCP 加速软件，对 Shadowsocks 客户端和服务器端间的传输速度有显著提升。客户端和服务器端间的传输速度有显著提升。

如果选择的是Centos6或者CentOs 7  那么恭喜你可以安装加速，如果选的是其他的，查看[如何修改CentOS6、CentOS7内核支持安装锐速的内核](https://www.wn789.com/4689.html)
1.修改内核支持为锐速加速
CentOS6
```
uname -r #查看当前内核版本
rpm -ivh http://xz.wn789.com/CentOSkernel/kernel-firmware-2.6.32-504.3.3.el6.noarch.rpm
rpm -ivh http://xz.wn789.com/CentOSkernel/kernel-2.6.32-504.3.3.el6.x86_64.rpm --force
```
CentOS7
```
rpm -ivh http://xz.wn789.com/CentOSkernel/kernel-3.10.0-229.1.2.el7.x86_64.rpm --force
rpm -qa | grep kernel #查看内核是否安装成功
```
![](https://www.wn789.com/wp-content/uploads/2017/09/20170910211907-1.png)

2.重启VPS，查看内核是否更换成功。
reboot #重启VPS
uname -r #当前使用内核版本
![](https://www.wn789.com/wp-content/uploads/2017/09/20170910212011.png)
3、安装锐速。执行下面一键安装命令安装锐速无限制版。
```
wget -N --no-check-certificate https://raw.githubusercontent.com/wn789/serverspeeder/master/serverspeeder.sh
bash serverspeeder.sh
```
如果不出意外显示下图内容，就表示安装成功了。
![](https://www.wn789.com/wp-content/uploads/2017/09/20170910214028-1.png)

还有一种加速方式 BBR
[安装方式传送门](https://www.wn789.com/9469.html)

### 安装后效果
1G 内存 看youtube 1080p 不卡。

### 总结
一般来说3人用一个VPS 服务器是完全没问题的，不会有卡的问题，除非三个人都是天天看youtube 1080的主，如果只是查资料的话，5-7人用一个1G内存你的都没问题的，分摊下来，一个月也是没多少钱的，懒得搭建服务器的话，买别人搭好的也行,[传送门](https://emm.kiwi/)  和 [另一个传送门](https://onclouds.top)，Google+ 上有一个 [免费分享账号社群](https://plus.google.com/communities/104092405342699579599)，不过前提是你能翻墙出去，才能加入这个社区，这是一个先有鸡还是先有蛋的问题。

本教程参考了以下链接
[老左常用国内/国外VPS推荐](http://www.laozuo.org/myvps)
[轻松在 VPS 搭建 Shadowsocks 翻墙](https://www.diycode.cc/topics/738)
[Shadowsocks 一键安装脚本](https://teddysun.com/486.html)
[Vultr VPS安装单边加速工具](https://www.wn789.com/9469.html)