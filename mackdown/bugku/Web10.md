# Web10 Header 抓包

## 解题

打开环境，一看“什么也没有”，F12查看源代码，也是什么都没有。

![截屏2021-05-30 下午2.39.44](http://media.cdn.461blog.cn/uPic/20210530-14-39-%E6%88%AA%E5%B1%8F2021-05-30%20%E4%B8%8B%E5%8D%882.39.44.png)

作为一道CTF题目， 没有Flag是不可能的。

再看一看，Flag有没有可能被缓存到了缓存或者Cookie里面。打开“存储”选项卡，发现Cookie和缓存也是空空如也。

既然什么都没有，就抓包试一下。打开Fiddler进行抓包。

![截屏2021-05-30 下午2.45.40](http://media.cdn.461blog.cn/uPic/20210530-14-45-%E6%88%AA%E5%B1%8F2021-05-30%20%E4%B8%8B%E5%8D%882.45.40.png)

Cookie和浏览器的开发者工具一样，显示为空。

查看Header信息，在Header信息中找到Flag。

## 其他的

其实一开始有扫描根目录的想法，但是感觉Web10的位置不能太难，就先选择了用抓包工具试一下。

## 工具 

[工具列表 - Tools Page](https://ctf.461blog.cn/tools/)

- Fiddler - 网络抓包工具
- Burpsuite - 网络抓包工具(效果等同于Fiddler，二者任选其一即可)

