---
layout: post
title: linux环境变量---查看和设置
date: 2017-06-30 16:35:00.000000000 +08:00
---
## 1、查看linux环境变量

- env 查看当前用户的所有环境变量；
- 查看单个环境变量值；如echo $PATH

## 2、常用的环境变量

- PATH：在shell中输入的所有命令都会在该目录查找命令路径；该变量在我们日常环境变量设置中相当常用；
- LD_LIBRARY_PATH：c程序相关的动态引用库路径；一般在程序运行过程中，需要调用c相关的库时，会到该路径下查到对应库；
-  LIB：c程序相关的静态库路径；在安装或编译程序时，往往到该路径下查找链接库。

## 3、环境变量设置

1）用户可以用过编辑~/.bashrc文件来设定环境变量，基本形式如下：

```shell
export PATH=/biocluster/data/bioexec/software/samtools-1.3/bin/:$PATH
```

也可以把新添加的路径写在变量中，再将该变量插入PATH中；

```shell
YJ_PATH=/biocluster/data/biobk/user_test/yangjie/software/A：/biocluster/data/biobk/user_test/yangjie/software/B
export PATH=$YJ_PATH:$PATH
```

当改变~/.bashrc后，可以新开一个shell窗口使环境变量生效，也可通过source ~/.bashrc使其生效。

2）用户也可以通过在命令行export某路径来实现环境变量的临时更换，如:

```shell
export PATH=/biocluster/*/*/software/samtools-1.3:$PATH
```

3）环境变量设置规则

当我们去查看别人的~/.bashrc文件时，往往发现除了常见的PATH以外，还有PYTHON_HOME、JAVA_HOME、R_LIB等等这类环境变量。

我们需要记住的规则就是PATH、 LD_LIBRARY_PATH是系统固有的两个环境变量名称，除此之外的带着软件名称标签的各类环境变量一般来自用于自己命名、或者对应软件设定的命名。

- **对一般软件，只需将该软件的可执行程序目录和库文件目录添加至PATH路径**；
- 部分软件需要将库文件目录添加至LD_LIBRARY_PATH；（很少）
- 其他有些软件需要必须设定它自己要求的环境变量（如我们系统的python3要求必须设置PYTHON_HOME），这类特殊要求一般在软件的官方文档中有说明，具体按照文档说明设置即可。

4）环境变量文件

- 系统环境变量文件 ：/etc/profile  和 /etc/bashrc
- 用户私有环境变量文件：~/.bash_profile 和 ~/.bashrc

linux在实际运行时，先执行系统级环境变量，再执行用户私有环境变量文件。

~/.bash_profile 与 ~/.bashrc都可以设定环境变量，二者区别在于：bash_profile设定后的环境变量只有在用户重新登入系统时才会生效；bashrc则是重新开一个shell窗口时，即可生效。

一般在实际工作中，我们偏向设定~/.bashrc。



<Author: JessieYang>
