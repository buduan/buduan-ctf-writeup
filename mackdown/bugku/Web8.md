# Web8 PHP文件包含

U1S1，这个题确实不太简单。而且考察的不只是文件包含。而且有一些比较恶心的阻碍(具体看后续)。

## 了解相关函数

在这到题里面，会用到如下几个PHP函数。

##### 1.include()

这个函数用于包含并运行指定文件。 

例子：

Vars.php：

```php
<?php

$color = 'green';
$fruit = 'apple';

?>
```

test.php：

```php
<?php

echo "A $color $fruit"; // A

include 'vars.php';

echo "A $color $fruit"; // A green apple

?>
```

运行结果：

```
A 
A green apple
```

##### 2.$_REQUEST

`$_REQUEST[string]` 可以获取到GET和POST method请求的参数。

其中string为参数名称，字符串类型(string)

##### 3.eval

`eval(string)`用于将字符串(string)作为代码执行。

案例：来自PHP手册 - php.net

```php
 <?php
	$string = 'cup';
	$name = 'coffee';
	$str = 'This is a $string with my $name in it.';
	echo $str. "\n";
	eval("\$str = \"$str\";");
	echo $str. "\n";
?> 
```



输出：

```
This is a $string with my $name in it.
This is a cup with my coffee in it.

```

**Tips：字符串中任何代码都会被作为代码执行，除了为加转意符号的变量**

[Eval函数 - PHP手册](https://www.php.net/manual/zh/function.eval.php)

##### 4.show_source() / highlight_file()

## 解题

首先打开场景，会看到一串代码。![截屏2021-05-21 下午12.45.55](http://media.cdn.461blog.cn/uPic/20210521-12-45-%E6%88%AA%E5%B1%8F2021-05-21%20%E4%B8%8B%E5%8D%8812.45.55.png)

代码中通过`include( )`函数引入了flag.php，如果我们直接访问flag.php的话是看不到flag的。

然后用`$_REQUEST`获取了参数名为hello的请求的值作为变量a的值。`$_REQUEST`前面的 `@` 起到了屏蔽所有错误提示信息的作用（这就是前文所述比较恶心的地方，因为如果后面出现错误没法通过错误提示判断）。

之后用 `eval( )`函数运行了代码 `var_dump( （此处是$a的内容） );`。

加入$a = 1的话，就是运行`vur_dump(1)`.

所以我们需要先截断`vur_dump( )`，之后`show_source( )`或者`highlight_file( )`，查看一下源代码。

tips：这里会有很多人认为直接传入`show_source( )`或者`highlight_file( )`，而忽略截断`vur_dump( )`

所以说`$a`（参数hello被传入）的值应为`1);highlight_file('flag.php'`。这样运行的代码就是`var_dump(1);highlight_file('flag.php');`

所以打开网址``http://场景地址/index.php?hello=1);highlight_file(%27flag.php%27``就可以获得源代码。通过查看源代码可以再注释里面看到flag。

![截屏2021-05-21 下午12.48.07](http://media.cdn.461blog.cn/uPic/20210521-12-48-%E6%88%AA%E5%B1%8F2021-05-21%20%E4%B8%8B%E5%8D%8812.48.07.png)