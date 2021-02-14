# 旋转矩阵

### 1. 刚体

刚体是指在运动中和受力作用后，物体的形状和大小不变，且内部的各点相对位置不变。

SLAM问题中的相机可以看作是刚体。

### 2. 点，向量和坐标系

向量是从原点指向某处的一个箭头，注意不要将向量与它的坐标这两个概念混淆。一个向量是空间中的一个东西，这个东西不是和若干个实数相关联的，只有我们指定三维空间中的某个坐标系时，才能讨论向量在该坐标系下的坐标。例如向量<a href="https://www.codecogs.com/eqnedit.php?latex=\vec{a}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\vec{a}" title="\vec{a}" /></a>在线性空间基<a href="https://www.codecogs.com/eqnedit.php?latex=(\vec{e1},&space;\vec{e2},&space;\vec{e3})" target="_blank"><img src="https://latex.codecogs.com/gif.latex?(\vec{e1},&space;\vec{e2},&space;\vec{e3})" title="(\vec{e1}, \vec{e2}, \vec{e3})" /></a>下的坐标可以表示为：

<a href="https://www.codecogs.com/eqnedit.php?latex=\vec{a}&space;=&space;\begin{pmatrix}&space;\vec{e1}&space;&&space;\vec{e2}&space;&&space;\vec{e3}&space;\end{pmatrix}&space;\begin{pmatrix}&space;a1\\&space;a2\\&space;a3&space;\end{pmatrix}&space;=&space;a1\vec{e1}&space;&plus;&space;a2\vec{e2}&space;&plus;&space;a3\vec{e3}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\vec{a}&space;=&space;\begin{pmatrix}&space;\vec{e1}&space;&&space;\vec{e2}&space;&&space;\vec{e3}&space;\end{pmatrix}&space;\begin{pmatrix}&space;a1\\&space;a2\\&space;a3&space;\end{pmatrix}&space;=&space;a1\vec{e1}&space;&plus;&space;a2\vec{e2}&space;&plus;&space;a3\vec{e3}" title="\vec{a} = \begin{pmatrix} \vec{e1} & \vec{e2} & \vec{e3} \end{pmatrix} \begin{pmatrix} a1\\ a2\\ a3 \end{pmatrix} = a1\vec{e1} + a2\vec{e2} + a3\vec{e3}" /></a>

因此一个向量的具体取值一是与向量本身有关， 二是和选取的坐标系有关。

#### 2.1 向量内积和外积

向量内积也称点乘，计算方式为对应实数相乘相加

向量外积也称叉乘，结果为向量，该向量垂直与运算的两个向量，a x b = a ^ b = a的反对称矩阵点乘向量b

^符号是反对称符号

<a href="https://www.codecogs.com/eqnedit.php?latex=a&space;=&space;\begin{pmatrix}&space;a1\\&space;a2\\&space;a3&space;\end{pmatrix}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?a&space;=&space;\begin{pmatrix}&space;a1\\&space;a2\\&space;a3&space;\end{pmatrix}" title="a = \begin{pmatrix} a1\\ a2\\ a3 \end{pmatrix}" /></a>

对应的反对称矩阵为：

<a href="https://www.codecogs.com/eqnedit.php?latex=\begin{pmatrix}&space;0&space;&&space;-a3&space;&&space;a2\\&space;a3&space;&&space;0&space;&&space;-a1\\&space;-a2&space;&&space;a1&space;&&space;0&space;\end{pmatrix}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\begin{pmatrix}&space;0&space;&&space;-a3&space;&&space;a2\\&space;a3&space;&&space;0&space;&&space;-a1\\&space;-a2&space;&&space;a1&space;&&space;0&space;\end{pmatrix}" title="\begin{pmatrix} 0 & -a3 & a2\\ a3 & 0 & -a1\\ -a2 & a1 & 0 \end{pmatrix}" /></a>

这样在在计算向量的外积的时候，我们就将这个运算转换成了线性运算。

而外积可以很好描述向量在三维空间中的旋转，假设三维空间中有一个向量a，该向量在经过一定的旋转之后旋转到向量b，向量a和向量b的外积为一个向量c，该向量的方向垂直于向量a和向量b，同时也是右手法则大拇指指向的方形，且外积的值与旋转的角度有关

