---
layout: post
title: 大写数字转换成阿拉伯数据
date: 2017-07-23 12:31:00.000000000 +08:00
---

​        

以下代码支持千亿以内的转换。

```python
# -*- coding: utf-8 -*-

mapping = {
u'一':1, u'二':2, u'三':3, u'四':4, u'五':5, u'六':6, u'七':7,
u'八':8, u'九':9, u'十':10, u'百':10**2, u'千':10**3, u'万':10**4,
u'亿':10**8
}

def main(input):
    output = 0
    midput = 0
    idx = 0
    length = len(input)
    while idx < length:
        if input[idx] == u'零':
            idx += 1
            continue
        if ( idx + 1 < length) and mapping[input[idx]] < mapping[input[idx+1]]:
            if idx - 1 >=0 and input[idx-1] != u'零' or idx - 1 < 0:
                mid = mapping[input[idx]]*mapping[input[idx+1]]
                midput += mid
                if mapping[input[idx+1]] >= 10**4:
                    output += midput
                    midput = 0
                idx += 2
                continue
            elif input[idx-1] == u'零':
                if mapping[input[idx+1]] < 10**4: 
                    mid = mapping[input[idx]]*mapping[input[idx+1]]
                    midput += mid
                    idx += 2
                    continue
                else:
                    mid = mapping[input[idx]]
                    midput += mid
                    idx += 1
                    continue
        elif mapping[input[idx]] >= 10**4:
           midput = midput * mapping[input[idx]]
           output += midput
           midput = 0
           idx += 1
           continue
        else:
           midput += mapping[input[idx]]
           output += midput
           idx += 1 
    print output 

if __name__=='__main__':
    str = u'三百零一万'
    print str
    main(str)

```