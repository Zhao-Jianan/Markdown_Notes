**计算机图形学 Computer Graphics**
# 图形学概述
## 计算机图形学定义
使用计算机来合成和处理视觉信息
## 计算机图形学应用
- 游戏 Video Games
- 电影 Movies
- 动画 Animations
- 设计 Design
- 可视化 Visualization
- VR Virtual Reality
- AR Augmented Reality
- 数字插画 Digital Illustration
- 模拟 Simulation
- 图形用户界面 Graphical User Interfaces
- 文字排版 Typography

## 为什么学习图形学
### 基础挑战
- 创造逼真的虚拟世界并与之互动
- 需要理解物理世界的方方面面
- 新的计算方法、显示技术

### 技术挑战
- （透视）投影、曲线、曲面的数学
- 光照和阴影的物理
- 3D 图形的表示/操作
- 动画/模拟
- 3D 图形软件编程和硬件

### Computer Graphics is AWESOME!


## 图形学的四个重要部分
### 光栅化 Rasterization
- 将几何图元geometry primitives（3D 三角形/多边形）投影到屏幕上
- 将投影图元分解为碎片fragments（像素）
- 视频游戏（实时应用）的黄金标准

### 曲线和网格 Curves and Meshes

### 光线追踪 Ray Tracing
从相机发射光线穿过每个像素
- 计算交点intersection和阴影shading
- 持续反射bounce光线直至击中光源

动画/电影（离线应用）的黄金标准

### 动画/模拟 Animation / Simulation
- 关键帧动画
- 质量弹簧系统

# 线性代数 Linear Algebra
## 图形依赖关系
### 基础数学
- 线性代数
- 微积分
- 统计学
### 基础物理学
- 光学
- 力学
### 其他
- 信号处理
- 数值分析
### 以及一些美学知识

## 向量 Vectors
### 概念
通常写为

$$
\Large \vec{a}
$$

或粗体显示

$$
\Large \mathbf{a}
$$

或使用起点和终点

$$
\overrightarrow{AB}
$$

- 方向和长度
- 没有绝对的起始位置


### 向量归一化 Vector Normalization
向量的幅值（长度）写为

$$
\Large \|\vec{a}\|
$$

#### 单位向量
幅值为 1 的向量

求向量的单位向量（归一化）：

$$
\hat{\mathbf{a}} = \frac{\vec{a}}{\|\vec{a}\|}
$$

用于表示方向

### 向量加法 Vector Addition
- 几何学Geometrically
平行四边形定律和三角形定律
- 代数学Algebraically
简单添加坐标

### 笛卡尔坐标 Cartesian Coordinates
X 和 Y 可以是任意（通常是正交单位）向量

#### 1. 向量 **A** 的坐标表示（**A =**）：

**二维向量**：

$$
\mathbf{A} = \begin{pmatrix} x \\ y \end{pmatrix}
$$

**三维向量**：

$$
\mathbf{A} = \begin{pmatrix} x \\ y \\ z \end{pmatrix}
$$


#### 2. 向量 **A** 的转置（**A.T =**）：

**二维向量**：

$$
\mathbf{A}^T = \begin{pmatrix} x & y \end{pmatrix}
$$

**三维向量**：

$$
\mathbf{A}^T = \begin{pmatrix} x & y & z \end{pmatrix}
$$

#### 3. 向量 **A** 的幅值（**||A|| =**）：

**二维向量**：

$$
\|\mathbf{A}\| = \sqrt{x^2 + y^2}
$$

**三维向量**：

$$
\|\mathbf{A}\| = \sqrt{x^2 + y^2 + z^2}
$$  


### 向量乘法 Vector Multiplication
- 点积
- 叉积
- 正交基和坐标系

#### 点积 Dot (scalar) Product

$$
\vec{a} \cdot \vec{b} = k \|\vec{a}\| \|\vec{b}\| \cos \theta
$$

$$
\cos \theta = \frac{\vec{a} \cdot \vec{b}}{\|\vec{a}\| \|\vec{b}\|}
$$

对于单位向量
$$
\cos \theta = \hat{a} \cdot \hat{b}
$$


##### 特性 Properties

$$
\vec{a} \cdot \vec{b} = \vec{b} \cdot \vec{a}
$$

$$
\vec{a} \cdot (\vec{b} + \vec{c}) = \vec{a} \cdot \vec{b} + \vec{a} \cdot \vec{c}
$$

$$
(k \vec{a}) \cdot \vec{b} = \vec{a} \cdot (k \vec{b}) = k (\vec{a} \cdot \vec{b})
$$

##### 笛卡尔坐标系中的点积
逐个分量相乘，然后相加

**In 2D**:

$$ 
\vec{a} \cdot \vec{b} = \begin{pmatrix} x_a \\ y_a \end{pmatrix} \cdot \begin{pmatrix} x_b \\ y_b \end{pmatrix} = x_a x_b + y_a y_b
$$

**In 3D**:

$$ 
\vec{a} \cdot \vec{b} = 
\begin{pmatrix} x_a \\ y_a \\ z_a \end{pmatrix} \cdot 
\begin{pmatrix} x_b \\ y_b \\ z_b \end{pmatrix} = x_a x_b + y_a y_b + z_a z_b
$$  

##### 图形学中的点积
- 计算两个向量之间的夹角
（例如，光源与表面夹角的余弦值）
- 计算一个向量在另一个向量上的投影
- 测量两个方向的接近程度
- 分解向量
- 确定前向/后向

##### 投影点积
将 \( \vec{a} \) 投影到 \( \vec{b} \)
必须沿着 \( \vec{b} \) (或沿着 \( \vec{a} \))

$$
\hat{a} \cdot \vec{b} = k \hat{b}
$$

它的幅值 \( k \)是多少？
Magnitude \( k \):

$$
k = \frac{\left| \vec{a} \cdot \vec{b} \right|}{\|\vec{b}\|}
$$

And also:

$$
k = \|\vec{b}\| \cos \theta
$$



#### 叉积（向量积）Cross (vector) Product
- 叉积与两个初始向量正交
- 方向由右手定则确定
- 有助于构建坐标系

##### 特性

$$
\vec{x} \times \vec{y} = +\vec{z}
$$

$$
\vec{y} \times \vec{x} = -\vec{z}
$$

$$
\vec{y} \times \vec{z} = +\vec{x}
$$

$$
\vec{z} \times \vec{y} = -\vec{x}
$$

$$
\vec{z} \times \vec{x} = +\vec{y}
$$

$$
\vec{x} \times \vec{z} = -\vec{y}
$$

$$
\vec{a} \times \vec{b} = -\vec{b} \times \vec{a}
$$

$$
\vec{a} \times \vec{a} = \vec{0}
$$

$$
\vec{a} \times (\vec{b} + \vec{c}) = \vec{a} \times \vec{b} + \vec{a} \times \vec{c}
$$

$$
\vec{a} \times (k \vec{b}) = k (\vec{a} \times \vec{b})
$$

##### 笛卡尔公式

$$
\vec{a} \times \vec{b} =
\begin{vmatrix}
\hat{i} & \hat{j} & \hat{k} \\
x_a & y_a & z_a \\
x_b & y_b & z_b
\end{vmatrix}= \begin{pmatrix}
y_a z_b - y_b z_a \\
z_a x_b - x_a z_b \\
x_a y_b - y_a x_b
\end{pmatrix}
$$


$$
\vec{a} \times \vec{b} = A^* \vec{b} =
\begin{pmatrix}
0 & -z_a & y_a \\
z_a & 0 & -x_a \\
-y_a & x_a & 0
\end{pmatrix}
\begin{pmatrix}
x_b \\
y_b \\
z_b
\end{pmatrix}
$$

##### 图形学中的叉积
- 确定左/右
- 确定内/外


#### 正交基础/坐标系 Orthonormal Bases / Coordinate Frames
- 对于表示点、位置和地点非常重要
- 通常，有多组坐标系
  - 全局、局部、世界、模型、模型部分（头部、手部等）
- 关键问题是在这些系统/基准之间的转换

##### 正交坐标系中的框架
任意 3 个向量（三维空间）的集合

$$
k \vec{u} = k \vec{v} = k \vec{w}
$$

$$
\|\vec{k}\| = 1
$$

$$
\vec{u} \cdot \vec{v} = \vec{v} \cdot \vec{w} = \vec{u} \cdot \vec{w} = 0
$$

$$
\vec{w} = \vec{u} \times \vec{v} \quad \text{(right-handed)}
$$

$$
\vec{p} = (\vec{p} \cdot \vec{u}) \vec{u} + (\vec{p} \cdot \vec{v}) \vec{v} + (\vec{p} \cdot \vec{w}) \vec{w} \quad \text{(projection)}
$$


## 矩阵
- 神奇的二维数组，萦绕在每一门计算机科学课程中
- 在图形学中，广泛用于表示变换
  - 平移、旋转、剪切、缩放

### 矩阵概念
- 数字数组（m × n = m 行，n 列）
- 标量的加法和乘法很简单：
逐个元素

$$
\begin{pmatrix}
1 & 3 \\
5 & 2 \\
0 & 4
\end{pmatrix}
$$

### 矩阵-矩阵乘法
A 中的列数必须 = B 中的行数
(M x **N**) (**N** x P) = (M x P)

$$
\begin{pmatrix}
1 & 3 \\
5 & 2 \\
0 & 4
\end{pmatrix}
\begin{pmatrix}
3694 \\
2783
\end{pmatrix}=\begin{pmatrix}
1 \times 3694 + 3 \times 2783 \\
5 \times 3694 + 2 \times 2783 \\
0 \times 3694 + 4 \times 2783
\end{pmatrix}
$$

乘积中的元素 (i, j) 是 A 元素第 i 行与 B 元素第 j 列的点积

#### 性质
- 非交换律
（AB 和 BA 通常不同）
- 结合律和分配律

$$
(AB)C = A(BC)
$$

$$
A(B + C) = AB + AC
$$

$$
(A + B)C = AC + BC
$$

### 矩阵-向量乘法
将向量视为列矩阵 (m×1)

点变换的关键

关于 y 轴的二维反射

$$
\begin{pmatrix}
0 & 1 \\
1 & 0
\end{pmatrix}
\begin{pmatrix}
x \\
y\end{pmatrix}=\begin{pmatrix}-y \\
x\end{pmatrix}
$$

### 矩阵的转置
交换行和列 (ij -> ji)

$$
\begin{pmatrix}
1 & 2 \\
3 & 4 \\
5 & 6
\end{pmatrix}^T=\begin{pmatrix}
1 & 3 & 5 \\
2 & 4 & 6
\end{pmatrix}
$$

#### 性质

$$
(AB)^T = B^T A^T
$$

### 单位矩阵及其逆

