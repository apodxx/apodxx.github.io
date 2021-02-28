---
layout: post
title: pandas基础学习3 DateFrame简介2
date: 2021-02-01
tag: 机器学习
---



```python
import pandas as pd
import numpy as np
```


```python
xuhao = ['one','two','three','four','five','six','seven']
data = pd.DataFrame(np.random.randn(7,4), index=xuhao, columns=list('abcd'))
```


```python
data
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>-0.309267</td>
      <td>-0.270537</td>
      <td>-0.289924</td>
      <td>-1.619206</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-1.163394</td>
      <td>0.200229</td>
      <td>1.356976</td>
      <td>-0.754607</td>
    </tr>
    <tr>
      <th>three</th>
      <td>0.520898</td>
      <td>0.966406</td>
      <td>-0.096485</td>
      <td>-1.561740</td>
    </tr>
    <tr>
      <th>four</th>
      <td>1.553751</td>
      <td>-0.897781</td>
      <td>0.838232</td>
      <td>-0.004692</td>
    </tr>
    <tr>
      <th>five</th>
      <td>-0.692554</td>
      <td>-0.624643</td>
      <td>-0.764845</td>
      <td>1.365466</td>
    </tr>
    <tr>
      <th>six</th>
      <td>0.436710</td>
      <td>1.409946</td>
      <td>1.096413</td>
      <td>0.558250</td>
    </tr>
    <tr>
      <th>seven</th>
      <td>1.991297</td>
      <td>0.317776</td>
      <td>0.150799</td>
      <td>-0.241524</td>
    </tr>
  </tbody>
</table>
</div>




```python
data.describe()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>7.000000</td>
      <td>7.000000</td>
      <td>7.000000</td>
      <td>7.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>0.333920</td>
      <td>0.157342</td>
      <td>0.327309</td>
      <td>-0.322579</td>
    </tr>
    <tr>
      <th>std</th>
      <td>1.153957</td>
      <td>0.832571</td>
      <td>0.784996</td>
      <td>1.090595</td>
    </tr>
    <tr>
      <th>min</th>
      <td>-1.163394</td>
      <td>-0.897781</td>
      <td>-0.764845</td>
      <td>-1.619206</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>-0.500910</td>
      <td>-0.447590</td>
      <td>-0.193205</td>
      <td>-1.158174</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>0.436710</td>
      <td>0.200229</td>
      <td>0.150799</td>
      <td>-0.241524</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>1.037325</td>
      <td>0.642091</td>
      <td>0.967323</td>
      <td>0.276779</td>
    </tr>
    <tr>
      <th>max</th>
      <td>1.991297</td>
      <td>1.409946</td>
      <td>1.356976</td>
      <td>1.365466</td>
    </tr>
  </tbody>
</table>
</div>




```python
data.mean()
```




    a    0.333920
    b    0.157342
    c    0.327309
    d   -0.322579
    dtype: float64




```python
data.mean(1)
```




    one     -0.622233
    two     -0.090199
    three   -0.042730
    four     0.372378
    five    -0.179144
    six      0.875330
    seven    0.554587
    dtype: float64




