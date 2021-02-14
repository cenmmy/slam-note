# 初识视觉SLAM

### 视觉SLAM做的事情
+ 我在什么地方？
+ 周围的环境是什么样的？

我在什么地方这个问题对应SLAM问题中的定位问题，周围的环境是什么样的对应SLAM问题中的建图问题。

### 视觉SLAM中不同的相机选择
+ 单目相机
+ 双目相机 (常用)
+ 深度相机

#### 1. 单目相机的优缺点

优点：成本低

缺点：无法通过单张图片计算场景中的物体与相机的距离，平移之后才能计算深度且该深度值是相对的，无法确定真实尺度。

#### 2. 双目相机的优缺点

优点： 可以计算出场景中的物体与相机的真实的距离

缺点：需要大量计算，相机的配置和标定比较复杂

#### 3. 深度相机的优缺点

优点： 通过物理的方法直接测量物体与相机之间的距离，不需要大量的计算

缺点：测量范围窄，噪声大，视野小，易受日光影响，无法测量透射材质。因此深度相机主要用于室内。

### 经典视觉SLAM框架

![](./imgs/经典SLAM框架.png)

+ 传感器数据：读取双目相机的图像数据
+ 视觉里程计：估算相邻相机间的运动，以及局部地图的样子
+ 后端优化：接收不同时刻视觉里程计测量的相机位姿以及回环检测的信息，对它们进行优化，得到全局一致的轨迹和地图。
+ 回环检测：判断机器人之前是否到过该位置
+ 建图：建立与任务要求对应的地图。

#### 1. 视觉里程计

![](./imgs/视觉里程计输入和输出.png)

从上图中可以看出视觉里程计的作用主要是计算相邻图像之间相机的运动和图像中各个像素对应的空间位置

相机的运动叠加起来就构成了相机运动的轨迹

图像中各个像素点对应世界坐标系下的位置构成了地图

因此视觉里程计解决了我们之前提出的定位和建图的问题。

#### 2. 后端优化和回环检测

尽管视觉里程计完成了视觉SLAM的所要解决的问题，但是视觉里程计只是对相邻两个图像进行估计，这种估计是存在误差的，因此我们需要通过后端优化和回环检测来消除这种误差。

### SLAM问题的数学表述

<a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{X}_\mathbf{k}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{X}_\mathbf{k}" title="\mathbf{X}_\mathbf{k}" /></a>表示k时刻相机的位置，使用数学表述为

<a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{X}_\mathbf{k}&space;=&space;f\left&space;(&space;\mathbf{x}_{\mathbf{k}&space;-&space;1},&space;\mathbf{u}_\mathbf{k},&space;\mathbf{w}_\mathbf{k}&space;\right&space;)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{X}_\mathbf{k}&space;=&space;f\left&space;(&space;\mathbf{x}_{\mathbf{k}&space;-&space;1},&space;\mathbf{u}_\mathbf{k},&space;\mathbf{w}_\mathbf{k}&space;\right&space;)" title="\mathbf{X}_\mathbf{k} = f\left ( \mathbf{x}_{\mathbf{k} - 1}, \mathbf{u}_\mathbf{k}, \mathbf{w}_\mathbf{k} \right )" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{X}_\mathbf{k&space;-&space;1}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{X}_\mathbf{k&space;-&space;1}" title="\mathbf{X}_\mathbf{k - 1}" /></a> 表示上一个时刻相机的位置， <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{U}_\mathbf{k}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{U}_\mathbf{k}" title="\mathbf{U}_\mathbf{k}" /></a>表示当前时刻运动传感器获取到的数据，<a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{W}_\mathbf{k}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{W}_\mathbf{k}" title="\mathbf{W}_\mathbf{k}" /></a>表示当前时刻的噪声。

<a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{Z}_\mathbf{kj}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{Z}_\mathbf{kj}" title="\mathbf{Z}_\mathbf{kj}" /></a>表示相机的时刻k从第j个路标点获取到的观测数据，使用数学表述为

<a href="https://www.codecogs.com/eqnedit.php?latex=z_{k,j}&space;=&space;h\left&space;(&space;y_j,&space;x_k,&space;v_{k,j}&space;\right&space;)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?z_{k,j}&space;=&space;h\left&space;(&space;y_j,&space;x_k,&space;v_{k,j}&space;\right&space;)" title="z_{k,j} = h\left ( y_j, x_k, v_{k,j} \right )" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=y_i" target="_blank"><img src="https://latex.codecogs.com/gif.latex?y_i" title="y_i" /></a>表示第i个路标， <a href="https://www.codecogs.com/eqnedit.php?latex=x_k" target="_blank"><img src="https://latex.codecogs.com/gif.latex?x_k" title="x_k" /></a>表示k时刻相机的位置，<a href="https://www.codecogs.com/eqnedit.php?latex=v_{k,j}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?v_{k,j}" title="v_{k,j}" /></a>表示此次观测的噪声。

因此slam问题用数学表述为

<a href="https://www.codecogs.com/eqnedit.php?latex=\left\{\begin{matrix}&space;x_k&space;=&space;f\left(x_{k-1},&space;u_k,&space;w_k&space;\right&space;)\\&space;z_{k,j}&space;=&space;h\left(y_j,&space;x_k,&space;v_{k,j}&space;\right&space;)&space;\end{matrix}\right." target="_blank"><img src="https://latex.codecogs.com/gif.latex?\left\{\begin{matrix}&space;x_k&space;=&space;f\left(x_{k-1},&space;u_k,&space;w_k&space;\right&space;)\\&space;z_{k,j}&space;=&space;h\left(y_j,&space;x_k,&space;v_{k,j}&space;\right&space;)&space;\end{matrix}\right." title="\left\{\begin{matrix} x_k = f\left(x_{k-1}, u_k, w_k \right )\\ z_{k,j} = h\left(y_j, x_k, v_{k,j} \right ) \end{matrix}\right." /></a>
