---
layout: post
title: Tree and Tree Algorithms
# subtitle:  Neutron Network and Deep Learning
date: 2018-01-04
published: True
mathjax: True
catalog: true
tags:
  - data structure & algorithms
---
## TOC
1. Introduction
{:toc}

# Introduction
这篇文章主要介绍树相关算法, 首先介绍树的两种定义, 而后介绍树的遍历, 之后为二叉堆, 之后介绍的二叉搜索树, 然后时平衡树AVL树, 最后总结了四种map抽象数据结构的复杂度.

# Definition of Tree

树的定义有两个,一个是普通定义, 一个是递归的定义:
1. 普通版: 树由节点和边组成, 一个树有以下定义:.....(按住不表)
2. **递归版: 一个树要么是空的, 要么由根和0个或几个子树构成, 每个子树都是一个树**

**注意:**

递归版定义在后面树算法中很有用处, 树的定义都是从递归开始的, 可见**递归思想**在树算法中的重要作用.

Binary tree
--


```python
class BinaryTree:
    def __init__(self,rootObj):
        self.key = rootObj
        self.leftChild = None
        self.rightChild = None

    def insertLeft(self,newNode):
        if self.leftChild == None:
            self.leftChild = BinaryTree(newNode)
        else:
            t = BinaryTree(newNode)
            t.leftChild = self.leftChild
            self.leftChild = t

    def insertRight(self,newNode):
        if self.rightChild == None:
            self.rightChild = BinaryTree(newNode)
        else:
            t = BinaryTree(newNode)
            t.rightChild = self.rightChild
            self.rightChild = t


    def getRightChild(self):
        return self.rightChild

    def getLeftChild(self):
        return self.leftChild

    def setRootVal(self,obj):
        self.key = obj

    def getRootVal(self):
        return self.key


r = BinaryTree('a')
print(r.getRootVal())
print(r.getLeftChild())
r.insertLeft('b')
print(r.getLeftChild())
print(r.getLeftChild().getRootVal())
r.insertRight('c')
print(r.getRightChild())
print(r.getRightChild().getRootVal())
r.getRightChild().setRootVal('hello')
print(r.getRightChild().getRootVal())

```

    a
    None
    <__main__.BinaryTree instance at 0x7fc697b69e18>
    b
    <__main__.BinaryTree instance at 0x7fc697b69d40>
    c
    hello


Parse Tree(语义树)
--
Parse tree can be used to represent real-world constructions like **sentences or mathematicals**

这个二叉树只适用于括号尽量在右边的，即二叉树想下延伸的。而对于括号在前面或中间都是不行的。


```python
from tools import Stack, BinaryTree

def buildParseTree(fpexp):
    fpexp = fpexp.split()
    eTree = BinaryTree('')
    pStack = Stack()
    pStack.push(eTree)
    currentTree = eTree
    for item in fpexp:
        if item == "(":
            currentTree.insertLeft('')
            pStack.push(currentTree)
            currentTree = currentTree.getLeftChild()
        elif item in  ['+','-','/','*']:
            currentTree.setRootVal(item)
            currentTree.insertRight('')
            pStack.push(currentTree)
            currentTree = currentTree.getRightChild()
        elif item not in ['+','-','/','*', ')']:
#             print(item)
            currentTree.setRootVal(int(item))
            parent = pStack.pop()
            currentTree = parent
        elif item == ')':
            parent = pStack.pop()
            currentTree = parent
        else:
#             print(item)
            raise ValueError
    return eTree

pt = buildParseTree("( ( 10 + 5 ) * 3 )")

```

# Tree Traversals

**二叉树的遍历**
1. 先序遍历
    + 访问根节点
    + 先序遍历左子树
    + 先序遍历右子树
2. 中序遍历
    + 中序遍历左子树
    + 访问根节点
    + 中序遍历右子树
3. 后序遍历
    + 后序遍历左子树
    + 后序遍历右子树
    + 访问根节点

在[递归思想]()那一节中, 我们提到了**递归和循环的转换**, 下面给出两个版本的遍历:

递归版本遍历
--


