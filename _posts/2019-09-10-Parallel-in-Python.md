---
layout: post
title: Parallel in Python
subtitle:
date: 2019-09-10
published: True
tags:
  - Python
  - multiprocess
  - multithread
---
# Process VS Thread
A process is an instance of program (e.g. Jupyter notebook, Python interpreter). Processes spawn threads (sub-processes) to handle subtasks like reading keystrokes, loading HTML pages, saving files. Threads live inside processes and share the same memory space.

**Scenarios fo multi-process and multi-thread**：

1. Processes speed up Python operations that are **CPU intensive** because they benefit from multiple cores and avoid the GIL.
2. Threads are best for **IO tasks** or tasks involving external systems because threads can combine their work more efficiently. Processes need to pickle their results to combine them which takes time.
3. Threads provide no benefit in python for CPU intensive tasks because of the GIL.

[Ref](https://medium.com/@bfortuner/python-multithreading-vs-multiprocessing-73072ce5600b)



# Concurrent & parallel （并发和并行）

1. 并行是并发的子集
2. 并发：不同任务同时进行
3. 并行：同task被分为subtask 然后并行执行

# Parallel in Python

python 3.2之前用 Multiprocess，Thread管理。python 3.2后用 concurent.future 管理， 有线程池和进程池。[参考链接](https://python-parallel-programmning-cookbook.readthedocs.io/zh_CN/latest/chapter4/02_Using_the_concurrent.futures_Python_modules.html)

## Python 并行序列化的问题
机器学习，实验验证效果过程中，出错如下：
```shell
TypeError: can't pickle _thread.RLock objects
```
### 之前代码如下
```python
class Validator:
    def __init__(self, model):
        # 初始化机器学习模型
        self.model = model
    
    def run(self, num):
        # 并行调用 self._single_run
    
    def _single_run(self):
        # 模型推断
        self.model.inference
        
if __name__ == "__main__":
    model = ml_model
    validator = Validator(model=model)
    validator.run()
    
```

### 原因
千辛万苦定位问题，主要原因为在并行之前，会用pickle模块将这个模型类进行序列化，然而可能这个模型类无法被序列化，于是出现这个问题。

[Ref](https://blog.csdn.net/weixin_41935140/article/details/81153611)

### 不太优雅的解决方式
目前采用的不太优雅的解决方案：
```python
# 初始化机器学习模型
model = ml_model

class Validator:
    def __init__(self):
        pass
    
    def run(self, num):
        # 并行调用 self._single_run

    def _single_run(self):
        # 模型推断
        model.inference

if __name__ == "__main__":
    validator = Validator(model=model)
    validator.run()
```

### concurent.future, multiprocess error when running on windows 
error：
```
concurrent.futures.process.BrokenProcessPool: A process in the process pool was terminated abruptly while the future was running or pending.
```
How fix:

Put the main() under `if __name__ == "__main__"`:

## Parellel and tensorflow
error:

Tensorflow hangs when initializing vairable in multi process setting

How to solve:

Put the follow code under `if __name__ == "main":`
```
mp.set_start_method("spawn:)
```

[Ref](https://github.com/tensorflow/tensorflow/issues/5448)

# Appendix
## concurent.future.ThreadPool, ProcessPool example

```
import concurrent.futures                                                                
import time                                                                              
number_list = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]                                            
                                                                                         
def evaluate_item(x):                                                                    
        # 计算总和，这里只是为了消耗时间                                                                
        result_item = count(x)                                                           
        # 打印输入和输出结果                                                                      
        return 1                                                                         
                                                                                         
def  count(number) :                                                                     
        for i in range(0, 10000000):                                                     
                i=i+1                                                                    
        return i * number                                                                
                                                                                         
if __name__ == "__main__":                                                               
        # 顺序执行                                                                           
        start_time = time.time()                                                         
        for item in number_list:                                                         
                print(evaluate_item(item))                                               
        print("Sequential execution in " + str(time.time() - start_time), "seconds")     
        # 线程池执行                                                                          
        start_time_1 = time.time()                                                       
        with concurrent.futures.ThreadPoolExecutor(max_workers=5) as executor:           
                futures = [executor.submit(evaluate_item, item) for item in number_list] 
                for future in concurrent.futures.as_completed(futures):                  
                        print(future.result())                                           
        print ("Thread pool execution in " + str(time.time() - start_time_1), "seconds") 
        # 进程池                                                                            
        start_time_2 = time.time()                                                       
        with concurrent.futures.ProcessPoolExecutor(max_workers=5) as executor:          
                futures = [executor.submit(evaluate_item, item) for item in number_list] 
                for future in concurrent.futures.as_completed(futures):                  
                        print(future.result())                                           
        print ("Process pool execution in " + str(time.time() - start_time_2), "seconds")
```