$$
I_{3 \times 3} =
\begin{pmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{pmatrix}
$$

$$
AA^{-1} = A^{-1}A = I
$$

$$
(AB)^{-1} = B^{-1}A^{-1}
$$

### 矩阵形式的向量乘法
#### 点乘

$$
\vec{a} \cdot \vec{b} = \vec{a}^T \vec{b}
= \begin{pmatrix}
x_a & y_a & z_a
\end{pmatrix}
\begin{pmatrix}
x_b \\
y_b \\
z_b
\end{pmatrix}
= x_a x_b + y_a y_b + z_a z_b
$$

#### 叉乘

$$
\vec{a} \times \vec{b} = A^* \vec{b} =
\begin{pmatrix}
0 & -z_a & y_a \\
z_a & 0 & -x_a \\
-y_a & x_a & 0
\end{pmatrix}
\begin{pmatrix}
x_b \\
y_b \\
z_b
\end{pmatrix}
$$

# 变换 Transformation
## 为何学习变换
###  建模
- 建模：平移 Modeling: translation
- 建模：旋转 Modeling: rotation
- 建模：缩放 Modeling: scaling
### 视图
- 视图：（3D 到 2D）投影 Viewing: (3D to 2D) projection

## 二维变换
### 用矩阵表示变换
#### 缩放变换
##### 缩放

$$
\text{scale}' = S \, \text{scale}
$$

##### 缩放变换

$$
x' = s_x \, x \\
y' = s_y \, y
$$

##### 缩放矩阵

$$
\begin{pmatrix}
x' \\
y'
\end{pmatrix}=\begin{pmatrix}
0 & s \\
s & 0\end{pmatrix}\begin{pmatrix}
x \\
y\end{pmatrix}
$$

##### 非均匀缩放

$$
\begin{pmatrix}
x' \\
y'
\end{pmatrix}=\begin{pmatrix}
s_x & 0 \\
0 & s_y
\end{pmatrix}
\begin{pmatrix}
x \\
y
\end{pmatrix}
$$

##### 反射矩阵

$$
\begin{pmatrix}
x' \\
y'
\end{pmatrix}=\begin{pmatrix}
-1 & 0 \\
0  & 1\end{pmatrix}\begin{pmatrix}
x \\
y
\end{pmatrix}
$$

##### 剪切矩阵 Shear Matrix

$$
\begin{pmatrix}
x' \\
y'\end{pmatrix}=\begin{pmatrix}
1 & a \\
0 & 1
\end{pmatrix}
\begin{pmatrix}
x \\
y
\end{pmatrix}
$$

y=0 时水平位移为 0
y=1 时水平位移为 a
垂直位移始终为 0

##### 旋转矩阵

$$
\begin{pmatrix}
x' \\
y'
\end{pmatrix}=\begin{pmatrix}
\cos\theta & -\sin\theta \\
\sin\theta & \cos\theta
\end{pmatrix}
\begin{pmatrix}
x \\
y
\end{pmatrix}
$$

#### 线性变换
**线性变换=矩阵（相同维度）**
展开写法

$$
x' = a x + b y \\
y' = c x + d y
$$

二维一般线性变换公式

$$
\begin{pmatrix}
x' \\
y'\end{pmatrix}=\begin{pmatrix}
a & b \\
c & d\end{pmatrix}\begin{pmatrix}
x \\
y\end{pmatrix}
$$

矩阵乘法简记

$$
\mathbf{x'} = M \mathbf{x}
$$



## 齐次坐标 Homogeneous Coordinates
### 为什么要用齐次坐标
- 平移不能用矩阵形式表示
  - 平移不是线性变换
- 但我们不希望平移成为一种特殊情况
- 是否有一种统一的方式来表示所有转换？
（以及成本是多少？）
  - 解决方案：齐次坐标

### 齐次坐标定义
添加第三个坐标（w 坐标）
- 二维点 = (x, y, 1)T
- 二维向量 = (x, y, 0)T

平移的矩阵表示

$$
\begin{pmatrix}
x' \\
y' \\
1\end{pmatrix}=\begin{pmatrix}
1 & 0 & t_x \\
0 & 1 & t_y \\
0 & 0 & 1
\end{pmatrix}
\begin{pmatrix}
x \\
y \\
1\end{pmatrix}=\begin{pmatrix}
x + t_x \\
y + t_y \\
1\end{pmatrix}
$$

如果结果的 w 坐标为 1 或 0，则运算有效
- 向量 + 向量 = 向量
- 点 - 点 = 向量
- 点 + 向量 = 点
- 点 + 点 = ??

$$
\begin{pmatrix}
w \\
x \\
y \\
1\end{pmatrix}
\ \text{(in homogeneous coordinates)}
\ \rightarrow\ 
\begin{pmatrix}
x/w \\
y/w \\
1\end{pmatrix}
\ \text{(in Cartesian coordinates),\ where\ } w \neq 0
$$

## 仿射变换 Affine Transformations
仿射映射 = 线性映射 + 平移

$$
\begin{pmatrix}
x' \\
y'
\end{pmatrix}=\begin{pmatrix}
a & b \\
c & d
\end{pmatrix}
\begin{pmatrix}
x \\
y\end{pmatrix}
+\begin{pmatrix}
t_x \\
t_y
\end{pmatrix}
$$

使用齐次坐标：

$$
\begin{pmatrix}
x' \\
y' \\
1\end{pmatrix}=\begin{pmatrix}
a & b & t_x \\
c & d & t_y \\
0 & 0 & 1
\end{pmatrix}
\begin{pmatrix}
x \\
y \\
1\end{pmatrix}
$$

## 二维变换 2D Transformations
### 缩放 Scale

$$
S(s_x, s_y) =
\begin{pmatrix}
s_x & 0   & 0 \\
0   & s_y & 0 \\
0   & 0   & 1
\end{pmatrix}
$$

### 旋转 Rotation

$$
R(\alpha) =
\begin{pmatrix}
\cos\alpha & -\sin\alpha & 0 \\
\sin\alpha & \cos\alpha  & 0 \\
0          & 0           & 1
\end{pmatrix}
$$

### 平移 Translation

$$
T(t_x, t_y) =
\begin{pmatrix}
1 & 0 & t_x \\
0 & 1 & t_y \\
0 & 0 & 1
\end{pmatrix}
$$

### 逆变换 Inverse Transform

$$
M^{-1}
$$

是矩阵和几何意义上的变换的逆


### 组合变换 Composing Transforms
**变换顺序很重要**
矩阵乘法不满足交换律

$$
R_{45} \cdot T(1, 0) \cdot M 
\neq 
T(1, 0) \cdot R_{45} \cdot M
$$

**注意，矩阵是从右到左应用的**

$$
T(1,0) \cdot R_{45^\circ} \cdot
\begin{pmatrix}
x \\
y \\
1\end{pmatrix}=\begin{pmatrix}
1 & 0 & 1 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{pmatrix}
\begin{pmatrix}
\cos 45^\circ & -\sin 45^\circ & 0 \\
\sin 45^\circ &  \cos 45^\circ & 0 \\
0             &  0             & 1
\end{pmatrix}
\begin{pmatrix}
x \\
y \\
1\end{pmatrix}
$$

仿射变换序列 A1, A2, A3, ...
- 通过矩阵乘法组合
  - 对性能至关重要！

$$
A_n \left( \cdots A_2 \left( A_1 
\begin{pmatrix}
x \\
y \\
1
\end{pmatrix}
\right) \cdots \right)=A_n \cdots A_2 A_1
\begin{pmatrix}
x \\
y \\
1
\end{pmatrix}
$$

预乘 n 个矩阵，得到一个表示组合变换的矩阵

#### 分解复杂变换
如何绕给定点 c 旋转？
1. 将中心平移至原点
2. 旋转
3. 平移回原点

$$
T(\mathbf{c}) \cdot R(\alpha) \cdot T(-\mathbf{c})
=\begin{pmatrix}
1 & 0 & c_x \\
0 & 1 & c_y \\
0 & 0 & 1
\end{pmatrix}
\begin{pmatrix}
\cos\alpha & -\sin\alpha & 0 \\
\sin\alpha &  \cos\alpha & 0 \\
0          &  0          & 1
\end{pmatrix}
\begin{pmatrix}
1 & 0 & -c_x \\
0 & 1 & -c_y \\
0 & 0 & 1
\end{pmatrix}
$$


## 三维变换 3D Transforms
同样使用齐次坐标

$$
\text{3D Point} = 
\begin{pmatrix}
x \\
y \\
z \\
1
\end{pmatrix}
$$

$$
\text{3D Vector} = 
\begin{pmatrix}
x \\
y \\
z \\
0
\end{pmatrix}
$$

使用 4×4 矩阵进行仿射变换
$$
\begin{pmatrix}
x' \\
y' \\
z' \\
1
\end{pmatrix}=\begin{pmatrix}
a & b & c & t_x \\
d & e & f & t_y \\
g & h & i & t_z \\
0 & 0 & 0 & 1
\end{pmatrix}
\begin{pmatrix}
x \\
y \\
z \\
1
\end{pmatrix}
$$


### 缩放

$$
S(s_x, s_y, s_z) =
\begin{pmatrix}
s_x & 0 & 0 & 0 \\
0 & s_y & 0 & 0 \\
0 & 0 & s_z & 0 \\
0 & 0 & 0 & 1
\end{pmatrix}
$$

### 平移

$$
T(t_x, t_y, t_z) =
\begin{pmatrix}
1 & 0 & 0 & t_x \\
0 & 1 & 0 & t_y \\
0 & 0 & 1 & t_z \\
0 & 0 & 0 & 1
\end{pmatrix}
$$

### 旋转
#### 绕 x、y 或 z 轴旋转
绕 x 轴旋转

$$
R_x(\alpha) =
\begin{pmatrix}
1 & 0 & 0 & 0 \\
0 & \cos\alpha & -\sin\alpha & 0 \\
0 & \sin\alpha & \cos\alpha & 0 \\
0 & 0 & 0 & 1
\end{pmatrix}
$$

绕 y 轴旋转

$$
R_y(\alpha) =
\begin{pmatrix}
\cos\alpha & 0 & \sin\alpha & 0 \\
0 & 1 & 0 & 0 \\
-\sin\alpha & 0 & \cos\alpha & 0 \\
0 & 0 & 0 & 1
\end{pmatrix}
$$

绕 z 轴旋转

$$
R_z(\alpha) =
\begin{pmatrix}
\cos\alpha & -\sin\alpha & 0 & 0 \\
\sin\alpha & \cos\alpha & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1
\end{pmatrix}
$$

#### 组合旋转矩阵

$$
R_{xyz}(\alpha, \beta, \gamma) = R_x(\alpha) \cdot R_y(\beta) \cdot R_z(\gamma)
$$

#### 欧拉角 Euler angles
- 常用于飞行模拟器：滚转 roll、俯仰 pitch、偏航 yaw

#### 罗德里格斯的旋转公式
Rodrigues’ Rotation Formula

绕轴 n 旋转角度 α

$$
R(\mathbf{n}, \alpha) = \cos(\alpha) I + (1 - \cos(\alpha)) \mathbf{n} \mathbf{n}^T + \sin(\alpha)
\begin{pmatrix}
0 & -n_z & n_y \\
n_z & 0 & -n_x \\
-n_y & n_x & 0
\end{pmatrix}
$$


## 观测变换 Viewing transformation
### 视图/相机变换 View / Camera Transformation
##### 什么是视图变换
思考如何拍摄照片
- 找到一个好的位置并安排好人物（模型变换）
- 找到一个合适的“角度”来放置相机（视图变换）
- 茄子！（投影变换）

##### 如何执行视图转换
首先定义摄像机
- 位置

$$
\vec{e}
$$

- 观察/注视方向

$$
\hat{g}
$$

- 向上方向
（假设观察者为观察者）

$$
\hat{t}
$$

关键观察
- 如果相机和所有物体同时移动，“照片”将会是相同的

我们总是将相机变换到
- 原点，Y 轴向上，Z 轴向右
- 物体也跟着相机变换


变换相机M_view
- 因此它位于原点，在 Y 上，看 -Z

数学中的 M_view

$$
M_{view} = R_{view} T_{view}
$$

- 将 e 平移到原点

$$
T_{view} =
\begin{pmatrix}
1 & 0 & 0 & -x_e \\
0 & 1 & 0 & -y_e \\
0 & 0 & 1 & -z_e \\
0 & 0 & 0 & 1
\end{pmatrix}
$$

- 将 g 旋转到 -Z 轴
- 将 t 旋转到 Y 轴
- 将 (g x t) 旋转到 X 轴
- 考虑其逆旋转：X 到 (g x t)，Y 到 t，Z 到 -g


#### 视图/相机变换总结
- 与相机一起变换物体
- 直到相机位于原点，Y 轴向上，Z 轴向下
- 也称为模型视图变换
- 用于投影变换！


### 投影变换 Projection transformation 
计算机图形学中的投影
- 3D 到 2D
- 正交投影
- 透视投影

#### 正交变换 Orthographic projection 
简单的理解方式
- 相机位于原点，视角为-Z轴，视角为Y轴
- 降低Z轴坐标
- 将生成的矩形平移并缩放至[-1, 1]²

一般来说
- 我们想要将长方体 [l, r] x [b, t] x [f, n] 映射到
“规范（正则、规范、标准）”立方体 [-1, 1]3

略有不同的顺序（与“简单方法”略有不同）
- 通过平移将长方体置于中心
- 缩放为“标准”立方体

变换矩阵
- 先平移（中心到原点），然后缩放（长/宽/高到 2）

$$
M_{ortho} =
\begin{pmatrix}
\frac{2}{r - l} & 0 & 0 & \frac{-(r + l)}{r - l} \\
0 & \frac{2}{t - b} & 0 & \frac{-(t + b)}{t - b} \\
0 & 0 & \frac{2}{n - f} & \frac{-(n + f)}{n - f} \\
0 & 0 & 0 & 1
\end{pmatrix}
$$

警告
- 沿 -Z 轴观察 / 会使近处和远处的判断不直观 (n > f)
- 仅供参考：这就是为什么 OpenGL（一种图形 API）使用左手坐标系


#### 透视变换 Perspective projection
在计算机图形学、艺术和视觉系统中最常见
- 远处的物体较小
- 平行线不平行；汇聚于一点

回顾齐次坐标的性质
- (x, y, z, 1)、(kx, ky, kz, k != 0)、(xz, yz, z2, z != 0) 均表示三维空间中的同一点 (x, y, z)
- 例如，(1, 0, 0, 1) 和 (2, 0, 0, 2) 均表示 (1, 0, 0)。

##### 如何进行透视投影
- 首先将视锥体“挤压”成长方体 (n -> n, f -> f) (M_persp->ortho)
- 进行正交投影（M_ortho，已为人所知！）

为了找到变换
- 回顾关键思想：找到变换后的点 (x’, y’, z’) 与原始点 (x, y, z) 之间的关系

$$
y' = \frac{n}{z} y
$$

$$
x' = \frac{n}{z} x \quad (\text{similar to } y')
$$

在齐次坐标中

$$
\begin{pmatrix}
x \\
y \\
z \\
1
\end{pmatrix}=\begin{pmatrix}
\frac{n_x}{z} \\
\frac{n_y}{z} \\
\text{unknown} \\
1
\end{pmatrix}
$$

因此“挤压”（透视到正交）投影可以实现这一点

$$
M_{persp} = 
\begin{pmatrix}
\frac{n_x}{z} & 0 & 0 & 0 \\
0 & \frac{n_y}{z} & 0 & 0 \\
0 & 0 & \frac{1}{z} & 0 \\
0 & 0 & 0 & 1
\end{pmatrix}
$$

$$
\begin{pmatrix}
x' \\
y' \\
z' \\
1
\end{pmatrix}=
M_{persp} \cdot 
\begin{pmatrix}
x \\
y \\
z \\
1\end{pmatrix}=\begin{pmatrix}
\frac{n_x}{z} \\
\frac{n_y}{z} \\
\text{unknown} \\
z\end{pmatrix}
$$

$$
M_{persp\_ortho} =
\begin{pmatrix}
n & 0 & 0 & 0 \\
0 & n & 0 & 0 \\
\text{?} & \text{?} & \text{?} & \text{?} \\
0 & 0 & 0 & 1
\end{pmatrix}
$$

观察：第三行负责 z'
- 近平面上的任何点都不会改变
- 远平面上任何点的 z 值都不会改变


近平面上的任何一点都不会改变
所以第三行必须是 (0 0 A B) 的形式

$$
\begin{pmatrix}
0 & 0 & A & B
\end{pmatrix}
\begin{pmatrix}
x \\
n \\
y \\
1
\end{pmatrix}
= n^2
$$

那么近平面的 l、r、b、t 分别是多少？
- 如果明确指定，很好
- 有时人们更喜欢：
垂直视场 (fovY) 和
长宽比
（假设对称，即 l = -r，b = -t）

如何将 fovY 和aspect 转换为 l、r、b、t？
- 简单

$$
\tan \left( \frac{\text{fovY}}{2} \right) = \frac{t}{|n|}
$$

$$
\text{aspect} = \frac{r}{t}
$$

#### MVP 之后是什么
- 模型变换（放置物体）--M
- 视图变换（放置相机）--V
- 投影变换 --P
  - 正交投影（长方体到“标准”立方体 [-1, 1]3）
  - 透视投影（平截头体到“标准”立方体）
- 标准立方体到？



# 光栅化 Rasterization
#### 标准立方体到屏幕
- 什么是屏幕？
  - 像素数组
  - 数组大小：分辨率
  - 典型的光栅显示
- 光栅 == 德语中的屏幕
  - 光栅化 == 在屏幕上绘制
- 像素（仅供参考，“图像元素”的缩写）
  - 目前：像素是一个具有均匀颜色的小方块
  - 颜色是（红、绿、蓝）的混合

定义屏幕空间 *与“老虎书”略有不同*
- 像素的索引形式为 (x, y)，其中 x 和 y 均为整数
- 像素的索引从（0, 0）到（宽度 - 1，高度 - 1）
- 像素 (x, y) 的中心位置为(x + 0.5, y + 0.5)
- 屏幕覆盖范围(0, 0) 到 (宽度, 高度)

- 与 z 轴无关
- 在 xy 平面上变换：[-1, 1]² 为 [0, width] x [0, height]
- 视口变换矩阵

$$
M_{\text{viewport}} =
\begin{pmatrix}
\frac{\text{width}}{2} & 0 & 0 & \frac{\text{width}}{2} \\
0 & \frac{\text{height}}{2} & 0 & \frac{\text{height}}{2} \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1
\end{pmatrix}
$$

下一步：将三角形栅格化为像素

## 三角形
### 绘图机器
- CNC Sharpie 绘图机
- 激光切割机

### 不同的光栅显示
- 示波器 Oscilloscope
- 示波器艺术 Oscilloscope Art
- 阴极射线管 Cathode Ray Tube
- 电视 - 光栅显示器 CRT Television - Raster Display CRT
- 帧缓冲器：光栅显示的内存 Frame Buffer: Memory for a Raster Display
- 平板显示器 Flat Panel Displays
- LCD（液晶显示器）像素 LCD (Liquid Crystal Display) Pixel
  - 原理：通过扭转偏振来阻挡或透射光线
  - 背光照明（例如荧光灯或LED）
  - 通过部分扭转实现中等强度
- LED阵列显示屏 LED Array Display
- 电泳（电子墨水）显示器 Electrophoretic (Electronic Ink) Display

### 光栅化：绘制到光栅显示器
- 多边形网格 Polygon Meshes
- 三角形网格 Triangle Meshes

### 三角形 - 基本形状基元
#### 为什么是三角形？
- 最基本的多边形
- 拆分其他多边形

#### 独特属性
- 保证平面性
- 内部定义明确
- 三角形顶点插值方法明确（重心插值）

哪些像素值近似于三角形？
- 输入：三角形顶点在屏幕上的投影位置
- 输出：一组近似三角形的像素值



### 简单方法：采样
#### 函数采样
在某一点求函数值就是采样

我们可以通过采样来离散化函数
```
for (int x = 0; x < xmax; ++x)
  output[x] = f(x);
```
采样是图形学的核心思想

我们采样时间（一维）、面积（二维）、方向（二维）、体积（三维）……

##### 光栅化作为二维采样
- 如果每个像素中心位于三角形内则进行采样
- 定义二元函数：inside(tri, x, y)

$$
\text{inside}(t, x, y) =
\begin{cases}
1, & \text{如果点 } (x, y) \text{ 在三角形 } t \text{ 内} \\
0, & \text{否则}
\end{cases}
$$

光栅化 = 采样二维指示函数
```
for (int x = 0; x < xmax; ++x) 
  for (int y = 0; y < ymax; ++y) 
    image[x][y] = inside(tri, 
                        x + 0.5, 
                        y + 0.5);
```

评估 inside（tri，x，y）
- 边缘情况
- 检查屏幕上的所有像素？
- 增量三角形遍历（更快？）

### 真实显示器上的光栅化
真实的液晶屏像素（特写）Real LCD Screen Pixels (Closeup)

锯齿 Aliasing（锯齿 Jaggies）


## 抗锯齿 Antialiasing
采样在计算机图形学中无处不在
- 光栅化 = 采样 2D 位置
- 照片 = 采样图像传感器平面
- 视频 = 采样时间

### 采样伪影（错误/失误/不准确）
- 锯齿状（楼梯图案）– 空间采样
- 成像中的莫尔条纹 – 欠采样图像
- 马车轮错觉（假运动）– 时间采样

混叠伪像的背后原因
**信号变化太快（高频），但采样速度太慢**

### 抗锯齿思路：采样前模糊（预滤波）
#### 频域 Frequency Domain
##### 傅里叶变换
将函数表示为正弦和余弦的加权和

$$
f(x) = \frac{A}{2} + \frac{2A \cos(t\theta)}{\pi} - \frac{2A \cos(3t\theta)}{3\pi} + \frac{2A \cos(5t\theta)}{5\pi} - \frac{2A \cos(7t\theta)}{7\pi} + \cdots
$$

傅里叶变换将信号分解为频率

$$
F(\omega) = \int_{-1}^{1} f(x) e^{-2\pi i \omega x} \, dx
$$

$$
f(x) = \int_{-1}^{1} F(\omega) \, e^{2\pi i \omega x} \, d\omega
$$

$$
e^{ix} = \cos x + i \sin x
$$

更高的频率需要更快的采样
- 低频信号：充分采样以便合理重构
- 高频信号采样不足：重建结果错误地显示为来自低频信号

欠采样造成频率混叠
- 高频信号采样不足：样本错误地看起来像来自低频信号
- 在给定采样率下无法区分的两个频率,被称为“混叠”


##### 过滤
过滤 = 去除某些频率成分
- 可视化图像频率内容
- 仅滤除低频（边缘）
- 滤除高频（模糊）
- 滤除低频和高频

过滤 = 卷积（= 平均）
卷积: “滑动窗口”中的逐点局部平均

卷积定理
时域中的卷积等于频域中的乘法，反之亦然
时域卷积 = 频域乘法
时域乘法 = 频域卷积

选项 1：
- 在空域中进行卷积滤波
选项 2：
- 变换至频域（傅里叶变换）
- 与卷积核的傅里叶变换相乘
- 变换回空域（逆傅里叶变换）

盒子函数 = “低通”滤波器
更宽的滤波核 = 更低的频率

采样 = 重复频率内容
混叠 = 混合频率内容

### 抗锯齿
#### 如何减少混叠误差？
##### 选项1：提高采样率
- 本质上是增加傅里叶域中副本之间的距离
- 更高分辨率的显示器、传感器、帧缓冲区……
- 但是：成本高昂且可能需要非常高的分辨率
##### 选项2：抗混叠
- 在重复之前使傅里叶内容“更窄”
- 即在采样前滤除高频

抗锯齿 = 限制，然后重复

#### 实用的前置过滤器
1像素宽度的盒式滤波器（低通、模糊）

#### 通过像素区域中的平均值进行抗锯齿
解决方案：
- 将 f(x,y) 与 1 像素的盒状模糊进行卷积
- 卷积 = 滤波 = 平均
- 然后在每个像素的中心进行采样

#### 通过计算平均像素值进行抗锯齿
在光栅化一个三角形时，f(x,y) = inside(triangle,x,y) 的像素区域内的平均值等于三角形覆盖的像素面积


### 超级采样抗锯齿 (MSAA)
通过对像素内的多个位置进行采样并取平均值来近似 1 像素盒式滤波器的效果

点采样：每个像素一个样本

#### 超级采样步骤
- 步骤1：在每个像素中进行 NxN 次采样。
- 步骤2：对每个像素“内部”的 NxN 个样本进行平均
- 结果：显示器发出的相应信号

### 抗锯齿的现状
天下没有免费的午餐！
- MSAA 的成本是多少？
里程碑
- FXAA（快速近似抗锯齿）
- TAA（时间抗锯齿）
超分辨率/超级采样
- 从低分辨率到高分辨率
- 本质上仍然存在“样本不足”的问题
- DLSS（深度学习超级采样）

## 可见性Visibility /遮挡occlusion
### 画家算法
- 灵感源自画家的绘画方式
- 从后向前绘制，在帧缓冲区中覆盖
- 需要深度排序（n 个三角形，复杂度为 O(n log n)）
- 可能存在无法解析的深度顺序

### Z 缓冲 Z-Buffering
这是最终获胜的算法
### 思路
- 存储每个样本（像素）的当前最小 z 值
- 需要额外的缓冲区来存储深度值
  - 帧缓冲区存储颜色值
  - 深度缓冲区（z 缓冲区）存储深度值

注意：为简单起见，我们假设z 值始终为正
（z 值越小 -> 更近，z 值越大 -> 更远）

### Z-Buffer算法
将深度缓冲区初始化为 ∞
光栅化期间：
```
for (each triangle T)
  for (each sample (x,y,z) in T)
    if (z < zbuffer[x,y]) // closest sample so far
      framebuffer[x,y] = rgb; // update color
      zbuffer[x,y] = z; // update depth
    else
      ; // do nothing, this sample is occluded
```

### Z-Buffer算法复杂度
复杂度
- 对于 n 个三角形，复杂度为 O(n)（假设覆盖率恒定）
- 如何在线性时间内对 n 个三角形进行排序？
  - 以不同的顺序绘制三角形？

**最重要的可见性算法**
- 已在所有 GPU 上硬件实现

# 着色 Shading
## 定义
韦氏词典： 用平行线或色块使插图或图表变暗或着色

可简单认为着色是将材料应用于物体的过程

## 光照与基本着色模型
### Blinn-Phong反射模型
感知观察
- 镜面高光
- 漫反射
- 环境光

#### 着色是局部的
计算特定着色点处反射至相机的光线

##### 输入
- 观察者方向 v
- 表面法线 n
- 光线方向 l
（针对多个光源）
- 表面参数
（颜色、光泽度等）

**不会产生阴影！（阴影≠阴影）**

#### 漫反射 Diffuse Reflection
光线向各个方向均匀散射
- 所有观察方向的表面颜色均相同

但究竟接收了多少光（能量）呢？
- 朗伯余弦定律 Lambert’s cosine law
  - 立方体顶面接收一定量的光
  - 60度旋转的立方体顶面遮挡了一半的光线
  - 一般而言，单位面积的光通量与 cos θ = l • n 成正比


光衰减 Light Falloff

##### 朗伯（漫反射）着色
着色不受视线方向影响

公式

$$
L_d = k_d \left( \frac{I}{r^2} \right) \max(0, \mathbf{n} \cdot \mathbf{l})
$$

符号说明

| 符号                          | 含义                             |
|:----------------------------|:--------------------------------|
| \(L_d\)                      | 漫反射光照强度（Diffuse Lighting） |
| \(k_d\)                      | 材质的漫反射系数（Diffuse Reflectivity） |
| \(I\)                        | 光源强度（Light Intensity）         |
| \(r\)                        | 点到光源的距离（Distance to Light Source） |
| \(\mathbf{n}\)               | 表面的法向量（Normal Vector at the Point） |
| \(\mathbf{l}\)               | 指向光源的单位向量（Normalized Light Direction Vector） |
| \(\max(0, \mathbf{n} \cdot \mathbf{l})\) | 法线与光线夹角余弦值和 0 的较大者，用于避免背面受光 |

产生漫射外观

#### 镜面反射 Specular
强度**取决于**视线方向
- 镜面反射方向附近光线明亮

V 接近镜像方向 <==>半向量接近法线
- 通过单位向量点积测量“近”


镜面反射光照公式

$$
L_s = k_s \left(\frac{I}{r^2}\right) \max(0, \cos \alpha)^p
= k_s \left(\frac{I}{r^2}\right) \max(0, \mathbf{n} \cdot \mathbf{h})^p
$$

符号说明

| 符号                                | 含义                                |
|:------------------------------------|:------------------------------------|
| \(L_s\)                             | 镜面反射光照强度（Specular Lighting） |
| \(k_s\)                             | 材质的镜面反射系数（Specular Reflectivity） |
| \(I\)                               | 光源强度（Light Intensity）          |
| \(r\)                               | 点到光源的距离（Distance to Light Source） |
| \(\alpha\)                          | 视线方向与反射方向的夹角（Angle between View Direction and Reflection） |
| \(p\)                               | 高光指数（Shininess Exponent）       |
| \(\mathbf{n}\)                     | 表面的法向量（Normal Vector）

余弦幂增加 p 值可缩小反射瓣

#### 环境光 Ambient
不依赖任何因素的阴影
- 添加恒定颜色以解释忽略的照明并填充黑色阴影
- 这是近似的/假的！


环境光照公式

$$
L_a = k_a I_a
$$

符号说明

| 符号       | 含义                            |
|:-----------|:--------------------------------|
| \(L_a\)    | 环境光照强度（Ambient Lighting）|
| \(k_a\)    | 材质的环境光反射系数（Ambient Reflectivity）|
| \(I_a\)    | 环境光强度（Ambient Light Intensity）|


### Blinn-Phong反射模型
Ambient + Diffuse + Specular = Blinn-Phong  Reflection

Phong 光照模型公式

$$
L = L_a + L_d + L_s
$$

展开为：

$$
L = k_a I_a + k_d \left(\frac{I}{r^2}\right) \max(0, \vec{n} \cdot \vec{l}) + k_s \left(\frac{I}{r^2}\right) \max(0, \vec{n} \cdot \vec{h})^p
$$

符号说明

| 符号       | 含义                                    |
|:-----------|:----------------------------------------|
| \(L\)       | 最终像素亮度值                          |
| \(L_a\)     | 环境光分量                               |
| \(L_d\)     | 漫反射分量                               |
| \(L_s\)     | 镜面反射分量                             |
| \(k_a\)     | 材质环境光反射系数                       |
| \(I_a\)     | 环境光强度                               |
| \(k_d\)     | 材质漫反射反射系数                       |
| \(k_s\)     | 材质镜面反射系数                         |
| \(I\)       | 点光源强度                               |
| \(r\)       | 光源到表面点的距离                       |
| \(\vec{n}\) | 表面法线单位向量                         |
| \(\vec{l}\) | 指向光源方向的单位向量                   |
| \(\vec{h}\) | 半角向量（视线方向与光源方向的中间向量）|
| \(p\)       | 镜面高光的反射强度控制指数               |


## 着色频率 Shading Frequencies
### 平面着色
为每个三角形添加阴影
- 三角形面是平面的——只有一个法线向量
- 不适用于光滑表面

### Gouraud 着色
为每个顶点着色
- 从三角形内的各个顶点插入颜色
- 每个顶点都有一个法向量

### Phong 着色
为每个像素着色
在每个三角形上插值法向量
- 计算每个像素的完整着色模型
- **注意不是 Blinn-Phong 反射模型**


### 定义每个顶点的法线向量
- 最好从底层几何体获取顶点法线
  - 例如，考虑一个球体
- 否则，必须从三角形面推断顶点法线
  - 简单方案：平均周围面的法线

### 定义每像素法线向量
顶点法线的重心插值

不要忘记对插值方向进行归一化


## 图形（实时渲染）管线 Graphics (Real-time Rendering) 
Pipeline

### 图形管线 Graphics Pipeline
这是现代 GPU 的主要渲染流程，分为几个阶段：
#### 整体流程
1. **Application阶段（应用阶段）**
   - 负责生成顶点数据，发送到图形管线
   - **输入**：3D 空间中的顶点数据（Vertex Stream）

2. **Vertex Processing阶段（顶点处理阶段）**
   - 对每个顶点进行变换（如模型、视图、投影变换）
   - 输出顶点在屏幕空间中的位置

3. **Triangle Processing阶段（顶点处理阶段）**
   - 将屏幕空间中的顶点组合成三角形
   - **输出**：三角形流（Triangle Stream）

4. **Rasterization阶段（光栅化阶段）**
   - 将三角形转化为像素覆盖的片元（Fragment）
   - **输出**：片元流（Fragment Stream）

5. **Fragment Processing阶段（片元处理阶段）**
   - 对每个片元进行着色、纹理采样、光照计算等
   - **输出**：着色后的片元（Shaded Fragments）

6. **Framebuffer Operations阶段（帧缓冲操作阶段）**
   - 对着色后的片元进行深度测试、混合等操作，写入帧缓冲区
   - **输出**：最终图像像素

7. **Display（显示阶段）**
   - 将帧缓冲区的图像显示在屏幕上

#### 数据流说明
| 阶段               | 输入                         | 输出                      |
|:------------------|:----------------------------|:--------------------------|
| Application 应用        | 3D 顶点数据                  | 顶点流（Vertex Stream）    |
| Vertex Processing 顶点处理   | 顶点流                       | 屏幕空间顶点               |
| Triangle Processing 三角形组装 | 屏幕空间顶点                 | 三角形流（Triangle Stream）|
| Rasterization 光栅化      | 三角形流                     | 片元流（Fragment Stream）  |
| Fragment Processing 片元处理  | 片元流                       | 着色片元（Shaded Fragments）|
| Framebuffer Operations 帧缓冲操作| 着色片元                     | 像素（Pixels）             |
| Display 显示              | 像素数据                     | 屏幕显示图像               |



### 着色器程序
- 编写顶点和片段处理阶段的程序
- 描述单个顶点（或片段）的操作

GLSL 片段着色器程序示例
```
uniform sampler2D myTexture; // program parameter
uniform vec3 lightDir; // program parameter 
varying vec2 uv; // per fragment value (interp. by rasterizer) 
varying vec3 norm; // per fragment value (interp. by rasterizer)
void diffuseShader() 
{ 
  vec3 kd; 
  kd = texture2d(myTexture, uv); // material color from texture
  kd *= clamp(dot(–lightDir, norm), 0.0, 1.0); // Lambertian shading model
  gl_FragColor = vec4(kd, 1.0); // output fragment color
}
```

着色器函数每个片段执行一次
- 输出当前片段屏幕采样位置的表面颜色
- 此着色器执行纹理查找以获取该点的表面材质颜色，然后执行漫反射光照计算


#### Snail Shader Program
Inigo Quilez
Procedurally modeled, 800 line shader. 
http://shadertoy.com/view/ld3Gz2

#### Unreal Engine Kite Demo (Epic Games 2015)
目标：实时高度复杂的 3D 场景
- 场景中包含数十万到数百万个三角形
- 复杂的顶点和片段着色器计算
- 高分辨率（200-400 万像素 + 超级采样）
- 每秒 30-60 帧（VR 帧率更高）


### 图形管道实现：GPU
用于执行图形流水线计算的专用处理器
- Discrete GPU Card (NVIDIA GeForce Titan X)
- Integrated GPU: (Part of Intel CPU die)

GPU：异构多核处理器

## 纹理映射 Texture Mapping
表面是二维的
- 表面存在于三维世界空间中
- 每个三维表面点在二维图像（纹理）中也都有自己的位置

纹理应用于表面

纹理坐标 Texture Coordinates
每个三角形顶点都被分配一个纹理坐标 (u,v)

纹理可以多次使用！

### 跨三角形插值：重心坐标
为什么要进行插值？
- 指定顶点的值
- 获取跨三角形平滑变化的值

我们要插值什么？
- 纹理坐标、颜色、法向量……

我们如何进行插值？
- 重心坐标

### 重心坐标 Barycentric Coordinates
三角形坐标系(α, β, γ)

$$
(x, y) = \alpha A + \beta B + \gamma C
$$

$$
\alpha + \beta + \gamma = 1
$$

如果三个坐标都为非负值，则位于三角形内部

#### A(x, y) 的重心坐标是多少？

$$
(\alpha, \beta, \gamma) = (1, 0, 0)
$$

$$ 
(x, y) = \alpha A + \beta B + \gamma C = A
$$


#### 几何观点——比例面积

$$ \alpha = \frac{AA}{AA + AB + AC} $$

$$ \beta = \frac{AB}{AA + AB + AC} $$

$$ \gamma = \frac{AC}{AA + AB + AC} $$

#### 质心的重心坐标是多少？

$$(\alpha, \beta, \gamma) = \left( \frac{1}{3}, \frac{1}{3}, \frac{1}{3} \right)$$

$$(x, y) = \frac{1}{3} A + \frac{1}{3} B + \frac{1}{3} C$$

#### 重心坐标：公式

$$ \alpha = \frac{-(x - x_B)(y_C - y_B) + (y - y_B)(x_C - x_B)}{-(x_A - x_B)(y_C - y_B) + (y_A - y_B)(x_C - x_B)} $$

$$ \beta = \frac{-(x - x_C)(y_A - y_C) + (y - y_C)(x_A - x_C)}{-(x_B - x_C)(y_A - y_C) + (y_B - y_C)(x_A - x_C)} $$

$$ \gamma = 1 - \alpha - \beta $$

#### 使用重心坐标
在顶点处线性插值

$$ V = \alpha V_A + \beta V_B + \gamma V_C $$

V_A、V_B、V_C 可以是
位置、纹理
坐标、颜色、
法线、深度、
材质属性……

然而，重心坐标在投影下并不是不变的！

### 应用纹理
简单纹理映射：漫反射颜色 Diffuse Color

```
for each rasterized screen sample (x,y): // 通常是像素的中心
  (u,v) = evaluate texture coordinate at (x,y) // 使用重心坐标！
  texcolor = texture.sample(u,v);
  set sample’s color to texcolor; // 通常采用漫反射反照率K_d（回想一下Blinn-Phong反射模型）
```

### 纹理放大 Texture Magnification
如果纹理太小怎么办？
- 通常不希望出现这种情况——纹理分辨率不足

纹理上的像素 — 纹素 texel

#### 双线性插值 Bilinear Interpolation
双线性插值通常能以合理的成本获得相当好的结果


如果纹理太大怎么办？

超级采样有效吗？
- 可以，质量高，但成本高
- 高度最小化后，像素占用空间会包含许多纹素
- 像素中的信号频率过高
- 需要更高的采样频率
让我们换个角度来理解这个问题
- 如果不采样会怎样？
- 只需要获取一定范围内的平均值！

## 纹理抗锯齿Texture antialiasing (MIPMAP)
允许（快速、近似、方形）范围查询
“Mip” 源自拉丁语“multum in parvo”，意为小空间内的众多

计算 Mipmap 级别 D
使用相邻屏幕样本的纹理坐标估算纹理足迹

$$
D = \log_2 L
$$

$$
L = \max \left(
    \sqrt{\left( \frac{\partial u}{\partial x} \right)^2 + \left( \frac{\partial v}{\partial x} \right)^2},
    \sqrt{\left( \frac{\partial u}{\partial y} \right)^2 + \left( \frac{\partial v}{\partial y} \right)^2}
\right)
$$

### 三线性插值 Trilinear Interpolation
基于连续D值的线性插值

### 各向异性过滤
Ripmap 和面积总和表
- 可以查找轴对齐的矩形区域
- 对角线覆盖仍然是个问题

EWA 过滤
- 使用多重查找
- 加权平均
- Mipmap 层次结构仍然有用
- 可以处理不规则的覆盖


## 纹理的应用 Applications of Textures
纹理的多种用途
在现代 GPU 中，纹理 = 内存 + 范围查询（过滤）
- 将数据带入片段计算的通用方法

众多应用
- 环境光照
- 存储微几何体
- 程序化纹理
- 实体建模
- 体积渲染
- …





### 环境贴图 Environment Map
- 来自环境的光
- 使用环境进行渲染
#### 环境照明 Environmental Lighting
- 用于渲染真实光照
#### 球形环境贴图 Spherical Map
球形环境贴图存在的问题
- 容易变形（顶部和底部）
#### 立方体贴图Cube Map
一个向量沿着该方向映射到立方体点

立方体由 6 个方形纹理贴图构成
- 失真更少！
- 需要 dir->face 计算

#### 纹理会影响着色
- 纹理不必只代表颜色
- 如果它存储高度/法线会怎样？
- 凹凸/法线贴图
- 伪造详细的几何形状

#### 凹凸贴图
无需添加更多三角形即可添加表面细节
- 扰动每个像素的表面法线（仅用于着色计算）
- 纹理定义的每个纹素的“高度偏移”
- 如何修改法线矢量？

##### 如何扰动法线（在平面中）
- 原始表面法线 ```n(p) = (0, 1)```
- 在 p 点的导数为 ```dp = c * [h(p+1) - h(p)]```
- 扰动后的法线为 ```n(p) = (-dp, 1).normalized()```

##### 如何扰动法线（三维）
- 原始表面法线 ```n(p) = (0, 0, 1)```
- p 点处的导数为
  - ```dp/du = c1 * [h(u+1) - h(u)]```
  - ```dp/dv = c2 * [h(v+1) - h(v)]```
- 扰动后的法线为 ```n = (-dp/du, -dp/dv, 1).normalized()```
- 注意，这是在局部坐标系下！


##### 位移贴图
一种更高级的方法
- 使用与凹凸贴图相同的纹理
- 实际上移动的是顶点


### 3D程序噪声+实体建模
### 提供预计算着色
### 3D纹理和体积渲染

## 阴影 Shadow 
### 阴影映射 Shadow Mapping
#### 图像空间算法
- 阴影计算时无需了解场景几何形状
- 必须处理混叠伪影

#### 关键思想
- 不在阴影中的点必须同时被光线和相机看到

#### 算法渲染流程
##### 通道 1：从灯光渲染
来自光源的深度图像
##### 通道 2A：从眼睛渲染
眼睛拍摄的标准图像（带深度）

##### 通道 2B：投射到光源
将眼视图中的可见点投射回光源
- （重新投影）深度与光线和眼睛匹配。可见
- （重新投影）光线和眼睛的深度不一样。被遮挡了！！

#### 知名渲染技术
- 早期动画（例如《玩具总动员》）以及所有 3D 电子游戏的基本阴影技术

#### 阴影贴图问题
- 硬阴影（仅限点光源）
- 质量取决于阴影贴图分辨率
（基于图像的技术的普遍问题）
- 涉及浮点深度值的相等性比较
意味着比例、偏差和容差问题


# 几何体 Geometry
## 表示几何的多种方法
隐式
- 代数曲面
- 水平集
- 距离函数
- ...

显式
- 点云
- 多边形网格
- 细分，NURBS
- ...

每种选择都最适合不同的任务/几何类型

没有“最佳”表示——几何很难！
最佳表现取决于任务
### 几何的“隐式”表示
基于对点的分类
- 点满足某些特定关系

例如：球体：三维空间中的所有点，其中 x²+y²+z² = 1
更一般地，f(x,y,z) = 0

#### 隐式表面
**采样可能很困难**

$$
f(x, y, z) = (2 - \sqrt{x^2 + y^2})^2 + z^2 - 1
$$

哪些点位于 f(x,y,z) = 0 上？

有些任务很难用隐式表示

**简单内部/外部测试简单**

$$
f(x, y, z) = x^2 + y^2 + z^2 - 1
$$

隐式表示使一些任务变得简单



#### 计算机图形学中的更多隐式表示
##### 代数曲面
曲面是 x, y, z 多项式的零集
##### 构造立体几何
通过布尔运算组合隐式几何

###### 距离函数 Distance Functions
不使用布尔运算，而是使用距离函数逐渐将曲面融合在一起：
给出从任意位置到物体的最小距离（可以是有符号距离）

示例：混合（线性插值）移动边界
可以混合任意两个距离函数 d1、d2

##### 水平集方法 Level Set Methods
闭式方程难以描述复杂形状
替代方案：存储近似函数值的网格

当插值等于零时，表面就会被发现
提供对形状更明确的控制（就像纹理）

######  来自医学数据（CT、MRI 等）的水平集
水平集编码，例如恒定的组织密度

######  物理模拟中的水平集
水平集编码到气液边界的距离


##### 分形 Fractals
展现自相似性，在各个尺度上都具有细节
描述自然现象的“语言”
难以控制形状！



#### 隐式表示优缺点
##### 优点
- 描述紧凑（例如，函数）
- 某些查询简单（例如，物体内部、到表面的距离）
- 适用于射线与表面的相交（稍后详细介绍）
- 适用于简单形状，描述精确/无采样误差
- 易于处理拓扑变化（例如，流体）
##### 缺点
- 难以对复杂形状进行建模



### 几何的“显式”表示
所有点均直接给出或通过参数映射给出
#### 显式表面
**采样很容易**

$$
f(u, v) = \left( (2 + \cos u) \cos v, \ (2 + \cos u) \sin v, \ \sin u \right)
$$

**内部/外部测试困难**

$$
f(u, v) = \left( \cos u \sin v, \ \sin u \sin v, \ \cos v \right)
$$

triangle meshes 
Bezier surfaces 
subdivision surfaces 
NURBS 
point clouds

#### 点云 Point Cloud
最简单的表示：点列表 (x,y,z)
轻松表示任何类型的几何体
适用于大型数据集（>>1 个点/像素）
通常转换为多边形网格
在欠采样区域难以绘制

#### 多边形网格 Polygon Mesh
存储顶点和多边形（通常是三角形或四边形）
更易于处理/模拟，自适应采样
更复杂的数据结构
可能是图形学中最常见的表示形式


##### 波前对象文件 (Wavefront Object File, .obj) 格式
常用于图形研究
只是一个指定顶点、法线、纹理
坐标及其连通性的文本文件

#### 三角形网格 triangle meshes
#### 贝塞尔曲面 Bezier surfaces
#### 细分曲面 subdivision surfaces
#### NURBS

## 曲线 Curves
### 曲线用途
相机路径 Camera Paths
动画曲线 Animation Curves
矢量字体 Vector Fonts

### ⻉塞尔曲线 Bézier Curves
用切线定义三次贝塞尔曲线

$$
t_0 = 3(p_1 - p_0)
$$

$$
t_1 = 3(p_3 - p_2)
$$

#### 贝塞尔曲线的求解
##### 德卡斯特里奥(de Casteljau)算法
- 考虑三个点（二次贝塞尔曲线）
- 使用线性插值插入点
- 插入两边
- 递归重复
- 对 [0,1] 中的每个 t 运行相同的算法
- 总共四个输入点
  - 相同的递归线性插值


##### 代数公式
de Casteljau 算法给出了一个系数金字塔

示例：由三点构成的二次贝塞尔曲线

$$
b_1^0(t) = (1 - t) b_0 + t b_1
$$

$$
b_1^1(t) = (1 - t) b_1 + t b_2
$$

$$
b_2^0(t) = (1 - t) b_1^0 + t b_1^1
$$

$$
b_2^0(t) = (1 - t)^2 b_0 + 2t(1 - t) b_1 + t^2 b_2
$$

n 阶贝塞尔曲线的伯恩斯坦形式：

$$
b_n(t) = b_n^0(t) = \sum_{j=0}^{n} b_j B_j^n(t)
$$

其中：

- \( b_j \) 是控制点  
- \( B_j^n(t) \) 是第 \(j\) 个 \(n\) 阶 伯恩斯坦Bernstein 基函数，定义为：
  
$$
B_j^n(t) = \binom{n}{j} (1-t)^{n-j} t^j
$$


例如：假设 n = 3，我们在 R^3 中
也就是说，我们可以在三维空间中拥有如下控制点：

$$
\begin{aligned}
\mathbf{b}_0 &= (0, 2, 3) \\
\mathbf{b}_1 &= (2, 3, 5) \\
\mathbf{b}_2 &= (6, 7, 9) \\
\mathbf{b}_3 &= (3, 4, 5)
\end{aligned}
$$


这些点定义了一条三维贝塞尔曲线，它是 t 的三次多项式：

$$
\mathbf{b}_n(t) = \mathbf{b}_0 (1 - t)^3 + \mathbf{b}_1 \, 3t(1 - t)^2 + \mathbf{b}_2 \, 3t^2(1 - t) + \mathbf{b}_3 \, t^3
$$

#### 三次贝塞尔基函数
伯恩斯坦多项式

$$
B_i^n(t) = \binom{n}{i} \, t^i \, (1 - t)^{n-i}
$$

#### 贝塞尔曲线的性质
- 插值端点
  - 三次贝塞尔曲线：

$$
b(0) = b_0 \\
b(1) = b_3
$$

- 与端点线段相切
  - 三次贝塞尔曲线：

$$
b'(0) = 3(b_1 - b_0) \\
b'(1) = 3(b_3 - b_2)
$$

- 仿射变换属性
  - 通过变换控制点来变换曲线
- 凸包属性 Convex Hull
  - 曲线位于控制点的凸包内



#### 分段贝塞尔曲线 Piecewise Bézier Curves
高阶贝塞尔曲线很难控制！不常见

相反，串联多条低阶贝塞尔曲线
分段三次贝塞尔曲线是最常见的技术

*广泛使用（字体、路径、Illustrator、Keynote 等）*

##### 分段贝塞尔曲线连续性

$$
a : [k, k+1] \rightarrow \mathbb{R}^N \\
b : [k+1, k+2] \rightarrow \mathbb{R}^N
$$

###### C0 连续性

$$
a_n = b_0
$$

###### C1 连续性

$$
a_n = b_0 = \frac{1}{2}(a_{n-1} + b_1)
$$

### 其他类型的曲线
#### 样条曲线 Spline
- 一条连续曲线，通过给定的一组点，并具有一定数量的连续导数
- 简而言之，一条受控制的曲线

#### B 样条曲线 B-splines
- 基样条曲线的简称
- 比贝塞尔曲线需要更多信息
- 满足贝塞尔曲线的所有重要性质（即超集）


## 曲面 Surface
### 贝塞尔曲面 Bézier Surfaces
将贝塞尔曲线延伸至曲面

双三次贝塞尔曲面片
- 贝塞尔曲面和 4 x 4 控制点阵列

#### 贝塞尔曲面的求解
##### 评估参数 (u,v) 的表面位置
对于双三次贝塞尔曲面片，
- 输入：4x4 个控制点
- 输出为二维曲面，参数为 [0,1]² 中的 (u,v)

##### 方法：可分离一维 de Casteljau 算法
目标：计算与 (u,v) 对应的表面位置

(u,v) 可分离的 de Casteljau 算法应用

- 使用 de Casteljau 算法计算 u 中 4 条贝塞尔曲线上点 u 的位置。这为“移动”贝塞尔曲线提供了 4 个控制点。
- 使用一维 de Casteljau 算法计算“移动”曲线上点 v 的位置

## 网格操作：几何处理
- 网格细分（上采样）
- 网格简化（下采样）
- 网格规则化（相同数量的三角形）
### 网格细分（上采样）
Mesh subdivision (upsampling)
提高分辨率
#### 循环细分
三角形网格的常用细分规则
- 首先，创建更多三角形（顶点）
- 其次，调整它们的位置

将每个三角形分成四个
#### 更新顶点
根据权重分配新的顶点位置
- 新/旧顶点的更新方式不同

##### 对于新顶点
更新到

$$
\frac{3}{8} (A + B) + \frac{1}{8} (C + D)
$$

##### 对于旧顶点
例如此处的 6 度顶点
更新到

$$
(1 - n \cdot u) \cdot \text{original\_position} + u \cdot \text{neighbor\_position\_sum}
$$

#### Catmull-Clark 细分（通用网格）
每个细分步骤：
- 在每个面添加顶点
- 在每条边上添加中点
- 连接所有新顶点

##### Catmull-Clark 顶点更新规则（四边形网格）

$$
f = \frac{v1 + v2 + v3 + v4}{4}
$$

$$
e = \frac{v1 + v2 + f1 + f2}{4}
$$

**顶点**：

$$
v = f1 + f2 + f3 + f4 + 2(m1 + m2 + m3 + m4) + 4p
$$

其中：
- **m** 是边的中点
- **p** 是旧的“顶点”

#### 融合：整体形状和折痕

### 网格简化（下采样）
Mesh simplification (downsampling)
降低分辨率；尝试保持形状/外观

#### 目标
减少网格元素数量，同时保持整体形状

#### 折叠边缘 Collapsing An Edge
假设我们使用边折叠来简化网格

#### ⼆次误差度量 Quadric Error Metrics
简化会引入多少几何误差？
- 对顶点进行局部平均不是一个好主意
- 二次误差：新顶点应该最小化其与先前相关三角形平面的平方和（L2 距离）！

折叠一条边需要多少成本？
- 思路：计算边的中点，测量二次误差
- 更好的想法：选择最小化二次误差的点
- 更多详情：Garland & Heckbert 1997

#### 通过二次误差进行简化
迭代折叠边
哪些边？使用二次误差度量分配分数(Garland & Heckbert 1997)
- 将到表面的距离近似为到包含三角形的平面的距离之和
- 迭代折叠得分最小的边
- 贪婪算法……效果很好！



### 网格规则化（相同数量的三角形）
Mesh regularization
修改样本分布以提高质量


# 光线追踪 Ray Tracing
## 为什么使用光线追踪
光栅化无法很好地处理全局效果
- （柔和）阴影
- 尤其是当光线反射多次时

光栅化速度很快，但质量相对较低


光线追踪准确，但速度很慢
- 光栅化：实时，光线追踪：离线
- 在生产环境中渲染一帧大约需要 10000 CPU 核心小时


## 基本光线追踪算法
### 光线 Light Rays
关于光线的三个观点
1. 光沿直线传播（尽管这是错误的）
2. 光线即使相交也不会“碰撞”（尽管这仍然是错误的）
3. 光线从光源传播到眼睛（但在路径反转——互易律下，物理定律不变）

“如果你长时间凝视深渊，深渊也在凝视你。”——弗里德里希·威廉·尼采

### 光线投射 Ray Casting
Appel 1968 - 光线投射
1. 通过为每个像素投射一条光线来生成图像
2. 通过向光源发射光线来检查阴影

#### 生成视线
针孔相机模型 Pinhole Camera Model

#### 着色像素（仅限本地）

## 递归光线追踪
Whitted 风格

“An improved Illumination model for shaded display” T. Whitted, CACM 1980

时间：
- VAX 11/780 (1979) 74分钟
- PC (2006) 6秒
- GPU (2012) 1/30秒

## 射线-表面相交 Ray-Surface Intersection
### 射线方程
射线由其原点和方向向量定义
射线方程

$$
\text{Ray}(t) = \mathbf{o} + t \mathbf{d}, \quad 0 \leq t < 1
$$

参数说明：
$\mathbf{o}$：射线起点（origin）

$\mathbf{d}$：射线方向向量（direction）

$t$：射线参数，控制射线上点的位置，范围是 $0 \leq t < 1$

### 射线与球体相交
射线

$$
\mathbf{r}(t) = \mathbf{o} + t \mathbf{d}, \quad 0 \leq t < 1
$$

球体

$$
(\mathbf{p} - \mathbf{c})^2 - R^2 = 0
$$

什么是相交？
交点 p 必须同时满足射线方程和球面方程

$$
\left( \mathbf{o} + t \mathbf{d} - \mathbf{c} \right)^2 - R^2 = 0
$$


$$
a t^2 + b t + c = 0
$$

其中：

$$
a = \mathbf{d} \cdot \mathbf{d}
$$

$$
b = 2 (\mathbf{o} - \mathbf{c}) \cdot \mathbf{d}
$$

$$
c = (\mathbf{o} - \mathbf{c}) \cdot (\mathbf{o} - \mathbf{c}) - R^2
$$

$$
t = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
$$

### 射线与隐式表面的相交
射线

$$
\mathbf{r}(t) = \mathbf{o} + t \mathbf{d}, \quad 0 \leq t < 1
$$

一般隐式曲面：

$$
p : f(p) = 0
$$

代换射线方程：

$$
f(\mathbf{o} + t \mathbf{d}) = 0
$$

求实数正根


### 射线与三角形网格的相交
- 渲染：可见性、阴影、光照……
- 几何：内部/外部测试

如何计算？
让我们分解一下：
- 简单的想法：只需将射线与每个三角形相交
- 简单，但速度慢（加速？）
- 注意：可以有 0 个或 1 个相交（忽略多个相交）

### 射线与三角形的相交
三角形位于平面内
- 射线与平面相交
- 测试命中点是否位于三角形内
有很多优化方法……


#### 平面方程
平面由法向量和平面上的一个点定义

平面方程（若 p 满足该方程，则 p 在平面上）：

$$
\mathbf{p} : (\mathbf{p} - \mathbf{p_0}) \cdot \mathbf{N} = 0
$$

### 射线与平面的相交
光线方程

$$
\mathbf{r}(t) = \mathbf{o} + t \mathbf{d}, \quad 0 \leq t < 1
$$

平面方程

$$
\mathbf{p} : (\mathbf{p} - \mathbf{p_0}) \cdot \mathbf{N} = 0
$$

求解交点

$$
\mathbf{p} = \mathbf{r}(t) \quad \text{and solve for} \quad t
$$

$$
(\mathbf{p} - \mathbf{p_0}) \cdot \mathbf{N} = (\mathbf{o} + t \mathbf{d} - \mathbf{p_0}) \cdot \mathbf{N} = 0
$$

$$
t = \frac{(\mathbf{p_0} - \mathbf{o}) \cdot \mathbf{N}}{\mathbf{d} \cdot \mathbf{N}}
$$

$$
\mathbf{r}(t) = \mathbf{o} + t \mathbf{d}, \quad 0 \leq t < 1
$$


#### Möller Trumbore 算法
一种更快的方法，直接给出重心坐标

## 加速射线-表面相交
简单的光线与场景相交
- 详尽地测试光线与每个三角形的相交
- 找到最接近的点（即最小t值）

问题：
- 简单的算法 = 像素数⨉三角形数（⨉反弹次数）
- 非常慢！
为了通用起见，我们稍后使用“对象”一词代替三角形（但并不一定指整个对象）

### 边界体积 Bounding Volumes
避免相交的快速方法：将复杂物体与简单体积绑定
- 物体完全包含在体积中
- 如果物体没有撞击体积，则不会撞击物体
- 因此，先测试 BVol，如果撞击则测试物体

### 射线与盒子的相交
盒子是 3 对平板的交集

具体来说：
我们经常使用轴对齐包围盒 (AABB)（轴对轴包围盒）

即 BB 的任意一侧沿着 x、y 或 z轴

#### 射线与轴对齐盒的交集
计算与平板的交集，并取 tmin/tmax 区间的交集

一个三维盒子 = 三对无限大的平板
- 关键思想
  - 只有当射线进入所有平板对时，它才会进入盒子
  - 只要射线离开任意一对平板，它就会离开盒子
- 对于每一对平板，计算 tmin 和 tmax（负数也可以）
- 对于三维盒子，tenter = max{tmin}，texit = min{tmax}
- 如果 tenter < texit，我们知道射线会在盒子中停留一段时间（所以它们一定相交！）

- 然而，射线不是直线
  - 为了确保物理正确性，应该检查 t 是否为负！
- 如果 texit < 0 会怎样？
  - 盒子在射线“后面”——没有相交！
- 如果 texit >= 0 且 tenter < 0 会怎样？
  - 射线的原点在盒子内部——有相交！
- 综上所述，射线与 AABB 相交，当且仅当：
  - tenter < texit && texit >= 0

### 使用 AABB 加速光线追踪
#### 均匀空间分区（网格）
##### 预处理——构建加速网格
1. 查找边界框 Find bounding box
2. 创建网格 Create grid
3. 将每个对象存储在重叠的单元格中 Store each object in overlapping cells

##### 光线-场景相交
按射线遍历顺序遍历网格

对于每个网格单元
测试与该单元存储的所有对象的交集

##### 网格分辨率
一个单元格
- 无加速
单元格过多
- 多余的网格遍历导致效率低下

##### 启发式
- #cells = C * #objs 
- C ≈ 27 in 3D

##### 均匀网格——当它们有效时
网格非常适合处理大小和空间分布均匀的大量对象
##### 均匀网格——当它们失效时
“体育场里的茶壶”问题


#### 空间分区 Spatial Partitions
##### 空间分区例子
- Oct-Tree
- KD-Tree
- BSP-Tree

##### KD树预处理
##### KD树的数据结构 Data Structure for KD-Trees
- 内部节点存储
  - 分割轴：x、y 或 z 轴
  - 分割位置：分割平面沿轴的坐标
  - 子节点：指向子节点的指针
  - 内部节点不存储任何对象
- 叶节点存储
  - 对象列表

##### 遍历KD树


#### 对象分区和边界体积层次结构 (BVH)
Object Partitions & 
Bounding Volume Hierarchy (BVH)

- 查找边界框
- 递归地将对象集拆分为两个子集
- 重新计算子集的边界框
- 必要时停止
- 将对象存储在每个叶节点中


##### 构建 BVH
如何细分节点
- 选择要拆分的维度
- 启发式方法 #1：始终选择节点中最长的轴
- 启发式方法 #2：在中间对象的位置拆分节点

终止条件
- 启发式方法：当节点包含较少元素时停止

##### BVH 的数据结构
内部节点存储
- 边界框
- 子节点：指向子节点的指针

叶节点存储
- 边界框
- 对象列表

节点表示场景中图元的子集
- 子树中的所有对象

##### BVH遍历
```
Intersect(Ray ray, BVH node) {
  if (ray misses node.bbox) return;

  if (node is a leaf node)
    test intersection with all objs;
    return closest intersection;

  hit1 = Intersect(ray, node.child1);
  hit2 = Intersect(ray, node.child2);

  return the closer of hit1, hit2;
}
```

#### 空间分区与对象分区
- 空间分区（例如 KD 树）
  - 将空间划分为不重叠的区域
  - 一个对象可以包含在多个区域中
- 对象分区（例如 BVH）
  - 将对象集划分为不相交的子集
  - 每个集合的边界框可能在空间上重叠


## 辐射度量学 Radiometry
### 动机
在Blinn-Phong 模型中，例如，光强度 I 为 10
但是 10 是什么？

Whitted 式光线追踪能给出正确的结果吗？

所有答案都可以在辐射测量中找到
- 还有“路径追踪”的基础知识

### 定义
照明测量系统和单位
精确测量光的空间特性
- 新术语：辐射通量、强度、辐照度、辐射亮度

以物理上正确的方式进行照明计算


### 辐射能量和通量（功率）
Radiant Energy and Flux (Power)

定义：辐射能是电磁辐射的能量。其单位为焦耳，符号为：

$$
Q \, [J = \text{Joule}]
$$


定义：辐射通量（功率）是单位时间内发射、反射、传输或接收的能量

$$
\Phi = \frac{dQ}{dt} \quad [W = \text{Watt}] \quad [lm = \text{lumen}]
$$


通量Flux： 单位时间内流过传感器的光子数

### 重要的光照度量
| 光的类型         | 光照度量           | 英文对照              |
|-----------------|-----------------|--------------------|
| 光源发出的光     | 辐射强度         | Radiant Intensity  |
| 照射到表面的光   | 辐照度           | Irradiance         |
| 沿射线传播的光   | 辐射亮度         | Radiance           |


#### 辐射强度 Radiant Intensity
##### 定义
辐射（发光）强度是指点光源在单位立体角内发射的功率

$$
I(\nu) \equiv \frac{d\Phi}{d\omega} 
$$

$$
[\frac{W}{sr}] = [\frac{\text{lm}}{\text{sr}} = \text{cd} = \text{candela}]
$$

坎德拉是国际单位制七个基本单位之一

##### 角和立体角
###### 角度
圆周上对角弧长与半径的比值

$$
\theta = \frac{l}{r}
$$

圆有2π个弧度

###### 立体角
球面所对面积与半径平方之比

$$
\omega = \frac{A}{r^2}
$$

球体有4π个立体角

###### 微分立体角

$$
dA = (r\, d\theta)(r \sin \theta\, d\varphi) = r^2 \sin \theta\, d\theta\, d\varphi
$$

$$
d\omega = \frac{dA}{r^2} = \sin \theta\, d\theta\, d\varphi
$$

Sphere: S^2

$$
\Omega = \int_{S^2} d\omega 
= \int_0^\pi \int_0^{2\pi} \sin \theta\, d\theta\, d\varphi
= \left[-\cos \theta\right]_0^\pi \times \left[\varphi\right]_0^{2\pi}
= (2) \times (2\pi)
= 4\pi
$$

$\omega$用于表示方向向量（单位长度）

##### 各向同性点源 Isotropic Point Source

$$
\Phi = \int_{S^2} I\, d\omega = 4\pi I
$$

$$
I = \frac{\Phi}{4\pi}
$$

##### 现代LED灯
- 输出：815 流明（11W LED 替代60W 白炽灯）
-辐射强度？
假设各向同性：
Intensity = 815 lumens / 4pi sr  = 65 candelas

#### 辐照度 Irradiance
定义：辐照度是指照射到表面点的单位面积的功率

$$
E(x) \overset{\mathrm{def}}{=} \frac{d\Phi(x)}{dA}
$$

$$
[\frac{m}{W^2}] [\frac{m}{lm^2} = \text{lux}]
$$


##### 兰伯特余弦定律 Lambert’s Cosine Law
表面辐照度与光线方向和表面法线夹角的余弦成正比

- 立方体顶面接收一定量的能量

$$
E = \frac{\Phi}{A}
$$


- 60°旋转立方体的顶面接收一半功率

$$
E = \frac{1}{2} \frac{\Phi}{A}
$$

- 一般来说，单位面积的功率为

$$
\cos \theta = \mathbf{l} \cdot \mathbf{n}
$$

$$
E = \frac{\Phi}{A \cos \theta}
$$

##### 辐照度衰减

#### 辐射亮度 Radiance

辐射亮度是描述环境中光分布的基本场量
- 辐射亮度是与射线相关的量
- 渲染的核心在于计算辐射亮度

##### 定义
辐射度（亮度）是指表面在单位立体角、单位投影面积内发射、反射、透射或接收的功率。

$$
L(p, \mathbf{\omega}) \overset{\mathrm{def}}{=} \frac{d^2 \Phi(p, \omega)}{d\omega dA \cos \theta}
$$

$$
\left[ \frac{W}{\text{sr m}^2} \right] \quad \left[ \frac{\text{cd}}{\text{m}^2} = \frac{\text{lm}}{\text{sr m}^2} = \text{nit} \right]
$$


单位立体角每单位投影面积的功率


- 辐照度：单位投影面积的功率
- 强度：单位立体角的功率
因此
- 辐射亮度：单位立体角的辐照度
- 辐射亮度：单位投影面积的强度

##### 入射辐射亮度 Incident Radiance
入射辐射亮度是指到达表面的每单位立体角的辐射亮度

$$
L(p, \omega) = \frac{dE(p)}{d\omega \cos \theta} 
$$

即，它是沿给定射线（表面上的点和入射方向）到达表面的光

##### 出射辐射亮度 Exiting Radiance
出射表面辐射亮度是指离开表面的单位投影面积的强度

$$
L(p, \omega) = \frac{dI(p, \omega)}{dA \cos \theta} 
$$

例如，对于区域光来说，它是沿给定射线（表面上的点和出射方向）发射的光


##### 辐照度与辐射亮度
辐照度：区域 dA 接收的总功率
辐射亮度：区域 dA 从“方向” dω 接收的功率

$$
dE(p, \omega) = L_i(p, \omega) \cos \theta \, d\omega
$$

$$
E(p) = \int_{H2} L_i(p, \omega) \cos \theta \, d\omega
$$


##### 双向反射分布函数 (BRDF)
Bidirectional Reflectance Distribution Function

###### 点的反射
来自ω_i方向的辐射亮度转化为dA接收的功率E。
然后，功率E将转化为向任何其他方向ω的辐射亮度

双向反射分布函数 (BRDF) 表示从每个入射方向反射到每个出射方向ω_r的光量

$$
f_r(\omega_i \rightarrow \omega_r) = \frac{dL_r(\omega_r)}{dE_i(\omega_i)} 
= \frac{dL_r(\omega_r)}{L_i(\omega_i) \cos \theta_i \, d\omega_i}
\qquad [\text{sr}^{-1}]
$$

反射方程

$$
L_r(p, \omega_r) = \int_{H^2} f_r(p, \omega_i \rightarrow \omega_r) \, L_i(p, \omega_i) \, \cos \theta_i \, d\omega_i
$$

递归方程
反射辐射取决于入射辐射
但入射辐射取决于反射辐射（在场景中的另一点）


渲染方程

$$
L_o(p, \omega_o) = L_e(p, \omega_o) + \int_{\Omega^+} L_i(p, \omega_i) \, f_r(p, \omega_i, \omega_o) \, (\mathbf{n} \cdot \omega_i) \, d\omega_i
$$

## 概率论回顾 Probability Review
### 随机变量 Random Variables
随机变量：表示潜在值的分布
概率密度函数 (PDF)：描述随机过程选择值的相对概率

### 随机变量的期望值 Expected Value of a Random Variable
从随机分布中反复抽取样本得到的平均值
X的期望值：

$$
E[X] = \sum_{i=1}^{n} x_i p_i
$$

### 概率分布函数 (PDF)
Probability Distribution Function (PDF)

一个随机变量 X，它可以取一组连续的值，其中特定值的相对概率由连续概率密度函数 p(x) 给出

p(x) 的条件

$$
p(x) \geq 0  and  \int_{-\infty}^{+\infty} p(x) \, dx = 1
$$

X 的期望值

$$
E[X] = \int_{-\infty}^{+\infty} x \, p(x) \, dx
$$

### 随机变量函数
随机变量 X 的函数 Y 也是随机变量

$$
X \sim p(x)
$$

$$
Y = f(X)
$$

随机变量函数的期望值

$$
E[Y] = E[f(X)] = \int f(x)\, p(x)\, dx
$$

## 蒙特卡洛积分 Monte Carlo Integration
Why: 我们想解一个积分，但用解析解法可能太难了
What & How: 通过对函数值的随机样本进行平均来估计函数的积分

让我们为给定函数f(x)的定积分定义蒙特卡洛估计量

定积分

$$
\int_{a}^{b} f(x) \, dx
$$

随机变量

$$
X_i \sim p(x)
$$

蒙特卡洛估计量

$$
F_N = \frac{1}{N} \sum_{i=1}^{N} \frac{f(X_i)}{p(X_i)}
$$

注意：
- 样本越多，方差越小
- 对 x 进行采样，对 x 进行积分


## 路径追踪 Path Tracing
### 动机
Whitted 式光线追踪：
- 始终执行镜面反射/折射
- 停止在漫反射表面反弹

这些简化是否合理？
高阶：让我们逐步改进 Whitted 式光线追踪，并最终实现我们的路径追踪算法！


### Whitted 式光线追踪存在问题
- 对于光泽材质，射线应该在哪里反射？
- 漫反射材料之间没有反射？

Whitted 式光线追踪是错误的
但渲染方程是正确的

$$
L_o(p, \omega_o) = L_e(p, \omega_o) + \int_{\Omega^+} L_i(p, \omega_i) \, f_r(p, \omega_i, \omega_o) \, (\mathbf{n} \cdot \omega_i) \, d\omega_i
$$

但它涉及
- 求解半球积分，以及
- 递归执行

如何用数值方法求解积分？

### 一个简单的蒙特卡罗解决方案

$$
L_o(p, \omega_o) = \int_{\Omega^+} L_i(p, \omega_i) \, f_r(p, \omega_i, \omega_o) \, (\mathbf{n} \cdot \omega_i) \, d\omega_i 
\approx \frac{1}{N} \sum_{i=1}^{N} \frac{L_i(p, \omega_i) \, f_r(p, \omega_i, \omega_o) \, (\mathbf{n} \cdot \omega_i)}{p(\omega_i)}
$$

这是什么意思？
直接照明的正确着色算法！

```
shade(p, wo)
  Randomly choose N directions wi~pdf
  Lo = 0.0
  For each wi
    Trace a ray r(p, wi)
    If ray r hit the light
      Lo += (1 / N) * L_i * f_r * cosine / pdf(wi)
  Return Lo
```


### 引入全局照明
更进一步：如果光线击中物体怎么办？
Q 也反射光到 P！反射了多少？Q 的方向光！

```
shade(p, wo)
  Randomly choose N directions wi~pdf
  Lo = 0.0
  For each wi
    Trace a ray r(p, wi)
    If ray r hit the light
      Lo += (1 / N) * L_i * f_r * cosine / pdf(wi)
      Else If ray r hit an object at q
        Lo += (1 / N) * shade(q, -wi) * f_r * cosine / pdf(wi)
  Return Lo
```

### 路径追踪存在的问题
问题 1：随着 #bounces 的上升，#rays 爆炸

从现在开始，我们始终假设
每个着色点只追踪一条光线：
```
shade(p, wo)
  Randomly choose ONE direction wi~pdf(w)
  Trace a ray r(p, wi)
  If ray r hit the light
    Return L_i * f_r * cosine / pdf(wi)
  Else If ray r hit an object at q
    Return shade(q, -wi) * f_r * cosine / pdf(wi)
```

这就是路径追踪！（仅供参考，如果 N != 1，则为分布式光线追踪）

### 射线生成 Ray Generation
但这会很嘈杂！
没问题，只需在每个像素上追踪更多路径，然后平均它们的辐射亮度！

与光线追踪中的光线投射非常相似

```
ray_generation(camPos, pixel)
  Uniformly choose N sample positions within the pixel
  pixel_radiance = 0.0
  For each sample in the pixel
    Shoot a ray r(camPos, cam_to_sample)
    If ray r hit the scene at p
      pixel_radiance += 1 / N * shade(p, sample_to_cam)
  Return pixel_radiance
```

问题2：递归算法永远不会停止！
困境：光确实会不停地反弹！
减少反弹次数 == 减少能量！

解决方案：俄罗斯轮盘赌（RR）

俄罗斯轮盘赌的玩法完全取决于概率
- 如果概率为 0 < P < 1，则没问题
- 如果概率为 1 - P，则其他情况都无所谓


以前，我们总是向着色点发射射线，并得到着色结果

假设我们手动设置一个概率 P (0 < P < 1)
概率为 P 时，发射一条射线，

返回着色结果除以 P：Lo / P
概率为 1-P 时，不发射射线，结果为 0
这样，你仍然可以期望得到 Lo!：

$$
E = P \times \frac{L_o}{P} + (1 - P) \times 0 = L_o
$$

```
shade(p, wo)
  Manually specify a probability P_RR
  Randomly select ksi in a uniform dist. in [0, 1]
  If (ksi > P_RR) return 0.0;

  Randomly choose ONE direction wi~pdf(w)
  Trace a ray r(p, wi)
  If ray r hit the light
    Return L_i * f_r * cosine / pdf(wi) / P_RR
  Else If ray r hit an object at q
    Return shade(q, -wi) * f_r * cosine / pdf(wi) / P_RR
```

现在我们已经有了一个正确版本的路径追踪！
但它效率不高。


### 采样光
了解效率低下的原因

会有 1 条光线射入光源。因此，如果我们在着色点处对半球进行均匀采样，就会有很多光线被“浪费”。

蒙特卡洛方法允许任何采样方法，因此我们可以对光进行采样（因此不会有光线被“浪费”）。

假设对光进行均匀采样：
pdf = 1 / A (because ∫pdf dA = 1)

但渲染方程在立体角上积分：Lo = ∫Li fr cos dω

蒙特卡洛积分在 x 上采样，并在 x 上积分

既然我们对光进行采样，那么我们能否对光进行积分呢？

需要将渲染方程转化为 dA 的积分
需要 dω 和 dA 之间的关系

立体角的另一种定义：
单位球面上的投影面积

然后我们可以将渲染方程重写为

$$
L_o(x, \omega_o) = \int_{\Omega^+} L_i(x, \omega_i) \, f_r(x, \omega_i, \omega_o) \, \cos \theta \, d\omega_i
= \int_A L_i(x, \omega_i) \, f_r(x, \omega_i, \omega_o) \, \frac{\cos \theta \, \cos \theta'}{\|x' - x\|^2} \, dA
$$

现在来个光积分！
蒙特卡洛积分：
“f(x)”：里面的一切
PDF：1 / A

之前，我们假设光线是“意外地”通过均匀半球采样射出的

现在我们考虑来自两部分的辐射：
1. 光源（直接，无需反射率）
2. 其他反射体（间接，反射率）

```
shade(p, wo)
  # Contribution from the light source.
  Uniformly sample the light at x’ (pdf_light = 1 / A)
  L_dir = L_i * f_r * cos θ * cos θ’ / |x’ - p|^2 / pdf_light 

  # Contribution from other reflectors.
  L_indir = 0.0
  Test Russian Roulette with probability P_RR
  Uniformly sample the hemisphere toward wi (pdf_hemi = 1 / 2pi)
  Trace a ray r(p, wi)
  If ray r hit a non-emitting object at q
    L_indir = shade(q, -wi) * f_r * cos θ / pdf_hemi / P_RR
  Return L_dir + L_indir
```


## 光线追踪：过去与现代概念
- 过去
  - 光线追踪 == Whitted 式光线追踪
- 现代
  - 光传输的通用解决方案，包括
  - （单向和双向）路径追踪 path tracing 
  - 光子映射 Photon mapping
  - Metropolis light transport 大都会光传输
  - VCM / UPBP…


## 其他
- 对半球进行均匀采样
  - 如何进行？一般来说，如何对任意函数进行采样？
（采样）
- 蒙特卡洛积分允许任意概率密度函数 (pdf)
  - 最佳选择是什么？（重要性采样）
- 随机数重要吗？
  - 是的！（低差异序列）
-我可以对半球和光线进行采样。
  - 我可以将它们结合起来吗？可以！（多重采样）
- 像素的辐射度是所有经过它的路径的辐射度的平均值。
  - 为什么？（像素重建滤波器）
- 像素的辐射度是像素的颜色吗？
  - 不是。（伽马校正、曲线、色彩空间）
- 路径追踪还是“入门”吗？
  - 是的。朋友们，敬畏科学吧。



# 材料和外观 Materials and Appearances
Material == BRDF

## 漫反射/朗伯材质 Diffuse / Lambertian Material
光在每个输出方向上均等地反射

## 光泽材质 Glossy material (BRDF)
理想反射/折射材料 (BSDF*)
Ideal reflective / refractive material (BSDF*)

## 完美的镜面反射 Perfect Specular Reflection

## 镜面折射 Specular Refraction
光除了在表面反射外，还可以穿过表面透射。当光进入新的介质时，会发生折射

### 斯涅尔定律 Snell’s Law
透射角取决于
- 入射光线的折射率 (IOR)
- 出射光线的折射率 (IOR)

### 斯涅尔之窗 / 圆 Snell’s Window / Circle

### 菲涅尔反射/术语 Fresnel Reflection / Term
反射率取决于入射角（和光的偏振）


## 微面片材质 Microfacet Material
### 概念
微面理论

粗糙表面
- 宏观尺度：平坦且粗糙
- 微观尺度：凹凸不平且镜面反射

表面的各个元素如同镜子
- 被称为微面
- 每个微面都有其自身的法线


### 微面片双向反射分布函数 (BRDF)
关键点：微面片法线的分布
- 集中 <==> 光泽
- 扩散<==>弥漫

$$
f_r(\mathbf{i}, \mathbf{o}) = \frac{F(\mathbf{i}, \mathbf{h}) \cdot G(\mathbf{i}, \mathbf{o}, \mathbf{h}) \cdot D(\mathbf{h})}{4 (\mathbf{n} \cdot \mathbf{i}) (\mathbf{n} \cdot \mathbf{o})}
$$


## 各向同性/各向异性材质 Isotropic / Anisotropic Materials (BRDFs)
底层表面的方向性

### 各向异性 Anisotropic BRDFs
反射取决于方位角φ
由表面的定向微结构（例如拉丝金属）产生

$$
f_r(\theta_i, \phi_i; \theta_r, \phi_r) \ne f_r(\theta_i, \theta_r, \phi_r - \phi_i)
$$


#### 拉丝金属 Brushed Metal

#### 尼龙 Nylon
#### 天鹅绒 Velvet

### BRDF 的属性
非负性 Non-negativity 

$$
f_r(\mathbf{i}, \mathbf{r}) \geq 0
$$

线性 Linearity

$$
L_r(\mathbf{p}, \mathbf{r}) = \int_{\mathcal{H}^2} f_r(\mathbf{p}, \mathbf{i}, \mathbf{r}) \, L_i(\mathbf{p}, \mathbf{i}) \, \cos \theta_i \, d\omega_i
$$

互易原则 Reciprocity principle

$$
f_r(\mathbf{p}, \mathbf{r} \rightarrow \mathbf{i}) = f_r(\mathbf{p}, \mathbf{i} \rightarrow \mathbf{r})
$$


能量守恒 Energy conservation

$$
\forall \mathbf{r}, \quad \int_{\mathcal{H}^2} f_r(\mathbf{i}, \mathbf{r}) \cos \theta_i \, d\omega_i \leq 1
$$

### 各向同性与各向异性 Isotropic vs. anisotropic
如果各向同性

$$
f_r(\theta_i, \phi_i; \theta_r, \phi_r) = f_r(\theta_i, \theta_r, \phi_r - \phi_i)
$$

那么，根据互易律

$$
f_r(\theta_i, \theta_r, \phi_r - \phi_i) = f_r(\theta_r, \theta_i, \phi_i - \phi_r) = f_r(\theta_i, \theta_r, |\phi_r - \phi_i|)
$$

### 测量BRDF
#### 动机
无需开发/导出模型
- 自动包含所有散射效果
可使用真实材质进行精准渲染
- 适用于产品设计、特效等


#### 基于图像的BRDF测量 Image-Based BRDF Measurement
测角反射仪 gonioreflectometer

##### 一般方法
```
foreach outgoing direction wo
  move light to illuminate surface with a thin beam from wo
  for each incoming direction wi
  move sensor to be at direction wi from surface
  measure incident radiance
```

##### 提高效率
- 各向同性表面将维度从四维降低到三维
- 互易性将测量次数减少一半
- 巧妙的光学系统……


#### 测量 BRDF 的挑战
- 掠射角的精确测量
  - 由于菲涅尔效应，这一点至关重要
- 通过足够密集的采样进行测量，以捕捉高频镜面反射
- 逆反射
- 空间变化的反射率……


#### 测量双向反射分布函数 (BRDF) 的表示
理想特性
- 紧凑的表示
- 测量数据的精确表示
- 可高效评估任意方向对
- 具有良好的重要性采样分布


表格表示
将间隔均匀的样本存储在

$$
(\theta_i, \theta_o, |\phi_i - \phi_o|)
$$

- 改进：重新参数化角度,以更好地匹配镜面反射

通常需要重新采样测量值,并存入表格
存储要求非常高


# 渲染高级主题 Advanced Topics in Rendering
## 高级光传输 Advanced Light Transport
无偏光传输方法
- 双向路径追踪 (BDPT)
- Metropolis 光传输 (MLT)

偏光传输方法
- 光子映射
- 顶点连接与合并 (VCM)

即时辐射度（VPL/多种光照方法）

### 有偏蒙特卡罗估计量与无偏蒙特卡罗估计量
无偏蒙特卡罗技术不存在任何系统误差
- 无论使用多少个样本，无偏估计量的预期值始终是正确的值

否则，有偏
- 有一种特殊情况，当使用无限个样本时，预期值会收敛到正确值——一致

### 双向路径追踪 Bidirectional Path Tracing (BDPT)
路径连接着相机和光源

BDPT
- 追踪来自相机和光源的子路径
- 连接两个子路径的端点

适用于光传输在光侧较为复杂的情况
实现起来比较困难且速度较慢

### 大都会光传输 Metropolis Light Transport (MLT)
马尔可夫链蒙特卡洛 (MCMC) 应用
- 从当前样本跳转到下一个样本（附带 PDF）

非常擅长局部探索复杂的光路

#### 核心思想
- 局部扰动现有路径以获得新路径

#### 优点
- 适用于复杂的光路
- 也是无偏光

#### 缺点
- 难以估算收敛率
- 无法保证每个像素的收敛率相等
- 因此，通常会产生“脏”结果
- 因此，通常不用于渲染动画

### 光子映射 Photon Mapping
- 偏向方法 & 两阶段方法
- 非常擅长处理镜面-漫反射-镜面 (SDS) 路径并生成焦散

#### 方法
- 第一阶段——光子追踪
  - 从光源发射光子，使其四处反射，然后记录漫反射表面上的光子
- 第二阶段 — 光子收集（最终聚集）
  - 从相机发射子路径，使其四处弹跳，直到它们撞击漫反射表面

#### 计算 - 局部密度估计
- 思路：光子较多的区域应该更亮
- 对于每个着色点，找到最近的 N 个光子。取它们覆盖的表面积

- 为什么会有偏差？
- 局部密度估计 dN / dA != ΔN / ΔA
- 但在极限意义上
  - 发射更多光子 ->
  - 相同的 N 个光子覆盖更小的 ΔA ->
  - ΔA 更接近 dA
- 因此，虽然有偏差，但结果一致！

更容易理解渲染中的偏差
- 偏差 == 模糊
- 一致 == 无限采样情况下不模糊

为什么不使用“常量范围”搜索来估计密度？

### 顶点连接与合并 Vertex Connection and Merging
BDPT 与光子映射的结合

#### 核心思想
- 如果 BDPT 中的子路径的端点无法连接但可以合并，则不要浪费它们
- 使用光子映射来处理相邻“光子”的合并。

### 即时辐射度 (IR)
有时也称为多光源方法

核心思想
- 受光表面可视为光源

方法
- 发射光子路径，并假设每个子路径的终点为虚拟点光源 (VPL)
- 使用这些 VPL 照常渲染场景

优点：速度快，通常在漫反射场景中效果良好

缺点
- 当 VPL 靠近着色点时，会出现尖峰
- 无法处理光泽材质

## 高级外观建模 Advanced Appearance Modeling
### 非表面模型 Non-surface models
#### 参与介质 Participating Media
例如雾或云
光在穿过参与介质的任何时刻，都可能被（部分）吸收和散射
使用相位函数描述参与介质中任意点 x 的光散射角分布
##### 参与介质渲染
随机选择一个方向进行弹跳
- 随机选择一个距离进行直线运动
- 在每个“阴影点”处，连接到光源

#### 毛发/毛皮/纤维 (BCSDF)
##### 毛发外观 Hair Appearance
###### Kajiya-Kay Model

###### Marschner Model
玻璃状圆柱体
三种光相互作用类型：
R、TT、TRT
（R：反射，T：透射）

##### 毛皮外观 Fur Appearance 
如果作为人类头发渲染，则无法呈现漫射和饱和的外观
###### 人类头发与动物毛皮
毛发/毛皮纤维的常见特征
- 皮层 Cortex
  - 含有色素
  - 吸收光线
- 髓质 Medulla
  - 结构复杂
  - 散射光线
- 角质层 Cuticle
  - 覆盖有鳞片

毛发/毛皮纤维的区别

髓质的重要性

双圆柱模型 Double Cylinder Model
- 叶轮 Lobes

#### 颗粒材质 Granular Material
我们能否避免对所有粒子进行显式建模？
- 可以，但需要程序化定义



### 表面模型 Surface models
#### 半透明材质 (BSSRDF)
例如：
透光材质-玉石 Translucent Material-Jade
透光材质-水母 Translucent Material-Jellyfish

##### 次表面散射 Subsurface Scattering
由于光线入射点与出射点不同，导致许多表面呈现出不同的视觉特征
- 违反了 BRDF 的一个基本假设

##### 散射函数 Scattering Functions
BSSRDF：BRDF 的推广；某一点的辐射度
由另一点的入射微分辐照度引起：

$$
S(x_i, \mathbf{\omega}_i, x_o, \mathbf{\omega}_o)
$$

渲染方程的推广：对表面所有点和所有方向进行积分（！）

$$
L(x_o, \mathbf{\omega}_o) = \int_A \int_{\mathcal{H}^2} S(x_i, \mathbf{\omega}_i, x_o, \mathbf{\omega}_o) \, L_i(x_i, \mathbf{\omega}_i) \cos \theta_i \, d\omega_i \, dA
$$


##### 偶极子近似 Dipole Approximation
通过引入两个点源来近似光扩散

#### 布料 Cloth
扭转的纤维集合

两个级别的扭转
- 纱 Yarn
- 褶 Ply

机织或针织Woven or knitted

##### 布料渲染为表面
- 给定编织模式，计算整体行为
- 使用 BRDF 进行渲染

##### 布料渲染为参与介质
单根纤维的属性及其分布 -> 散射参数
- 渲染为参与介质

##### 布料渲染为实际纤维
显式渲染每根纤维

#### 精细材质（非统计 BRDF）Detailed Appearance
看起来不现实
现实世界更加复杂

##### 统计NDF与实际NDF
##### 定义细节
法线贴图
##### 困难路径采样问题
解决方案：像素上的 BRDF

p-NDF 具有锐化特征

##### 近期趋势：波动光学 Wave Optics


### 程序化外观 Procedural appearance
我们可以不使用纹理来定义细节吗？
- 是的！动态计算噪声函数
- 3D 噪声 -> 内部结构（如果被切割或损坏）

```
if noise(x, y, z) > threshold: 
 reflectance = 1 
else: 
 reflectance = 0
```

复杂的噪声函数可能非常强大

# 相机、镜头和光场 Cameras, Lenses and Light Fields

成像=合成+捕获
Imaging = Synthesis + Capture

## 相机 Cameras
### 相机内部
- 针孔和透镜在传感器上形成图像
- 快门使传感器曝光时间精确
- 传感器在曝光期间累积辐照度

为什么不用无透镜的传感器？
每个传感器点都会整合来自物体上所有点的光线，因此所有像素值都会相似，也就是说，传感器记录的是辐照度irradiance

### 针孔成像 Pinhole Image Formation
Mo Tzu (c. 470–c. 390 BC) 
Aristotle (384–322 BC) 
Ibn al-Haytham (965–1040)
Shen Kuo (1031–1095) 
Roger Bacon (c. 1214–1294) 
Johannes Kepler (1571–1630)

### 视场 Field of View (FOV)
焦距对视场的影响
- 对于固定的传感器尺寸，减小焦距可以增加视野


$$
\text{FOV} = 2 \arctan\left(\frac{h}{2f}\right)
$$


#### 焦距与视场
由于历史原因，通常用 35mm 格式胶片 (36 x 24mm) 上使用的镜头焦距来表示视角

35mm 格式焦距示例：
- 17mm 为广角 104°
- 50mm 为“标准”镜头 47°
- 200mm 为远摄镜头 12°

注意！当我们说现在的手机焦距大约为 28mm 时，指的是上述约定

#### 传感器尺寸对视场的影响
#### 传感器尺寸
#### 在较小的传感器上保持视野
为了保持视场，要根据传感器的宽度/高度按比例减小镜头的焦距


### 曝光 Exposure

$$
H = T \times E
$$


- 曝光量 = 时间 x 辐照度
- 曝光时间 (T)
  - 由快门控制
- 辐照度 (E)
  - 照射到传感器单位面积上的光功率
  - 由镜头光圈和焦距控制


#### 摄影中的曝光控制
光圈大小 Aperture size
- 通过打开/关闭光圈来更改光圈值（如果相机具有光圈控制功能）

快门速度 Shutter speed
- 更改传感器像素积分光线的持续时间

ISO 增益 (感光度) ISO gain
- 更改传感器值和数字图像值之间的放大倍数（模拟和/或数字）


##### ISO (增益)
曝光的第三个变量
胶片：以感光度换取颗粒感
数码：以感光度换取噪声
- 在模拟-数字转换（ADC）之前放大信号
- 线性效应（ISO 200 所需光量是 ISO 100 的一半）

##### F 值（F 档）：曝光级别 F-Number (F-Stop): Exposure Levels
写作 FN 或 F/N。N 是 f 值
非正式理解：圆形光圈的直径倒数

##### 物理快门（1/25 秒曝光）Physical Shutter (1/25 Sec Exposure)

##### 快门速度的作用
运动模糊：握手、拍摄对象移动

快门时间加倍，运动模糊加倍

注意：运动模糊并不总是坏事！
提示：考虑抗锯齿


滚动快门 Rolling shutter：在不同时间拍摄照片的不同部分

##### 恒定曝光：光圈值与快门速度
这些光圈和快门速度的组合提供等效曝光
| F-Stop | Shutter |
|--------|---------|
| 1.4    | 1/500   |
| 2.0    | 1/250   |
| 2.8    | 1/125   |
| 4.0    | 1/60    |
| 5.6    | 1/30    |
| 8.0    | 1/15    |
| 11.0   | 1/8     |
| 16.0   | 1/4     |
| 22.0   | 1/2     |
| 32.0   | 1       |

如果曝光过亮/过暗，可能需要调整光圈值和/或快门速度

摄影师必须在景深和运动模糊之间做出权衡，以拍摄移动的物体

#### 快与慢摄影 Fast and Slow Photography
##### 高速摄影 High-Speed Photography
正常曝光 = 超快快门速度 x （大光圈 和/或 高ISO）
##### 长曝光摄影 Long-Exposure Photography

## 镜头 Lenses
### 薄透镜近似 Thin Lens Approximation
#### 真实的镜头
真实的镜头设计非常复杂
真实镜头元件并不理想——像差
- 真正的平凸透镜（球面形状）
- 透镜不会将光线会聚到任何一点

#### 理想薄透镜——焦点
- 所有进入透镜的平行光线都会通过其焦点
- 所有通过焦点的光线经过透镜后都将是平行的
- 焦距可以任意改变（实际上，是的！）

#### 高斯薄透镜方程

$$
\frac{1}{f} = \frac{1}{z_i} + \frac{1}{z_o}
$$

### 散焦模糊 Defocus Blur
计算弥散圆（CoC）大小
弥散圆与光圈大小成正比

$$
\frac{C}{A} = \frac{d'}{z_i} = \frac{|z_s - z_i|}{z_i}
$$

#### 重新审视F值（又称F-Stop）
正式定义：镜头的 f 值定义为**焦距除以光圈直径**

实际镜头的常见 f 值：
1.4、2、2.8、4.0、5.6、8、11、16、22、32

f 值 2 有时写作 f/2，这反映了这样一个事实：
- 绝对光圈直径 (A) 可以通过将焦距 (f) 除以相对光圈 (N) 来计算


#### CoC 的大小与 F-Stop 成反比

$$
C = A \cdot \frac{|z_s - z_i|}{z_i} = \frac{f}{N} \cdot \frac{|z_s - z_i|}{z_i}
$$



#### 光线追踪理想薄透镜 Ray Tracing Ideal Thin Lenses
散焦模糊的光线追踪（薄透镜）

（一种可能的）设置：
- 选择传感器尺寸、镜头焦距和光圈大小
- 选择目标景深 zo
- 根据薄透镜方程计算相应的传感器景深 zi

渲染：
- 对于传感器（实际上是胶片）上的每个像素 x'
- 在镜头平面上随机采样 x''
- 已知穿过镜头的光线会击中 x''
（由于 x''' 处于焦点，因此将其视为虚拟光线 (x'，镜头中心)）
- 估算光线 x'' -> x''' 的辐射度

## 光场 Light Fields
### 景深 Depth of Field
将弥散圆设为图像平面上允许的最大模糊点，使其在最终观看条件下显得清晰

#### 景深弥散圆
场景中的深度范围，其中相应的 CoC 被认为足够小


#### 景深方程

$$
\text{DOF} = D_F - D_N
$$

$$
D_F = \frac{D_S f^2}{f^2 - N C (D_S - f)}
$$

$$
D_N = \frac{D_S f^2}{f^2 + N C (D_S - f)}
$$



### 光度计 Lumigraph
#### 全光函数 The Plenoptic Function
问：我们所能看见的所有事物的集合是什么？
答：全光函数（Adelson & Bergen）
让我们从一个静止的人开始，尝试将他能看到的一切参数化
##### 灰度快照 Grayscale snapshot

$$
P(\theta, \phi)
$$

是光的强度
- 从单一视角观察
- 在单一时间点
- 可见光谱波长的平均值
（也可以使用 P(x,y)，但球面坐标系更佳）

##### 彩色快照 Color snapshot

$$
P(\theta, \phi, \lambda)
$$

是光的强度
- 从单一视角观察
- 在单一时间点
- 作为波长的函数

##### 一部电影 Movie

$$
P(\theta, \phi, \lambda, t)
$$

是光的强度
- 从单一视角观察
- 随时间变化
- 作为波长的函数


##### 全息电影 Holographic movie

$$
P(\theta, \phi, \lambda, t, V_x, V_y, V_z)
$$

是光的强度
- 从任何角度看
- 随时间变化
- 作为波长的函数

##### 全光函数 The Plenoptic Function

$$
P(\theta, \phi, \lambda, t, V_x, V_y, V_z)
$$

能够重建每个时刻、每个位置、每个波长下所有可能的视角

包含每张照片、每部电影，以及任何人见过的一切！它完全捕捉了我们的视觉现实！对于一个fXncWion来说，还不错

##### 采样全光功能（顶视图）
只需查找——Quicktime VR

###### 射线 Ray
5D
- 3D位置
- 2D方向

###### 光线重用 Ray Reuse
无限线 Infinite line
- 假设光是恒定的（真空）

4D
- 二维方向
- 二维位置
- 非色散介质


仅需要全光面


#### 光度计 Lumigraph / Lightfield
斯坦福相机阵列 Stanford camera array
##### 整体成像 Integral Imaging
使用微透镜进行空间复用光场捕获：
- 在空间分辨率和角度分辨率之间进行固定的权衡

### 光场相机 Light Field Camera
#### Lytro光场相机
Lytro：由加州大学伯克利分校 Ren Ng 教授创立
微透镜设计

最重要的功能
- 计算重聚焦
（拍照后虚拟改变焦距、光圈大小等）


原理
- 每个像素（辐照度）现在存储为一个像素块（辐照度）
- 拍摄照片的特写视图

如何从光场照片中获取“常规”照片？
- 简单示例——始终选择每个块底部的像素
- 然后是中心像素和顶部像素
- 本质上是“移动相机”

计算/数字重新聚焦
- 相同思路：视觉上改变焦距，并相应地选择重新聚焦的光线方向

总而言之，所有这些功能之所以可用，是因为
- 光场包含一切

##### 光场相机存在的问题
- 空间分辨率不足
（使用同一块胶片来获取空间和方向信息）
- 成本高
（微透镜的设计复杂）
- 计算机图形学需要权衡利弊


# 颜色和感知 Color and Perception
## 颜色 Color 
### 颜色的物理基础 Physical Basis of Color
#### 光的基本成分
- 牛顿证明，阳光可以通过棱镜细分成彩虹
- 由此产生的光线无法通过第二个棱镜进一步细分

#### 可见光谱 The Visible Spectrum of Light
电磁辐射
- 不同频率（波长）的振荡

#### 光谱功率密度 Spectral Power Distribution (SPD)
光测量中的显著特性
- 各波长的光量
- 单位：
  - 辐射单位/纳米（例如：瓦/纳米）
  - 也可以无单位
- 当绝对单位不重要时，通常使用缩放至最大波长的“相对单位”进行跨波长比较

##### 日光光谱功率分布各异
##### 光源的光谱功率分布
描述波长的能量分布

##### 光谱功率分布的线性度

#### 什么是颜色
- 颜色是人类感知的一种现象；它并非光的普遍属性
- 不同波长的光并非“颜色”

## 色彩感知 Color perception 
### 颜色的生物学基础 Biological Basis of Color
#### 人眼的解剖学
##### 视网膜感光细胞：视杆细胞和视锥细胞
Retinal Photoreceptor Cells: Rods and Cones
视杆细胞是极弱光（“暗视”条件）下的主要受体，例如昏暗的月光
- 眼内约有1.2亿个视杆细胞
- 仅感知灰色，无颜色

视锥细胞是典型光照水平（“明视”）下的主要受体
- 眼内约有600-700万个视锥细胞
- 三种类型的视锥细胞，每种都有不同的光谱敏感度
- 提供颜色感知

##### 人类视锥细胞的光谱响应
人类眼睛中有三种类型的视锥细胞，分别对不同波长范围的光敏感，构成了三色视觉系统：
- S锥细胞（Short-wavelength）：主要响应蓝光（大约 420 nm）
- M锥细胞（Medium-wavelength）：主要响应绿光（大约 530 nm）
- L锥细胞（Long-wavelength）：主要响应红光（大约 560 nm）

三种视锥细胞类型的比例差异很大

12位色觉正常的不同人群视网膜中心凹边缘视锥细胞的分布。注意不同类型视锥细胞的百分比差异很大（假彩色图像）

### 色彩三刺激理论 Tristimulus Theory of Color
#### 人类视锥细胞的光谱响应
现在我们有三个探测器（S、M、L 视锥细胞），每个都有不同的光谱响应曲线

$$
S = \int I(\lambda) R_S(\lambda) \, d\lambda \\
M = \int I(\lambda) R_M(\lambda) \, d\lambda \\
L = \int I(\lambda) R_L(\lambda) \, d\lambda
$$


#### 人类视觉系统
- 人眼无法测量，大脑也无法接收关于每种光波长的信息
- 相反，眼睛“看到”的只有三个响应值（S、M、L），而这只是大脑可用的信息。

### 同色异谱现象 Metamerism
#### 同色异谱体 Metamers
同色异谱是指两个不同的光谱（∞维），但投射到相同的（S,M,L）（三维）响应
- 它们在人眼看来具有相同的颜色

同色异谱的存在对于色彩还原至关重要
- 无需还原真实世界场景的全部光谱
- 例如：同色异谱仅用三种颜色的像素，就能在显示器上还原真实世界场景的感知颜色

同色异谱现象十分显著
#### 色彩搭配背后的理论



## 色彩再现/匹配 Color reproduction / matching 
### 加色 Additive Color
给定一组原色光源，每束光都有各自的光谱分布（例如，R、G、B 显示像素）：

$$
sR(\lambda),\quad sG(\lambda),\quad sB(\lambda)
$$

调整这些灯的亮度，并将它们加在一起：

$$
R \cdot sR(\lambda) + G \cdot sG(\lambda) + B \cdot sB(\lambda)
$$

颜色现在由标量值描述：

$$
R, G，B
$$

### CIE RGB配色实验
与之前的加色配色相同，但原色为单色光（单一波长）
测试光也是单色光

### CIE RGB配色函数
对于任何光谱 s，感知颜色都通过以下公式进行匹配，用于缩放 CIE RGB 原色

$$
R_{\text{CIE RGB}} = \int_{\lambda} s(\lambda)\,\overline{r}(\lambda)\,d\lambda
$$

$$
G_{\text{CIE RGB}} = \int_{\lambda} s(\lambda)\,\overline{g}(\lambda)\,d\lambda
$$

$$
B_{\text{CIE RGB}} = \int_{\lambda} s(\lambda)\,\overline{b}(\lambda)\,d\lambda
$$

## 色彩空间 Color space
### 标准色彩空间 Standard Color Spaces
标准化 RGB (sRGB)
- 使特定显示器成为 RGB 标准
- 其他色彩设备通过校准模拟该显示器
- 目前已广泛采用
- 色域 (gamut) 有限

### 通用色彩空间：CIE XYZ
一组假想的标准色原色 X、Y、Z
- 不存在满足这些匹配函数的原色
- Y 为亮度（与颜色无关的亮度）

设计如下：
- 匹配函数严格为正
- 涵盖所有可观察颜色

#### 分离亮度、色度
亮度 Luminance：Y
色度 Chromaticity：x, y, z，定义为

$$
x = \frac{X}{X + Y + Z}
$$

$$
y = \frac{Y}{X + Y + Z}
$$

$$
z = \frac{Z}{X + Y + Z}
$$

由于 x + y + z = 1，我们只需记录其中两个
- 通常选择 x 和 y，得到特定亮度 Y 下的 (x, y) 坐标


#### CIE色度图 CIE Chromaticity Diagram
- 色度图边缘周围的纯（饱和）光谱颜色
- 色度图内部颜色不太纯（去饱和）
- 色度图的质心为白色（1/3, 1/3）

弯曲的边界
- 称为光谱轨迹
- 对应于单色光
（每个点代表单一波长的纯色）


内部的任何颜色都不太纯
- 即混合色



### 色域 Gamut
色域是由一组原色产生的一组色度

不同的色彩空间代表不同的色彩范围

因此，它们具有不同的色域，即它们覆盖色度图上的不同区域

**sRGB** 是互联网上常用的色彩空间



### 按感知组织的颜色空间 Perceptually Organized Color Spaces

#### HSV 颜色空间（色调-饱和度-色值）HSV Color Space (Hue-Saturation-Value)
坐标轴对应色彩的艺术特征
广泛用于“颜色选择器”
##### 色彩的感知维度
色相
- 颜色的“种类”，与属性无关
- 比色学相关值：主波长
- 艺术家相关值：所选颜料颜色
饱和度
- “色彩度”
- 比色学相关值：纯度
- 艺术家相关值：彩色管中颜料的比例
亮度（或明度）
- 总光量
- 比色学相关值：亮度
- 艺术家相关值：色调较浅，阴影较深

##### CIELAB 空间（又称 L*a*b*）
一种常用的色彩空间，力求实现感知的一致性
- L* 表示亮度
- a* 和 b* 表示对立色对
- a* 表示红绿色
- b* 表示蓝黄色


###### 互补色理论 Opponent Color Theory
CIE LAB 中色彩空间维度的神经学基础非常扎实
- 大脑似乎很早就使用三个轴来编码颜色：
  - 白 — 黑，红 — 绿，黄 — 蓝
- 白 — 黑轴代表亮度；其他轴决定色调和饱和度

一个证据：你可以有浅绿色、深绿色、黄绿色或蓝绿色，但你不可能有红绿色
- 因此红色是绿色的对立面
- 另一个证据：残像

**Everything is Relative**

#### CMYK：减色色彩空间 A Subtractive Color Space
##### 减色模型
- 混合越多，颜色越深

青色Cyan、品红色Magenta、黄色Yellow和 基色Key 广泛用于印刷

问题：
- 如果混合 C、M 和 Y 得到 K，那么为什么需要 K？


# 动画 Animation














































































































































































































































































