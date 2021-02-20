---
layout: post
title: pandas基础学习2 DataFrame简介
date: 2020-02-01
tag: 机器学习
---


```python
import pandas as pd
import numpy as np
```

DataFrame表示一个长方形表格，并包含排好序的列，每一列都可以是不同的数值类型（数字，字符串，布尔值）。DataFrame有行索引和列索引（row index, column index）；可以看做是分享所有索引的由series组成的字典。数据是保存在一维以上的区块里的。series创建的是一个列


```python

data = pd.DataFrame({ 'a' : [1,2,3,4],
                      'b' : pd.Series(1,index=list(range(4)),dtype='float32'),
                      'c' : np.array([3] * 4,dtype = 'int32')})
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
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>1.0</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1.0</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1.0</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>1.0</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>




```python
data.values
```




    array([[ 1.,  1.,  3.],
           [ 2.,  1.,  3.],
           [ 3.,  1.,  3.],
           [ 4.,  1.,  3.]], dtype=float32)




```python
xuhao = ['one','two','three','four','five','six']
df = pd.DataFrame(np.random.randn(6,4), index=xuhao, columns=list('abcd'))
```


```python
df
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
      <td>-0.333815</td>
      <td>0.249480</td>
      <td>-1.715385</td>
      <td>-0.770067</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-0.425955</td>
      <td>0.156519</td>
      <td>0.313454</td>
      <td>0.661829</td>
    </tr>
    <tr>
      <th>three</th>
      <td>-0.003607</td>
      <td>0.676290</td>
      <td>2.260861</td>
      <td>1.626270</td>
    </tr>
    <tr>
      <th>four</th>
      <td>0.514988</td>
      <td>0.179730</td>
      <td>1.586553</td>
      <td>-0.725601</td>
    </tr>
    <tr>
      <th>five</th>
      <td>-0.491455</td>
      <td>0.222179</td>
      <td>-0.549559</td>
      <td>0.827584</td>
    </tr>
    <tr>
      <th>six</th>
      <td>0.532381</td>
      <td>-0.719393</td>
      <td>1.413606</td>
      <td>-0.070122</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['a']
```




    one     -0.333815
    two     -0.425955
    three   -0.003607
    four     0.514988
    five    -0.491455
    six      0.532381
    Name: a, dtype: float64




```python
# 取多列时，用list形式表示 重要
df[['a','c']]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>c</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>-0.333815</td>
      <td>-1.715385</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-0.425955</td>
      <td>0.313454</td>
    </tr>
    <tr>
      <th>three</th>
      <td>-0.003607</td>
      <td>2.260861</td>
    </tr>
    <tr>
      <th>four</th>
      <td>0.514988</td>
      <td>1.586553</td>
    </tr>
    <tr>
      <th>five</th>
      <td>-0.491455</td>
      <td>-0.549559</td>
    </tr>
    <tr>
      <th>six</th>
      <td>0.532381</td>
      <td>1.413606</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 当选取多行时，使用切片
df[0:2]
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
      <td>-0.333815</td>
      <td>0.249480</td>
      <td>-1.715385</td>
      <td>-0.770067</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-0.425955</td>
      <td>0.156519</td>
      <td>0.313454</td>
      <td>0.661829</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.columns
```




    Index(['a', 'b', 'c', 'd'], dtype='object')




```python
df.index
```




    Index(['one', 'two', 'three', 'four', 'five', 'six'], dtype='object')




```python
df.index.name = 'year'; 
df.columns.name = 'state'
```


```python
labels = pd.Index(np.arange(3))
labels
```




    Int64Index([0, 1, 2], dtype='int64')




```python
df.values
```




    array([[-0.3338146 ,  0.24948038, -1.71538503, -0.77006651],
           [-0.42595487,  0.15651923,  0.31345399,  0.66182881],
           [-0.00360708,  0.67629011,  2.26086105,  1.62627001],
           [ 0.51498751,  0.17972987,  1.5865527 , -0.72560079],
           [-0.49145515,  0.22217899, -0.54955853,  0.82758401],
           [ 0.53238107, -0.71939338,  1.41360613, -0.07012222]])



对于一个较大的DataFrame，用head方法会返回前5行（注：这个函数在数据分析中经常使用，用来查看表格里有什么东西）


```python
df.head(3)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>state</th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
    </tr>
    <tr>
      <th>year</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>-0.333815</td>
      <td>0.249480</td>
      <td>-1.715385</td>
      <td>-0.770067</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-0.425955</td>
      <td>0.156519</td>
      <td>0.313454</td>
      <td>0.661829</td>
    </tr>
    <tr>
      <th>three</th>
      <td>-0.003607</td>
      <td>0.676290</td>
      <td>2.260861</td>
      <td>1.626270</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.tail(3)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>state</th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
    </tr>
    <tr>
      <th>year</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>four</th>
      <td>0.514988</td>
      <td>0.179730</td>
      <td>1.586553</td>
      <td>-0.725601</td>
    </tr>
    <tr>
      <th>five</th>
      <td>-0.491455</td>
      <td>0.222179</td>
      <td>-0.549559</td>
      <td>0.827584</td>
    </tr>
    <tr>
      <th>six</th>
      <td>0.532381</td>
      <td>-0.719393</td>
      <td>1.413606</td>
      <td>-0.070122</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['a']