```python
def preorder(tree):
    if tree:
        print(tree.getRootVal())
        preorder(tree.getLeftChild())
        preorder(tree.getRightChild())

def inorder(tree):
    if tree:
        inorder(tree.getLeftChild())
        print(tree.getRootVal())
        inorder(tree.getRightChild())

def postorder(tree):
    if tree:
        postorder(tree.getLeftChild())
        postorder(tree.getRightChild())
        print(tree.getRootVal())
```

循环版本遍历
--

根据leetcode中题目所得, 都是用栈的数据结构来实现遍历, 以下先给出先序遍历的循环版本


```python
# preorder
class Solution(object):
    def preorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        res = []
        stack = []
        while stack or root :
            if root:
                stack.append(root)
                res.append(root.val)
                root = root.left
            else:
                tempNode = stack.pop()
                # res.append()
                root = tempNode.right
        return res
```

# Implementing Priority Queue with Binary Heap

Queue is a fist-in first-out data structure. priority queue is a variation of queue in which the logic order of item is determined by its priority. 
We can use binary heap to implement priority queue, which will allow us both enqueue and dequeue items in $O(logn)

## Heap

To implement binary heap, we need **complete binary tree**. In complete binary tree

heap property:
    1. structure property: complete binary tree (all levels are full of nodes except for the last level, in which we fill from left to right)
        1. 2p and 2p+1 between parent and children
    2. order property: parent is no smaller than (no bigger than) children

Two types of heaps:
1. min heap: the smallest key is always at the front
2. max heap: the largest key is always at the front

如下，二叉堆第一个元素为0：
<img src='/img/deep_learning_course/heapList.png' width='800'>

```python
class MinHeap:
    def __init__(self, list_input=False):
        """
        heap property:
            1. structure property:
                complete tree, 2p and 2p+1 between parent and children
            2. order property:
                parent is smaller that children

        list_input: whether the input value is a list, if True, the first element of the list will be the key
        """
        self.lst = [0]
        self.size = 0  # size of heap
        self.list_input = list_input

    def push(self, value):
        self.lst.append(value)
        self.size += 1
        self.prec_up(self.size)

    def pop(self):
        min_value = self.lst.pop(1)
        self.size -= 1
        self.lst.insert(1, self.lst.pop())
        self.prec_down(1)
        return min_value

    def build_heap(self, lst):
        """
        Two methods to build from a entire list:
            1. iterate and insert one by one：　O(nlogn)
            2. start with the entire list: O(n)
        """
        i = len(lst) // 2
        self.lst = [0] + lst[:]
        self.size = len(lst)
        while i >= 0:
            self.prec_down(i)
            i -= 1

    def prec_up(self, i):
        if self.list_input:
            while i//2>0:
                idx = i//2
                if self.lst[idx][0] >= self.lst[i][0]:
                    self.lst[idx], self.lst[i] = self.lst[i], self.lst[idx]
                else:
                    return
                i = idx
        else:
            while i//2>0:
                idx = i//2
                if self.lst[idx] >= self.lst[i]:
                    self.lst[idx], self.lst[i] = self.lst[i], self.lst[idx]
                else:
                    return
                i = idx

    def prec_down(self, i):
        if self.list_input:
            while 2 * i <= self.size:
                idx = self.min_child(i)
                if self.lst[idx][0] <= self.lst[i][0]:
                    self.lst[idx], self.lst[i] = self.lst[i], self.lst[idx]
                    i = idx
                else:
                    return
        else:
            while 2*i <= self.size:
                idx = self.min_child(i)
                if self.lst[idx] <= self.lst[i]:
                    self.lst[idx], self.lst[i] = self.lst[i], self.lst[idx]
                    i = idx
                else:
                    return

    def min_child(self, i):
        if 2*i+1 > self.size:
            return 2*i
        if self.list_input:
            if self.lst[2 * i][0] < self.lst[2 * i + 1][0]:
                return 2 * i
            else:
                return 2 * i + 1
        else:
            if self.lst[2*i] < self.lst[2*i+1]:
                return 2*i
            else:
                return 2*i + 1
```

TODO: The complexity build_heap is O(n) ?

