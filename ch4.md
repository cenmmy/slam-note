# 李群和李代数

### 1. 李群和李代数基础

对于旋转矩阵和变换矩阵来说它们对加法不封闭

<a href="https://www.codecogs.com/eqnedit.php?latex=R_1&space;&plus;&space;R_2&space;\notin&space;SO\left&space;(&space;3&space;\right&space;)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?R_1&space;&plus;&space;R_2&space;\notin&space;SO\left&space;(&space;3&space;\right&space;)" title="R_1 + R_2 \notin SO\left ( 3 \right )" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=T_1&space;&plus;&space;T_2&space;\notin&space;SE\left&space;(&space;3&space;\right&space;)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?T_1&space;&plus;&space;T_2&space;\notin&space;SE\left&space;(&space;3&space;\right&space;)" title="T_1 + T_2 \notin SE\left ( 3 \right )" /></a>

实际上旋转矩阵和变换矩阵只对乘法封闭

<a href="https://www.codecogs.com/eqnedit.php?latex=R_1R_2&space;\in&space;SO\left&space;(&space;3&space;\right&space;)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?R_1R_2&space;\in&space;SO\left&space;(&space;3&space;\right&space;)" title="R_1R_2 \in SO\left ( 3 \right )" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=T_1T_2&space;\in&space;SE\left&space;(&space;3&space;\right&space;)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?T_1T_2&space;\in&space;SE\left&space;(&space;3&space;\right&space;)" title="T_1T_2 \in SE\left ( 3 \right )" /></a>

对于这种只有一种运算的集合，我们称之为群。

#### 1.1 群

群： 一种集合加上一种运算的代数结构。将集合记为<a href="https://www.codecogs.com/eqnedit.php?latex=A" target="_blank"><img src="https://latex.codecogs.com/gif.latex?A" title="A" /></a>, 运算记作<a href="https://www.codecogs.com/eqnedit.php?latex=\cdot" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\cdot" title="\cdot" /></a>，那么群可以记作<a href="https://www.codecogs.com/eqnedit.php?latex=G&space;=&space;\left(&space;A,&space;\cdot&space;\right&space;)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?G&space;=&space;\left(&space;A,&space;\cdot&space;\right&space;)" title="G = \left( A, \cdot \right )" /></a>。

群要求这个运算满足下面的条件

1. 封闭性： <a href="https://www.codecogs.com/eqnedit.php?latex=\forall&space;a_1,&space;a_2&space;\in&space;A,&space;a_1&space;\cdot&space;a_2&space;\in&space;A" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\forall&space;a_1,&space;a_2&space;\in&space;A,&space;a_1&space;\cdot&space;a_2&space;\in&space;A" title="\forall a_1, a_2 \in A, a_1 \cdot a_2 \in A" /></a>

2. 结合律：<a href="https://www.codecogs.com/eqnedit.php?latex=\forall&space;a_1,&space;a_2,&space;a_3&space;\in&space;A,&space;\left&space;(&space;a_1&space;\cdot&space;a_2&space;\right&space;)&space;\cdot&space;a_3&space;=&space;a_1&space;\cdot&space;\left&space;(&space;a_2&space;\cdot&space;a_3\right&space;)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\forall&space;a_1,&space;a_2,&space;a_3&space;\in&space;A,&space;\left&space;(&space;a_1&space;\cdot&space;a_2&space;\right&space;)&space;\cdot&space;a_3&space;=&space;a_1&space;\cdot&space;\left&space;(&space;a_2&space;\cdot&space;a_3\right&space;)" title="\forall a_1, a_2, a_3 \in A, \left ( a_1 \cdot a_2 \right ) \cdot a_3 = a_1 \cdot \left ( a_2 \cdot a_3\right )" /></a>

3. 幺元：<a href="https://www.codecogs.com/eqnedit.php?latex=\exists&space;a_0&space;\in&space;A,&space;s.t.&space;\forall&space;a&space;\in&space;A,&space;a_0&space;\cdot&space;a&space;=&space;a&space;\cdot&space;a_0&space;=&space;a" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\exists&space;a_0&space;\in&space;A,&space;s.t.&space;\forall&space;a&space;\in&space;A,&space;a_0&space;\cdot&space;a&space;=&space;a&space;\cdot&space;a_0&space;=&space;a" title="\exists a_0 \in A, s.t. \forall a \in A, a_0 \cdot a = a \cdot a_0 = a" /></a>

