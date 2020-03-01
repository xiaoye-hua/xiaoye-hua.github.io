---
layout: post
title: Searching
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

## Searching

+ 顺序查找　sequential search
+ 二分查找　binary search/img/deep_learning_course//img/deep_learning_course/
+ 哈希表和哈希查找　hashing


## Sequential search

Sequential search with *Unordered list*

<img src='/img/deep_learning_course/search_sequential.png' style='100%'>

... with *ordered list*:

<img src='/img/deep_learning_course/search_sequential_ordered.png', style='120%'>

## Binary search

The complexity is $O(log(n))$. It is important to note that for small values of n, the **additional cost of sorting** is probably **not worth** it.



```python
found = False

def recursionBinarySearch(alist, item):
    first = 0
    last = len(alist) - 1
    global found

    while first<= last and not found:
        mid = (first + last) // 2
        if alist[mid] == item:
            found = True
        elif alist[mid] > item:
            last = mid -1
            return recursionBinarySearch(alist[first:last], item)
        else:
            first = mid + 1
            return recursionBinarySearch(alist[first: last], item)
#         print('first', first, 'last', last)
    return found


testlist = [0, 1, 2, 8, 13, 17, 19, 32, 42,]
print(recursionBinarySearch(testlist, 3))
# print(binarySearch(testlist, 13))
```

    False


## Hashing

哈希表的搜索复杂度为O(1)，**Python中dictionary 和 set 是用哈希表实现的**．

### 哈希表

哈希表中每个位置被称为slot, 每个位置能容纳一个item，item的最初值为None,　每个位置都已从０开始数字命名．如下所示：

<img src='/img/deep_learning_course/hashing_slot.png' width=800>

### 哈希函数

哈希函数：根据给定的关键字，决定存储位置的函数。

基本原则：使得到的地址近可能多的均匀分布在给定空间

**解决冲突**
