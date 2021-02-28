---
layout: post
title: matplotlib基础1
date: 2021-02-04
tag: 机器学习
---



# python数据可视化 - Matplotlib快速简明教程

MATPLOTLIB是一个强大的绘图工具，能满足几乎所有的2D和一些3D绘图的需求。matplotlib是python科学计算中最基础、最重要的绘图库，一般使用matpltlib完全可以满足我们绘图需求，当然现在也出现了seaborn这样的构建在matplotlib之上绘图库，能够一定程度上简化我们绘图过程。但是他的基础还是matplotlib，所有利用python进行数据分析可视化，学习matplotlib是必须要打的基础。

matplotlib安装

推荐安装anaconda，matplotlib依赖numpy等等软件包，自己安装相对复杂

（一）导入matplotlib


```python
import matplotlib.pyplot as plt
```

下面我将使用例子来演示和讲解matplotlib绘图的技巧。

线图的画法，使用plt.plot


```python
x = [1,2,3,4]
y = [4,5,8,9]
plt.plot(x,y)
plt.show()       #这里要学会看图
```


![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3ag1qzzrj30a6070q2v.jpg)



```python
y = [4,5,8,9]
plt.plot(y)
plt.show()  
```


![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3ag1qiwlj30a6070t8n.jpg)



```python
x = [1,2,3,4]
y = [4,5,8,9]
y1 = [2,7,12,6]
plt.plot(x,y)
plt.plot(x,y1)
plt.show()  
```


![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3ag26m3pj30ac070aa3.jpg)



```python
plt.bar(x,y1)
plt.show()
```


![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3ag1u3xhj30ac070a9v.jpg)



```python
plt.bar(x,y)
plt.bar(x,y1,bottom=y)
plt.show()
```


![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3ag1zdhtj30am070glg.jpg)



```python
plt.barh(x,y1)
plt.show()
```


![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3ag1xz4xj30af070744.jpg)



```python
plt.scatter(x,y1)
plt.show()
```


![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3ag22ypfj30ac070dfn.jpg)



```python
plt.subplot(2,1,1)
plt.plot(x,y)
plt.subplot(2,1,2)
plt.plot(x,y1)
plt.show()
```


![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3ag2jmjmj30ac070jre.jpg)



```python
plt.figure()     #创建新的图表
```




    <matplotlib.figure.Figure at 0x119188a58>




```python
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


![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3ag2e41rj30ac070mx4.jpg)



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


![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3ag31lanj30ac070748.jpg)



```python

```


```python
plt.figure
```




    <function matplotlib.pyplot.figure>




```python
x = [1,2,3,4]
y = [4,5,8,9]

x1 = [1,2,3,4]
y1 = [5,9,12,14]

plt.plot(x,y,label = 'line one')
plt.plot(x1,y1,label = 'line two')
plt.xlabel('x_data')
plt.ylabel('y_data')
plt.title('title is here!')

plt.legend(loc=0)   #可选位置参数loc，0是最优
plt.show() 
```


![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3ag37wu9j30ar07rglo.jpg)


matplotlib图标正常显示中文


```python
import matplotlib.pyplot as plt
plt.rcParams['font.sans-serif']=['SimHei'] #用来正常显示中文标签
plt.rcParams['axes.unicode_minus']=False #用来正常显示负号
```


```python
x = [1,2,3,4]
y = [4,5,8,9]

x1 = [1,2,3,4]
y1 = [5,9,12,14]

plt.plot(x,y,label = 'line one')
plt.plot(x1,y1,label = 'line two')
plt.xlabel('x坐标')
plt.ylabel('y坐标')
plt.title('一个漂亮的图标!')

plt.legend(loc=0)   #可选位置参数loc，0是最优
plt.show() 
```

    /Users/apodx/anaconda/lib/python3.6/site-packages/matplotlib/font_manager.py:1297: UserWarning: findfont: Font family ['sans-serif'] not found. Falling back to DejaVu Sans
      (prop.get_family(), self.defaultFamily[fontext]))



![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3ag2kh8dj30aq07qq2z.jpg)


叠加画


```python
import numpy as np
# evenly sampled time at 200ms intervals
t = np.arange(0., 5., 0.2)
 
# red dashes, blue squares and green triangles
plt.plot(t, t, 'r--', t, t**2, 'bs', t, t**3, 'g^')
plt.show()
```

    /Users/apodx/anaconda/lib/python3.6/site-packages/matplotlib/font_manager.py:1297: UserWarning: findfont: Font family ['sans-serif'] not found. Falling back to DejaVu Sans
      (prop.get_family(), self.defaultFamily[fontext]))



![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3ag2zztej30ai070wed.jpg)



```python
import matplotlib.pyplot as plt
import numpy as np
```

设置图标的线型、属性、格式化字符串


```python
y = np.random.randn(10).cumsum()
```


```python
plt.plot(y,linewidth=2,color='r',linestyle='--',marker='o')    #lw , c, ls
plt.show()
```


![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3ayzmwywj30ao0700sq.jpg)



```python
y1 = np.random.randn(10).cumsum()
x = np.arange(10)
```


```python
plt.plot(x,y,'b-o',x,y1,'r--^')
plt.title('values for y and y1')
plt.xlabel('x')
plt.ylabel('y and y1')
plt.show()
```


![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3ayzooeaj30b207qdfz.jpg)


正弦和余弦函数


```python
x = np.linspace(-np.pi,np.pi,256,endpoint = True)
y = np.sin(x)
y1 = np.cos(x)
plt.plot(x,y,label = 'sin')
plt.plot(x,y1,label = 'cos')

plt.title('Function sin & cos')
#plt.xlim(-3.5,3.5)
#plt.ylim(-1,1) xy的范围
plt.xticks([-np.pi,0,np.pi],[r'$-\pi$',0,r'$+\pi$'])#设置一下特殊的刻度，两个列表第一个表示在那些位置，第二个表示该位置的样式
plt.axis([-3.2,3.2,-1.1,1.1])#设置刻度最小值和最大值
plt.grid()
plt.legend(loc = 0)

plt.show()
```


![png](http://ww1.sinaimg.cn/large/007Rg09mly1go3ayzoz6cj30aw07dt8z.jpg)



```python

```