```




    year
    one     -0.333815
    two     -0.425955
    three   -0.003607
    four     0.514988
    five    -0.491455
    six      0.532381
    Name: a, dtype: float64




```python
df.a
```




    year
    one     -0.333815
    two     -0.425955
    three   -0.003607
    four     0.514988
    five    -0.491455
    six      0.532381
    Name: a, dtype: float64




```python
df[['a','c']]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>state</th>
      <th>a</th>
      <th>c</th>
    </tr>
    <tr>
      <th>year</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>-0.333815</td>
      <td>-1.715385</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-0.425955</td>
      <td>0.313454</td>
    </tr>
    <tr>
      <th>three</th>
      <td>-0.003607</td>
      <td>2.260861</td>
    </tr>
    <tr>
      <th>four</th>
      <td>0.514988</td>
      <td>1.586553</td>
    </tr>
    <tr>
      <th>five</th>
      <td>-0.491455</td>
      <td>-0.549559</td>
    </tr>
    <tr>
      <th>six</th>
      <td>0.532381</td>
      <td>1.413606</td>
    </tr>
  </tbody>
</table>
</div>




```python
df[0:2]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>state</th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
    </tr>
    <tr>
      <th>year</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>-0.333815</td>
      <td>0.249480</td>
      <td>-1.715385</td>
      <td>-0.770067</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-0.425955</td>
      <td>0.156519</td>
      <td>0.313454</td>
      <td>0.661829</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 根据索引取值
df.loc['one']
```




    state
    a   -0.333815
    b    0.249480
    c   -1.715385
    d   -0.770067
    Name: one, dtype: float64




```python
# 根据索引取值多行
df.loc[['one','four']]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>state</th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
    </tr>
    <tr>
      <th>year</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>-0.333815</td>
      <td>0.24948</td>
      <td>-1.715385</td>
      <td>-0.770067</td>
    </tr>
    <tr>
      <th>four</th>
      <td>0.514988</td>
      <td>0.17973</td>
      <td>1.586553</td>
      <td>-0.725601</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 注意与上一行的区别 这里使用的是 冒号 
df.loc['one':'four']
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>state</th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
    </tr>
    <tr>
      <th>year</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>-0.333815</td>
      <td>0.249480</td>
      <td>-1.715385</td>
      <td>-0.770067</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-0.425955</td>
      <td>0.156519</td>
      <td>0.313454</td>
      <td>0.661829</td>
    </tr>
    <tr>
      <th>three</th>
      <td>-0.003607</td>
      <td>0.676290</td>
      <td>2.260861</td>
      <td>1.626270</td>
    </tr>
    <tr>
      <th>four</th>
      <td>0.514988</td>
      <td>0.179730</td>
      <td>1.586553</td>
      <td>-0.725601</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1 = df.loc['one':'four']
df1
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>state</th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
    </tr>
    <tr>
      <th>year</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>-0.333815</td>
      <td>0.249480</td>
      <td>-1.715385</td>
      <td>-0.770067</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-0.425955</td>
      <td>0.156519</td>
      <td>0.313454</td>
      <td>0.661829</td>
    </tr>
    <tr>
      <th>three</th>
      <td>-0.003607</td>
      <td>0.676290</td>
      <td>2.260861</td>
      <td>1.626270</td>
    </tr>
    <tr>
      <th>four</th>
      <td>0.514988</td>
      <td>0.179730</td>
      <td>1.586553</td>
      <td>-0.725601</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 这个语法挺好用的

df.loc['one':'four','a':'c']
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>state</th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
    </tr>
    <tr>
      <th>year</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>-0.333815</td>
      <td>0.249480</td>
      <td>-1.715385</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-0.425955</td>
      <td>0.156519</td>
      <td>0.313454</td>
    </tr>
    <tr>
      <th>three</th>
      <td>-0.003607</td>
      <td>0.676290</td>
      <td>2.260861</td>
    </tr>
    <tr>
      <th>four</th>
      <td>0.514988</td>
      <td>0.179730</td>
      <td>1.586553</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.loc[['one','four'],'c']
```




    year
    one    -1.715385
    four    1.586553
    Name: c, dtype: float64




