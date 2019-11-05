# LR算法


# CLUE
- LR是典型的线性分类器
- 目的：找到超平面

# CONTENT
  1. [分类算法](#分类算法)
      1. [分类算法的学习对象](#分类算法的学习对象)
      2. [学习目标](#学习目标)
      3. [分类算法的分类](#分类算法的分类)
  2. [logistic分类](#logistic分类)
      1. [问题的数学模型](#问题的数学模型)
      2. [数学模型的求解](#数学模型的求解)
### 分类算法
##### 分类算法的学习对象
m个样本（每个样本有n个特征，且对应1个标签。）
##### 学习目标
对新样本分类。
##### 分类算法的分类
- 线性可分
- 线性不可分
- 二分类（两种标签）
- 多分类（多种标签）

### logistic分类
它是线性可分二分类，是最简单的分类算法。
##### 问题的数学模型
样本可以表示为：
$$\boldsymbol{X}=
\left[\begin{matrix}
  x^{(1)}\\\\
  x^{(2)}\\\\
  \vdots\\\\
  x^{(m)}\\\\
\end{matrix}\right]=
\left[\begin{matrix}
  x_0^{(1)} & x_1^{(1)} & \cdots & x_n^{(1)}\\\\
  x_0^{(2)} & x_1^{(2)} & \cdots & x_n^{(2)}\\\\
  \vdots & \vdots & \ddots & \vdots\\\\
  x_0^{(m)} & x_1^{(m)} & \cdots & x_n^{(m)}\\\\
\end{matrix}\right],
(x_0^{(j)}=1,j=1,2,\cdots,m).
\tag{1.1}$$

$$\boldsymbol{y}=
\left[\begin{matrix}
  y^{(1)}\\\\
  y^{(2)}\\\\
  \vdots\\\\
  y^{(m)}\\\\
\end{matrix}\right]
\tag{1.2}$$


因为可以线性分为两类，故可以找到一个超平面
$f(\boldsymbol{x})=\boldsymbol{\theta}^T\boldsymbol{x}=0$
将样本正确分到两个不同的标签。其中
$$\boldsymbol{\theta}=
\left[\begin{matrix}
  \theta_{0}\\\\
  \theta_{1}\\\\
  \vdots\\\\
  \theta_{n}\\\\
\end{matrix}\right]
\tag{1.3}$$

所以我们把问题转化为在$n$维空间中寻找最合适的超平面，这个超平面用$n+1$维向量$\boldsymbol\theta$来表征。

##### 数学模型的求解
这时，特征$\boldsymbol{x}$到标签$y\in\{0,1\}$之间的映射，从$\boldsymbol{R^n}\to\{0,1\}$简化为$\boldsymbol{R}\to\{0,1\}$，即特征的线性组合$\boldsymbol{\theta}^T\boldsymbol{x}\in\boldsymbol{R}$到标签$y\in\{0,1\}$的映射。

那这个映射该如何表示？用sigmoid函数$g(z)=\frac{1}{1+e^{-z}}$！
<div align="center"><img src="https://p-blog.csdn.net/images/p_blog_csdn_net/chl033/612813/o_SigmoidFunction_701_2.gif" height="200"><p>图1.1</p></div>

此时，特征$\boldsymbol{x}$到标签$y\in\{0,1\}$之间的映射（我们称之为假设函数）为：
$$h_{\boldsymbol\theta}(\boldsymbol{x})=g(\boldsymbol\theta^T\boldsymbol{x})=\frac{1}{1+e^{-\boldsymbol\theta^T\boldsymbol{x}}}\tag{1.4}$$

为什么要用sigmoid函数？
- 它是$\boldsymbol{R}\to(0,1)$的映射。
- $\boldsymbol{\theta}^T\boldsymbol{x}$到原点的距离越远，分类的确信度越高。
- 通过假设函数我们可以构造似然函数（说明如下）。

$$P(y=1|\boldsymbol{x},\boldsymbol\theta)=h_{\boldsymbol\theta}(\boldsymbol{x}).$$
$$P(y=0|\boldsymbol{x},\boldsymbol\theta)=1-h_{\boldsymbol\theta}(\boldsymbol{x}).$$
将它们合并得到：
$$P(y|\boldsymbol{x},\boldsymbol\theta)=(h_{\boldsymbol\theta}(\boldsymbol{x}))^y(1-h_{\boldsymbol\theta}(\boldsymbol{x}))^{1-y}.\tag{1.5}$$
结合m个样本得到似然函数：
$$L(\boldsymbol\theta)=\prod_{i=1}^mP(y^{(i)}|\boldsymbol{x}^{(i)},\boldsymbol\theta)=\prod_{i=1}^m(h_{\boldsymbol\theta}(\boldsymbol{x}^{(i)}))^{y^{(i)}}(1-h_{\boldsymbol\theta}(\boldsymbol{x}^{(i)}))^{1-y^{(i)}}\tag{1.6}.$$
这样我们就可以使用极大似然法来求解最优参数了。取对数：
$$l(\boldsymbol\theta)=logL(\boldsymbol\theta)\prod_{i=1}^mP(y^{(i)}|\boldsymbol{x}^{(i)},\boldsymbol\theta)=\sum_{i=1}^m\left(y^{(i)}logh_{\boldsymbol\theta}(\boldsymbol{x}^{(i)})+(1-y^{(i)})log(1-h_{\boldsymbol\theta}(\boldsymbol{x}^{(i)}))\tag{1.7}\right).$$
将问题转换为梯度下降法，取损失函数为：
$$J(\boldsymbol\theta)=-\frac{1}{m}l(\boldsymbol\theta).\tag{1.8}$$
迭代公式：
$$\boldsymbol\theta^{new}=\boldsymbol\theta^{old}-\alpha\nabla J(\boldsymbol\theta)\tag{1.9}$$
对$\boldsymbol\theta$的第j个元素：
$$\theta_j^{new}=\theta_j^{old}-\alpha\frac{\partial}{\partial\theta_j}J(\boldsymbol\theta)\tag{1.10}$$
其中，$\frac{\partial}{\partial\theta_j}J(\boldsymbol\theta)$的求解：
<div align="center"><img src="https://img-blog.csdn.net/20131113203723187?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvZG9uZ3Rpbmd6aGl6aQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast"><p>图1.2</p></div>


故有：
$$\theta_j^{new}=\theta_j^{old}-\alpha\frac{1}{m}\sum_{i=1}^m\left(h_\boldsymbol\theta(\boldsymbol{x}^{(i)})-y^{(i)}\right)\boldsymbol{x}_j^{(i)}\tag{1.11}$$
向量化：
$$\boldsymbol\theta^{new}=\boldsymbol\theta^{old}-\alpha\frac{1}{m}\boldsymbol{X}^T\left(g\left(\boldsymbol{X\boldsymbol\theta}^{old}\right)-\boldsymbol{y}\right)\tag{1.12}$$
证明过程：

<div align="center"><img src="https://github.com/peter-lyr/NB/blob/master/algorithm/statics/logistic_regresion_%E6%A2%AF%E5%BA%A6%E4%B8%8B%E9%99%8D%E6%B3%95%E8%BF%AD%E4%BB%A3%E5%85%AC%E5%BC%8F%E5%90%91%E9%87%8F%E5%8C%96%E6%8E%A8%E5%AF%BC.jpg?raw=true"><p>图1.3</p></div>



  <!--$$Wx+b=0$$-->

  <!--实现：sigmoid函数、损失函数、极大似然法、梯度下降法-->

  <!--样本为：$(\boldsymbol{x}^{(1)},y^{(1)}),(\boldsymbol{x}^{(2)},y^{(2)}),\cdots,(\boldsymbol{x}^{(m)},y^{(m)}).$-->

  <!--sigmoid函数求给定参数时的输出概率：-->

  <!--$$P(y=1|\boldsymbol{x}^{(j)},\boldsymbol\theta)=\sigma(\boldsymbol\theta^T\boldsymbol{x}^{(j)})=\frac{1}{1+e^{-(\boldsymbol\theta^T\boldsymbol{x}^{(j)})}}$$-->
  <!--$$P(y|\boldsymbol{x}^{(j)},\boldsymbol\theta)=[\sigma(\boldsymbol\theta^T\boldsymbol{x}^{(j)})]^{y^{(j)}}[1-\sigma(\boldsymbol\theta^T\boldsymbol{x}^{(j)})]^{1-y^{(j)}}$$-->
  <!--其中，$\boldsymbol{x}^{(j)}=[1,{\boldsymbol{x}^{(j)}}^T]^T=[1,x_1^{(j)},x_2^{(j)},\cdots,x_n^{(j)}]^T,(j=1,2,\cdots,m)$，$\boldsymbol\theta=[b,w_1,w_2,\cdots,w_n]^T$，$b$为偏置，$w_i(i=1,2,\cdots,n)$为各个特征的权重，$y$的取值为$0,1$。-->
  <!--这样就能够在样本的特征和标签之间建立映射关系，这就是我们的（含参）模型。-->

  <!--建立好模型之后，构建损失函数通常使用似然函数：-->
  <!--$$L(y^{(1)},y^{(2)},\cdots,y^{(m)}|\boldsymbol{x}^{(1)},\boldsymbol{x}^{(2)},\cdots,\boldsymbol{x}^{(m)},\boldsymbol\theta)=\prod_{j=1}^{m}P(y|\boldsymbol{x}^{(j)},\boldsymbol\theta)$$-->
  <!--最大化似然函数通常转化为最大化对数似然函数。而对于LR，经常取损失函数为：-->
  <!--$$L=-\frac{1}{m}\sum_{j=1}^{m}\left[y^{(j)}log(\sigma(\boldsymbol\theta^T\boldsymbol{x}^{(j)}))+(1-y^{(j)})log(1-\sigma(\boldsymbol\theta^T\boldsymbol{x}^{(j)}))\right]$$-->
  <!--$L$是$\boldsymbol\theta$的函数。此时目标转化为求$L$最小时$\boldsymbol\theta$的值。-->

  <!--梯度下降法，对$L$求梯度：-->
  <!--$$\nabla L=\left[\frac{\partial}{\partial b}L,\frac{\partial}{\partial w_1}L,\frac{\partial}{\partial w_2}L,\cdots,\frac{\partial}{\partial w_n}L\right]^T$$-->
  <!--迭代公式：-->
  <!--$$\boldsymbol\theta_{s+1}=\boldsymbol\theta_s-\alpha\nabla L|_{\boldsymbol\theta=\boldsymbol\theta_s}$$-->


# SUMMARY
