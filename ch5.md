### 1. 相机模型

#### 1.1 针孔相机模型

相机的原理和针孔成像的原理相同

<a href="https://www.codecogs.com/eqnedit.php?latex=\frac{Z}{f}&space;=&space;-\frac{X}{X'}&space;=&space;-\frac{Y}{Y'}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\frac{Z}{f}&space;=&space;-\frac{X}{X'}&space;=&space;-\frac{Y}{Y'}" title="\frac{Z}{f} = -\frac{X}{X'} = -\frac{Y}{Y'}" /></a>

将成像的坐标转换到物体一侧

<a href="https://www.codecogs.com/eqnedit.php?latex=\frac{Z}{f}&space;=&space;\frac{X}{X'}&space;=&space;\frac{Y}{Y'}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\frac{Z}{f}&space;=&space;\frac{X}{X'}&space;=&space;\frac{Y}{Y'}" title="\frac{Z}{f} = \frac{X}{X'} = \frac{Y}{Y'}" /></a>

整理得

<a href="https://www.codecogs.com/eqnedit.php?latex=X'&space;=&space;f\frac{X}{Z}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?X'&space;=&space;f\frac{X}{Z}" title="X' = f\frac{X}{Z}" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=Y'&space;=&space;f\frac{Y}{Z}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?Y'&space;=&space;f\frac{Y}{Z}" title="Y' = f\frac{Y}{Z}" /></a>

将成像坐标转化为像素坐标

<a href="https://www.codecogs.com/eqnedit.php?latex=\left\{\begin{matrix}&space;u&space;=&space;\alpha&space;X'&space;&plus;&space;c_x\\&space;v&space;=&space;\beta&space;Y'&space;&plus;&space;c_y&space;\end{matrix}\right." target="_blank"><img src="https://latex.codecogs.com/gif.latex?\left\{\begin{matrix}&space;u&space;=&space;\alpha&space;X'&space;&plus;&space;c_x\\&space;v&space;=&space;\beta&space;Y'&space;&plus;&space;c_y&space;\end{matrix}\right." title="\left\{\begin{matrix} u = \alpha X' + c_x\\ v = \beta Y' + c_y \end{matrix}\right." /></a>

像素坐标系的原点通常位于左上角，<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;u" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\inline&space;u" title="u" /></a>轴与<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;x" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\inline&space;x" title="x" /></a>轴平行，<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;v" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\inline&space;v" title="v" /></a>轴向下与<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;y" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\inline&space;y" title="y" /></a>轴平行，设像素坐标相对于成像坐标在<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;u" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\inline&space;u" title="u" /></a>轴上缩放了<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\alpha" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\inline&space;\alpha" title="\alpha" /></a>倍，平移了<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;c_x" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\inline&space;c_x" title="c_x" /></a>，在<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;v" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\inline&space;v" title="v" /></a>轴上缩放了<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\beta" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\inline&space;\beta" title="\beta" /></a>倍，平移了<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;c_y" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\inline&space;c_y" title="c_y" /></a>。

整理得

<a href="https://www.codecogs.com/eqnedit.php?latex=\left\{\begin{matrix}&space;u&space;=&space;\alpha&space;f\frac{X}{Z}&space;&plus;&space;c_x\\&space;v&space;=&space;\beta&space;f\frac{Y}{Z}&space;&plus;&space;c_y&space;\end{matrix}\right." target="_blank"><img src="https://latex.codecogs.com/gif.latex?\left\{\begin{matrix}&space;u&space;=&space;\alpha&space;f\frac{X}{Z}&space;&plus;&space;c_x\\&space;v&space;=&space;\beta&space;f\frac{Y}{Z}&space;&plus;&space;c_y&space;\end{matrix}\right." title="\left\{\begin{matrix} u = \alpha f\frac{X}{Z} + c_x\\ v = \beta f\frac{Y}{Z} + c_y \end{matrix}\right." /></a>

合并<a href="https://www.codecogs.com/eqnedit.php?latex=\alpha&space;f" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\alpha&space;f" title="\alpha f" /></a>为<a href="https://www.codecogs.com/eqnedit.php?latex=f_x" target="_blank"><img src="https://latex.codecogs.com/gif.latex?f_x" title="f_x" /></a>, 合并<a href="https://www.codecogs.com/eqnedit.php?latex=\beta&space;f" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\beta&space;f" title="\beta f" /></a>为<a href="https://www.codecogs.com/eqnedit.php?latex=f_y" target="_blank"><img src="https://latex.codecogs.com/gif.latex?f_y" title="f_y" /></a>,整理得

