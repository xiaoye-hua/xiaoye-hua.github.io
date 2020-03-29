---
layout: post
title: Breadth First Search (BFS) & Depth First Search (DFS)
# subtitle:  Neutron Network and Deep Learning
date: 2018-02-01
published: True
mathjax: True
catalog: true
tags:
  - data structure & algorithms
---

<h1>Table of Contents<span class="tocSkip"></span></h1>
<div class="toc"><ul class="toc-item"><li><span><a href="#图" data-toc-modified-id="图-1"><span class="toc-item-num">1&nbsp;&nbsp;</span>图</a></span></li><li><span><a href="#算法" data-toc-modified-id="算法-2"><span class="toc-item-num">2&nbsp;&nbsp;</span>算法</a></span></li><li><span><a href="#实现" data-toc-modified-id="实现-3"><span class="toc-item-num">3&nbsp;&nbsp;</span>实现</a></span></li></ul></div>

# 图

以下面有向图为例, 以字典来表示这个图, 如下:


```python
a, b, c, d, e, f = '1', '2', '3', '4', '5', '6'
g = {a: [b, d], b:[c, d], c:[], d:[e], e:[b, f], f:[c]}
```

<img src='/img/deep_learning_course/BFS_DFS.png' width='800'>

# 算法

**Go and check leetcode problem num 102**

BFS用队列实现, DFS用栈实现. 由于栈和递归特殊的关系, DFS也可以用递归实现, 当然一般用递归实现.

**BFS**
通俗讲为从初始顶点开始, 先访问所有距离为1的顶点, 然后再访问所有距离为2的顶点(先被访问顶点的临节点要比后被访问节点临节点先访问)....

结果为: 1, 2, 4, 3, 5, 6

**DFS**
通俗讲为从初始顶点开始, 把一个分支访问完之后再访问下个分支...

结果为: 1, 2, 3, 4, 5, 6

# 实现

**BFS**

用queue实现


```python
def BFS(g, begin_point):
    visted = []
    queue = [begin_point]
    while len(queue) !=0:
        pop = queue.pop(0)
        if pop in visted:
            continue
        else:
            visted.append(pop)
        for next_point in g[pop]:
            if next_point not in visted:
                queue.append(next_point)
    print(visted)
```


```python
BFS(g, a)
```

    ['1', '2', '4', '3', '5', '6']


**DFS**

用栈实现


```python
def DFS(g, begin_point):
    visted = []
    stack = [begin_point]
    while len(stack) != 0:
        pop = stack.pop()
        if pop in visted:
            continue
        else:
            visted.append(pop)

#         lst = g[pop]
#         print('lst', lst)
#         print(type(lst))
#         print('lst reverse', lst.reverse())
#         r = lst.reverse()
        for next_point in list(reversed(g[pop])):
            if next_point not in visted:
                stack.append(next_point)

#         print('stack', stack)
#         print('visted', visted)
    print(visted)
```


```python
DFS(g, a)
```

    ['1', '2', '3', '4', '5', '6']


用递归实现


```python
visited = []
def DFS_r(g, begin_point):
    visited.append(begin_point)
    if len(visited) == len(g):
        return
    for next_point in g[begin_point]:
        if next_point not in visited:
            DFS_r(g, next_point)
```


```python
DFS_r(g, a)
visited
```




    ['1', '2', '3', '4', '5', '6']