<a href="https://www.codecogs.com/eqnedit.php?latex=a&space;\times&space;b&space;=&space;\begin{vmatrix}&space;a&space;\end{vmatrix}&space;\begin{vmatrix}&space;b&space;\end{vmatrix}&space;sin\theta" target="_blank"><img src="https://latex.codecogs.com/gif.latex?a&space;\times&space;b&space;=&space;\begin{vmatrix}&space;a&space;\end{vmatrix}&space;\begin{vmatrix}&space;b&space;\end{vmatrix}&space;sin\theta" title="a \times b = \begin{vmatrix} a \end{vmatrix} \begin{vmatrix} b \end{vmatrix} sin\theta" /></a>

因此外积对应的向量可以描述向量旋转的方向和大小，因此该向量也称为旋转向量。

### 3. 坐标系之间的欧式变换

SLAM中常常会遇到将相机坐标系中的向量转换为世界坐标系中的向量，例如在建图时，需要将视野中的特征点的坐标转换为世界坐标系下的坐标。

欧式变换：同一个向量在不同的坐标系下长度和夹角都不会发生变化。
例如：向量a在以

<a href="https://www.codecogs.com/eqnedit.php?latex=\begin{pmatrix}&space;e1,&space;&&space;e2,&space;&&space;e3&space;\end{pmatrix}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\begin{pmatrix}&space;e1,&space;&&space;e2,&space;&&space;e3&space;\end{pmatrix}" title="\begin{pmatrix} e1, & e2, & e3 \end{pmatrix}" /></a>

为基的坐标系下的坐标为

<a href="https://www.codecogs.com/eqnedit.php?latex=\begin{pmatrix}&space;a1,&space;&&space;a2,&space;&&space;a3&space;\end{pmatrix}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\begin{pmatrix}&space;a1,&space;&&space;a2,&space;&&space;a3&space;\end{pmatrix}" title="\begin{pmatrix} a1, & a2, & a3 \end{pmatrix}" /></a>

在以

<a href="https://www.codecogs.com/eqnedit.php?latex=\begin{pmatrix}&space;e1',&space;&&space;e2',&space;&&space;e3'&space;\end{pmatrix}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\begin{pmatrix}&space;e1',&space;&&space;e2',&space;&&space;e3'&space;\end{pmatrix}" title="\begin{pmatrix} e1', & e2', & e3' \end{pmatrix}" /></a>

为基的坐标系下的坐标为

<a href="https://www.codecogs.com/eqnedit.php?latex=\begin{pmatrix}&space;a1',&space;&&space;a2',&space;&&space;a3'&space;\end{pmatrix}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\begin{pmatrix}&space;a1',&space;&&space;a2',&space;&&space;a3'&space;\end{pmatrix}" title="\begin{pmatrix} a1', & a2', & a3' \end{pmatrix}" /></a>


因此根据欧式变换，两个坐标系下的向量是相同的

<a href="https://www.codecogs.com/eqnedit.php?latex=\begin{bmatrix}&space;e1,&space;&&space;e2,&space;&&space;e3&space;\end{bmatrix}&space;\begin{bmatrix}&space;a1\\&space;a2\\&space;a3&space;\end{bmatrix}&space;=&space;\begin{bmatrix}&space;e1',&space;&&space;e2',&space;&&space;e3'&space;\end{bmatrix}&space;\begin{bmatrix}&space;a1'\\&space;a2'\\&space;a3'&space;\end{bmatrix}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;e1,&space;&&space;e2,&space;&&space;e3&space;\end{bmatrix}&space;\begin{bmatrix}&space;a1\\&space;a2\\&space;a3&space;\end{bmatrix}&space;=&space;\begin{bmatrix}&space;e1',&space;&&space;e2',&space;&&space;e3'&space;\end{bmatrix}&space;\begin{bmatrix}&space;a1'\\&space;a2'\\&space;a3'&space;\end{bmatrix}" title="\begin{bmatrix} e1, & e2, & e3 \end{bmatrix} \begin{bmatrix} a1\\ a2\\ a3 \end{bmatrix} = \begin{bmatrix} e1', & e2', & e3' \end{bmatrix} \begin{bmatrix} a1'\\ a2'\\ a3' \end{bmatrix}" /></a>

等式两边同时左乘