```python
data.T
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>one</th>
      <th>two</th>
      <th>three</th>
      <th>four</th>
      <th>five</th>
      <th>six</th>
      <th>seven</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>-0.309267</td>
      <td>-1.163394</td>
      <td>0.520898</td>
      <td>1.553751</td>
      <td>-0.692554</td>
      <td>0.436710</td>
      <td>1.991297</td>
    </tr>
    <tr>
      <th>b</th>
      <td>-0.270537</td>
      <td>0.200229</td>
      <td>0.966406</td>
      <td>-0.897781</td>
      <td>-0.624643</td>
      <td>1.409946</td>
      <td>0.317776</td>
    </tr>
    <tr>
      <th>c</th>
      <td>-0.289924</td>
      <td>1.356976</td>
      <td>-0.096485</td>
      <td>0.838232</td>
      <td>-0.764845</td>
      <td>1.096413</td>
      <td>0.150799</td>
    </tr>
    <tr>
      <th>d</th>
      <td>-1.619206</td>
      <td>-0.754607</td>
      <td>-1.561740</td>
      <td>-0.004692</td>
      <td>1.365466</td>
      <td>0.558250</td>
      <td>-0.241524</td>
    </tr>
  </tbody>
</table>
</div>



[对sort_value和sort_index的相关解释](https://www.jianshu.com/p/f0ed06cd5003)



```python
data.sort_index(axis = 1,ascending = False)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>d</th>
      <th>c</th>
      <th>b</th>
      <th>a</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>-1.619206</td>
      <td>-0.289924</td>
      <td>-0.270537</td>
      <td>-0.309267</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-0.754607</td>
      <td>1.356976</td>
      <td>0.200229</td>
      <td>-1.163394</td>
    </tr>
    <tr>
      <th>three</th>
      <td>-1.561740</td>
      <td>-0.096485</td>
      <td>0.966406</td>
      <td>0.520898</td>
    </tr>
    <tr>
      <th>four</th>
      <td>-0.004692</td>
      <td>0.838232</td>
      <td>-0.897781</td>
      <td>1.553751</td>
    </tr>
    <tr>
      <th>five</th>
      <td>1.365466</td>
      <td>-0.764845</td>
      <td>-0.624643</td>
      <td>-0.692554</td>
    </tr>
    <tr>
      <th>six</th>
      <td>0.558250</td>
      <td>1.096413</td>
      <td>1.409946</td>
      <td>0.436710</td>
    </tr>
    <tr>
      <th>seven</th>
      <td>-0.241524</td>
      <td>0.150799</td>
      <td>0.317776</td>
      <td>1.991297</td>
    </tr>
  </tbody>
</table>
</div>




```python
data.sort_values(by='c')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>five</th>
      <td>-0.692554</td>
      <td>-0.624643</td>
      <td>-0.764845</td>
      <td>1.365466</td>
    </tr>
    <tr>
      <th>one</th>
      <td>-0.309267</td>
      <td>-0.270537</td>
      <td>-0.289924</td>
      <td>-1.619206</td>
    </tr>
    <tr>
      <th>three</th>
      <td>0.520898</td>
      <td>0.966406</td>
      <td>-0.096485</td>
      <td>-1.561740</td>
    </tr>
    <tr>
      <th>seven</th>
      <td>1.991297</td>
      <td>0.317776</td>
      <td>0.150799</td>
      <td>-0.241524</td>
    </tr>
    <tr>
      <th>four</th>
      <td>1.553751</td>
      <td>-0.897781</td>
      <td>0.838232</td>
      <td>-0.004692</td>
    </tr>
    <tr>
      <th>six</th>
      <td>0.436710</td>
      <td>1.409946</td>
      <td>1.096413</td>
      <td>0.558250</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-1.163394</td>
      <td>0.200229</td>
      <td>1.356976</td>
      <td>-0.754607</td>
    </tr>
  </tbody>
</table>
</div>




```python
data.index
```




    Index(['one', 'two', 'three', 'four', 'five', 'six', 'seven'], dtype='object')




```python
data.columns
```




    Index(['a', 'b', 'c', 'd'], dtype='object')




```python
a = pd.Series([1,2,3,4], index = ['d','a','b','c'])
```


```python
a.reindex(list('abcd'))
```




    a    2
    b    3
    c    4
    d    1
    dtype: int64




```python
a.reindex(list('abcde'))
```




    a    2.0
    b    3.0
    c    4.0
    d    1.0
    e    NaN
    dtype: float64




```python
a.reindex(list('abcde'),fill_value = 0)
```




    a    2
    b    3
    c    4
    d    1
    e    0
    dtype: int64




```python
data
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>-0.309267</td>
      <td>-0.270537</td>
      <td>-0.289924</td>
      <td>-1.619206</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-1.163394</td>
      <td>0.200229</td>
      <td>1.356976</td>
      <td>-0.754607</td>
    </tr>
    <tr>
      <th>three</th>
      <td>0.520898</td>
      <td>0.966406</td>
      <td>-0.096485</td>
      <td>-1.561740</td>
    </tr>
    <tr>
      <th>four</th>
      <td>1.553751</td>
      <td>-0.897781</td>
      <td>0.838232</td>
      <td>-0.004692</td>
    </tr>
    <tr>
      <th>five</th>
      <td>-0.692554</td>
      <td>-0.624643</td>
      <td>-0.764845</td>
      <td>1.365466</td>
    </tr>
    <tr>
      <th>six</th>
      <td>0.436710</td>
      <td>1.409946</td>
      <td>1.096413</td>
      <td>0.558250</td>
    </tr>
    <tr>
      <th>seven</th>
      <td>1.991297</td>
      <td>0.317776</td>
      <td>0.150799</td>
      <td>-0.241524</td>
    </tr>
  </tbody>
