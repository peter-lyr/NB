## TITLE
## CLUE
- 要做的事很容易确定：找到一个超平面，是的所有数据离它最近。
- 假设函数很容易找到：
$$f(\boldsymbol{x})=\boldsymbol\theta^T\boldsymbol{x}$$
- 很容易确定损失函数为：
$$J(\boldsymbol\theta)=\frac{1}{2m}\sum_{i=1}^m\left[f\left(\boldsymbol{x}^{(i)}\right)-y^{(i)}\right]^2$$
- 因为$J(\boldsymbol\theta)$是凸函数，所以可以使用最小二乘法，求得：
$$\boldsymbol\theta=(\boldsymbol{X}^T\boldsymbol{X})^{-1}\boldsymbol{X}^T\boldsymbol{y}$$
- 但是当数据量非常大时，需要对$J(\boldsymbol\theta)$进行优化，比如梯度下降法。
## CONTENT
  线性回归模型推导
  <button onclick="javascript:var a=document.getElementById('img0');if(a.style.width=='0px'){a.style.width='100%';this.innerText='隐藏';}else{a.style.width='0px';this.innerText='展开';}window.scrollTo(0,this.offsetTop)" style="background:#080;color:#fff;font-weight:bold;border-radius:10px;border:none;cursor:pointer;outline:none;overflow:auto">展开</button>
  <img id="img0" src="https://github.com/peter-lyr/NB/blob/master/algorithm/statics/%E7%BA%BF%E6%80%A7%E5%9B%9E%E5%BD%92%E6%A8%A1%E5%9E%8B%E6%8E%A8%E5%AF%BC.jpg?raw=true" style="width:0px"></img>
## SUMMARY
