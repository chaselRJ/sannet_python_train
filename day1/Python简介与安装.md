# Python简介与安装

Python 的创始人为 Guido van Rossum。在1989年的圣诞节的晚上，他为了在阿姆斯特丹打发时间，决定开发一个新的脚本语言，他希望该语言既有shell的简单又能像C一样功能全面，于是Python 诞生了。

Python 崇尚优美、清晰、简洁。

## Python 是一门什么样的语言

> 编程语言主要从以下几个角度进行分类：1. 编译型和解释型 2. 静态语言和动态语言 3. 强类型定义语言和若类型定义语言

## Python 解释器

### CPython

### PyPy

### JPython

### IronPython

## Python 发展史

+ 1989年，为了打发圣诞节假期，Guido开始写Python语言的编译器。Python这个名字，来自Guido所挚爱的电视剧Monty Python’s Flying Circus。他希望这个新的叫做Python的语言，能符合他的理想：创造一种C和shell之间，功能全面，易学易用，可拓展的语言。
+ 1991年，第一个Python编译器诞生。它是用C语言实现的，并能够调用C语言的库文件。从一出生，Python已经具有了：类，函数，异常处理，包含表和词典在内的核心数据类型，以及模块为基础的拓展系统。
+ Python 1.0 - January 1994 增加了 lambda, map, filter and reduce.
+ Python 2.0 - October 16, 2000，加入了内存回收机制，构成了现在Python语言框架的基础
+ Python 2.4 - November 30, 2004, 同年目前最流行的WEB框架Django 诞生
+ Python 2.5 - September 19, 2006
+ Python 2.6 - October 1, 2008
+ Python 2.7 - July 3, 2010
In November 2014, it was announced that Python 2.7 would be supported until 2020, and reaffirmed that there would be no 2.8 release as users were expected to move to Python 3.4+ as soon as possible
+ Python 3.0 - December 3, 2008
+ Python 3.1 - June 27, 2009
+ Python 3.2 - February 20, 2011
+ Python 3.3 - September 29, 2012
+ Python 3.4 - March 16, 2014
+ Python 3.5 - September 13, 2015
+ Python 3.6 - December 23, 2016

## Python版本选择

Python2 与 Python3 语法上有差异，不兼容。（Python2写的代码不能在Python3平台上面运行，Python3写的代码也不能在Python2环境下运行）

Python2.7的支持到2020年结束。（www.python.org)

**如何选择版本：**

1. 考虑自己的项目准备使用的第三方模块是否支持2.x和3.x。
2. 如果2.x和3.x都支持，建议选择3.x。因为3.x相比2.x优化了很多。

**个人建议：**

两个都学

1. 云计算相关开发

如果是从事运维和云计算方面的开发，建议学习python2。因为目前大部分云计算的产品都提供了python2的支持，但是不一定提供python3的支持。


**Why Python3 exists**

1. Text and binary data in Python 2 are a mess

## 安装Python

### CentOS 6.x 编译安装

1.安装开发工具包

```
sudo yum groupinstall "Development Tools" -y
```

2.安装编译python所依赖的库

```
sudo yum install -y readline readline-devel zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel
```

3.去python官网下载源码包(https://www.python.org)

```
tar -zxvf Python-2.7.11.tgz
cd Python-2.7.11
./configure --prefix=/usr/local
sudo make && sudo make install

sudo rm -f /usr/bin/python
sudo ln -sv /usr/local/bin/python /usr/bin/python
```

**注意**：修改yum程序：yum程序只能使用python2.6，不支持2.7，因此需要修改yum程序的代码：
编辑sudo vi /usr/bin/yum程序，将文件开头的#!/usr/bin/python改为#!/usr/bin/python2.6

4.验证
控制台输入python -V，正确返回Python版本，即表示安装成功。

```
[lvjin@localhost ~]$ python -V
Python 2.7.11
```

### windows

http://www.python.org/downloads/

下载exe文件双击安装。

### 安装python包管理工具pip

```
yum install -y wget
wget https://bootstrap.pypa.io/get-pip.py
sudo python get-pip.py
```

编辑~/.pip/pip.conf(没有则创建)

```
[global]
index-url = https://pypi.mirrors.ustc.edu.cn/simple
```

### 下载安装ipython

ipython是一个python的交互式shell，比默认的python shell好用的多，支持变量自动补全，自动缩进，支持bash shell命令，内置了许多很有用的功能和函数。

```
sudo pip install ipython
```

安装完之后，在控制台输入ipython，进入ipython的交互界面。

## Hello World

```python
print 'hello world'
```
在交互式环境的提示符>>>下，直接输入代码，按回车，就可以立刻得到代码执行结果。现在，试试输入100+200，看看计算结果是不是300：

对比一下其他语言的hello world

```c++
#include <iostream>
int main(void)
{
	std::cout<<"Hello world";
}
```

```c
#include <stdio.h>
int main()
{
	printf('Hello World')
}
```

```Java
public class HelloWorld{
  public static void main(String args[]){
    System.out.println("Hello World!");
  }
}
```

```php
<?php
	echo "hello world!";
?>
```

```ruby
puts "Hello world."
```

```
package main
import "fmt"

func main(){
    fmt.Printf("Hello World");
}
```

## python程序

在Python的交互式命令行写程序，好处是一下就能得到结果，坏处是没法保存，下次还想运行的时候，还得再敲一遍。

所以，实际开发的时候，我们总是使用一个文本编辑器来写代码，写完了，保存为一个文件，这样，程序就可以反复运行了。

现在，我们就把上次的'hello, world'程序用文本编辑器写出来，保存下来。

python源程序文件通常以.py为扩展名，如下，新建一个名为test.py

```python
#!/usr/bin/python				//指明脚本文件的解释程序。
import platform
print platform.uname()
```

## 直接运行

chmod +x 
