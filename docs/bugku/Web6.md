# Web6 JS注释UniCode编码

打开题目环境，可以看到一个提示“flag就在这里”这是一个Javascript的Alert组件，点击确定会反复提示，且页面并没有进行加载。

![image-20210518122310485](http://media.cdn.461blog.cn/uPic/20210518-12-25-image-20210518122310485.png)

通过F12检查一下代码，发现未加载完全时会影响开发者工具的查看器。所以要利用浏览器来阻止网页弹出提示框。

![image-20210518122310485](http://media.cdn.461blog.cn/uPic/20210518-12-30-%E6%88%AA%E5%B1%8F2021-05-18%20%E4%B8%8B%E5%8D%8812.29.55.png)

![截屏2021-05-18 下午12.27.00](http://media.cdn.461blog.cn/uPic/20210518-12-31-%E6%88%AA%E5%B1%8F2021-05-18%20%E4%B8%8B%E5%8D%8812.27.00.png)

之后找到他的script脚本，在一堆alert()下面，可以发现一个可能是flag的东西。

这是一串unicode编码过的字符串，通过工具进行解码，可得到flag。

![截屏2021-05-18 下午12.33.49](http://media.cdn.461blog.cn/uPic/20210518-12-33-%E6%88%AA%E5%B1%8F2021-05-18%20%E4%B8%8B%E5%8D%8812.33.49.png)

flag{1e0501cad5f880exxxxxx32c85cd47f1}

工具：

- [站长之家在线Unicode转换](http://tool.chinaz.com/tools/unicode.aspx)