4. 逆：<a href="https://www.codecogs.com/eqnedit.php?latex=\forall&space;a&space;\in&space;A,&space;\exists&space;a^{-1}&space;\in&space;A,&space;s.t.&space;a&space;\cdot&space;a^{-1}&space;=&space;a_0" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\forall&space;a&space;\in&space;A,&space;\exists&space;a^{-1}&space;\in&space;A,&space;s.t.&space;a&space;\cdot&space;a^{-1}&space;=&space;a_0" title="\forall a \in A, \exists a^{-1} \in A, s.t. a \cdot a^{-1} = a_0" /></a>

我们可以验证旋转矩阵集合和变换矩阵集合关于矩阵乘法构成群，因此它们才能被称为特殊正交群和特殊欧式群

#### 1.2 李代数的引出

旋转矩阵满足

<a href="https://www.codecogs.com/eqnedit.php?latex=RR^T&space;=&space;I" target="_blank"><img src="https://latex.codecogs.com/gif.latex?RR^T&space;=&space;I" title="RR^T = I" /></a>

旋转矩阵表示相机的旋转，它随时间变换，因此有

<a href="https://www.codecogs.com/eqnedit.php?latex=R\left&space;(&space;t&space;\right&space;)&space;R&space;\left&space;(&space;t&space;\right&space;)^T&space;=&space;I" target="_blank"><img src="https://latex.codecogs.com/gif.latex?R\left&space;(&space;t&space;\right&space;)&space;R&space;\left&space;(&space;t&space;\right&space;)^T&space;=&space;I" title="R\left ( t \right ) R \left ( t \right )^T = I" /></a>

两边对t求导

<a href="https://www.codecogs.com/eqnedit.php?latex=\dot{R}\left&space;(t&space;\right&space;)R\left&space;(t&space;\right&space;)^T&space;&plus;&space;R\left&space;(&space;t&space;\right&space;)\dot{R}\left&space;(&space;t\right&space;)^T&space;=&space;0" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\dot{R}\left&space;(t&space;\right&space;)R\left&space;(t&space;\right&space;)^T&space;&plus;&space;R\left&space;(&space;t&space;\right&space;)\dot{R}\left&space;(&space;t\right&space;)^T&space;=&space;0" title="\dot{R}\left (t \right )R\left (t \right )^T + R\left ( t \right )\dot{R}\left ( t\right )^T = 0" /></a>

整理得

<a href="https://www.codecogs.com/eqnedit.php?latex=\dot{R}\left&space;(t&space;\right&space;)R\left&space;(t&space;\right&space;)^T&space;=&space;-\left&space;(&space;\dot{R}&space;\left&space;(&space;t&space;\right&space;)R\left&space;(&space;t\right&space;)^T&space;\right&space;)^T" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\dot{R}\left&space;(t&space;\right&space;)R\left&space;(t&space;\right&space;)^T&space;=&space;-\left&space;(&space;\dot{R}&space;\left&space;(&space;t&space;\right&space;)R\left&space;(&space;t\right&space;)^T&space;\right&space;)^T" title="\dot{R}\left (t \right )R\left (t \right )^T = -\left ( \dot{R} \left ( t \right )R\left ( t\right )^T \right )^T" /></a>

可以看出为反对称矩阵，因此存在

<a href="https://www.codecogs.com/eqnedit.php?latex=\varphi\left&space;(t&space;\right&space;)\hat{}&space;=&space;\dot{R}\left&space;(t&space;\right&space;)R\left&space;(t&space;\right&space;)^T" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\varphi\left&space;(t&space;\right&space;)\hat{}&space;=&space;\dot{R}\left&space;(t&space;\right&space;)R\left&space;(t&space;\right&space;)^T" title="\varphi\left (t \right )\hat{} = \dot{R}\left (t \right )R\left (t \right )^T" /></a>

等式两边同乘R(t)