</table>
</div>




```python
data.reindex(['four', 'five', 'six', 'seven','one', 'two', 'three'])
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>four</th>
      <td>1.553751</td>
      <td>-0.897781</td>
      <td>0.838232</td>
      <td>-0.004692</td>
    </tr>
    <tr>
      <th>five</th>
      <td>-0.692554</td>
      <td>-0.624643</td>
      <td>-0.764845</td>
      <td>1.365466</td>
    </tr>
    <tr>
      <th>six</th>
      <td>0.436710</td>
      <td>1.409946</td>
      <td>1.096413</td>
      <td>0.558250</td>
    </tr>
    <tr>
      <th>seven</th>
      <td>1.991297</td>
      <td>0.317776</td>
      <td>0.150799</td>
      <td>-0.241524</td>
    </tr>
    <tr>
      <th>one</th>
      <td>-0.309267</td>
      <td>-0.270537</td>
      <td>-0.289924</td>
      <td>-1.619206</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-1.163394</td>
      <td>0.200229</td>
      <td>1.356976</td>
      <td>-0.754607</td>
    </tr>
    <tr>
      <th>three</th>
      <td>0.520898</td>
      <td>0.966406</td>
      <td>-0.096485</td>
      <td>-1.561740</td>
    </tr>
  </tbody>
</table>
</div>




```python
data.reindex(columns = ['c', 'd', 'a', 'b'])
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>c</th>
      <th>d</th>
      <th>a</th>
      <th>b</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>-0.289924</td>
      <td>-1.619206</td>
      <td>-0.309267</td>
      <td>-0.270537</td>
    </tr>
    <tr>
      <th>two</th>
      <td>1.356976</td>
      <td>-0.754607</td>
      <td>-1.163394</td>
      <td>0.200229</td>
    </tr>
    <tr>
      <th>three</th>
      <td>-0.096485</td>
      <td>-1.561740</td>
      <td>0.520898</td>
      <td>0.966406</td>
    </tr>
    <tr>
      <th>four</th>
      <td>0.838232</td>
      <td>-0.004692</td>
      <td>1.553751</td>
      <td>-0.897781</td>
    </tr>
    <tr>
      <th>five</th>
      <td>-0.764845</td>
      <td>1.365466</td>
      <td>-0.692554</td>
      <td>-0.624643</td>
    </tr>
    <tr>
      <th>six</th>
      <td>1.096413</td>
      <td>0.558250</td>
      <td>0.436710</td>
      <td>1.409946</td>
    </tr>
    <tr>
      <th>seven</th>
      <td>0.150799</td>
      <td>-0.241524</td>
      <td>1.991297</td>
      <td>0.317776</td>
    </tr>
  </tbody>
</table>
</div>




