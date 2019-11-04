<!--为了方便笔记的查找，使用不同的标记来标识懂或不懂等等信息-->
<!--啥：表示新知识，不太懂-->
<!--哦：表示已经看懂了，而且很重要-->
<style>li{list-style-type:none;}</style>
<table style="font-size:14px;word-wrap:break-word;word-break:break-all;vertical-align:top;"><tr><td style="font-size:16px" colspan=2>
<!--title-->

集成学习

<!--title-->
</td></tr><tr><td style="width:312px">
<!--clue-->

<h4>概念：</h4>
<li>不是一个单独的机器学习算法；</li>
<li>通过构建并结合多个机器学习器来完成学习任务；</li>
<li>用于分类问题集成，回归问题集成，特征选取集成，异常点检测集成等等；</li>

<h4>两个主要的问题</h4>
<li>如何得到若干个个体学习器：
<ul>
<li>同质（最广泛）：
<ul>
<li>CART决策树</li>
<li>神经网络</li>
</ul>
</li>
<li>异质</li>
</ul>
</li>
<li>如何选择一种结合策略，将这些个体学习器集合成一个强学习器</li>

<h4>同质个体学习器分类</h4>
<li>个体学习器之间存在强依赖关系：
<ul>
<li>boosting系列算法</li>
</ul>
</li>
<li>个体学习器之间不存在强依赖关系：
<ul>
<li>bagging<font color=red>啥</font></li>
<li>随机森林<font color=red>啥</font></li>
</ul></li>

<h4>boosting主要分类</h4>
<li>AdaBoost算法
<font color=red>啥</font></li>
<li>提升树boosting tree系列算法：
<ul>
<li>梯度提升树gradient boosting tree<font color=red>啥</font></li>
</ul>
</li>

<h4>集成学习之结合策略<font color=red>啥</font></h4>
<li>平均法</li>
<li>投票法</li>
<li>学习法</li>

<!--clue-->
</td><td style="width:800px">
<!--content-->

<a href="https://www.cnblogs.com/pinard/p/6131423.html">集成学习原理小结</a>
<br>
<a href="https://www.cnblogs.com/pinard/p/6133937.html">集成学习之Adaboost算法原理小结</a>

<!--content-->
</td></tr><tr><td colspan=2 style="font-size:16px;font-weight:bold">
<!--summary-->

所以现在我只知道集成学习的概况，具体的还不懂。

<!--summary-->
</td></tr></table>
