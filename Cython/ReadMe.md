# Cython

---
## 类型声明

- 语法
```cython
def some_function(some_type some_parameter):
    cdef another_type variable
```
- 严格的变量和参数类型
- 去除boxes

根据这个语法

```python
# python写法
def step_time(planet, time_span, n_steps):
    """Make a number of time steps forward """
    
    dt = time_span / n_steps
    for j in xrange(n_steps):
        single_step(planet, dt)
```
```cython
# cython写法        
def step_time(planet, double time_span, int n_steps):
    """Make a number of time steps forward """
    cdef double dt
    cdef int j
    dt = time_span / n_steps
    for j in xrange(n_steps):
        single_step(planet, dt)
```

---
## 类的类型声明

- 严格的成员变量类型和方法
根据这个语法

```python
# python写法
class Planet(object):
    def __init__(self):
        # Some initial position and velocity
        self.x = 1.0
        self.y = 0.0
        self.z = 0.0
        self.vx = 0.0
        self.vy = 0.5
        self.vz = 0.0
        
        # Some mass
        self.m = 1.0
```
```cython
# cython写法        
cdef class Planet(object):
    cdef public double x, y, z, vx, vy, vz, m
    
    def __init__(self):
        # Some initial position and velocity
        self.x = 1.0
        self.y = 0.0
        self.z = 0.0
        self.vx = 0.0
        self.vy = 0.5
        self.vz = 0.0
        
        # Some mass
        self.m = 1.0
```
---
## 函数声明
语法：
- 去除Python-specific函数
```cython
def some_function(int a, int b):
    """能被Cython和Python同时调用"""
    ...
cdef some_function(int a, int b):
    """仅仅被Cython调用"""
    ...
cpdef some_function(int a, int b):
    """同时被Cython（优化过）和Python（未优化）调用"""
    ...
```

---
## 和C交互
我们能使用标准的C代码库进行计算。

```cython
cdef extern from "math.h":
    double sin(double x)
```

---
## 解放GIL
克服多线程问题：解放Cython中的GIL
```cython
cdef extern from "math.h":
    double sin(double x) nogil
```

---
## 总结

通过以上方式，Cython实现了下述特性：
- 通过使用```cdef some_type```和```cdef class```去除了boxing操作
- 通过```cdef some_function```去除了函数调用
- 通过使用```cdef extern from```调用某些C函数
- 使用nogil去除GIL运行多线程

---
## Cython和NumPy

```cython
import numpy as np
cimport numpy as np
cdef np.ndarray[np.double_t, ndim=2] some_array
some_array = np.zeros((50, 50), dtype=np.double)
```

---
## 参考资料

[Cython 入门教程](https://charlesnord.github.io/2017/03/11/cython-tuto/)

[Cython tutorial](https://python.g-node.org/python-summerschool-2011/_media/materials/cython/cython-slides.pdf)

[cython/Demos](https://github.com/cython/cython/tree/master/Demos) cython github仓库中的Demos。

[Cython Basic Tutorial](http://cython.readthedocs.io/en/latest/src/tutorial/cython_tutorial.html) Cython官方教程。