Refer to [Sorting Algorithms](https://xiaoye-hua.github.io/2017/12/29/%E6%8E%92%E5%BA%8F%E7%AE%97%E6%B3%95%E6%80%BB%E7%BB%93/) for heap sorting. 

# 二叉树搜索(Binary search tree)

可以实现map ADT 的方式：
1. hash tables
2. binary search on a list
3. binary search trees

map ADT的操作：
<img src='/img/deep_learning_course/mapADT.png' width='800'>


**搜索二叉树性质**: left subtree < root < right subtree

复杂度分析：对于put函数来说，复杂度介于O(logn)和O(n)之间。


```python
class TreeNode:
    def __init__(self,key,val,left=None,right=None,parent=None):
        self.key = key
        self.payload = val
        self.leftChild = left
        self.rightChild = right
        self.parent = parent

    def hasLeftChild(self):
        return self.leftChild

    def hasRightChild(self):
        return self.rightChild

    def isLeftChild(self):
        return self.parent and self.parent.leftChild == self

    def isRightChild(self):
        return self.parent and self.parent.rightChild == self

    def isRoot(self):
        return not self.parent

    def isLeaf(self):
        return not (self.rightChild or self.leftChild)

    def hasAnyChildren(self):
        return self.rightChild or self.leftChild

    def hasBothChildren(self):
        return self.rightChild and self.leftChild

    def replaceNodeData(self,key,value,lc,rc):
        self.key = key
        self.payload = value
        self.leftChild = lc
        self.rightChild = rc
        if self.hasLeftChild():
            self.leftChild.parent = self
        if self.hasRightChild():
            self.rightChild.parent = self


class BinarySearchTree:

    def __init__(self):
        self.root = None
        self.size = 0

    def length(self):
        return self.size

    def __len__(self):
        return self.size

    def put(self,key,val):
        if self.root:
            self._put(key,val,self.root)
        else:
            self.root = TreeNode(key,val)
        self.size = self.size + 1

    def _put(self,key,val,currentNode):
        if key < currentNode.key:
            if currentNode.hasLeftChild():
                   self._put(key,val,currentNode.leftChild)
            else:
                   currentNode.leftChild = TreeNode(key,val,parent=currentNode)
        else:
            if currentNode.hasRightChild():
                   self._put(key,val,currentNode.rightChild)
            else:
                   currentNode.rightChild = TreeNode(key,val,parent=currentNode)

    def __setitem__(self,k,v):
       self.put(k,v)

    def get(self,key):
       if self.root:
           res = self._get(key,self.root)
           if res:
                  return res.payload
           else:
                  return None
       else:
           return None

    def _get(self,key,currentNode):
       if not currentNode:
           return None
       elif currentNode.key == key:
           return currentNode
       elif key < currentNode.key:
           return self._get(key,currentNode.leftChild)
       else:
           return self._get(key,currentNode.rightChild)

    def __getitem__(self,key):
       return self.get(key)

    def __contains__(self,key):
       if self._get(key,self.root):
           return True
       else:
           return False

    def delete(self,key):
      if self.size > 1:
         nodeToRemove = self._get(key,self.root)
         if nodeToRemove:
             self.remove(nodeToRemove)
             self.size = self.size-1
         else:
             raise KeyError('Error, key not in tree')
      elif self.size == 1 and self.root.key == key:
         self.root = None
         self.size = self.size - 1
      else:
         raise KeyError('Error, key not in tree')

    def __delitem__(self,key):
       self.delete(key)

    def spliceOut(self):
       if self.isLeaf():
           if self.isLeftChild():
                  self.parent.leftChild = None
           else:
                  self.parent.rightChild = None
       elif self.hasAnyChildren():
           if self.hasLeftChild():
                  if self.isLeftChild():
                     self.parent.leftChild = self.leftChild
                  else:
                     self.parent.rightChild = self.leftChild
                  self.leftChild.parent = self.parent
           else:
                  if self.isLeftChild():
                     self.parent.leftChild = self.rightChild
                  else:
                     self.parent.rightChild = self.rightChild
                  self.rightChild.parent = self.parent

    def findSuccessor(self):
      succ = None
      if self.hasRightChild():
          succ = self.rightChild.findMin()
      else:
          if self.parent:
                 if self.isLeftChild():
                     succ = self.parent
                 else:
                     self.parent.rightChild = None
                     succ = self.parent.findSuccessor()
                     self.parent.rightChild = self
      return succ

    def findMin(self):
      current = self
      while current.hasLeftChild():
          current = current.leftChild
      return current

    def remove(self,currentNode):
         if currentNode.isLeaf(): #leaf
           if currentNode == currentNode.parent.leftChild:
               currentNode.parent.leftChild = None
           else:
               currentNode.parent.rightChild = None
         elif currentNode.hasBothChildren(): #interior
           succ = currentNode.findSuccessor()
           succ.spliceOut()
           currentNode.key = succ.key
           currentNode.payload = succ.payload

         else: # this node has one child
           if currentNode.hasLeftChild():
             if currentNode.isLeftChild():
                 currentNode.leftChild.parent = currentNode.parent
                 currentNode.parent.leftChild = currentNode.leftChild
             elif currentNode.isRightChild():
                 currentNode.leftChild.parent = currentNode.parent
                 currentNode.parent.rightChild = currentNode.leftChild
             else:
                 currentNode.replaceNodeData(currentNode.leftChild.key,
                                    currentNode.leftChild.payload,
                                    currentNode.leftChild.leftChild,
                                    currentNode.leftChild.rightChild)
           else:
             if currentNode.isLeftChild():
                 currentNode.rightChild.parent = currentNode.parent
                 currentNode.parent.leftChild = currentNode.rightChild
             elif currentNode.isRightChild():
                 currentNode.rightChild.parent = currentNode.parent
                 currentNode.parent.rightChild = currentNode.rightChild
             else:
                 currentNode.replaceNodeData(currentNode.rightChild.key,
                                    currentNode.rightChild.payload,
                                    currentNode.rightChild.leftChild,
                                    currentNode.rightChild.rightChild)




mytree = BinarySearchTree()
mytree[3]="red"
mytree[4]="blue"
mytree[6]="yellow"
mytree[2]="at"

print(mytree[6])
print(mytree[2])

```

    yellow
    at


# 平衡二叉树-AVL Tree

**通过不断调整树的balanceFactor来生成平衡的树，进而提高树的效率。**

Unbalanced Tree $\rightarrow$ performance degrade to O(n) $\rightarrow$ AVL tree

**平衡因子(Balance factor)**:

balanceFactor = height(leftsubtree) - height(rightsubtree)

balanceFactor = 0, 1, -1  $\rightarrow$ balance tree

AVL Tree
--
添加节点后，由节点的**左右**来更新(调整歪斜等)父节点的balanceFator

Left Rotation
--
如下图(右旋转类似)：
1. 将右节点B作为新的root
2. 将原来的rootA变为B的左孩子
1. 若B有左孩子，将其作为A的右孩子
<img src='/img/deep_learning_course/leftRotation.png' width='600'>

Balance factor of -2
--
如下图，
<img src='/img/deep_learning_course/balance2.png' width='400'>
解决办法：
1. 如果需要左旋转，先验证其右孩子是否向左偏重
2. 若是，则对其右孩子进行右旋转，然后对其进行左旋转
<img src='/img/deep_learning_course/balance22.png' width='800'>
代码如下：

    def rebalance(self,node):
        if node.balanceFactor < 0:
             if node.rightChild.balanceFactor > 0:
                self.rotateRight(node.rightChild)
                self.rotateLeft(node)
             else:
                self.rotateLeft(node)
        elif node.balanceFactor > 0:
             if node.leftChild.balanceFactor < 0:
                self.rotateLeft(node.leftChild)
                self.rotateRight(node)
             else:
                self.rotateRight(node)



还有一类平衡二叉树为[红黑树]()

# Summary of Map ADT

下面总结了四种map抽象数据结构的复杂度: 二分搜索的list, hash table, 二叉搜索树, 平衡树

<img src='/img/deep_learning_course/map.png' width='800'>
