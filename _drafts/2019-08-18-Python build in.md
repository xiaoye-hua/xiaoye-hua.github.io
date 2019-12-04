---
layout: post
title: Python build in
subtitle:
date: 2019-08-23
# category: 工具
tags:
  - Python
published: False
---

# *args & **kwargs
[链接](https://www.geeksforgeeks.org/args-kwargs-python/)

# abstrct base class (ABC)
What is abstract class and abstract method????
1. we can't instantiate an instance from
2. Abstract classes are classes that contain one or more abstract methods. An abstract method is a method that is declared, but contains no implementation.
2. A class that is derived from an abstract class cannot be instantiated unless all of its abstract methods are overridden.

abstract method and hook
1. we	use	abstract	methods	when	the	subclass	must	provide	the	implementatio
2. hook	is	used	when	it	is	optional	for	the	subclass	to	implement	it.

```
# template design pattern
from	abc	import	abstractmethod,	ABCMeta
class	Trip(metaclass=ABCMeta):
				@abstractmethod
				def	setTransport(self):
								pass
				@abstractmethod
				def	day1(self):
								pass
				@abstractmethod
				def	day2(self):
								pass
				@abstractmethod
				def	day3(self):
								pass
        # abstract method
        @abstractmethod
				def	returnHome(self):
								pass
				# hook
				def	itinerary(self):
								self.setTransport()
								self.day1()
								self.day2()
								self.day3()
								self.returnHome()
```
# 思考
1. pgfParser 可以做成template design pattern
2. game 要集成abstract class, 用kwargs
3.
