---
layout: post
title: matplotlib基础1
date: 2021-02-04
tag: 机器学习
---



```python
import matplotlib.pyplot as plt
import numpy as np
```


```python
x = [1,2,3,4]
y = [4,5,8,9]
y1 = [2,7,12,6]
```


```python
plt.subplot(2,1,1)
plt.plot(x,y)
plt.subplot(2,1,2)
plt.plot(x,y1)
plt.show()
```


![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3b17x3hej30ac070jre.jpg)



```python
plt.figure()     #创建新的图表
```




    <matplotlib.figure.Figure at 0x10d2f7c50>




```python
plt.figure(figsize=(8,8))#设置图形区域的大小
plt.subplot(2,3,1)
plt.plot(x,y)
plt.subplot(2,3,2)
plt.bar(x,y1)
plt.subplot(2,3,3)
plt.barh(x,y1)
plt.subplot(2,3,4)
plt.boxplot(y1)
plt.subplot(2,3,5)
plt.scatter(x,y1)
plt.subplot(2,3,6)
plt.pie(y1)
plt.show()
```


    <matplotlib.figure.Figure at 0x10d2f7c50>



![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3b1816pnj30dg0d1q34.jpg)



```python
plt.figure() 
plt.subplot(2,2,1)
plt.scatter(x,y)
plt.subplot(2,2,2)
plt.bar(x,y1)
plt.subplot(2,1,2)
plt.plot(x,y1)
plt.show()
```


![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3b1813prj30ac070748.jpg)



```python

```



```python
import matplotlib.pyplot as plt
import numpy as np
```

箱型图


```python
data = [23,22,23,45,22,34,23,26,24,25,28,36,34,23,21,26,39,42,37,27,20,18]
```


```python
plt.subplot(1,1,1) #图像中显示的是最小值 最大值 1/2 1/4 和3/4的数值分布情况
plt.boxplot(data)
plt.show()
```


![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3b2nti71j30ac070t8i.jpg)


直方图


```python
plt.subplot(1,1,1)
plt.hist(data)#显示各个区间的数值范围
plt.show()
```


![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3b2nrc0oj30a6070a9v.jpg)



```python
data = np.random.randn(1000)
plt.hist(data,bins = 50,color = 'red')

plt.show()
```


![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3b2nrk75j30ac070web.jpg)


饼图


```python
labels = 'Frogs', 'Hogs', 'Dogs', 'Logs'
sizes = [15, 30, 45, 10]
explode = (0, 0.1, 0, 0)  # 将某一块或者某几块突出出来 权重越大 凸出越大

plt.pie(sizes, explode=explode, labels=labels, autopct='%1.1f%%',
        shadow=True, startangle=90)
plt.axis('equal')  # Equal aspect ratio ensures that pie is drawn as a circle.

plt.show()
```


![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3b2o0yerj309w06mdfz.jpg)



```python
cols = ['c','m','r','b']
plt.pie(sizes,
        labels=labels,
        colors=cols,
        startangle=90,
        shadow= True,
        explode=(0,0.1,0,0),
        autopct='%1.1f%%')
plt.show()
```


![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3b2o766pj30a306mmx9.jpg)



```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```


```python

```

直方图,
直方图非常像条形图，倾向于通过将区段组合在一起来显示分布,主要用来显示数据分布情况


```python
import numpy as np
```


```python
x = np.random.randint(1,100,100)
bins = [0,10,20,30,40,50,60,70,80,90,100]

plt.hist(x, bins,rwidth=0.7)
plt.show()
```

散点图


```python
x = np.random.randint(1,10,50)
y = np.random.randint(1,10,50)

x1 = np.random.randint(11,20,50)
y2 = np.random.randint(11,20,50)

plt.scatter(x,y,label='one', color='g', s=25, marker="^")
plt.scatter(x1,y2,label='two', color='r', s=25, marker="o")

plt.xlabel('x')
plt.ylabel('y')
plt.title('i am title')
plt.legend()
plt.show()
```


