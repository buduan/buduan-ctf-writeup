# Web11目录扫描和密码爆破

## 解题

打开场景，看到一个“黑页”。在F12开发者工具中查看源代码没有发现任何信息。缓存，Cookie，以及用Fiddler查看Header信息也是如此。

![截屏2021-05-30 下午10.36.40](http://media.cdn.461blog.cn/uPic/20210530-22-36-%E6%88%AA%E5%B1%8F2021-05-30%20%E4%B8%8B%E5%8D%8810.36.40.png)

打开Kali Linux，在终端输入 `dirbuster  ` 打开目录扫描工具DirBuster。

在第一行的Target输入靶场的域名(或IP)及端口号，扫描方式选择第二个 HEAD和GET结合。线程数根据电脑及Kali Linux虚拟机(若Kali Linux系统在虚拟机中运行的话)的配置进行设置。

之后选择词典路径，这里使用工具自带的词典就好，词典文件在 /usr/share/dirbuster/wordlists 目录中。

![截屏2021-05-30 下午10.53.18](http://media.cdn.461blog.cn/uPic/20210530-22-53-%E6%88%AA%E5%B1%8F2021-05-30%20%E4%B8%8B%E5%8D%8810.53.18.png)

扫描差不多的时候，可以在新页面中的Results选项卡中查看结果，发现一个比较可以的shell.php。

解释一下Shell在计算机中的含义：

> 在计算机科学中，*Shell*俗称壳（用来区别于核），是指“为使用者提供操作界面”的软件（command interpreter，命令解析器）。它类似于DOS下的COMMAND.COM和后来的cmd.exe。它接收用户命令，然后调用相应的应用程序。 
>
> （来自百度百科）

![截屏2021-05-30 下午11.00.43](http://media.cdn.461blog.cn/uPic/20210530-23-00-%E6%88%AA%E5%B1%8F2021-05-30%20%E4%B8%8B%E5%8D%8811.00.43.png)

打开Shell.php，发现需要输入密码进行访问。![截屏2021-05-30 下午11.03.28](http://media.cdn.461blog.cn/uPic/20210530-23-03-%E6%88%AA%E5%B1%8F2021-05-30%20%E4%B8%8B%E5%8D%8811.03.28.png)

之后使用BurpSuite工具进行扫描。

- 扫描方法：https://blog.csdn.net/weixin_41489908/article/details/115434107

> 进入选项—设置，修改代理
>
> preferen–setting
>
> ![在这里插入图片描述](http://media.cdn.461blog.cn/uPic/20210530-23-29-watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RyeWhlYXJ0,size_16,color_FFFFFF,t_70-20210530232958472.png)
>
> 然后打开burpsuite 设置代理
>
> ![在这里插入图片描述](http://media.cdn.461blog.cn/uPic/20210530-23-30-watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RyeWhlYXJ0,size_16,color_FFFFFF,t_70-20210530233009020.png)
>
> 按步骤设置代理地址端口，和浏览器设置一样
>
> ![在这里插入图片描述](http://media.cdn.461blog.cn/uPic/20210530-23-30-watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RyeWhlYXJ0,size_16,color_FFFFFF,t_70-20210530233031157.png)
>
> 然后在浏览器里面输入搭建好的服务器地址
>
> ![在这里插入图片描述](http://media.cdn.461blog.cn/uPic/20210530-23-30-watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RyeWhlYXJ0,size_16,color_FFFFFF,t_70-20210530233034918.png)
>
> 注意localhost是主机IP地址
>
> 拦截到下面的内容
>
> ![在这里插入图片描述](http://media.cdn.461blog.cn/uPic/20210530-23-30-watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RyeWhlYXJ0,size_16,color_FFFFFF,t_70-20210530233040655.png)
>
> 右键点击send to intruder
>
> 然后点击 intruder
>
> ![在这里插入图片描述](http://media.cdn.461blog.cn/uPic/20210530-23-29-watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RyeWhlYXJ0,size_16,color_FFFFFF,t_70-20210530232925361.png)
>
> 按顺序操作，第三步最后操作
>
> 添加破解字典用户名，密码
>
> ![在这里插入图片描述](http://media.cdn.461blog.cn/uPic/20210530-23-28-watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RyeWhlYXJ0,size_16,color_FFFFFF,t_70.png)
>
> ![在这里插入图片描述](http://media.cdn.461blog.cn/uPic/20210530-23-31-watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RyeWhlYXJ0,size_16,color_FFFFFF,t_70-20210530233108528.png)
>
>
> 最后开始破解
>
> 结束后看长度不一样的就是破解出的用户名密码
>
> ![在这里插入图片描述](http://media.cdn.461blog.cn/uPic/20210530-23-31-watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3RyeWhlYXJ0,size_16,color_FFFFFF,t_70-20210530233116401.png)
>
> 引用自CSDN @[星辰流炎](https://blog.csdn.net/tryheart)
>
> 原文链接：https://blog.csdn.net/tryheart/article/details/108207053

最后通过扫描结果，最终得到密码hack，获取到flag。

## 工具

- BurpSuite - 暴力破解密码