---
layout: post
title: Recursion
# subtitle:  Neutron Network and Deep Learning
date: 2017-12-29
published: True
mathjax: True
catalog: true
tags:
  - data structure & algorithms
---
## TOC
1. Searching
{:toc}

# Introduction

递归思想是很重要的思想, 之前作为小白的我理解起来感觉很吃力. 之后参考了几本书和leetcode上的题目, 终于有所收获.

递归思想需要和[动态规划](http://blog.csdn.net/guohua1992/article/details/79389348)对比着看. 动态规划相当于把递归过程转化成里循环过程. 同时递归思想和分治法又密不可分.

在[Python Algorithm](https://www.goodreads.com/book/show/9537756-python-algorithms)一书中有很精彩的解释, 这本书中一个很重要思想就是把一个问题看成一个**归纳问题**:
1. 假设T(n)成立, 我如何推到T(n-1)(弱假设)或者T(n/2)(强假设) $\longrightarrow$ 递归
2. 假设T(n-1)或T(n/2)成立, 如何推到T(n)  $\longrightarrow$ 循环构成的动态规划

{:toc}

# The three laws of recursion

+ A recursive algorithm must have a **base case**
+ A recursive algorithm must **change its state and more toward the base case**
+ A recursive algorithm must **call itself, recursively**

# Understand recursion

## Example of recursion:

### **Coverting an integer to a string in any base**


```python
def toStr(n,base):
   convertString = "0123456789ABCDEF"
   if n < base:
      return convertString[n]
   else:
      return toStr(n//base,base) + convertString[n%base]

print(toStr(1453,16))
```

Workflow of the function above:


<img src='/img/deep_learning_course/recursion_workflow.png', style='90%'>

### How python implement recursion: *stack frame*

When a function is called in Python:

+ a stack frame is allocated to handle the local variables of the functions
+ when the function returns, the return value is left on top of the stack for the calling function to access

<img src='/img/deep_learning_course/recursion_python.png' width=400>

这就解释了在很多问题中可以通过栈的数据结构来将递归问题转化为循环, 比如[树的遍历]()

# Visualizing Recursion

若下面代码无法执行，参照链接[tree example](http://interactivepython.org/runestone/static/pythonds/Recursion/pythondsintro-VisualizingRecursion.html)和[Sierpinski triangle](http://interactivepython.org/runestone/static/pythonds/Recursion/pythondsSierpinskiTriangle.html)

## Tree Example


```python
import turtle

def tree(branchLen,t):
    if branchLen > 5:
        t.forward(branchLen)
        t.right(20)
        tree(branchLen-15,t)
        t.left(40)
        tree(branchLen-15,t)
        t.right(20)
        t.backward(branchLen)

def main():
    t = turtle.Turtle()
    myWin = turtle.Screen()
    t.left(90)
    t.up()
    t.backward(100)
    t.down()
    t.color("green")
    tree(75,t)
    myWin.exitonclick()

main()
```

## Sierpinski Triangle


```python
import turtle

def tree(branchLen,t):
    if branchLen > 5:
        t.forward(branchLen)
        t.right(20)
        tree(branchLen-15,t)
        t.left(40)
        tree(branchLen-15,t)
        t.right(20)
        t.backward(branchLen)

def main():
    t = turtle.Turtle()
    myWin = turtle.Screen()
    t.left(90)
    t.up()
    t.backward(100)
    t.down()
    t.color("green")
    tree(75,t)
    myWin.exitonclick()

main()

```

# Complex Recursion Problem

## Tower of Hanoi

Problem: Transfer all 64 disks from one of the three poles to another, with two important constraints:

+ only move one disk at a time
+ never place a larger disk on top of a smaller one



<img src ='/img/deep_learning_course/recursion_hanoi.png', style='100%'>


```python
def moveTower(height,fromPole, toPole, withPole):
    if height >= 1:
        moveTower(height-1,fromPole,withPole,toPole)
        moveDisk(fromPole,toPole)
        moveTower(height-1,withPole,toPole,fromPole)

def moveDisk(fp,tp):
    print("moving disk from",fp,"to",tp)

moveTower(3,"A","B","C")

```

    ('moving disk from', 'A', 'to', 'B')
    ('moving disk from', 'A', 'to', 'C')
    ('moving disk from', 'B', 'to', 'C')
    ('moving disk from', 'A', 'to', 'B')
    ('moving disk from', 'C', 'to', 'A')
    ('moving disk from', 'C', 'to', 'B')
    ('moving disk from', 'A', 'to', 'B')


## Dynamic Programming

动态编程（Dynamic Programming)

one strategy for some optimization problems(e.g optimize some value)

动态编程与分治法类似，其基本四项也是将求解问题分解为若干子问题，先求解子问题然后从这些子问题的解得到原问题的解。与分治法不同的是，适合于用动态规划求解的问题，*经分解得到子问题往往不是互相独立的*。若用分治法来解这类问题，则分解得到的子问题数目太多，有些子问题被重复计算了很多次。如果我们能够保存已解决的子问题的答案，而在需要时再找出已求得的答案，这样就可以避免大量的重复计算，节省时间。我们可以用一个表来记录所有已解的子问题的答案。不管该子问题以后是否被用到，只要它被计算过，就将其结果填入表中

Problem: making changes using the fewest coins

Solution(as shown in the figure below):

+ we start with one cent, the solution is one
+ 第二行，对于２，最少硬币数为２
+ 第五行，对于５，最少硬币数为５
+ 依次类推得到表

举例说，对于11,假设硬币面值为［１，５，１０］，有三种：

+ 11-1 = 10(1)(10对应的是１，总共２)
+ 11-5 = 6(2)(６对应２，总共３)
+ 11-10=1(1)(１对应１，总共２)

<img src='/img/deep_learning_course/recursion_dp.png' style='100%'>


```python
def dpMakeChange(coinValueList,change,minCoins,coinsUsed):
   for cents in range(change+1):
      coinCount = cents
      newCoin = 1
      for j in [c for c in coinValueList if c <= cents]:
            if minCoins[cents-j] + 1 < coinCount:
               coinCount = minCoins[cents-j]+1
               newCoin = j
      minCoins[cents] = coinCount
      coinsUsed[cents] = newCoin
   return minCoins[change]

def printCoins(coinsUsed,change):
   coin = change
   while coin > 0:
      thisCoin = coinsUsed[coin]
      print(thisCoin)
      coin = coin - thisCoin

def main():
    amnt = 63
    clist = [1,5,10,21,25]
    coinsUsed = [0]*(amnt+1)
    coinCount = [0]*(amnt+1)

    print("Making change for",amnt,"requires")
    print(dpMakeChange(clist,amnt,coinCount,coinsUsed),"coins")
    print("They are:")
    printCoins(coinsUsed,amnt)
    print("The used list is as follows:")
    print(coinsUsed)

main()

```

    ('Making change for', 63, 'requires')
    (3, 'coins')
    They are:
    21
    21
    21
    The used list is as follows:
    [1, 1, 1, 1, 1, 5, 1, 1, 1, 1, 10, 1, 1, 1, 1, 5, 1, 1, 1, 1, 10, 21, 1, 1, 1, 25, 1, 1, 1, 1, 5, 10, 1, 1, 1, 10, 1, 1, 1, 1, 5, 10, 21, 1, 1, 10, 21, 1, 1, 1, 25, 1, 10, 1, 1, 5, 10, 1, 1, 1, 10, 1, 10, 21]


总结：

感觉这个例子中dynamic programming的思想其实也类似与recursion的思想，在递归中，会引用已有的一段类似重复的代码，而在dynamic programming中，用表代替了那段代码

# Summry

+ Recursion can take the place of iteration in some cases.
+ Recursion is not always the answer. Sometimes a recursive solution may be more computationally expensive than an alternative algorithm
