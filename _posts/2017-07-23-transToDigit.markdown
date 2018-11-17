---
layout: post
title: 大写数字转换成阿拉伯数据
date: 2017-07-23 12:31:00.000000000 +08:00
---

​        

以下代码支持千亿以内的转换。

```python
# -*- coding: utf-8 -*-

digits = {
u'一':1, u'二':2, u'三':3, u'四':4, u'五':5, u'六':6, u'七':7,
u'八':8, u'九':9, u'零':0
}

units = {u'十':10, u'百':10**2, u'千':10**3, u'万':10**4, u'亿':10**8}

def main(inputs):
    output = 0
    unit = 0
    midput = []
    for idx in xrange(len(inputs)-1, -1, -1):
        if inputs[idx] in units:
            unit = units[inputs[idx]]
            if unit == 10000 or unit == 100000000:
                midput.append(unit)
                unit = 1
        if inputs[idx] in digits:
            if unit:
                midput.append(digits[inputs[idx]] * unit)
                unit = 0
            else:
                midput.append(digits[inputs[idx]])
    if unit == 10:
        midput.append(unit)

    val, tmp = 0, 0
    for x in reversed(midput):
        if x == 10000 or x == 100000000:
            val += tmp * x
            tmp = 0
        else:
            tmp += x
    val += tmp
    return val

if __name__=='__main__':
    s = u'一百零二亿五千零一万零一千零三十八'
    print main(s)

```