![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3b2nwyprj30b007q0sp.jpg)



```python
fig, ax = plt.subplots()
ax.scatter(x,y, label='scatter exp', color='g', s=25, marker="^")
ax.set_xlabel('x_data', fontsize=15)
ax.set_ylabel('y_data', fontsize=15)
ax.set_title('scatter exp')
ax.grid(True)

plt.show()
```

饼图


```python
labels = 'Frogs', 'Hogs', 'Dogs', 'Logs'
sizes = [15, 30, 45, 10]
explode = (0, 0.1, 0, 0)  # only "explode" the 2nd slice (i.e. 'Hogs')

fig1, ax1 = plt.subplots()
ax1.pie(sizes, explode=explode, labels=labels, autopct='%1.1f%%',
        shadow=True, startangle=90)
ax1.axis('equal')  # Equal aspect ratio ensures that pie is drawn as a circle.

plt.show()
```

也可以向下面这样


```python
cols = ['c','m','r','b']
plt.pie(sizes,
        labels=labels,
        colors=cols,
        startangle=90,
        shadow= True,
        explode=(0,0.1,0,0),
        autopct='%1.1f%%')
plt.show()
```


```python
plt.style.available
```




    ['seaborn-notebook',
     'dark_background',
     'seaborn-bright',
     'seaborn-ticks',
     'seaborn-muted',
     'seaborn-deep',
     'seaborn-whitegrid',
     'bmh',
     'fivethirtyeight',
     'seaborn-dark-palette',
     'seaborn-paper',
     'seaborn-white',
     'seaborn-pastel',
     'seaborn-colorblind',
     'seaborn-talk',
     'seaborn-poster',
     'seaborn-dark',
     'ggplot',
     'grayscale',
     'classic',
     'seaborn-darkgrid']




```python
plt.style.use('ggplot')
plt.pie(sizes,
        labels=labels,
        colors=cols,
        startangle=90,
        shadow= True,
        explode=(0,0.1,0,0),
        autopct='%1.1f%%')
plt.show()
```


```python

```


面向对象绘图


```python
import matplotlib.pyplot as plt
import numpy as np
```


```python
x = np.random.randint(1,11,30)
y = np.random.randint(1,6,30)

y1 = y + 5

plt.figure(figsize=(8,6))

plt.scatter(x,y,label='one', color='g', s=25, marker="^")
plt.scatter(x,y1,label='two', color='r', s=25, marker="o")

x_ticks_label = ['one','two','three','four','five','six','seven','eight','nine','ten']
plt.xticks(np.arange(1,11),x_ticks_label,rotation = -70 ,fontsize = 14)

plt.xlabel('x')
plt.ylabel('y')
plt.title('i am title')
plt.legend()
plt.show()
```


![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3b60raq8j30dt0bpq31.jpg)



```python
fig, ax = plt.subplots()
ax.scatter(x,y, label='scatter exp', color='g', s=25, marker="^")
ax.scatter(x,y1, label='scatter exp', color='r', s=25, marker="o")
ax.set_xlabel('x_data', fontsize=15)
ax.set_ylabel('y_data', fontsize=15)
ax.set_title('scatter exp')
ax.grid(True)

plt.show()
```


![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3b60q18fj30aw07xglk.jpg)



```python
x = [1,2,3,4]
y = [4,5,8,9]
y1 = [3,6,2,5]
fig, ax = plt.subplots(2,2,figsize = (8,6))
ax[0][0].bar(x,y)
ax[0][0].bar(x,y1,bottom = y)
ax[0][1].barh(x,y)
ax[1][0].plot(x,y)
ax[1][1].scatter(x,y)
plt.tight_layout()     #避免过于拥挤
plt.show()
```


![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3b60vt6xj30fj0bs74c.jpg)



```python
plt.scatter?
```


```python

```