<a href="https://www.codecogs.com/eqnedit.php?latex=\dot{R}\left&space;(t&space;\right&space;)&space;=&space;\varphi\left&space;(t&space;\right&space;)\hat{}R\left(t&space;\right&space;)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\dot{R}\left&space;(t&space;\right&space;)&space;=&space;\varphi\left&space;(t&space;\right&space;)\hat{}R\left(t&space;\right&space;)" title="\dot{R}\left (t \right ) = \varphi\left (t \right )\hat{}R\left(t \right )" /></a>

设t0 = 0, R(0) = I, 根据泰勒公式

<a href="https://www.codecogs.com/eqnedit.php?latex=\begin{align}&space;R\left&space;(t&space;\right&space;)&space;&&space;\approx&space;R\left(t_0&space;\right&space;)&space;&plus;&space;\dot{R}\left&space;(t_0&space;\right&space;)\left&space;(t&space;-&space;t_0&space;\right&space;)&space;\\&space;&&space;=&space;I&space;&plus;&space;\varphi\left&space;(0&space;\right&space;)\hat{}\left(t&space;\right&space;)&space;\end{align}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\begin{align}&space;R\left&space;(t&space;\right&space;)&space;&&space;\approx&space;R\left(t_0&space;\right&space;)&space;&plus;&space;\dot{R}\left&space;(t_0&space;\right&space;)\left&space;(t&space;-&space;t_0&space;\right&space;)&space;\\&space;&&space;=&space;I&space;&plus;&space;\varphi\left&space;(0&space;\right&space;)\hat{}\left(t&space;\right&space;)&space;\end{align}" title="\begin{align} R\left (t \right ) & \approx R\left(t_0 \right ) + \dot{R}\left (t_0 \right )\left (t - t_0 \right ) \\ & = I + \varphi\left (0 \right )\hat{}\left(t \right ) \end{align}" /></a>

同时设<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\varphi\left(t&space;\right&space;)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\inline&space;\varphi\left(t&space;\right&space;)" title="\varphi\left(t \right )" /></a>在<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;t_0" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\inline&space;t_0" title="t_0" /></a>附近保持为常数<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\varphi\left(t0&space;\right&space;)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\inline&space;\varphi\left(t0&space;\right&space;)" title="\varphi\left(t0 \right )" /></a>，因此有：

<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\dot{R}\left(t&space;\right&space;)&space;=&space;\varphi\left(t_0&space;\right&space;)\hat{}R\left(t&space;\right&space;)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\inline&space;\dot{R}\left(t&space;\right&space;)&space;=&space;\varphi\left(t_0&space;\right&space;)\hat{}R\left(t&space;\right&space;)" title="\dot{R}\left(t \right ) = \varphi\left(t_0 \right )\hat{}R\left(t \right )" /></a>

这是一个微分方程，且R(0) = I，根据一阶线性微分方程求解得

<a href="https://www.codecogs.com/eqnedit.php?latex=R\left(t&space;\right&space;)&space;=&space;exp\left(\varphi\left(t_0&space;\right&space;)\hat{}t&space;\right&space;)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?R\left(t&space;\right&space;)&space;=&space;exp\left(\varphi\left(t_0&space;\right&space;)\hat{}t&space;\right&space;)" title="R\left(t \right ) = exp\left(\varphi\left(t_0 \right )\hat{}t \right )" /></a>

从结果来看，我们找到了旋转矩阵和反对乘矩阵通过指数关系发生了联系，给定某时刻的旋转矩阵，我们能够找到一个反对称矩阵，它描述了旋转矩阵局部的导数关系

#### 1.3 李代数

每个李群都有与之对应的李代数，李代数描述了李群的局部性质，李群的定义如下：

李代数由一个集合V，一个数域F和一个二元运算[,]组成，并且满足一些性质。

上一节提到的<a href="https://www.codecogs.com/eqnedit.php?latex=\varphi" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\varphi" title="\varphi" /></a>事实上是一种李代数，对应的李括号为

