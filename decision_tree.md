<!--为了方便笔记的查找，使用不同的标记来标识懂或不懂等等信息-->
<!--啥：表示新知识，不太懂-->
<!--哦：表示已经看懂了，而且很重要-->
<table style="font-size:14px;word-wrap:break-word;word-break:break-all;vertical-align:top;"><tr><td colspan=2>
<!--title-->

决策树的生成过程

<!--title-->
</td></tr><tr><td style="width:312px">
<!--clue-->

<h4>概念：</h4>
基于样本特征做分类

<h4>三要素：</h4>
<li>特征选择</li>
<li>决策树生成</li>
<li>决策树剪枝</li>

<h4>特征选择的依据(计算)</h4>
<li>信息增益</li>
<li>信息增益率</li>
<li>基尼指数</li>

<h4>ID3、C4.5的不足</h4>
<li>偏向于取值较多或较少的特征</li>
<li>...</li>

<h4>CART分类树、回归树及其剪枝</h4>
<li>过拟合，泛化能力差</li>
<li>类似于线性回归的正则化</li>
<li>预剪枝、后剪枝</li>
<li>多次剪枝、交叉验证<font color=red>啥</font></li>

<h4>决策树算法优缺点</h4>
<li>简单直观</li>
<li>...</li>
<li>容易过拟合</li>
<li>不稳定（集成学习）</li>
<li>...</li>

<!--clue-->
</td><td style="width:800px">
<!--content-->

<a href="https://www.cnblogs.com/muzixi/p/6566803.html" target="_blank">决策树--信息增益，信息增益比，Geni指数的理解</a>
<br>
<a href="https://www.cnblogs.com/pinard/p/6050306.html">决策树算法原理(上)</a>
<br>
<a href="https://www.cnblogs.com/pinard/p/6053344.html">决策树算法原理(下)</a>
<br>

<p>信息熵
<br>
每个随机变量的自信息$I(y=c_k)=-log_2 p_k$以各自概率为权的加总：
<br>
$H(y)=\sum_{k=1}^{K}p_kI(y=c_k)=-\sum_{k=1}^{K}p_klog_2 p_k=-\sum_{k=1}^{K}p(y=c_k)log_2p(y=c_k)$。
<br>
经验信息熵
<br>
$H(y)=H(D)=-\sum_{k=1}^{K}\frac{|C_k|}{|D|}log_2 \frac{|C_k|}{|D|}$。
</p>

<p>条件熵<br>
给定特征A时y的信息熵就是条件熵：<br>
$H(y|A)=\sum_{j=1}^{m}p(A=a_j)H(y|A=a_j)$
<br>
特征A将D分为m个部分$a_1,a_2,...,a_m$，
从中抽取一个样本，属于$a_j$部分的概率为：<br>
$p(A=a_j)$
<br>
对于$a_j$部分，分类仍然有K中情况，故这部分的条件信息熵（计算方式同信息熵）为：<br>
$H(y|A=a_j)=-\sum_{k=1}^{K}p(y=c_k|A=a_j)log_2p(y=c_k|A=a_j)$
<br>
注意，$H(y|A)$和$H(y|A=a_j)$是完全不一样的，前者是后者的加总。<br>
经验条件熵<br>
$H(y|A)=H(y|D)=-\sum_{j=1}^{m}\frac{|D_j|}{|D|}\sum_{k=1}^{K}\frac{|D_{jk}|}{|D_j|}log_2\frac{|D_{jk}|}{|D_j|}$
</p>

<p>信息增益（互信息）<br>
根据特征A分类的信息增益为：<br>
$g(y,A)=H(y)-H(y|A)$
</p>

<p>信息增益比<br>
$g_R(y,A)=\frac{g(y,A)}{H_A(y)}$
<br>
其中$H_A(y)$是y关于A的熵：<br>
$H_A(y)=-\sum_{j=1}^{m}p(y^A=a_j)log_2p(y^A=a_j)$
<br>
注意，$H(y)$是关于y随机变量的信息熵，而$H_A(y)$是关于$A$这特特征所对应的随机变量的信息熵。
<font color=red>哦</font><br>
它对应的经验熵为：<br>
$H_A(y)=H_A(D)=-\sum_{j=1}^{m}\frac{|D_j|}{|D|}log_2\frac{|D_j|}{|D|}$
</p>

<p>基尼系数<br>
</p>

<!--content-->
</td></tr><tr><td colspan=2 style="font-weight:bold">
<!--summary-->

<li>生成决策树，就是从给定的训练数据集中，依据特征选择的准则，递归的选择最优划分特征，并根据此特征将特征将训练数据进行分割，使得各子数据集有一个最好的分类的过程。</li>

<!--summary-->
</td></tr></table>