<a href="https://www.codecogs.com/eqnedit.php?latex=\left\{\begin{matrix}&space;u&space;=&space;f_x\frac{X}{Z}&space;&plus;&space;c_x\\&space;v&space;=&space;f_y\frac{Y}{Z}&space;&plus;&space;c_y&space;\end{matrix}\right." target="_blank"><img src="https://latex.codecogs.com/gif.latex?\left\{\begin{matrix}&space;u&space;=&space;f_x\frac{X}{Z}&space;&plus;&space;c_x\\&space;v&space;=&space;f_y\frac{Y}{Z}&space;&plus;&space;c_y&space;\end{matrix}\right." title="\left\{\begin{matrix} u = f_x\frac{X}{Z} + c_x\\ v = f_y\frac{Y}{Z} + c_y \end{matrix}\right." /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=f_x" target="_blank"><img src="https://latex.codecogs.com/gif.latex?f_x" title="f_x" /></a>和<a href="https://www.codecogs.com/eqnedit.php?latex=f_y" target="_blank"><img src="https://latex.codecogs.com/gif.latex?f_y" title="f_y" /></a>的单位为像素。

使用矩阵表示为

<a href="https://www.codecogs.com/eqnedit.php?latex=\begin{bmatrix}&space;u\\&space;v\\&space;1&space;\end{bmatrix}&space;=&space;\frac{1}{Z}&space;\begin{bmatrix}&space;f_x&space;&&space;0&space;&&space;c_x\\&space;0&space;&&space;f_y&space;&&space;c_y\\&space;0&space;&&space;0&space;&&space;1&space;\end{bmatrix}&space;\begin{bmatrix}&space;X\\&space;Y\\&space;Z&space;\end{bmatrix}&space;=&space;\frac{1}{Z}KP" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;u\\&space;v\\&space;1&space;\end{bmatrix}&space;=&space;\frac{1}{Z}&space;\begin{bmatrix}&space;f_x&space;&&space;0&space;&&space;c_x\\&space;0&space;&&space;f_y&space;&&space;c_y\\&space;0&space;&&space;0&space;&&space;1&space;\end{bmatrix}&space;\begin{bmatrix}&space;X\\&space;Y\\&space;Z&space;\end{bmatrix}&space;=&space;\frac{1}{Z}KP" title="\begin{bmatrix} u\\ v\\ 1 \end{bmatrix} = \frac{1}{Z} \begin{bmatrix} f_x & 0 & c_x\\ 0 & f_y & c_y\\ 0 & 0 & 1 \end{bmatrix} \begin{bmatrix} X\\ Y\\ Z \end{bmatrix} = \frac{1}{Z}KP" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=Z\begin{bmatrix}&space;u\\&space;v\\&space;1&space;\end{bmatrix}&space;=&space;\begin{bmatrix}&space;f_x&space;&&space;0&space;&&space;c_x\\&space;0&space;&&space;f_y&space;&&space;c_y\\&space;0&space;&&space;0&space;&&space;1&space;\end{bmatrix}&space;\begin{bmatrix}&space;X\\&space;Y\\&space;Z&space;\end{bmatrix}&space;=&space;KP" target="_blank"><img src="https://latex.codecogs.com/gif.latex?Z\begin{bmatrix}&space;u\\&space;v\\&space;1&space;\end{bmatrix}&space;=&space;\begin{bmatrix}&space;f_x&space;&&space;0&space;&&space;c_x\\&space;0&space;&&space;f_y&space;&&space;c_y\\&space;0&space;&&space;0&space;&&space;1&space;\end{bmatrix}&space;\begin{bmatrix}&space;X\\&space;Y\\&space;Z&space;\end{bmatrix}&space;=&space;KP" title="Z\begin{bmatrix} u\\ v\\ 1 \end{bmatrix} = \begin{bmatrix} f_x & 0 & c_x\\ 0 & f_y & c_y\\ 0 & 0 & 1 \end{bmatrix} \begin{bmatrix} X\\ Y\\ Z \end{bmatrix} = KP" /></a>

我们称K为相机的内参，平时标定相机的时候，就是为了确定这些内参。

有内参就有外参，将世界坐标系下的坐标转换为相机坐标系下的坐标的旋转矩阵和平移向量就是相机的外参。

<a href="https://www.codecogs.com/eqnedit.php?latex=ZP_uv&space;=&space;Z\begin{bmatrix}&space;u\\&space;v\\&space;1&space;\end{bmatrix}&space;=&space;K\left&space;(RP_w&space;&plus;&space;t\right&space;)&space;=&space;KTP_w" target="_blank"><img src="https://latex.codecogs.com/gif.latex?ZP_uv&space;=&space;Z\begin{bmatrix}&space;u\\&space;v\\&space;1&space;\end{bmatrix}&space;=&space;K\left&space;(RP_w&space;&plus;&space;t\right&space;)&space;=&space;KTP_w" title="ZP_uv = Z\begin{bmatrix} u\\ v\\ 1 \end{bmatrix} = K\left (RP_w + t\right ) = KTP_w" /></a>


