---
layout: post
title: Python中的*args 和 **kwargs
date: 2017-06-08 19:29:24.000000000 +08:00
---


*args 和 **kwargs 主要用于函数的定义，可以将不确定数量的参数传递给一个函数。

## *args的用法

*args是用来发送一个非键值对的可变数量的参数列表给一个函数。

例子1：

```python
def test_var_args(f_arg, *args):

    print  "first normal arg:", f_arg

    for arg in args:

        print "another arg through *argv:", arg

test_var_args(‘python’, 'IT','IS','GOOD')
```

产生输入如下：

```Python
first normal arg: python
another arg through *argv: IT
another arg through *argv: IS
another arg through *argv: GOOD
```



## **kwargs的用法

**kwargs允许将不定个数的key-value键值对作为参数传递给函数。

例子2：

```python
def greet_me(**kwargs):

	for key, value in kwargs.items():

		print key, value

greet_me(name='python', version='2.7.2')
```

```python
version 2.7
name python
```



## 使用 *args和 **kwargs来调用函数

*args 和 **kwargs既可以作为函数参数定义，还可以作为调用参数来调用函数。比如，你有如下一个函数：

```python
def test_args_kwargs(arg1, arg2, arg3):
    print arg1,arg2,arg3
```

那么，我们可以使用*args 或者 **kwargs来给这个函数传递参数，如下：

```
#使用*args
args=('abc',1,100)
test_args_kwargs(*args)

#使用**kwargs
kwargs={"arg2":1,"arg1":3,"arg3":"abc"}
test_args_kwargs(**kwargs)
```



## 标准参数与*args、**kwargs在使用时的顺序

那么如果你想在函数里同时使用所有这三种参数， 顺序是这样的：

```python
some_func(fargs, *args, **kwargs)
```

例子3：

```python
def test_args_kwargs(f_arg0, arg1, arg2,arg3=None, arg4=None):
	print f_arg0,arg1,arg2,arg3,arg4

>>> arg=(1,)
>>> kwargs={"arg4":'python',"arg2":2}
>>> test_args_kwargs(0,*arg,**kwargs)
0 1 2 None python
```

