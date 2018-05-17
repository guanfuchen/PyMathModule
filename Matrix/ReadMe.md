# Matrix
增加矩阵相关知识。

---
## 迹

### 迹的定义
方阵A的迹，记作$tr(A)$是A的对角线元素之和：
$$tr(A)=\sum_{i}a_{ii}$$

### 迹的性质

线性性质：
$$tr(A+B)=tr(A)+tr(B) \tag{1}$$
$$tr(c \cdot A)=c \cdot tr(A) \tag{2}$$
$$tr(AB)=tr(BA) \tag{3}$$
$$tr(ABC)=tr(BCA)=tr(CAB) \tag{4}$$
$$tr(AA^T)=\sum_{i}\sum_{j}{a_{ij}^2} \tag{5}$$
$$tr(A)=tr(A^T)$$

证明过程：
- 性质1:
$$tr(A+B)=\sum_{i}(a_{ii}+b_{ii})=\sum_{i}{a_{ii}}+\sum_{i}{b_{ii}}=tr(A)+tr(B)$$
- 性质2:
$$tr(c \cdot A)=\sum_{i}(c \cdot a_{ii})=c \cdot \sum_{i}(a_{ii}) = c \cdot tr(A)$$
- 性质3:
$$tr(AB)=\sum_{i}\sum_{k}(a_{ik}b_{ki})=\sum_{i}\sum_{k}(b_{ik}a_{ki})=tr(BA)$$
- 性质4:
性质4可由性质3推导得到。
- 性质5:
性质5表示矩阵的转置和矩阵的乘积的迹等于原矩阵的所有元素之和。
$$tr(AA^T)=\sum_{i}\sum_{j}a_{ij}a_{ij}=\sum_{i}\sum_{j}a_{ij}^2$$


[线性代数(二十七) ： 矩阵的迹](https://blog.csdn.net/mathmetics/article/details/17504179)

[迹](https://zh.wikipedia.org/wiki/%E8%B7%A1)

[利用矩阵的迹巧妙解决矩阵的求导问题](https://blog.csdn.net/u012354244/article/details/46655709)

### 迹的梯度性质

由迹的定义可知迹可以看作是矩阵的实标量函数，所以我们可以通过求实标量函数的梯度来求迹的梯度。

#### 单个矩阵的迹

$$\frac{\partial{tr(A)}}{\partial{A}}=I_m, A \in R^{m*m} \tag{6}$$

#### 两个矩阵的迹
一般通过函数求导去考虑，比如$AB$对$A$的求导为$B$，那么假设$A$的维度是$m*n$，B的维度是$n*m$，结果应该和被求梯度的维度相同，即$A$的维度，那么结果应该是$B^T$。
$$\frac{\partial{tr(AB)}}{\partial{A}}=B^T \tag{6}$$
$$\frac{\partial{tr(A^TB)}}{\partial{A}}=B$$
$$\frac{\partial{tr(BA^T)}}{\partial{A}}=B$$
$$\frac{\partial{tr(BA)}}{\partial{A}}=B^T$$
$$\frac{\partial{tr(AA^T)}}{\partial{A}}=2A \tag{7}$$
$$\frac{\partial{tr(A^2)}}{\partial{A}}=2A^T \tag{8}$$
$$\frac{\partial{tr(A B A^T C)}}{\partial{A}}=(B A^T C)+CAB) \tag{9}$$

证明过程：
由于涉及到多个未知数的组合，其中参考标量函数的求导规则，可以将其中一个看作未知数，另一个看作是常数，先一个求导一个不求导，后一个不求导一个求导然后相加。
- 公式7
$$\frac{\partial{tr(AA^T)}}{\partial{A}}=\frac{\partial{tr(A F(A^T)) }}{\partial{A}}+\frac{\partial{tr(F(A) A^T) }}{\partial{A}}=A+A=2A$$
- 公式8
$$\frac{\partial{tr(A^2)}}{\partial{A}}=\frac{\partial{tr(AA)}}{\partial{A}}=\frac{\partial{tr(A F(A))}}{\partial{A}}+\frac{\partial{tr(F(A) A)}}{\partial{A}}=A^T+A^T=2A^T$$
- 公式9
$$\frac{\partial{tr(A B A^T C)}}{\partial{A}}=\frac{\partial{tr(A^T C A B)}}{\partial{A}}=\frac{\partial{tr(A F(B A^T C))}}{\partial{A}}+\frac{\partial{tr(A^T F(C A B))}}{\partial{A}}=(B A^T C)+CAB$$



[Matrix Calculus - Notes on the Derivative of a Trace](http://cal.cs.illinois.edu/~johannes/research/matrix%20calculus.pdf)

[矩阵迹求导](http://www.cnblogs.com/porco/p/4495495.html)

[矩阵函数求导](https://bruceking.site/2017/11/05/matrix-funciton-derivative/)

[矩阵微分笔记](http://cherishlc.iteye.com/blog/1765932) 作者通过学习张贤达,矩阵分析与应用,清华大学出版社,2004总结了矩阵的微分。

---
## 参考资料
