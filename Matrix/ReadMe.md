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
## 共轭转置

矩阵$A$的共轭转置（hermitian conjugate transpose）$A^H$定义为：
$$(A^H)_{i,j}=\bar{A}_{j,i}$$
其中$\bar{(\cdot)}$表示标量的复共轭，共轭转置的定义就是对一个矩阵转置后进行共轭操作，或者先进行共轭操作然后进行转置。
$$A^H=\overline{A^T}=(\overline{A})^T$$

例子：
$$A=\left[\begin{matrix}3+i & 5\\ 5 & -i\end{matrix}\right]$$
$$A^H=\left[\begin{matrix}3-i & 2+2i\\ 5 & -i\end{matrix}\right]$$

[共轭转置](https://zh.wikipedia.org/wiki/%E5%85%B1%E8%BD%AD%E8%BD%AC%E7%BD%AE)

[numpy.matrix.H](https://docs.scipy.org/doc/numpy-1.14.0/reference/generated/numpy.matrix.H.html) np中获取共轭转置矩阵。


---
## 主元

主元（pivot）是矩阵的一个演算元素，高斯消元法首先选出主元，用于特定计算。

在矩阵算法中，主元必须是非零元素，甚至是距零最远的元素。主元所在的列组成列空间的一个基，整体上，寻找主元的过程增加了算法的计算量，但是这对于保持计算结果的数值稳定性来说是完全有价值的。

[主元](https://zh.wikipedia.org/wiki/%E4%B8%BB%E5%85%83)

---
## 逆、左右逆和伪逆

### 逆矩阵

逆矩阵（inverse matrix）：给定一个$n$阶方阵$A$，若存在一个$n$阶方阵$B$，使得$AB=BA=I_n$，其中$I_n$为$n$阶单位矩阵，则称$A$是可逆的，且$B$是$A$的逆矩阵，记作$A^{-1}$。

只有方阵才有逆矩阵，若方阵$A$的逆矩阵存在，则称$A$为非奇异方阵或可逆方阵。

求解思路如下所示：
- 伴随矩阵法：
如果矩阵$A$可逆，那么$A^{-1}=\frac{A^{*}}{|A|}$，其中$A^{*}$是$A$的伴随矩阵。
- 初等变换法：
如果矩阵$A$和$B$互逆，那么通过对$A$进行初等行变换（初等列变换）就相当于在$A$的左边（右边）乘以相应的初等矩阵，所以我们可以同时对$A$和$I$进行相同的初等行变换（初等列变换）。这样，当矩阵$A$变为$I$时，$I$就变为$A$的逆矩阵$B$。**其中左乘一个矩阵相当于对这个矩阵进行行变换，右乘就是列变换。**

逆矩阵具有如下性质：
1. $$(A^{-1})^{-1}=A$$
2. $$(\lambda A)^{-1}=\frac{1}{\lambda} A^{-1}$$
3. $$(A B)^{-1}=B^{-1} A^{-1}$$
4. $$(A^T)^{-1}=(A^{-1})^{T}$$
5. $$det(A^{-1})=\frac{1}{det(A)}$$

## 广义逆
广义逆又称为伪逆，是对逆阵的推广，一般所说的伪逆是指摩尔-彭若斯广义逆（MP逆），在求解线性最小二乘问题中有重要应用。

矩阵$A$的广义逆是指另一矩阵具有部分逆矩阵的特性，但是不一定具有逆矩阵的所有特性。假设一矩阵$A \in R^{nxm}$以及另一矩阵$A^{g} \in R^{mxn}$，若$A^{g}$满足$A A^{g} A = A$，则$A^{g}$称为$A$的广义逆。

构造广义逆的目的时针对可逆矩阵以外的矩阵，可以找到一矩阵有一些类似逆矩阵的特性。任意的矩阵都存在广义逆阵，若一矩阵存在逆矩阵，逆矩阵即为其唯一的广义逆阵。

### 广义逆提出的原因

考虑线性方程：
$$Ax=y$$
其中$A$为$nxm$的矩阵，而$y$是$A$的列空间。若矩阵$A$为可逆矩阵，那么$x=A^{-1}y$为方程的解。如果矩阵$A$不可逆或者不是方阵，那么需要一个适合的$mxn$矩阵$G$使得以下成立：
$$AGy=y$$
因此$Gy$是$Ax=y$的解。那么$mxn$的矩阵$G$也会使下述成立：
$$AGA=A$$
那么广义逆定义：假设一个$nxm$的矩阵$A$，$mxn$的矩阵$G$使下述式子的矩阵被称为$A$的广义逆矩阵。
$$AGA=A$$

### 性质
$$A A^{g} A = A$$
$$A^{g} A A^{g}=A^{g}$$
$$(A A^{g})^H=A A^{g}$$
$$(A^{g} A)^H=A^{g} A$$
这四个条件蕴含了一个事情：$A A^{g}$必然是一个效果等同单位矩阵但又不是单位矩阵的矩阵。一般利用$SVD$分解计算伪逆：
$$A=U \Sigma V^{H}$$
$$A^{g}=V \Sigma^{+} U^{H}$$
其中$\Sigma$矩阵使一个对角线矩阵，它的伪逆矩阵的步骤如下：
- 将对角线上的元素取倒数
- 将整个矩阵转置一次

### 最小二乘
最小二乘问题如下，其中$X \in R^{m*n}$，$y \in R^{m*1}$
$$XA=y$$
如果$X$可逆，那么$A=X^{-1}y$，否则$A=X^{g}y$。

之前的另一种解法是使用$X^T X A = X^T y$进行求解，那么$A=(X^T X)^{-1} X^T y$，其中$(X^T X)^{-1} X^T$被称为$X$的左逆，因为$((X^T X)^{-1} X^T) X=I$。

同上引出$X$的右逆为$X^T (X^T X)^{-1}$，因为$X X^T (X^T X)^{-1}=I$。

---
## 参考资料

[（数学概念）矩阵的逆、伪逆、左右逆，最小二乘，投影矩阵](https://www.cnblogs.com/AndyJee/p/5082508.html)

[逆矩阵 wiki](https://zh.wikipedia.org/wiki/%E9%80%86%E7%9F%A9%E9%98%B5)

[Moore–Penrose inverse](https://en.wikipedia.org/wiki/Moore%E2%80%93Penrose_inverse#Singular_value_decomposition_.28SVD.29)

MIT线性代数 左右逆和伪逆 34集

[最小二乘法](https://zh.wikipedia.org/wiki/%E6%9C%80%E5%B0%8F%E4%BA%8C%E4%B9%98%E6%B3%95)

[线性代数之伪逆矩阵(pseudoinverse matrix)](https://www.qiujiawei.com/linear-algebra-16/)