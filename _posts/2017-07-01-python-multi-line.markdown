---
layout: post
title: Multi-Line Strings in Python
date: 2017-07-01 17:06:00.000000000 +08:00
---

​        在Python中，如何来定义一个多行的字符串呢？下面将介绍三种方法，以及他们的优缺点，最后会给出我自己的建议。

# 连接(Concatenation)

最容易联想到的就是连接字符串，如下：

```python
str1 = "This is the first line" + \
       "The second line" + \
       "end line"
```

点评：这种方法非常难看，很不美观。稍微改良的一种方式就是去掉"+"，就像下面这样：

```python
str1 = "This is the first line" \
       "The second line" \
       "end line"
```

# 多行语法(Multi-Line String Syntax)

python提供了一种built-in的方式定义多行字符串，如下：

```python
template = """This is first part of the line.
 The second line.
 The end line."""
```

点评：这种方式比concatenation好多了，但是还是有一些瑕疵，从第二行开始，不能有缩进，不然缩进的部分会被当做字符串中的空格处理，就像这样：

```python
>>> template = """This is the first line.
                  This is the second line.
                  This is the third line."""
>>> print(template)
This is the first line.
              This is the second line.
              This is the third line.
```

# 元组语法(Tuple Syntax)

先来例子直观感受下：

```python
>>>template = ("This is the first line."
             "This is the second line."
             "This is the end line.")
>>> print template
This is the first line.This is the second line.This is the end line.
```

点评：优雅，干净，不易出错。



小评：如果在定义一个超长字符串是，一行写不下，需要另起一行，不妨使用下python的元组语法：简单好用。