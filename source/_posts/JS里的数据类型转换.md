---
title: JS里的数据类型转换
date: 2019-03-18 20:30:21
categories: 
- 前端学习
tags:
- JavaScript
---
一、tostring()
1、除了null和undefined不能转
2、XXX+''   or   1+'1'

二、Boolean()
1、0、NAN、null、undefined、''这五个值为false，其余所有为true
2、!! XXX

三、Number()
1、四种方法转化为数值类型
Number('1')
parseInt('1',10)
'1'-0
+'1'

四、深拷贝与浅拷贝
深拷贝：b变a不变
浅拷贝：b变a随着变

五、垃圾回收
如果一个对象未被引用，就是垃圾，可以被回收