<a href="https://www.codecogs.com/eqnedit.php?latex=\begin{bmatrix}&space;\mathbf{e}_1^\mathbf{T}\\&space;\mathbf{e}_2^\mathbf{T}\\&space;\mathbf{e}_3^\mathbf{T}&space;\end{bmatrix}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;\mathbf{e}_1^\mathbf{T}\\&space;\mathbf{e}_2^\mathbf{T}\\&space;\mathbf{e}_3^\mathbf{T}&space;\end{bmatrix}" title="\begin{bmatrix} \mathbf{e}_1^\mathbf{T}\\ \mathbf{e}_2^\mathbf{T}\\ \mathbf{e}_3^\mathbf{T} \end{bmatrix}" /></a>

等式转换为了

<a href="https://www.codecogs.com/eqnedit.php?latex=\begin{bmatrix}&space;\mathbf{a}_\mathbf{1}\\&space;\mathbf{a}_\mathbf{2}\\&space;\mathbf{a}_\mathbf{3}&space;\end{bmatrix}&space;=&space;\begin{bmatrix}&space;\mathbf{e}_\mathbf{1}^\mathbf{T}\mathbf{e'}_\mathbf{1}&space;&&space;\mathbf{e}_\mathbf{1}^\mathbf{T}\mathbf{e'}_\mathbf{2}&space;&&space;\mathbf{e}_\mathbf{1}^\mathbf{T}\mathbf{e'}_\mathbf{3}\\&space;\mathbf{e}_\mathbf{2}^\mathbf{T}\mathbf{e'}_\mathbf{1}&space;&&space;\mathbf{e}_\mathbf{2}^\mathbf{T}\mathbf{e'}_\mathbf{2}&space;&&space;\mathbf{e}_\mathbf{2}^\mathbf{T}\mathbf{e'}_\mathbf{3}\\&space;\mathbf{e}_\mathbf{3}^\mathbf{T}\mathbf{e'}_\mathbf{1}&space;&&space;\mathbf{e}_\mathbf{3}^\mathbf{T}\mathbf{e'}_\mathbf{2}&space;&&space;\mathbf{e}_\mathbf{3}^\mathbf{T}\mathbf{e'}_\mathbf{3}&space;\end{bmatrix}&space;\begin{bmatrix}&space;\mathbf{a'}_\mathbf{1}\\&space;\mathbf{a'}_\mathbf{2}\\&space;\mathbf{a'}_\mathbf{3}&space;\end{bmatrix}&space;=&space;\mathbf{R}\mathbf{a'}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;\mathbf{a}_\mathbf{1}\\&space;\mathbf{a}_\mathbf{2}\\&space;\mathbf{a}_\mathbf{3}&space;\end{bmatrix}&space;=&space;\begin{bmatrix}&space;\mathbf{e}_\mathbf{1}^\mathbf{T}\mathbf{e'}_\mathbf{1}&space;&&space;\mathbf{e}_\mathbf{1}^\mathbf{T}\mathbf{e'}_\mathbf{2}&space;&&space;\mathbf{e}_\mathbf{1}^\mathbf{T}\mathbf{e'}_\mathbf{3}\\&space;\mathbf{e}_\mathbf{2}^\mathbf{T}\mathbf{e'}_\mathbf{1}&space;&&space;\mathbf{e}_\mathbf{2}^\mathbf{T}\mathbf{e'}_\mathbf{2}&space;&&space;\mathbf{e}_\mathbf{2}^\mathbf{T}\mathbf{e'}_\mathbf{3}\\&space;\mathbf{e}_\mathbf{3}^\mathbf{T}\mathbf{e'}_\mathbf{1}&space;&&space;\mathbf{e}_\mathbf{3}^\mathbf{T}\mathbf{e'}_\mathbf{2}&space;&&space;\mathbf{e}_\mathbf{3}^\mathbf{T}\mathbf{e'}_\mathbf{3}&space;\end{bmatrix}&space;\begin{bmatrix}&space;\mathbf{a'}_\mathbf{1}\\&space;\mathbf{a'}_\mathbf{2}\\&space;\mathbf{a'}_\mathbf{3}&space;\end{bmatrix}&space;=&space;\mathbf{R}\mathbf{a'}" title="\begin{bmatrix} \mathbf{a}_\mathbf{1}\\ \mathbf{a}_\mathbf{2}\\ \mathbf{a}_\mathbf{3} \end{bmatrix} = \begin{bmatrix} \mathbf{e}_\mathbf{1}^\mathbf{T}\mathbf{e'}_\mathbf{1} & \mathbf{e}_\mathbf{1}^\mathbf{T}\mathbf{e'}_\mathbf{2} & \mathbf{e}_\mathbf{1}^\mathbf{T}\mathbf{e'}_\mathbf{3}\\ \mathbf{e}_\mathbf{2}^\mathbf{T}\mathbf{e'}_\mathbf{1} & \mathbf{e}_\mathbf{2}^\mathbf{T}\mathbf{e'}_\mathbf{2} & \mathbf{e}_\mathbf{2}^\mathbf{T}\mathbf{e'}_\mathbf{3}\\ \mathbf{e}_\mathbf{3}^\mathbf{T}\mathbf{e'}_\mathbf{1} & \mathbf{e}_\mathbf{3}^\mathbf{T}\mathbf{e'}_\mathbf{2} & \mathbf{e}_\mathbf{3}^\mathbf{T}\mathbf{e'}_\mathbf{3} \end{bmatrix} \begin{bmatrix} \mathbf{a'}_\mathbf{1}\\ \mathbf{a'}_\mathbf{2}\\ \mathbf{a'}_\mathbf{3} \end{bmatrix} = \mathbf{R}\mathbf{a'}" /></a>