```python
data.reindex(columns = ['c', 'd', 'a', 'b','e'])
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>c</th>
      <th>d</th>
      <th>a</th>
      <th>b</th>
      <th>e</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>-0.289924</td>
      <td>-1.619206</td>
      <td>-0.309267</td>
      <td>-0.270537</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>two</th>
      <td>1.356976</td>
      <td>-0.754607</td>
      <td>-1.163394</td>
      <td>0.200229</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>three</th>
      <td>-0.096485</td>
      <td>-1.561740</td>
      <td>0.520898</td>
      <td>0.966406</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>four</th>
      <td>0.838232</td>
      <td>-0.004692</td>
      <td>1.553751</td>
      <td>-0.897781</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>five</th>
      <td>-0.764845</td>
      <td>1.365466</td>
      <td>-0.692554</td>
      <td>-0.624643</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>six</th>
      <td>1.096413</td>
      <td>0.558250</td>
      <td>0.436710</td>
      <td>1.409946</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>seven</th>
      <td>0.150799</td>
      <td>-0.241524</td>
      <td>1.991297</td>
      <td>0.317776</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 删除某一列
del data['b']
```


```python
data
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>c</th>
      <th>d</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>-0.309267</td>
      <td>-0.289924</td>
      <td>-1.619206</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-1.163394</td>
      <td>1.356976</td>
      <td>-0.754607</td>
    </tr>
    <tr>
      <th>three</th>
      <td>0.520898</td>
      <td>-0.096485</td>
      <td>-1.561740</td>
    </tr>
    <tr>
      <th>four</th>
      <td>1.553751</td>
      <td>0.838232</td>
      <td>-0.004692</td>
    </tr>
    <tr>
      <th>five</th>
      <td>-0.692554</td>
      <td>-0.764845</td>
      <td>1.365466</td>
    </tr>
    <tr>
      <th>six</th>
      <td>0.436710</td>
      <td>1.096413</td>
      <td>0.558250</td>
    </tr>
    <tr>
      <th>seven</th>
      <td>1.991297</td>
      <td>0.150799</td>
      <td>-0.241524</td>
    </tr>
  </tbody>
</table>
</div>


data.drop('six',inplace = True)
​ inplace = True：不创建新的对象，直接对原始对象进行修改；

​ inplace = False：对数据进行修改，创建并返回新的对象承载其修改结果。

默认是False，即创建新的对象进行修改，原对象不变，和深复制和浅复制有些类似。

```python
# 删除某一行
data.drop('six')
# 删除多行时 data.drop(['one','two'])

```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>c</th>
      <th>d</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>-0.309267</td>
      <td>-0.289924</td>
      <td>-1.619206</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-1.163394</td>
      <td>1.356976</td>
      <td>-0.754607</td>
    </tr>
    <tr>
      <th>three</th>
      <td>0.520898</td>
      <td>-0.096485</td>
      <td>-1.561740</td>
    </tr>
    <tr>
      <th>four</th>
      <td>1.553751</td>
      <td>0.838232</td>
      <td>-0.004692</td>
    </tr>
    <tr>
      <th>five</th>
      <td>-0.692554</td>
      <td>-0.764845</td>
      <td>1.365466</td>
    </tr>
    <tr>
      <th>seven</th>
      <td>1.991297</td>
      <td>0.150799</td>
      <td>-0.241524</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 使用drop删除某一列
data.drop('a',axis =1)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>c</th>
      <th>d</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>-0.289924</td>
      <td>-1.619206</td>
    </tr>
    <tr>
      <th>two</th>
      <td>1.356976</td>
      <td>-0.754607</td>
    </tr>
    <tr>
      <th>three</th>
      <td>-0.096485</td>
      <td>-1.561740</td>
    </tr>
    <tr>
      <th>four</th>
      <td>0.838232</td>
      <td>-0.004692</td>
    </tr>
    <tr>
      <th>five</th>
      <td>-0.764845</td>
      <td>1.365466</td>
    </tr>
    <tr>
      <th>six</th>
      <td>1.096413</td>
      <td>0.558250</td>
    </tr>
    <tr>
      <th>seven</th>
      <td>0.150799</td>
      <td>-0.241524</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 本身的data 并没有发生变化 没有没有inplace
data1 = data.drop('a',axis =1)
```