```python
df.loc[['one','four'],['c','d']]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>state</th>
      <th>c</th>
      <th>d</th>
    </tr>
    <tr>
      <th>year</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>-1.715385</td>
      <td>-0.770067</td>
    </tr>
    <tr>
      <th>four</th>
      <td>1.586553</td>
      <td>-0.725601</td>
    </tr>
  </tbody>
</table>
</div>




```python
# 第a列的一到四行
df.loc['one':'four','a']
```




    year
    one     -0.333815
    two     -0.425955
    three   -0.003607
    four     0.514988
    Name: a, dtype: float64




```python
df.loc[:,['b','d']]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>state</th>
      <th>b</th>
      <th>d</th>
    </tr>
    <tr>
      <th>year</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>0.249480</td>
      <td>-0.770067</td>
    </tr>
    <tr>
      <th>two</th>
      <td>0.156519</td>
      <td>0.661829</td>
    </tr>
    <tr>
      <th>three</th>
      <td>0.676290</td>
      <td>1.626270</td>
    </tr>
    <tr>
      <th>four</th>
      <td>0.179730</td>
      <td>-0.725601</td>
    </tr>
    <tr>
      <th>five</th>
      <td>0.222179</td>
      <td>0.827584</td>
    </tr>
    <tr>
      <th>six</th>
      <td>-0.719393</td>
      <td>-0.070122</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.loc['two','c']
```




    0.31345398766932131




```python
# 与loc的区别是前包括后不包括
df.iloc[3]                         
```




    state
    a    0.514988
    b    0.179730
    c    1.586553
    d   -0.725601
    Name: four, dtype: float64




```python
df.iloc[1:3,0:2]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>state</th>
      <th>a</th>
      <th>b</th>
    </tr>
    <tr>
      <th>year</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>two</th>
      <td>-0.425955</td>
      <td>0.156519</td>
    </tr>
    <tr>
      <th>three</th>
      <td>-0.003607</td>
      <td>0.676290</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.iloc[1:3,:]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>state</th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
    </tr>
    <tr>
      <th>year</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>two</th>
      <td>-0.425955</td>
      <td>0.156519</td>
      <td>0.313454</td>
      <td>0.661829</td>
    </tr>
    <tr>
      <th>three</th>
      <td>-0.003607</td>
      <td>0.676290</td>
      <td>2.260861</td>
      <td>1.626270</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.iloc[2,3]
```




    1.6262700090364508




```python
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>state</th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
    </tr>
    <tr>
      <th>year</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>-0.333815</td>
      <td>0.249480</td>
      <td>-1.715385</td>
      <td>-0.770067</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-0.425955</td>
      <td>0.156519</td>
      <td>0.313454</td>
      <td>0.661829</td>
    </tr>
    <tr>
      <th>three</th>
      <td>-0.003607</td>
      <td>0.676290</td>
      <td>2.260861</td>
      <td>1.626270</td>
    </tr>
    <tr>
      <th>four</th>
      <td>0.514988</td>
      <td>0.179730</td>
      <td>1.586553</td>
      <td>-0.725601</td>
    </tr>
    <tr>
      <th>five</th>
      <td>-0.491455</td>
      <td>0.222179</td>
      <td>-0.549559</td>
      <td>0.827584</td>
    </tr>
    <tr>
      <th>six</th>
      <td>0.532381</td>
      <td>-0.719393</td>
      <td>1.413606</td>
      <td>-0.070122</td>
    </tr>
  </tbody>
</table>
</div>




```python
df[df>0]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>state</th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
    </tr>
    <tr>
      <th>year</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>NaN</td>
      <td>0.249480</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>two</th>
      <td>NaN</td>
      <td>0.156519</td>
      <td>0.313454</td>
      <td>0.661829</td>
    </tr>
    <tr>
      <th>three</th>
      <td>NaN</td>
      <td>0.676290</td>
      <td>2.260861</td>
      <td>1.626270</td>
    </tr>
    <tr>
      <th>four</th>
      <td>0.514988</td>
      <td>0.179730</td>
      <td>1.586553</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>five</th>
      <td>NaN</td>
      <td>0.222179</td>
      <td>NaN</td>
      <td>0.827584</td>
    </tr>
    <tr>
      <th>six</th>
      <td>0.532381</td>
      <td>NaN</td>
      <td>1.413606</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
df[df.a<0]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>state</th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
    </tr>
    <tr>
      <th>year</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>-0.333815</td>
      <td>0.249480</td>
      <td>-1.715385</td>
      <td>-0.770067</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-0.425955</td>
      <td>0.156519</td>
      <td>0.313454</td>
      <td>0.661829</td>
    </tr>
    <tr>
      <th>three</th>
      <td>-0.003607</td>
      <td>0.676290</td>
      <td>2.260861</td>
      <td>1.626270</td>
    </tr>
    <tr>
      <th>five</th>
      <td>-0.491455</td>
      <td>0.222179</td>
      <td>-0.549559</td>
      <td>0.827584</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['e'] = 3
```


