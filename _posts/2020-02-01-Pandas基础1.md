---
layout: post
title: pandas基础学习1 初始Series
date: 2020-02-01
tag: 机器学习
---

```python
import pandas as pd
```

数据结构其实就是Series和DataFrame。

series是一个像数组一样的一维序列，并伴有一个数组表示label，叫做index。创建一个series的方法也很简单：


```python
s = pd.Series([1,3,5,6,8])
```


```python
s
```




    0    1
    1    3
    2    5
    3    6
    4    8
    dtype: int64



可以看到，左边表示index，右边表示对应的value。可以通过value和index属性查看：


```python
s.values
```




    array([1, 3, 5, 6, 8])




```python
s = pd.Series([1,3,5,6,8],index = ['a','b','c','d','e'])
s
```




    a    1
    b    3
    c    5
    d    6
    e    8
    dtype: int64




```python
s.index
```




    Index(['a', 'b', 'c', 'd', 'e'], dtype='object')



可以用index的label来选择


```python
s['a']
```




    1




```python
s[['b','a']]
```




    b    3
    a    1
    dtype: int64



这里['b', 'a']其实被当做了索引，尽管这个索引是用string构成的。


```python
s[s>4]
```




    c    5
    d    6
    e    8
    dtype: int64




```python
s*4
```




    a     4
    b    12
    c    20
    d    24
    e    32
    dtype: int64




```python
import numpy as np
np.mean(s)
```




    4.6




```python
# 求均值
s.mean()
```




    4.6




```python
'a' in s.index
```




    True




```python
b = pd.Series({'a':1,'b':2,'c':3})
```


```python
b
```




    a    1
    b    2
    c    3
    dtype: int64




```python
b = pd.Series({'a':1,'b':2,'c':3}, index = ['b','c','d'] )
```


```python
b
```




    b    2.0
    c    3.0
    d    NaN
    dtype: float64



NaN表示缺失数据，用之后我们提到的话就用missing或NA来指代。pandas中的isnull和notnull函数可以用来检测缺失数据：


```python
pd.isnull(b)
```




    b    False
    c    False
    d     True
    dtype: bool




```python
b.isnull()
```




    b    False
    c    False
    d     True
    dtype: bool




```python
pd.notnull(b)
```




    b     True
    c     True
    d    False
    dtype: bool




```python
b = pd.Series({'a':1,'b':2,'c':3})
```


```python
c = pd.Series({'b':10,'c':11,'e':12})
```


```python
b + c
```




    a     NaN
    b    12.0
    c    14.0
    e     NaN
    dtype: float64



series的index能被直接更改


```python

```