```python
data1
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>c</th>
      <th>d</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>-0.289924</td>
      <td>-1.619206</td>
    </tr>
    <tr>
      <th>two</th>
      <td>1.356976</td>
      <td>-0.754607</td>
    </tr>
    <tr>
      <th>three</th>
      <td>-0.096485</td>
      <td>-1.561740</td>
    </tr>
    <tr>
      <th>four</th>
      <td>0.838232</td>
      <td>-0.004692</td>
    </tr>
    <tr>
      <th>five</th>
      <td>-0.764845</td>
      <td>1.365466</td>
    </tr>
    <tr>
      <th>six</th>
      <td>1.096413</td>
      <td>0.558250</td>
    </tr>
    <tr>
      <th>seven</th>
      <td>0.150799</td>
      <td>-0.241524</td>
    </tr>
  </tbody>
</table>
</div>




```python
data 
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>c</th>
      <th>d</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>-0.309267</td>
      <td>-0.289924</td>
      <td>-1.619206</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-1.163394</td>
      <td>1.356976</td>
      <td>-0.754607</td>
    </tr>
    <tr>
      <th>three</th>
      <td>0.520898</td>
      <td>-0.096485</td>
      <td>-1.561740</td>
    </tr>
    <tr>
      <th>four</th>
      <td>1.553751</td>
      <td>0.838232</td>
      <td>-0.004692</td>
    </tr>
    <tr>
      <th>five</th>
      <td>-0.692554</td>
      <td>-0.764845</td>
      <td>1.365466</td>
    </tr>
    <tr>
      <th>six</th>
      <td>0.436710</td>
      <td>1.096413</td>
      <td>0.558250</td>
    </tr>
    <tr>
      <th>seven</th>
      <td>1.991297</td>
      <td>0.150799</td>
      <td>-0.241524</td>
    </tr>
  </tbody>
</table>
</div>




```python
data + data1
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>c</th>
      <th>d</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>NaN</td>
      <td>-0.579848</td>
      <td>-3.238411</td>
    </tr>
    <tr>
      <th>two</th>
      <td>NaN</td>
      <td>2.713952</td>
      <td>-1.509214</td>
    </tr>
    <tr>
      <th>three</th>
      <td>NaN</td>
      <td>-0.192970</td>
      <td>-3.123480</td>
    </tr>
    <tr>
      <th>four</th>
      <td>NaN</td>
      <td>1.676464</td>
      <td>-0.009383</td>
    </tr>
    <tr>
      <th>five</th>
      <td>NaN</td>
      <td>-1.529690</td>
      <td>2.730932</td>
    </tr>
    <tr>
      <th>six</th>
      <td>NaN</td>
      <td>2.192827</td>
      <td>1.116500</td>
    </tr>
    <tr>
      <th>seven</th>
      <td>NaN</td>
      <td>0.301598</td>
      <td>-0.483048</td>
    </tr>
  </tbody>
</table>
</div>



在DataFrame中，数据对齐同时发生在行和列上：


```python
df1 = pd.DataFrame(np.arange(9.).reshape((3, 3)), columns=list('bcd'),
                   index=['one', 'two', 'three'])
df2 = pd.DataFrame(np.arange(12.).reshape((4, 3)), columns=list('bde'),
                   index=['three', 'four', 'five', 'six'])
```


```python
df1
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>0.0</td>
      <td>1.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>two</th>
      <td>3.0</td>
      <td>4.0</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>three</th>
      <td>6.0</td>
      <td>7.0</td>
      <td>8.0</td>
    </tr>
  </tbody>
</table>
</div>