<a href="https://www.codecogs.com/eqnedit.php?latex=[\varphi_1,&space;\varphi_2]&space;=&space;\left&space;(&space;\Phi_1\Phi_2&space;-&space;\Phi_2\Phi_1&space;\right&space;)^\vee" target="_blank"><img src="https://latex.codecogs.com/gif.latex?[\varphi_1,&space;\varphi_2]&space;=&space;\left&space;(&space;\Phi_1\Phi_2&space;-&space;\Phi_2\Phi_1&space;\right&space;)^\vee" title="[\varphi_1, \varphi_2] = \left ( \Phi_1\Phi_2 - \Phi_2\Phi_1 \right )^\vee" /></a>

特殊正交群对应的的李代数记为so(3)

<a href="https://www.codecogs.com/eqnedit.php?latex=so\left(3&space;\right&space;)&space;=&space;\left&space;\{&space;\varphi&space;\in&space;\mathbb{R},&space;\Phi&space;=&space;\varphi^\wedge&space;\in&space;\mathbb{R}^{3\times3}&space;\right&space;\}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?so\left(3&space;\right&space;)&space;=&space;\left&space;\{&space;\varphi&space;\in&space;\mathbb{R},&space;\Phi&space;=&space;\varphi^\wedge&space;\in&space;\mathbb{R}^{3\times3}&space;\right&space;\}" title="so\left(3 \right ) = \left \{ \varphi \in \mathbb{R}, \Phi = \varphi^\wedge \in \mathbb{R}^{3\times3} \right \}" /></a>

特殊欧式群对应的李代数为se(3)

<a href="https://www.codecogs.com/eqnedit.php?latex=se\left&space;(&space;3&space;\right&space;)&space;=&space;\left&space;\{&space;\varepsilon&space;=&space;\begin{bmatrix}&space;\rho&space;\\&space;\varphi&space;\end{bmatrix}&space;\in&space;\mathbb{R}^6,&space;\rho&space;\in&space;\mathbb{R}^3,&space;\varphi&space;\in&space;so\left&space;(&space;3&space;\right&space;),&space;\varepsilon^\wedge&space;=&space;\begin{bmatrix}&space;\varphi^\wedge&space;&&space;\rho&space;\\&space;0^T&space;&&space;0&space;\end{bmatrix}&space;\in&space;\mathbb{R}^{4&space;\times&space;4}&space;\right&space;\}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?se\left&space;(&space;3&space;\right&space;)&space;=&space;\left&space;\{&space;\varepsilon&space;=&space;\begin{bmatrix}&space;\rho&space;\\&space;\varphi&space;\end{bmatrix}&space;\in&space;\mathbb{R}^6,&space;\rho&space;\in&space;\mathbb{R}^3,&space;\varphi&space;\in&space;so\left&space;(&space;3&space;\right&space;),&space;\varepsilon^\wedge&space;=&space;\begin{bmatrix}&space;\varphi^\wedge&space;&&space;\rho&space;\\&space;0^T&space;&&space;0&space;\end{bmatrix}&space;\in&space;\mathbb{R}^{4&space;\times&space;4}&space;\right&space;\}" title="se\left ( 3 \right ) = \left \{ \varepsilon = \begin{bmatrix} \rho \\ \varphi \end{bmatrix} \in \mathbb{R}^6, \rho \in \mathbb{R}^3, \varphi \in so\left ( 3 \right ), \varepsilon^\wedge = \begin{bmatrix} \varphi^\wedge & \rho \\ 0^T & 0 \end{bmatrix} \in \mathbb{R}^{4 \times 4} \right \}" /></a>

### 2. 指数映射和对数映射

前面我们验证过 

<a href="https://www.codecogs.com/eqnedit.php?latex=R&space;=&space;exp\left&space;(&space;\varphi^\wedge&space;\right&space;)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?R&space;=&space;exp\left&space;(&space;\varphi^\wedge&space;\right&space;)" title="R = exp\left ( \varphi^\wedge \right )" /></a>

可以推导出