中间的矩阵R称为旋转矩阵，用来描述坐标系的旋转，旋转矩阵为行列式为1的正交阵，同理，行列式为1的正交阵为旋转矩阵。

<a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{SO}\left&space;(&space;\mathbf{n}&space;\right&space;)&space;=&space;\left&space;\{&space;\mathbf{R}\in&space;\mathbb{R}^{n\times&space;n}\mid&space;\mathbf{R}\mathbf{R}^\mathbf{T}&space;=&space;\mathbf{I},&space;det\left(\mathbf{R}&space;\right&space;)&space;=&space;\mathbf{1}&space;\right&space;\}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{SO}\left&space;(&space;\mathbf{n}&space;\right&space;)&space;=&space;\left&space;\{&space;\mathbf{R}\in&space;\mathbb{R}^{n\times&space;n}\mid&space;\mathbf{R}\mathbf{R}^\mathbf{T}&space;=&space;\mathbf{I},&space;det\left(\mathbf{R}&space;\right&space;)&space;=&space;\mathbf{1}&space;\right&space;\}" title="\mathbf{SO}\left ( \mathbf{n} \right ) = \left \{ \mathbf{R}\in \mathbb{R}^{n\times n}\mid \mathbf{R}\mathbf{R}^\mathbf{T} = \mathbf{I}, det\left(\mathbf{R} \right ) = \mathbf{1} \right \}" /></a>


SO(n)被称为特殊正交阵，SO(3)称为三维空间的特殊正交阵，用来表示三维空间的旋转。

由于旋转矩阵是正交阵，因此

