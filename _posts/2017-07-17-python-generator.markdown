---
layout: post
title: Generator in Python
date: 2017-07-17 16:24:00.000000000 +08:00
---

​        在Python中，带有yield关键字的函数被称之为generator（生成器）。何为yield，又何为generator呢？首先给出一个概念性的认识，后续给出相应的例子来进行阐述。

​         一个带有yield关键字的函数就是一个generator，它是函数，但是又和普通函数不同；生成一个generator，形式上像是函数调用，但是它不会执行任何函数代码，直到对它进行next()或者send(None)调用才会开始执行。虽然执行流程和函数执行流程一样，但是，每当执行到一个yield语句，流程就会中断，并返回一个值（yield 后面的值）；等到再次对它进行next()调用，将会从yield的下一个语句继续执行。整个过程像是在函数执行过程中被“中断”了多次，每次中断都会通过yield返回一个值。


