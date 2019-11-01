<!--为了方便笔记的查找，使用不同的标记来标识懂或不懂等等信息-->
<!--啥：表示新知识，不太懂-->
<!--哦：表示已经看懂了，而且很重要-->
<table style="font-size:14px;word-wrap:break-word;word-break:break-all;vertical-align:top;"><tr><td colspan=2>
<!--title-->

决策树的生成过程

<!--title-->
</td></tr><tr><td style="width:300px">
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


<!--content-->
</td></tr><tr><td colspan=2 style="font-weight:bold">
<!--summary-->

<li>生成决策树，就是从给定的训练数据集中，依据特征选择的准则，递归的选择最优划分特征，并根据此特征将特征将训练数据进行分割，使得各子数据集有一个最好的分类的过程。</li>

<!--summary-->
</td></tr></table>
