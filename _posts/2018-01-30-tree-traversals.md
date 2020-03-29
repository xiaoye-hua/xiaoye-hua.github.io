---
layout: post
title: Tree Traversals
# subtitle:  Neutron Network and Deep Learning
date: 2018-01-30
published: True
mathjax: True
catalog: true
tags:
  - data structure & algorithms
---


<h1>Table of Contents<span class="tocSkip"></span></h1>
<div class="toc"><ul class="toc-item"><li><span><a href="#定义树节点" data-toc-modified-id="定义树节点-1"><span class="toc-item-num">1&nbsp;&nbsp;</span>定义树节点</a></span></li><li><span><a href="#由前序，中序到后序" data-toc-modified-id="由前序，中序到后序-2"><span class="toc-item-num">2&nbsp;&nbsp;</span>由前序，中序到后序</a></span></li><li><span><a href="#由后序，中序到前序" data-toc-modified-id="由后序，中序到前序-3"><span class="toc-item-num">3&nbsp;&nbsp;</span>由后序，中序到前序</a></span></li></ul></div>

# 定义树节点

**一定要注意递归的思想**


```python
#定义node
class Node:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None
```

# 由前序，中序到后序

前：GDAFEMHZ

中：ADEFGHMZ


```python
preorder = 'GDAFEMHZ'
inorder = 'ADEFGHMZ'
preorder = [i for i in preorder]
inorder = [i for i in inorder]

# create_tree 和print_post 函数都不需要额外的记忆量

def create_tree(preorder, inorder):
    if len(preorder) == 0:
        return None
    root = Node(preorder[0])
    idx = inorder.index(preorder[0])
    root.left = create_tree(preorder[1:idx+1], inorder[0:idx])
    root.right = create_tree(preorder[idx+1:], inorder[idx+1:])
    return root



def print_post(root):
    if not root:
        return []
    res = []
    res += print_post(root.left)
    res += print_post(root.right)
    res += [root.value]
    return res

```


```python
## 测试print_post函数
a, b, c, d, e, f, g = [Node(i) for i in range(1, 8)]
a.left = b
a.right = c
b.left = d
b.right = e
c.left = f
c.right = g
print_post(a)
```




    [4, 5, 2, 6, 7, 3, 1]




```python
# 测试
root =  create_tree(preorder, inorder)
res = print_post(root)
print('Post order is : ', ''.join(res))
```

    Post order is :  AEFDHZMG


# 由后序，中序到前序

后：AEFDHZMG

中：ADEFGHMZ


```python
postorder = 'AEFDHZMG'
inorder = 'ADEFGHMZ'
postorder = [i for i in postorder]
inorder = [i for i in inorder]

# create_tree 和print_post 函数都不需要额外的记忆量

def create_tree(postorder, inorder):
    if len(postorder) == 0:
        return None
    root = Node(postorder[-1])
    idx = inorder.index(postorder[-1])
    root.left = create_tree(postorder[0:idx], inorder[0:idx])
    root.right = create_tree(postorder[idx:-1], inorder[idx+1:])
    return root



def print_pre(root):
    if not root:
        return []
    res = [root.value]
    res += print_pre(root.left)
    res += print_pre(root.right)
    return res

```


```python
## 测试print_pre函数
a, b, c, d, e, f, g = [Node(i) for i in range(1, 8)]
a.left = b
a.right = c
b.left = d
b.right = e
c.left = f
c.right = g
print_pre(a)
```




    [1, 2, 4, 5, 3, 6, 7]




```python
# 测试
root =  create_tree(postorder, inorder)
res = print_pre(root)
print('Pre order is : ', ''.join(res))
```

    Pre order is :  GDAFEMHZ
