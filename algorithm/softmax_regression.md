## SR算法
## CLUE
- 多分类问题
- softmax函数
- softmax回归特性
- SR和LR关系
## CONTENT
### softmax函数
softmax函数，或称归一化指数函数，对向量进行归一化，凸显其中最大的值并抑制远低于最大值的其他分量。
<div align="center"><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/e348290cf48ddbb6e9a6ef4e39363568b67c09d3" alt=""></div>
<div align="center"><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/001ce4c2c74e78a66a4d7d04ab92cbd0d0fdec02" alt=""></div>
这可以被视作K个线性函数<img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/933ef5b00ec8c1e9470c87352dca2e9810fb003c" alt="">对softmax函数的复合。
<iframe src="https://zh.wikipedia.org/wiki/Softmax函数" frameborder="0" width="100%" height="280px"></iframe>

假设函数为：
<div align="center"><img src="http://deeplearning.stanford.edu/wiki/images/math/a/1/b/a1b0d7b40fe624cd8a24354792223a9d.png" alt=""></div>
代价函数为：
<div align="center"><img src="http://deeplearning.stanford.edu/wiki/images/math/7/6/3/7634eb3b08dc003aa4591a95824d4fbd.png" alt=""></div>
而logistic回归代价函数可以改为：
<div align="center"><img src="http://deeplearning.stanford.edu/wiki/images/math/5/4/9/5491271f19161f8ea6a6b2a82c83fc3a.png" alt=""></div>

可以看到，Softmax代价函数与logistic 代价函数在形式上非常类似，只是在Softmax损失函数中对类标记的$k$个可能值进行了累加。
对于$J(\theta)$的最小化问题，目前还没有闭式解法。因此，我们使用迭代的优化算法（例如梯度下降法，或 L-BFGS）。

### Softmax回归模型参数化的特点
Softmax回归有一个不寻常的特点：它有一个“冗余”的参数集。从$\theta_j$中减去$\psi$完全不影响假设函数的预测结果！
这表明前面的softmax回归模型中存在冗余的参数。更正式一点来说，Softmax模型被过度参数化了。
对于任意一个用于拟合数据的假设函数，可以求出多组参数值，这些参数得到的是完全相同的假设函数$h_\theta$。
$J(\theta)$是一个非严格的凸函数，因此梯度下降时不会遇到局部最优解的问题。但是Hessian矩阵是奇异的/不可逆的，这会直接导致采用牛顿法优化就遇到数值计算的问题）

### 权重衰减（正则化）
<div align="center"><img src="http://deeplearning.stanford.edu/wiki/images/math/4/7/1/471592d82c7f51526bb3876c6b0f868d.png" alt=""></div>

有了这个权重衰减项以后$\lambda>0$，代价函数就变成了严格的凸函数，这样就可以保证得到唯一的解了。此时的Hessian矩阵变为可逆矩阵，并且因为$J(\theta)$是凸函数，梯度下降法和 L-BFGS 等算法可以保证收敛到全局最优解。
$J(\theta)$的导数：
<div align="center"><img src="http://deeplearning.stanford.edu/wiki/images/math/3/a/f/3afb4b9181a3063ddc639099bc919197.png" alt=""></div>

### Softmax回归与Logistic 回归的关系
当类别数 $k = 2$ 时，softmax 回归退化为 logistic 回归。
这表明 softmax 回归是 logistic 回归的一般形式。
<iframe src="https://blog.csdn.net/pi9nc/article/details/19336629" frameborder="0" width="100%" height="280px"></iframe>

## SUMMARY
要理解softmax函数和sigmoid函数，它们都是深度学习的基础，SR和LR都是线性分类器。