<a href="https://www.codecogs.com/eqnedit.php?latex=exp\left&space;(&space;\varphi^\wedge&space;\right&space;)&space;=&space;cos\theta&space;I&space;&plus;&space;\left&space;(&space;1&space;-&space;cos\theta&space;\right&space;)aa^T&space;&plus;&space;sin\theta&space;a^\wedge" target="_blank"><img src="https://latex.codecogs.com/gif.latex?exp\left&space;(&space;\varphi^\wedge&space;\right&space;)&space;=&space;cos\theta&space;I&space;&plus;&space;\left&space;(&space;1&space;-&space;cos\theta&space;\right&space;)aa^T&space;&plus;&space;sin\theta&space;a^\wedge" title="exp\left ( \varphi^\wedge \right ) = cos\theta I + \left ( 1 - cos\theta \right )aa^T + sin\theta a^\wedge" /></a>

同理

<a href="https://www.codecogs.com/eqnedit.php?latex=\varphi&space;=&space;ln\left&space;(&space;R&space;\right&space;)^\vee&space;=&space;\left&space;(&space;\sum_{n=0}^{\infty&space;}&space;\frac{\left&space;(&space;-1&space;\right&space;)^n}{n&plus;1}\left&space;(&space;R&space;-&space;I&space;\right&space;)^{n&plus;1}&space;\right&space;)^\vee" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\varphi&space;=&space;ln\left&space;(&space;R&space;\right&space;)^\vee&space;=&space;\left&space;(&space;\sum_{n=0}^{\infty&space;}&space;\frac{\left&space;(&space;-1&space;\right&space;)^n}{n&plus;1}\left&space;(&space;R&space;-&space;I&space;\right&space;)^{n&plus;1}&space;\right&space;)^\vee" title="\varphi = ln\left ( R \right )^\vee = \left ( \sum_{n=0}^{\infty } \frac{\left ( -1 \right )^n}{n+1}\left ( R - I \right )^{n+1} \right )^\vee" /></a>

### 3. 李代数求导和扰动模型

#### 3.1 BCH公式与近似公式

我们知道旋转矩阵的集合对应李群，旋转向量的集合对应李代数，这里我们需要弄清楚当两个旋转矩阵相乘时，李代数与之对应的运算是怎样的，同样当两个李代数做加法时，对应李群的运算是怎么样的。

两个李代数指数的乘积的完整形式由BCH公式给出

<a href="https://www.codecogs.com/eqnedit.php?latex=ln\left&space;(exp\left&space;(&space;A&space;\right&space;)&space;exp&space;\left&space;(&space;B&space;\right&space;)\right&space;)&space;=&space;A&space;&plus;&space;B&space;&plus;&space;\frac{1}{2}\left&space;[&space;A,&space;B&space;\right&space;]&space;&plus;&space;\frac{1}{12}\left[&space;A,&space;\left[A,B&space;\right&space;]&space;\right&space;]&space;-&space;\frac{1}{12}\left&space;[&space;B,&space;\left&space;[&space;A,&space;B&space;\right&space;]&space;\right&space;]&space;&plus;&space;..." target="_blank"><img src="https://latex.codecogs.com/gif.latex?ln\left&space;(exp\left&space;(&space;A&space;\right&space;)&space;exp&space;\left&space;(&space;B&space;\right&space;)\right&space;)&space;=&space;A&space;&plus;&space;B&space;&plus;&space;\frac{1}{2}\left&space;[&space;A,&space;B&space;\right&space;]&space;&plus;&space;\frac{1}{12}\left[&space;A,&space;\left[A,B&space;\right&space;]&space;\right&space;]&space;-&space;\frac{1}{12}\left&space;[&space;B,&space;\left&space;[&space;A,&space;B&space;\right&space;]&space;\right&space;]&space;&plus;&space;..." title="ln\left (exp\left ( A \right ) exp \left ( B \right )\right ) = A + B + \frac{1}{2}\left [ A, B \right ] + \frac{1}{12}\left[ A, \left[A,B \right ] \right ] - \frac{1}{12}\left [ B, \left [ A, B \right ] \right ] + ..." /></a>

BCH公式告诉我们，当处理两个矩阵指数之积时，它们会产生一些由李括号组成的余项，特别的，在SO(3)上，当李代数为小量时，小量二次以上的项都可以忽略，此时BCH拥有线性的近似表达：

