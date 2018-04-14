---
layout: post
title: 'codewars刷题'
subtitle: 'Python打印*组成的三角形'
date: 2018-04-14 15:29:12
categories: [刷题]
cover: 'https://upload-images.jianshu.io/upload_images/2348227-f39ea4c7c14d49ca.jpg'
tags: [codewars,python]
---

题目要求:
>Description:
Build Tower
Build Tower by the following given argument:
number of floors (integer and always greater than 0).
Tower block is represented as *
Python: return a list;
JavaScript: returns an Array;
C#: returns a string[];
PHP: returns an array;
C++: returns a vector<string>;
Haskell: returns a [String];
Ruby: returns an Array;
Have fun!
for example, a tower of 3 floors looks like below
[
  '  *  ', 
  ' *** ', 
  '*****'
]
and a tower of 6 floors looks like below
[
  '     *     ', 
  '    ***    ', 
  '   *****   ', 
  '  *******  ', 
  ' ********* ', 
  '***********'
]

简单来说就是函数返回一个列表，里面是一个等差数列组成的`*`，注意空格。

对python的基础库不太了解，用了个笨办法解决：

```
def tower_builder(n_floors):
    # build here
    s = '*'
    e = s + (n_floors - 1) * 2 * s
    l = e.__len__()
    def space(n):
        m = (l - n) * 0.5
        return int(m) * ' '
    return [space(i) + i * s + space(i) for i in range(1, (n_floors+1)*2-1, 2)]
```
而且第一次犯了个错误，都知道在python中可以这样重复字符串，![image.png](https://upload-images.jianshu.io/upload_images/2348227-5877887212e789a4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
float类型不能直接与字符串相乘，这样会出错：
![image.png](https://upload-images.jianshu.io/upload_images/2348227-2090032ca2f2d873.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
` return int(m) * ' '`，如果没做类型转换，会出错的~

看到别人的解法，才知道原来string有个center方法，╮(╯▽╰)╭

```
def tower_builder(n):
    return [("*" * (i*2-1)).center(n*2-1) for i in range(1, n+1)]
```