<a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{A}^{-1}&space;=&space;\mathbf{A}^T" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{A}^{-1}&space;=&space;\mathbf{A}^T" title="\mathbf{A}^{-1} = \mathbf{A}^T" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{a'}&space;=&space;\mathbf{A}^{-1}\mathbf{a}&space;=&space;\mathbf{A}^{T}\mathbf{a}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{a'}&space;=&space;\mathbf{A}^{-1}\mathbf{a}&space;=&space;\mathbf{A}^{T}\mathbf{a}" title="\mathbf{a'} = \mathbf{A}^{-1}\mathbf{a} = \mathbf{A}^{T}\mathbf{a}" /></a>

因此旋转矩阵的逆或转置表示相反的旋转。

欧式变换中除了旋转还有平移，因此

<a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{a}&space;=&space;\mathbf{A}\mathbf{a}&space;&plus;&space;\mathbf{t}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{a}&space;=&space;\mathbf{A}\mathbf{a}&space;&plus;&space;\mathbf{t}" title="\mathbf{a} = \mathbf{A}\mathbf{a} + \mathbf{t}" /></a>

其中t为三维向量表示平移。

### 4. 变换矩阵与齐次坐标

上一节中我们讲到向量在不同坐标系中的变换可以使用旋转矩阵和平移向量来表示

<a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{a}_\mathbf{1}&space;=&space;\mathbf{A}_\mathbf{1}\mathbf{a'}_\mathbf{1}&space;&plus;&space;\mathbf{t}_\mathbf{1}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{a}_\mathbf{1}&space;=&space;\mathbf{A}_\mathbf{1}\mathbf{a'}_\mathbf{1}&space;&plus;&space;\mathbf{t}_\mathbf{1}" title="\mathbf{a}_\mathbf{1} = \mathbf{A}_\mathbf{1}\mathbf{a'}_\mathbf{1} + \mathbf{t}_\mathbf{1}" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{a}_\mathbf{2}&space;=&space;\mathbf{A}_\mathbf{2}\mathbf{a}_\mathbf{1}&space;&plus;&space;\mathbf{t}_\mathbf{2}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{a}_\mathbf{2}&space;=&space;\mathbf{A}_\mathbf{2}\mathbf{a}_\mathbf{1}&space;&plus;&space;\mathbf{t}_\mathbf{2}" title="\mathbf{a}_\mathbf{2} = \mathbf{A}_\mathbf{2}\mathbf{a}_\mathbf{1} + \mathbf{t}_\mathbf{2}" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{a}_\mathbf{2}&space;=&space;\mathbf{A}_\mathbf{2}\left&space;(&space;\mathbf{A}_\mathbf{1}\mathbf{a'}&space;&plus;&space;\mathbf{t}_\mathbf{1}&space;\right&space;)&space;&plus;&space;\mathbf{t}_\mathbf{2}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{a}_\mathbf{2}&space;=&space;\mathbf{A}_\mathbf{2}\left&space;(&space;\mathbf{A}_\mathbf{1}\mathbf{a'}&space;&plus;&space;\mathbf{t}_\mathbf{1}&space;\right&space;)&space;&plus;&space;\mathbf{t}_\mathbf{2}" title="\mathbf{a}_\mathbf{2} = \mathbf{A}_\mathbf{2}\left ( \mathbf{A}_\mathbf{1}\mathbf{a'} + \mathbf{t}_\mathbf{1} \right ) + \mathbf{t}_\mathbf{2}" /></a>

可以看到使用旋转矩阵和平移向量来表示不是线性关系，这样的形式在变换过多之后会变得十分复杂。

使用齐次坐标来解决这个问题

<a href="https://www.codecogs.com/eqnedit.php?latex=\begin{bmatrix}&space;\mathbf{a'}\\&space;\mathbf{1}&space;\end{bmatrix}&space;=&space;\begin{bmatrix}&space;\mathbf{R}&space;&&space;\mathbf{t}\\&space;\mathbf{0}^\mathbf{T}&space;&&space;\mathbf{1}&space;\end{bmatrix}&space;\begin{bmatrix}&space;\mathbf{a}\\&space;\mathbf{1}&space;\end{bmatrix}&space;=&space;\mathbf{T}\begin{bmatrix}&space;\mathbf{a}\\&space;\mathbf{1}&space;\end{bmatrix}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;\mathbf{a'}\\&space;\mathbf{1}&space;\end{bmatrix}&space;=&space;\begin{bmatrix}&space;\mathbf{R}&space;&&space;\mathbf{t}\\&space;\mathbf{0}^\mathbf{T}&space;&&space;\mathbf{1}&space;\end{bmatrix}&space;\begin{bmatrix}&space;\mathbf{a}\\&space;\mathbf{1}&space;\end{bmatrix}&space;=&space;\mathbf{T}\begin{bmatrix}&space;\mathbf{a}\\&space;\mathbf{1}&space;\end{bmatrix}" title="\begin{bmatrix} \mathbf{a'}\\ \mathbf{1} \end{bmatrix} = \begin{bmatrix} \mathbf{R} & \mathbf{t}\\ \mathbf{0}^\mathbf{T} & \mathbf{1} \end{bmatrix} \begin{bmatrix} \mathbf{a}\\ \mathbf{1} \end{bmatrix} = \mathbf{T}\begin{bmatrix} \mathbf{a}\\ \mathbf{1} \end{bmatrix}" /></a>

这样两次变换的累加就变成