```python

df2
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>b</th>
      <th>d</th>
      <th>e</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>three</th>
      <td>0.0</td>
      <td>1.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>four</th>
      <td>3.0</td>
      <td>4.0</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>five</th>
      <td>6.0</td>
      <td>7.0</td>
      <td>8.0</td>
    </tr>
    <tr>
      <th>six</th>
      <td>9.0</td>
      <td>10.0</td>
      <td>11.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1+df2
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
      <th>e</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>five</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>four</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>one</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>six</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>three</th>
      <td>6.0</td>
      <td>NaN</td>
      <td>9.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>two</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1.iloc[1:2]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>two</th>
      <td>3.0</td>
      <td>4.0</td>
      <td>5.0</td>
    </tr>
  </tbody>
</table>
</div>


loc为Selection by Label函数，即为按标签取数据，标签是什么，就是上面的’0’~‘4’, ‘A’~‘B’。
iloc函数为Selection by Position，即按位置选择数据，即第n行，第n列数据，只接受整型参数

```python
df1['b']
```




    one      0.0
    two      3.0
    three    6.0
    Name: b, dtype: float64




```python
np.abs(data)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>c</th>
      <th>d</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>0.309267</td>
      <td>0.289924</td>
      <td>1.619206</td>
    </tr>
    <tr>
      <th>two</th>
      <td>1.163394</td>
      <td>1.356976</td>
      <td>0.754607</td>
    </tr>
    <tr>
      <th>three</th>
      <td>0.520898</td>
      <td>0.096485</td>
      <td>1.561740</td>
    </tr>
    <tr>
      <th>four</th>
      <td>1.553751</td>
      <td>0.838232</td>
      <td>0.004692</td>
    </tr>
    <tr>
      <th>five</th>
      <td>0.692554</td>
      <td>0.764845</td>
      <td>1.365466</td>
    </tr>
    <tr>
      <th>six</th>
      <td>0.436710</td>
      <td>1.096413</td>
      <td>0.558250</td>
    </tr>
    <tr>
      <th>seven</th>
      <td>1.991297</td>
      <td>0.150799</td>
      <td>0.241524</td>
    </tr>
  </tbody>
</table>
</div>




```python
np.mean(a)
```




    2.5




```python
1 / df1
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>inf</td>
      <td>1.000000</td>
      <td>0.500</td>
    </tr>
    <tr>
      <th>two</th>
      <td>0.333333</td>
      <td>0.250000</td>
      <td>0.200</td>
    </tr>
    <tr>
      <th>three</th>
      <td>0.166667</td>
      <td>0.142857</td>
      <td>0.125</td>
    </tr>
  </tbody>
</table>
</div>




```python
frame = pd.DataFrame(np.arange(12.).reshape((4, 3)),
                     columns=list('bde'),
                    index=['one', 'two', 'three', 'four'])
series = frame.iloc[0]
```


```python
frame
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>b</th>
      <th>d</th>
      <th>e</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>0.0</td>
      <td>1.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>two</th>
      <td>3.0</td>
      <td>4.0</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>three</th>
      <td>6.0</td>
      <td>7.0</td>
      <td>8.0</td>
    </tr>
    <tr>
      <th>four</th>
      <td>9.0</td>
      <td>10.0</td>
      <td>11.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
series
```




    b    0.0
    d    1.0
    e    2.0
    Name: one, dtype: float64




```python
frame - series
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>b</th>
      <th>d</th>
      <th>e</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>two</th>
      <td>3.0</td>
      <td>3.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>three</th>
      <td>6.0</td>
      <td>6.0</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>four</th>
      <td>9.0</td>
      <td>9.0</td>
      <td>9.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
series2 = pd.Series(range(3), index=['b', 'e', 'f'])
frame + series2
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>b</th>
      <th>d</th>
      <th>e</th>
      <th>f</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>0.0</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>two</th>
      <td>3.0</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>three</th>
      <td>6.0</td>
      <td>NaN</td>
      <td>9.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>four</th>
      <td>9.0</td>
      <td>NaN</td>
      <td>12.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
series3 = frame['d']
frame
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>b</th>
      <th>d</th>
      <th>e</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>0.0</td>
      <td>1.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>two</th>
      <td>3.0</td>
      <td>4.0</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>three</th>
      <td>6.0</td>
      <td>7.0</td>
      <td>8.0</td>
    </tr>
    <tr>
      <th>four</th>
      <td>9.0</td>
      <td>10.0</td>
      <td>11.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
frame.sub(series3, axis='index')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>b</th>
      <th>d</th>
      <th>e</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>-1.0</td>
      <td>0.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-1.0</td>
      <td>0.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>three</th>
      <td>-1.0</td>
      <td>0.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>four</th>
      <td>-1.0</td>
      <td>0.0</td>
      <td>1.0</td>
    </tr>
  </tbody>
</table>
</div>




```python

```


```python

```
