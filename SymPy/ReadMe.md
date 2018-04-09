# SymPy

SymPy是一个符号计算的Python库。SymPy支持符号计算、高精度计算、模式匹配、绘图、解方程、微积分、组合数学、离散数学、几何学、概率与统计、物理学等方面的功能。

---
## 示例

```python
from sympy import integrate, log, exp, symbols, derive_by_array
x = symbols('x')
sigmoid = 1/(1+exp(-x))
sigmoid_derive = derive_by_array(sigmoid, x)
# 给定x计算y
sigmoid_derive.evalf(subs={x:0})
```

- sigmoid.ipynb
使用SymPy计算sigmoid函数和对应的导数，同时配合NumPy、Matplotlib计算和绘图。


---
# 参考链接

[Basic Operations](http://docs.sympy.org/latest/tutorial/basic_operations.html)

[SymPy教程](http://www.asmeurer.com/sympy_doc/dev-py3k/tutorial/tutorial.zh.html)
