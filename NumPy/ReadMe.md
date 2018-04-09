# NumPy

NumPy是Python语言的一个扩充程序库，支持高维数组和矩阵运算，也提供大量数学函数库。本质上，NumPy与MATLAB都是利用BLAS与LAPACK来提供高效率的线性代数运算。

NumPy的核心功能是提供了**“ndarray”（多维数组）**数据结构。

## 示例

```python
import numpy as np
# 列向量1，2，3
x = np.array([1, 2, 3])

# 3x3矩阵
m1 = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
```