```python
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>state</th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
      <th>e</th>
    </tr>
    <tr>
      <th>year</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>-0.333815</td>
      <td>0.249480</td>
      <td>-1.715385</td>
      <td>-0.770067</td>
      <td>3</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-0.425955</td>
      <td>0.156519</td>
      <td>0.313454</td>
      <td>0.661829</td>
      <td>3</td>
    </tr>
    <tr>
      <th>three</th>
      <td>-0.003607</td>
      <td>0.676290</td>
      <td>2.260861</td>
      <td>1.626270</td>
      <td>3</td>
    </tr>
    <tr>
      <th>four</th>
      <td>0.514988</td>
      <td>0.179730</td>
      <td>1.586553</td>
      <td>-0.725601</td>
      <td>3</td>
    </tr>
    <tr>
      <th>five</th>
      <td>-0.491455</td>
      <td>0.222179</td>
      <td>-0.549559</td>
      <td>0.827584</td>
      <td>3</td>
    </tr>
    <tr>
      <th>six</th>
      <td>0.532381</td>
      <td>-0.719393</td>
      <td>1.413606</td>
      <td>-0.070122</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['f'] = np.arange(6)
```


```python
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>state</th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
      <th>e</th>
      <th>f</th>
    </tr>
    <tr>
      <th>year</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>-0.333815</td>
      <td>0.249480</td>
      <td>-1.715385</td>
      <td>-0.770067</td>
      <td>3</td>
      <td>0</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-0.425955</td>
      <td>0.156519</td>
      <td>0.313454</td>
      <td>0.661829</td>
      <td>3</td>
      <td>1</td>
    </tr>
    <tr>
      <th>three</th>
      <td>-0.003607</td>
      <td>0.676290</td>
      <td>2.260861</td>
      <td>1.626270</td>
      <td>3</td>
      <td>2</td>
    </tr>
    <tr>
      <th>four</th>
      <td>0.514988</td>
      <td>0.179730</td>
      <td>1.586553</td>
      <td>-0.725601</td>
      <td>3</td>
      <td>3</td>
    </tr>
    <tr>
      <th>five</th>
      <td>-0.491455</td>
      <td>0.222179</td>
      <td>-0.549559</td>
      <td>0.827584</td>
      <td>3</td>
      <td>4</td>
    </tr>
    <tr>
      <th>six</th>
      <td>0.532381</td>
      <td>-0.719393</td>
      <td>1.413606</td>
      <td>-0.070122</td>
      <td>3</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['g'] = pd.Series([4,5,6,7],index = ['one','three','five','seven'])
```


```python
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>state</th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
      <th>e</th>
      <th>f</th>
      <th>g</th>
    </tr>
    <tr>
      <th>year</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>-0.333815</td>
      <td>0.249480</td>
      <td>-1.715385</td>
      <td>-0.770067</td>
      <td>3</td>
      <td>0</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>two</th>
      <td>-0.425955</td>
      <td>0.156519</td>
      <td>0.313454</td>
      <td>0.661829</td>
      <td>3</td>
      <td>1</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>three</th>
      <td>-0.003607</td>
      <td>0.676290</td>
      <td>2.260861</td>
      <td>1.626270</td>
      <td>3</td>
      <td>2</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>four</th>
      <td>0.514988</td>
      <td>0.179730</td>
      <td>1.586553</td>
      <td>-0.725601</td>
      <td>3</td>
      <td>3</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>five</th>
      <td>-0.491455</td>
      <td>0.222179</td>
      <td>-0.549559</td>
      <td>0.827584</td>
      <td>3</td>
      <td>4</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>six</th>
      <td>0.532381</td>
      <td>-0.719393</td>
      <td>1.413606</td>
      <td>-0.070122</td>
      <td>3</td>
      <td>5</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
del df['g']
```


```python
zd ={'one':{'a' : 12, 'b' : 13},
     'two':{'a' : 34, 'c' : 36}}
data = pd.DataFrame(zd)
```


```python
data
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>one</th>
      <th>two</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>a</th>
      <td>12.0</td>
      <td>34.0</td>
    </tr>
    <tr>
      <th>b</th>
      <td>13.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>c</th>
      <td>NaN</td>
      <td>36.0</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