<a href="https://www.codecogs.com/eqnedit.php?latex=ln\left&space;(exp\left(\varphi_1^\wedge&space;\right&space;)exp\left(\varphi_2^\wedge&space;\right&space;)&space;\right&space;)^\vee&space;\approx&space;\left\{\begin{matrix}&space;J_l\left&space;(\varphi_2&space;\right&space;)^{-1}&space;&plus;&space;\varphi_2&space;\\&space;J_r\left&space;(\varphi_1&space;\right&space;)^{-1}&space;&plus;&space;\varphi_1&space;\end{matrix}\right." target="_blank"><img src="https://latex.codecogs.com/gif.latex?ln\left&space;(exp\left(\varphi_1^\wedge&space;\right&space;)exp\left(\varphi_2^\wedge&space;\right&space;)&space;\right&space;)^\vee&space;\approx&space;\left\{\begin{matrix}&space;J_l\left&space;(\varphi_2&space;\right&space;)^{-1}&space;&plus;&space;\varphi_2&space;\\&space;J_r\left&space;(\varphi_1&space;\right&space;)^{-1}&space;&plus;&space;\varphi_1&space;\end{matrix}\right." title="ln\left (exp\left(\varphi_1^\wedge \right )exp\left(\varphi_2^\wedge \right ) \right )^\vee \approx \left\{\begin{matrix} J_l\left (\varphi_2 \right )^{-1} + \varphi_2 \\ J_r\left (\varphi_1 \right )^{-1} + \varphi_1 \end{matrix}\right." /></a>

第一个近似告诉我们当一个旋转矩阵左乘一个微小旋转矩阵时，可以近似地看作在其对应的李代数上加上了

<a href="https://www.codecogs.com/eqnedit.php?latex=J_1\left&space;(&space;\varphi_2&space;\right&space;)^{-1}\varphi_1" target="_blank"><img src="https://latex.codecogs.com/gif.latex?J_1\left&space;(&space;\varphi_2&space;\right&space;)^{-1}\varphi_1" title="J_1\left ( \varphi_2 \right )^{-1}\varphi_1" /></a>

同理第二个近似描述了旋转矩阵右乘一个微小旋转矩阵时，可以近似看作其对应的李代数加上了

<a href="https://www.codecogs.com/eqnedit.php?latex=J_r\left&space;(&space;\varphi_1&space;\right&space;)^{-1}\varphi_2" target="_blank"><img src="https://latex.codecogs.com/gif.latex?J_r\left&space;(&space;\varphi_1&space;\right&space;)^{-1}\varphi_2" title="J_r\left ( \varphi_1 \right )^{-1}\varphi_2" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=J_l" target="_blank"><img src="https://latex.codecogs.com/gif.latex?J_l" title="J_l" /></a>其实就是BCH近似雅可比

<a href="https://www.codecogs.com/eqnedit.php?latex=J_l&space;=&space;J&space;=&space;\frac{sin\theta}{\theta}I&space;&plus;&space;\left&space;(&space;1&space;-&space;\frac{sin\theta}{\theta}&space;\right&space;)aa^T&space;&plus;&space;\frac{1&space;-&space;cos\theta}{\theta}a^{\wedge}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?J_l&space;=&space;J&space;=&space;\frac{sin\theta}{\theta}I&space;&plus;&space;\left&space;(&space;1&space;-&space;\frac{sin\theta}{\theta}&space;\right&space;)aa^T&space;&plus;&space;\frac{1&space;-&space;cos\theta}{\theta}a^{\wedge}" title="J_l = J = \frac{sin\theta}{\theta}I + \left ( 1 - \frac{sin\theta}{\theta} \right )aa^T + \frac{1 - cos\theta}{\theta}a^{\wedge}" /></a>

对应的逆为：

