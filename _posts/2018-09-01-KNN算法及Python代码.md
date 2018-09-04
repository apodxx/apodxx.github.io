---
layout: post
title: KNN算法及Python代码
date: 2018-09-01
tag: 机器学习
---

# KNN算法

KNN（K-Nearest Neighbor）工作原理：存在一个样本数据集合，也称为训练样本集，并且样本集中每个数据都存在标签，即我们知道样本集中每一数据与所属分类对应的关系。输入没有标签的数据后，将新数据中的每个特征与样本集中数据对应的特征进行比较，提取出样本集中特征最相似数据（最近邻）的分类标签。一般来说，我们只选择样本数据集中前k个最相似的数据，这就是k近邻算法中k的出处，通常k是不大于20的整数。最后选择k个最相似数据中出现次数最多的分类作为新数据的分类。

在计算两个对象特征之间的距离时，在这里采用的欧式距离即：
![](http://p0kzdnfmg.bkt.clouddn.com/18-9-4/24015253.jpg)

看到这个公式，相比你一定不会陌生，平面直角坐标系中求两点的距离常用的便是这个公式

## 代码实例

接下来我们便是对代码进行编写，在这里使用的是`jupyter`,使用的过的人都说好，使用它我们能更直观的看到输出结果，而且最终还能保存成markdown，html和pdf等形式

```python
from numpy import *
# 训练数据
train=array([[1,2],[3,4],[5,6],[7,8]])
# 测试数据
test=array([3,3])
# 欧氏距离计算方法[(x2-x1),(y2-y1)]
tileArr=tile(test,(train.shape[0],1))
diff=tileArr-train
print(tileArr)
diff
```

结果输出：

    [[3 3]
     [3 3]
     [3 3]
     [3 3]]
  
    array([[ 2,  1],
           [ 0, -1],
           [-2, -3],
           [-4, -5]])




```python
# 欧氏距离计算方法  1. 先求平方[(x2-x1),(y2-y1)]**2

sqdiff=diff**2
sqdiff
```


结果输出：

    array([[ 4,  1],
           [ 0,  1],
           [ 4,  9],
           [16, 25]], dtype=int32)




```python
# 欧氏距离计算方法 2. 再想加△x**2+△y**2

sum(sqdiff,axis=1)
```



结果输出：

    array([ 5,  1, 13, 41], dtype=int32)




```python
# 欧氏距离计算方法 3. 最后开方(△x**2+△y**2)**0.5

dist=sum(sqdiff,axis=1)**0.5

dist
```


结果输出：

    array([2.23606798, 1.        , 3.60555128, 6.40312424])


```python
# 对距离进行排序，结果以序号表示
sortedDistIndex=argsort(dist)
sortedDistIndex
```

结果输出：

    array([1, 0, 2, 3], dtype=int64)


```python
# 对类型进行归类 投票方式
type=['A','A','B','B']
classCount={}
for i in range(0,3):
    vote=type[sortedDistIndex[i]]
    classCount[vote]=classCount.get(vote,0)+1
classCount
```

    {'A': 2, 'B': 1}

```python
# 投票方式最多者为最终结果

import operator
sorted(classCount.items(),key=operator.itemgetter(1),reverse=True)
```

    [('A', 2), ('B', 1)]

```python
count=sorted(classCount.items(),key=operator.itemgetter(1),reverse=True)
count
```

    [('A', 2), ('B', 1)]

```python
count[0]
```

    ('A', 2)


```python
count[0][0]
```

结果输出：

    'A'