<a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{a}_\mathbf{2}&space;=&space;\mathbf{T}_\mathbf{2}\mathbf{T}_\mathbf{1}\mathbf{a'}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{a}_\mathbf{2}&space;=&space;\mathbf{T}_\mathbf{2}\mathbf{T}_\mathbf{1}\mathbf{a'}" title="\mathbf{a}_\mathbf{2} = \mathbf{T}_\mathbf{2}\mathbf{T}_\mathbf{1}\mathbf{a'}" /></a>

转换矩阵又称为特殊欧式群

<a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{S}\mathbf{E}\left(&space;\mathbf{3}&space;\right&space;)&space;=&space;\left&space;\{&space;\mathbf{T}&space;=&space;\begin{bmatrix}&space;\mathbf{R}&space;&&space;\mathbf{t}\\&space;\mathbf{0}^\mathbf{T}&space;&&space;\mathbf{1}&space;\end{bmatrix}&space;\in&space;\mathbb{R}^{\mathbf{4}\times\mathbf{4}}&space;\mid&space;\mathbf{R}&space;\in&space;\mathbf{SO}\left(\mathbf{3}&space;\right&space;),&space;\mathbf{t}&space;\in&space;\mathbb{R}^\mathbf{3}\right&space;\}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{S}\mathbf{E}\left(&space;\mathbf{3}&space;\right&space;)&space;=&space;\left&space;\{&space;\mathbf{T}&space;=&space;\begin{bmatrix}&space;\mathbf{R}&space;&&space;\mathbf{t}\\&space;\mathbf{0}^\mathbf{T}&space;&&space;\mathbf{1}&space;\end{bmatrix}&space;\in&space;\mathbb{R}^{\mathbf{4}\times\mathbf{4}}&space;\mid&space;\mathbf{R}&space;\in&space;\mathbf{SO}\left(\mathbf{3}&space;\right&space;),&space;\mathbf{t}&space;\in&space;\mathbb{R}^\mathbf{3}\right&space;\}" title="\mathbf{S}\mathbf{E}\left( \mathbf{3} \right ) = \left \{ \mathbf{T} = \begin{bmatrix} \mathbf{R} & \mathbf{t}\\ \mathbf{0}^\mathbf{T} & \mathbf{1} \end{bmatrix} \in \mathbb{R}^{\mathbf{4}\times\mathbf{4}} \mid \mathbf{R} \in \mathbf{SO}\left(\mathbf{3} \right ), \mathbf{t} \in \mathbb{R}^\mathbf{3}\right \}" /></a>

与旋转矩阵相同，转换矩阵的逆表示相反的转换。

### 5. 旋转向量和欧拉角
#### 5.1 旋转向量

我们之前提到的旋转矩阵和变换矩阵存在一个问题就是冗余，比如说旋转矩阵使用了9个量来描述3个自由度的变换，即沿x,y,z轴的旋转；变换矩阵使用16个量来描述6个自由度的变换，即沿x,y,z轴的旋转和沿x,y,z轴的平移；所以说这种表述是冗余的，而且旋转矩阵和变换矩阵自身存在约束，即它们必须是一个正交阵，且行列式为1,因此对其进行估计或优化时比较困难。

之前我们介绍过向量之间的外积表示旋转，结果向量的方式为旋转轴的方向，大小和旋转的角度相关。因此我们可以使用旋转向量来代替旋转矩阵，同理可以使用旋转向量和平移向量来代替变换矩阵。

假设有一个旋转轴为<a href="https://www.codecogs.com/eqnedit.php?latex=n" target="_blank"><img src="https://latex.codecogs.com/gif.latex?n" title="n" /></a>, 旋转角度为<a href="https://www.codecogs.com/eqnedit.php?latex=\theta" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\theta" title="\theta" /></a>，那么它对应的旋转向量为<a href="https://www.codecogs.com/eqnedit.php?latex=n\theta" target="_blank"><img src="https://latex.codecogs.com/gif.latex?n\theta" title="n\theta" /></a>

从旋转向量到旋转矩阵之间的转换可以通过罗德里格斯公式来求

<a href="https://www.codecogs.com/eqnedit.php?latex=R&space;=&space;cos&space;\theta&space;I&space;&plus;&space;\left&space;(&space;1&space;-&space;cos\theta&space;\right&space;)nn^T&space;&plus;&space;sin\theta&space;n\hat{}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?R&space;=&space;cos&space;\theta&space;I&space;&plus;&space;\left&space;(&space;1&space;-&space;cos\theta&space;\right&space;)nn^T&space;&plus;&space;sin\theta&space;n\hat{}" title="R = cos \theta I + \left ( 1 - cos\theta \right )nn^T + sin\theta n\hat{}" /></a>

从旋转矩阵到旋转向量的之间的转换

<a href="https://www.codecogs.com/eqnedit.php?latex=\theta&space;=&space;arccos\left(\frac{tr\left&space;(&space;R&space;\right&space;)&space;-&space;1}{2}&space;\right&space;)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\theta&space;=&space;arccos\left(\frac{tr\left&space;(&space;R&space;\right&space;)&space;-&space;1}{2}&space;\right&space;)" title="\theta = arccos\left(\frac{tr\left ( R \right ) - 1}{2} \right )" /></a>

对于转轴<a href="https://www.codecogs.com/eqnedit.php?latex=n" target="_blank"><img src="https://latex.codecogs.com/gif.latex?n" title="n" /></a>, 经过旋转轴上的向量在旋转后不发生改变，因此

<a href="https://www.codecogs.com/eqnedit.php?latex=Rn&space;=&space;n" target="_blank"><img src="https://latex.codecogs.com/gif.latex?Rn&space;=&space;n" title="Rn = n" /></a> , 即旋转向量为特征值1对应的旋转特征向量。

推导过程过于复杂，记住结论即可。

#### 5.2 欧拉角

旋转矩阵和旋转向量虽然能够描述旋转，但是对人类来说非常不直观，而欧拉角可以直观地描述各个方向上的旋转，常用的欧拉角为（俯仰角，偏航角和滚转角）

但是欧拉角和旋转向量又一个缺点那就是奇异性(万向锁), 理论上证明了只要想使用3个实数来表达三维旋转时，都会不可避免遇到奇异性问题。（数学上的奇异性一般是指，函数在该点未定义（not defined，比如取值为无穷），或者不可微（fails to be well-behaved）。）

### 6. 四元数

前面说过旋转向量和欧拉角具有奇异性，而四元数既是紧凑的也没有奇异性。

<a href="https://www.codecogs.com/eqnedit.php?latex=q&space;=&space;q_0&space;&plus;&space;q_1i&space;&plus;&space;q_2j&space;&plus;&space;q_3k" target="_blank"><img src="https://latex.codecogs.com/gif.latex?q&space;=&space;q_0&space;&plus;&space;q_1i&space;&plus;&space;q_2j&space;&plus;&space;q_3k" title="q = q_0 + q_1i + q_2j + q_3k" /></a>

四元数的三个虚部满足下面的关系式：

<a href="https://www.codecogs.com/eqnedit.php?latex=\left\{\begin{matrix}&space;i^2&space;=&space;j^2&space;=&space;k^2&space;=&space;-1\\&space;ij&space;=&space;k,&space;ji&space;=&space;-k\\&space;jk&space;=&space;i,&space;kj&space;=&space;-i\\&space;ki&space;=&space;j,&space;ik&space;=&space;-j&space;\end{matrix}\right." target="_blank"><img src="https://latex.codecogs.com/gif.latex?\left\{\begin{matrix}&space;i^2&space;=&space;j^2&space;=&space;k^2&space;=&space;-1\\&space;ij&space;=&space;k,&space;ji&space;=&space;-k\\&space;jk&space;=&space;i,&space;kj&space;=&space;-i\\&space;ki&space;=&space;j,&space;ik&space;=&space;-j&space;\end{matrix}\right." title="\left\{\begin{matrix} i^2 = j^2 = k^2 = -1\\ ij = k, ji = -k\\ jk = i, kj = -i\\ ki = j, ik = -j \end{matrix}\right." /></a>

旋转的四元数形式为：

<a href="https://www.codecogs.com/eqnedit.php?latex=q&space;=&space;\begin{bmatrix}&space;cos\frac{\theta}{2},&space;n_xsin\frac{\theta}{2},&space;n_y\frac{\theta}{2},&space;n_z\frac{\theta}{2}&space;\end{bmatrix}^T" target="_blank"><img src="https://latex.codecogs.com/gif.latex?q&space;=&space;\begin{bmatrix}&space;cos\frac{\theta}{2},&space;n_xsin\frac{\theta}{2},&space;n_y\frac{\theta}{2},&space;n_z\frac{\theta}{2}&space;\end{bmatrix}^T" title="q = \begin{bmatrix} cos\frac{\theta}{2}, n_xsin\frac{\theta}{2}, n_y\frac{\theta}{2}, n_z\frac{\theta}{2} \end{bmatrix}^T" /></a>