<a href="https://www.codecogs.com/eqnedit.php?latex=J_l^{-1}&space;=&space;\frac{\theta}{2}cot\frac{\theta}{2}I&space;&plus;&space;\left&space;(&space;1&space;-&space;\frac{\theta}{2}cot\frac{\theta}{2}&space;\right&space;)aa^T&space;-&space;\frac{\theta}{2}a^\wedge" target="_blank"><img src="https://latex.codecogs.com/gif.latex?J_l^{-1}&space;=&space;\frac{\theta}{2}cot\frac{\theta}{2}I&space;&plus;&space;\left&space;(&space;1&space;-&space;\frac{\theta}{2}cot\frac{\theta}{2}&space;\right&space;)aa^T&space;-&space;\frac{\theta}{2}a^\wedge" title="J_l^{-1} = \frac{\theta}{2}cot\frac{\theta}{2}I + \left ( 1 - \frac{\theta}{2}cot\frac{\theta}{2} \right )aa^T - \frac{\theta}{2}a^\wedge" /></a>

而右乘雅可比只需对自变量取负号即可

<a href="https://www.codecogs.com/eqnedit.php?latex=J_r\left&space;(&space;\varphi&space;\right&space;)&space;=&space;J_l\left&space;(&space;-\varphi&space;\right&space;)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?J_r\left&space;(&space;\varphi&space;\right&space;)&space;=&space;J_l\left&space;(&space;-\varphi&space;\right&space;)" title="J_r\left ( \varphi \right ) = J_l\left ( -\varphi \right )" /></a>

上面讨论了矩阵乘法对应的李代数操作，下面讨论李代数加法对应的矩阵操作

<a href="https://www.codecogs.com/eqnedit.php?latex=exp\left&space;(&space;\left(\varphi&space;&plus;&space;\Delta\varphi&space;\right&space;)^\wedge&space;\right&space;)&space;=&space;exp\left(&space;\left(\varphi&space;&plus;&space;J_lJ_l^{-1}\Delta\varphi&space;\right&space;)^\wedge&space;\right&space;)&space;=&space;exp\left&space;(&space;\left&space;(&space;J_l\Delta\varphi&space;\right&space;)^\wedge&space;\right&space;)exp\left(\varphi^\wedge&space;\right&space;)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?exp\left&space;(&space;\left(\varphi&space;&plus;&space;\Delta\varphi&space;\right&space;)^\wedge&space;\right&space;)&space;=&space;exp\left(&space;\left(\varphi&space;&plus;&space;J_lJ_l^{-1}\Delta\varphi&space;\right&space;)^\wedge&space;\right&space;)&space;=&space;exp\left&space;(&space;\left&space;(&space;J_l\Delta\varphi&space;\right&space;)^\wedge&space;\right&space;)exp\left(\varphi^\wedge&space;\right&space;)" title="exp\left ( \left(\varphi + \Delta\varphi \right )^\wedge \right ) = exp\left( \left(\varphi + J_lJ_l^{-1}\Delta\varphi \right )^\wedge \right ) = exp\left ( \left ( J_l\Delta\varphi \right )^\wedge \right )exp\left(\varphi^\wedge \right )" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=exp\left&space;(&space;\left(\varphi&space;&plus;&space;\Delta\varphi&space;\right&space;)^\wedge&space;\right&space;)&space;=&space;exp\left(&space;\left(\varphi&space;&plus;&space;J_rJ_r^{-1}\Delta\varphi&space;\right&space;)^\wedge&space;\right&space;)&space;=&space;exp\left(\varphi^\wedge&space;\right&space;)exp\left&space;(&space;\left&space;(&space;J_r\Delta\varphi&space;\right&space;)^\wedge&space;\right&space;)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?exp\left&space;(&space;\left(\varphi&space;&plus;&space;\Delta\varphi&space;\right&space;)^\wedge&space;\right&space;)&space;=&space;exp\left(&space;\left(\varphi&space;&plus;&space;J_rJ_r^{-1}\Delta\varphi&space;\right&space;)^\wedge&space;\right&space;)&space;=&space;exp\left(\varphi^\wedge&space;\right&space;)exp\left&space;(&space;\left&space;(&space;J_r\Delta\varphi&space;\right&space;)^\wedge&space;\right&space;)" title="exp\left ( \left(\varphi + \Delta\varphi \right )^\wedge \right ) = exp\left( \left(\varphi + J_rJ_r^{-1}\Delta\varphi \right )^\wedge \right ) = exp\left(\varphi^\wedge \right )exp\left ( \left ( J_r\Delta\varphi \right )^\wedge \right )" /></a>

#### 3.2 SO(3)李代数上的求导
