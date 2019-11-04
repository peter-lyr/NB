<table style="font-size:16px;word-wrap:break-word;word-break:break-all;"><tr><td style="font-size:16px" colspan=2>
<!--================================================================================-->

LR算法

<!--================================================================================-->
</td></tr><tr><td style="width:312px;vertical-align:top;">
<!--((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((((-->

<li>LR是典型的线性分类器</li>
<li>目的：找到超平面

$$Wx+b=0$$
</li>
<li>实现：sigmoid函数、损失函数、极大似然法、梯度下降法</li>

<!--))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))))-->
</td><td style="width:800px;vertical-align:top;">
<!--[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[-->

样本为：$(\boldsymbol{x}^{(1)},y^{(1)}),(\boldsymbol{x}^{(2)},y^{(2)}),...,(\boldsymbol{x}^{(m)},y^{(m)}).$

sigmoid函数求给定参数时的输出概率：

$$P(y=1|\boldsymbol{x}^{(j)},\boldsymbol\theta)=\sigma(\boldsymbol\theta^T\boldsymbol{x}^{(j)})=\frac{1}{1+e^{-(\boldsymbol\theta^T\boldsymbol{x}^{(j)})}}$$
$$P(y|\boldsymbol{x}^{(j)},\boldsymbol\theta)=[\sigma(\boldsymbol\theta^T\boldsymbol{x}^{(j)})]^{y^{(j)}}[1-\sigma(\boldsymbol\theta^T\boldsymbol{x}^{(j)})]^{1-y^{(j)}}$$
其中，$\boldsymbol{x}^{(j)}=[1,{\boldsymbol{x}^{(j)}}^T]^T=[1,x_1^{(j)},x_2^{(j)},...,x_n^{(j)}]^T,(j=1,2,...,m)$，$\boldsymbol\theta=[b,w_1,w_2,...,w_n]^T$，$b$为偏置，$w_i(i=1,2,...,n)$为各个特征的权重，$y$的取值为$0,1$。
这样就能够在样本的特征和标签之间建立映射关系，这就是我们的（含参）模型。
<br><br><br>
建立好模型之后，构建损失函数通常使用似然函数：
$$L(y^{(1)},y^{(2)},...,y^{(m)}|\boldsymbol{x}^{(1)},\boldsymbol{x}^{(2)},...,\boldsymbol{x}^{(m)},\boldsymbol\theta)=\prod_{j=1}^{m}P(y|\boldsymbol{x}^{(j)},\boldsymbol\theta)$$
最大化似然函数通常转化为最大化对数似然函数。而对于LR，经常取损失函数为：
$$L=-\frac{1}{m}\sum_{j=1}^{m}\left[y^{(j)}log(\sigma(\boldsymbol\theta^T\boldsymbol{x}^{(j)}))+(1-y^{(j)})log(1-\sigma(\boldsymbol\theta^T\boldsymbol{x}^{(j)}))\right]$$
$L$是$\boldsymbol\theta$的函数。此时目标转化为求$L$最小时$\boldsymbol\theta$的值。
<br><br><br>
梯度下降法，对$L$求梯度：
$$\nabla L=\left[\frac{\partial}{\partial b}L,\frac{\partial}{\partial w_1}L,\frac{\partial}{\partial w_2}L,...,\frac{\partial}{\partial w_n}L\right]^T$$
迭代公式：
$$\boldsymbol\theta_{s+1}=\boldsymbol\theta_s-\alpha\nabla L|_{\boldsymbol\theta=\boldsymbol\theta_s}$$

<!--]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]-->
</td></tr><tr><td colspan=2 style="font-size:16px;font-weight:bold">
<!--{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{{-->



<!--}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}}-->
</td></tr></table>
