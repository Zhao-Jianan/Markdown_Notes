# 深度学习基础
## 数据操作
### N维数组
#### N维数组是机器学习和神经网络的主要数据结构
- 0-d(标量)----一个类别
- 1-d(向量)----一个特征向量
- 2-d(矩阵)----一个样本--特征矩阵
- 3-d(RGB图片--宽*高*通道)
- 4-d(RGB图片批量--批量大小*宽*高*通道)
- 5-d(视频批量--批量大小*宽*高*通道)
### 创建数组
#### 创建数组需要
- 形状 
例如3*4矩阵
- 每个元素的数据类型  
例如32位浮点数
- 每个元素的值  
例如全是0或者随机数
  - 正态分布
  - 随机分布
### 访问元素
一个元素
```
x[1,2]
```
一行元素
```
x[1,:]
```
一列元素
```
x[:,1]
```
连续子区域
```
x[1:3, 1:]
```
分散子区域
```
x[::3, ::2]
```
## 线性代数
### 标量
#### 简单操作

$$
c = a + b
$$


$$
c = a \cdot b
$$


$$
c = \sin a
$$

#### 长度

$$
|a| =
\begin{cases} 
a, & \text{if } a > 0 \\ 
-a, & \text{otherwise} 
\end{cases}
$$


$$
|a + b| \leq |a| + |b|
$$


$$
|a \cdot b| = |a| \cdot |b|
$$

### 向量
#### 简单操作

$$
c = a + b \quad \text{where} \quad c_i = a_i + b_i
$$


$$
c = \alpha \cdot b \quad \text{where} \quad c_i = \alpha \cdot b_i
$$


$$
c = \sin a \quad \text{where} \quad c_i = \sin a_i
$$

#### 长度

$$
\|a\|_2 = \left[ \sum a_i^2 \right]^{\frac{1}{2}}
$$


$$
\|a\| \geq 0 \quad \text{for all } a
$$


$$
\|a + b\| \leq \|a\| + \|b\|
$$


$$
\|a \cdot b\| = |a| \cdot \|b\|
$$


$$
c = a + b
$$


$$
c = \alpha \cdot b
$$

##### 点乘

$$
a^T b = \sum a_i b_i
$$

##### 正交

$$
a^T b = \sum a_i b_i = 0
$$


### 矩阵
#### 简单操作

$$
C = A + B \quad \text{where} \quad C_{ij} = A_{ij} + B_{ij}
$$


$$
C = \alpha \cdot B \quad \text{where} \quad C_{ij} = \alpha \cdot B_{ij}
$$


$$
C = \sin A \quad \text{where} \quad C_{ij} = \sin A_{ij}
$$

#### 乘法
##### 矩阵乘以向量

$$
c = A b \quad \text{where} \quad c_i = \sum_j A_{ij} b_j
$$

##### 矩阵乘以矩阵

$$
C = A B \quad \text{where} \quad C_{ik} = \sum_j A_{ij} B_{jk}
$$

#### 范数

$$
c = A \cdot b \quad \text{hence} \quad \|c\| \leq \|A\| \cdot \|b\|
$$

##### 取决于如何衡量b和c的长度
##### 常见范数
###### 矩阵范数：最小的满足上面公式的值
###### Frobenius范数

$$
\|A\|_{\text{Frob}} = \left[ \sum_{i,j} A_{ij}^2 \right]^{\frac{1}{2}}
$$


#### 特殊矩阵
##### 对称和反对称
1. **对称矩阵（Symmetric Matrix）**： 

$$
A_{ij} = A_{ji}, \quad \forall i, j
$$

2. **反对称（斜对称）矩阵（Skew-Symmetric Matrix）**： 

$$
A_{ij} = -A_{ji}, \quad \forall i, j
$$

##### 正定

$$
\|x\|_2^2 = x^T x \geq 0 \quad \Longrightarrow \quad x^T A x \geq 0
$$

##### 正交矩阵
- 所有行都相互正交
- 所有行都有单位长度

$$
\sum_j \Sigma U_{ij} U_{kj} = \delta_{ik}
$$

- 可以写成 

$$
U U^T = I
$$

##### 置换矩阵

$$
P_{ij} =
\begin{cases}
1, & \text{if } j = \pi(i) \\
0, & \text{otherwise}
\end{cases}
$$

置换矩阵是正交矩阵
#### 特征向量和特征值
- 不被矩阵改变竞向的向量
-

$$
Ax = \lambda x
$$

- 对称矩阵总是可以找到特征向量

## 微积分
导数是切线的斜率
### 标量导数
| 函数 \( y \) | 导数 \( \frac{dy}{dx} \) |
|-------------|------------------|
| \( y = a \) | \( 0 \) （a 不是 x 的函数） |
| \( y = x^n \) | \( n x^{n-1} \) |
| \( y = \exp(x) \) | \( \exp(x) \) |
| \( y = \log(x) \) | \( \frac{1}{x} \) |
| \( y = \sin(x) \) | \( \cos(x) \) |
| \( y = u + v \) | \( \frac{du}{dx} + \frac{dv}{dx} \) |
| \( y = uv \) | \( \frac{du}{dx} v + \frac{dv}{dx} u \) |
| \( y = f(u), u=g(x) \) | \( \frac{df}{du} \cdot \frac{du}{dx} \) |

### 亚导数
将导数拓展到不可微的函数
### 梯度
将导数拓展到向量
#### ∂y/∂X

$$
X = \begin{bmatrix} x_1 \\ x_2 \\ \vdots \\ x_n \end{bmatrix}
$$


$$
\frac{\partial y}{\partial X} =
\begin{bmatrix}
\frac{\partial y}{\partial x_1}, \frac{\partial y}{\partial x_2}, \dots, \frac{\partial y}{\partial x_n}
\end{bmatrix}
$$


##### 样例
| 函数 \( y \) | 导数 \( \frac{\partial y}{\partial X} \) |
|-------------|-------------------------|
| \( y = a \) | \( 0^T \) （0 是一个向量） |
| \( y = au \) | \( a \cdot \frac{\partial u}{\partial X} \) |
| \( y = \sum(X) \) | \( 1^T \) （1 是一个向量） |
| \( y = \|X\|_2 \) | \( 2 X^T \) |
| \( y = u + v \) | \( \frac{\partial u}{\partial X} + \frac{\partial v}{\partial X} \) |
| \( y = uv \) | \( \frac{\partial u}{\partial X} \cdot v + \frac{\partial v}{\partial X} \cdot u \) |
| \( y = \langle u, v \rangle \) | \( u^T \frac{\partial v}{\partial X} + v^T \frac{\partial u}{\partial X} \) |



#### ∂Y/∂x

$$
Y = \begin{bmatrix} y_1 \\ y_2 \\ \vdots \\ y_m \end{bmatrix}
$$


$$
\frac{\partial Y}{\partial x} =
\begin{bmatrix}
\frac{\partial y_1}{\partial x} \\
\frac{\partial y_2}{\partial x} \\
\vdots \\
\frac{\partial y_m}{\partial x}
\end{bmatrix}
$$

##### ∂y/∂X是行向量，∂Y/∂x是列向量
##### 这个被称为分子布局符号，反过来的版本叫分母布局符号

#### ∂Y/∂X

$$
X = \begin{bmatrix} x_1 \\ x_2 \\ \vdots \\ x_n \end{bmatrix}
$$


$$
Y = \begin{bmatrix} y_1 \\ y_2 \\ \vdots \\ y_m \end{bmatrix}
$$


$$
\frac{\partial Y}{\partial X} = 
\begin{bmatrix}
\frac{\partial y_1}{\partial x_1} & \frac{\partial y_1}{\partial x_2} & \dots & \frac{\partial y_1}{\partial x_n} \\
\frac{\partial y_2}{\partial x_1} & \frac{\partial y_2}{\partial x_2} & \dots & \frac{\partial y_2}{\partial x_n} \\
\vdots & \vdots & \ddots & \vdots \\
\frac{\partial y_m}{\partial x_1} & \frac{\partial y_m}{\partial x_2} & \dots & \frac{\partial y_m}{\partial x_n}
\end{bmatrix}
$$


##### 样例
| 函数 \( Y \)         | 导数 \( \frac{\partial Y}{\partial X} \)           |
|---------------------|-----------------------------------------------|
| \( Y = a \)         | \( 0 \) （0 是一个矩阵）                        |
| \( Y = X \)         | \( I \) （单位矩阵）                            |
| \( Y = AX \)        | \( A \)                                        |
| \( Y = X^T A \)     | \( A^T \)                                      |
| \( Y = aU \)        | \( a \frac{\partial U}{\partial X} \)          |
| \( Y = AU \)        | \( A \frac{\partial U}{\partial X} \)          |
| \( Y = U + V \)     | \( \frac{\partial U}{\partial X} + \frac{\partial V}{\partial X} \) |


### 拓展到矩阵

## 链式法则
### 标量链式法则

$$
y = f(u), \quad u = g(x)
$$


$$
\frac{\partial y}{\partial x} = \frac{\partial y}{\partial u} \cdot \frac{\partial u}{\partial x}
$$

### 向量链式法则

$$
\frac{\partial y}{\partial X} = \frac{\partial y}{\partial u} \cdot \frac{\partial u}{\partial X}
$$


$$
(1, n) \quad (1, ) \quad (1, n)
$$


$$
\frac{\partial y}{\partial X} = \frac{\partial y}{\partial U} \cdot \frac{\partial U}{\partial X}
$$


$$
(1, n) \quad (1, k) \quad (k, n)
$$


$$
\frac{\partial Y}{\partial X} = \frac{\partial Y}{\partial U} \cdot \frac{\partial U}{\partial X}
$$


$$
(m, n) \quad (m, k) \quad (k, n)
$$


## 自动求导
### 自动求导概念
- 自动求导计算一个函数在指定值上的导数
- 自动求导有别于符号求导和数值求导

### 计算图
- 将代码分解成操作子
- 将计算表示成一个无环图
- 显示构造
  - Tensorflow
  - Theano
  - MXNet
- 隐式构造
  - PyTorch
  - MXNet

### 自动求导的两种模式
#### 链式法则

$$
\frac{\partial y}{\partial x} = \frac{\partial y}{\partial u_n} \cdot \frac{\partial u_n}{\partial u_{n-1}} \cdot \dots \cdot \frac{\partial u_2}{\partial u_1} \cdot \frac{\partial u_1}{\partial x}
$$

#### 正向积累

$$
\frac{\partial y}{\partial x} = \frac{\partial y}{\partial u_n} \left( \frac{\partial u_n}{\partial u_{n-1}} \left( \dots \left( \frac{\partial u_2}{\partial u_1} \cdot \frac{\partial u_1}{\partial x} \right) \right) \right)
$$

#### 反向积累，又称反向传递

$$
\frac{\partial y}{\partial x} = \left( \left( \frac{\partial y}{\partial u_n} \cdot \frac{\partial u_n}{\partial u_{n-1}} \right) \dots \frac{\partial u_2}{\partial u_1} \right) \cdot \frac{\partial u_1}{\partial x}
$$

- 构造计算图 
- 前向:执行图,存储中间结果 
- 反向:从相反竞向执行图 
  - 去除不需要的枝
### 复杂度
#### 计算复杂度
O(n), n 是操作子个数 

通常正向和反向的代价类似 
#### 内存复杂度
O(n),因为需要存储正向的所有中间结果 
#### 跟正向累积对比: 
- O(n) 计算复杂度用来计算一个变量的梯度 
- O(1) 内存复杂度


# 线性神经网络
## 线性回归
### 定义
给定 n 维输入

$$
X = \begin{bmatrix} x_1 \\ x_2 \\ \vdots \\ x_n \end{bmatrix}
$$

线性模型有一个 n 维权重和一个标量偏差 

$$
W = \begin{bmatrix} w_1 \\ w_2 \\ \vdots \\ w_n \end{bmatrix}, \quad b
$$

输出是输入的加权和 

$$
y = w_1 x_1 + w_2 x_2 + \dots + w_n x_n + b
$$


$$
y = \langle W, X \rangle + b
$$



- 线性回归是对n维输入的加权,外加偏差
- 使用平方损失来衡量预测值和真实值的差异
- 线性回归有显式解
- 线性模型可以看做是单层神经网络

### 衡量预估质量
- 比较真实值和预估值,例如房屋售价和估价 
- 假设y是真实值, y_hat是估计值,我们可以比较  

$$
l(y, \hat{y}) = \frac{1}{2} (y - \hat{y})^2
$$

这个叫做平方损失

### 训练数据
- 收集一些数据点来决定参数值(权重和偏差),例如过去6个月卖的房子 
- 这被称之为训练数据 
- 通常越多越好 
- 假设有n个样本,记  


$$
X = \begin{bmatrix} x_1 \\ x_2 \\ \vdots \\ x_n \end{bmatrix}
$$


$$
y = \begin{bmatrix} y_1 \\ y_2 \\ \vdots \\ y_n \end{bmatrix}
$$


### 参数学习
训练损失

$$
l(X,y,w,b) = \frac{1}{2n} \sum_{i=1}^{n} \left( y_i - \langle x_i, w \rangle - b \right)^2 = \frac{1}{2n} \| y - Xw - b \|^2
$$


最小化损失来学习参数


$$
w^*, b^* = \arg \min l(X, y, w, b)
$$



### 显示解
将偏差加入权重

$$
X \leftarrow \begin{bmatrix} X \\ 1 \end{bmatrix}, \quad w \leftarrow \begin{bmatrix} w \\ b \end{bmatrix}
$$


$$
l(X, y, w) = \frac{1}{2n} \|y - Xw\|^2
$$


$$
\frac{\partial}{\partial w} l(X, y, w) = \frac{1}{n} (y - Xw)^T X
$$

损失是凸函数,所以最优解满足

$$
\frac{\partial}{\partial w} l(X, y, w) = 0
$$


## 基础优化方法
### 梯度下降
梯度下降通过不断沿着反梯度方向更新参数求解
#### 步骤
- 挑选一个初始值w_0
- 重复迭代参数 t=1,2,3 


$$
W_t = W_{t-1} - \eta \frac{\partial}{\partial W_{t-1}}
$$


- 沿梯度方向将增加损失函数值 
#### 学习率
步长的超参数
- 选择学习率，不能太小也不能太大
  - 学习率太小，收敛太慢
  - 学习率太大，会在局部最低点附近反复横跳

### 小批量随机梯度下降
- 小批量随机梯度下降是深度学习默认的求解算法
- 在整个训练集上算梯度太贵 
  - 一个深度神经网络模型可能需要数分钟至数小时

我们可以随机采样 b 个样本i_1, i_2,..., i_b来近似损失 

$$
\frac{1}{b} \sum l(X_i, y_i, W)
$$

b 是批量大小,另一个重要的超参数

#### 选择批量大小
一个重要的超参数
- 不能太小  
每次计算量太小,不适合并行来最大利用计算资源
- 不能太大  
内存消耗增加 浪费计算,例如如果所有样本都是相同的

## Softmax 回归
Softmax 回归 = 线性回归 + Softmax
### 概念
- Softmax 回归是一个多类分类模型 
- 使用 Softmax 操作子得到每个类的预测置信度 
- 使用交叉熵来衡量预测和标号的区别
### 回归 vs 分类
- 回归估计一个连续值 
- 分类预测一个离散类别
  - MNIST: 手写数字识别(10类)
  - ImageNet: 自然物体分类(1000类)

### 回归
#### 回归特点
- 单连续数值输出 
- 自然区间 
- 跟真实值的区别作为损失

### 分类
#### 分类特点
- 通常多个输出 
- 输出 i 是预测为第 i 类的置信度

### 均方损失
#### 对类别进行一位有效编码

$$
y = \begin{bmatrix} y_1 \\ y_2 \\ \vdots \\ y_n \end{bmatrix}
$$


$$
y_i = \begin{cases} 
1 & \text{if } i = y \\
0 & \text{otherwise}
\end{cases}
$$

#### 使用均方损失训练 
#### 最大值最为预测

$$
\hat{y} = \arg\max O_i
$$


### 无校验比例
#### 对类别进行一位有效编码 
#### 最大值最为预测

$$
\hat{y} = \arg\max O_i
$$

#### 需要更置信的识别正确类(大余量)

$$
O_y - O_i \geq \Delta(y, i)
$$


### 校验比例
#### 输出匹配概率(非负,和为 1)

$$
\hat{y} = \text{softmax}(O)
$$


$$
\hat{y}_i = \frac{\exp(O_i)}{\sum_k \exp(O_k)}
$$

#### 概率y和y_hat的区别作为损失

### 交叉熵损失
#### 交叉熵常用来衡量两个概率的区别

$$
H(p, q) = - \sum p_i \log(q_i)
$$

#### 将它作为损失

$$
l(y, \hat{y}) = - \sum y_i \log(\hat{y}_i) = - \log(\hat{y}_y)
$$

#### 其梯度是真实概率和预测概率的区别

$$
\frac{\partial}{\partial O_i} l(y, \hat{y}) = \text{softmax}(O)_i - y_i
$$


## 损失函数
### L2 Loss

$$
l(y, y') = \frac{1}{2}(y - y')^2
$$

### L1 Loss

$$
l(y, y') = |y - y'|
$$

### Huber's Robust Loss

$$
l(y, y') = 
\begin{cases}
|y - y'| - \frac{1}{2} & \text{if } |y - y'| > 1 \\
\frac{1}{2}(y - y')^2 & \text{otherwise}
\end{cases}
$$




# 多层感知机
## 感知机
### 概念
- 感知机是一个二分类模型,是最早的AI模型之一 
- 它的求解算法等价于使用批量大小为1的梯度下降 
- 它不能拟合 XOR 函数,导致的第一次 AI 寒冬

### 算法定义
给定输入x，权重w，和偏移b，感知机输出

$$
o = \sigma(\langle w, x \rangle + b)
$$



$$
\sigma(x) = 
\begin{cases}
1 & \text{if } x > 0 \\
0 & \text{otherwise}
\end{cases}
$$


### 二分类： -1或1
- Vs.回归输出实数
- Vs. Softmax回归输出概率

### 收敛定理
- 数据在半径r内 
- 余量ρ分类两类


$$
y(\mathbf{x}^T w + b) \geq \rho
$$



$$
\text{subject to } \|w\|^2 + b^2 \leq 1
$$


- 感知机保证在


$$
\frac{r^2 + 1}{\rho^2}
$$


步后收敛

### XOR 问题 (Minsky & Papert, 1969)
感知机不能拟合 XOR 函数,它只能产生线性分割面

## 多层感知机
### 概念
- 多层感知机使用隐藏层和激活函数来得到非线性模型 
- 常用激活函数是Sigmoid,Tanh,ReLU 
- 使用 Softmax 来处理多类分类 
- 超参数为隐藏层数,和各个隐藏层大小

### Sigmoid 激活函数
将输入投影到 (0, 1), 是一个软的

$$
\sigma(x) =
\begin{cases}
1 & \text{if } x > 0 \\
0 & \text{otherwise}
\end{cases}
$$

#### 公式

$$
\sigma(x) = \frac{1}{1 + \exp(-x)}
$$


### Tanh 激活函数
将输入投影到 (-1, 1)
#### 公式

$$
\tanh(x) = \frac{1 - \exp(-2x)}{1 + \exp(-2x)}
$$


### ReLU 激活函数
ReLU: rectified linear unit
#### 公式

$$
\text{ReLU}(x) = \max(x, 0)
$$


### 多类分类

$$
y_1, y_2, \dots, y_k = \text{softmax}(o_1, o_2, \dots, o_k)
$$


## 模型选择
### 训练误差和泛化误差
- 训练误差
模型在训练数据上的误差 
- 泛化误差
模型在新数据上的误差

### 验证数据集和测试数据集
#### 验证数据集
用来评估模型好坏的数据集 
- 例如拿出 50% 的训练数据 
- 不要跟训练数据混在一起(常犯错误)
#### 测试数据集
只用一次的数据集。例如 
- 未来的考试 
- 我出价的房子的实际成交价 
- 用在 Kaggle 私有排行榜中的数据集

### K-则交叉验证
在没有足够指数据时使用(这是常态)
#### 算法
- 将训练数据分割成 K 块 
- For i = 1, …, K 
- 使用第 i 块作为验证数据集,其余的作为训练数据集 
- 报告 K 个验证集误差的平均 
- 常用:K = 5 或 10


非大数据集上通常使用 k-折交叉验证

### 训练数据集和验证数据集
- 训练数据集----训练模型参数
- 验证数据集----选择模型超参数


## 过拟合(Overfitting)和欠拟合(Underfitting)
### 模型容量
- 拟合各种函数的能力 
- 低容量的模型难以拟合训练数据 
- 高容量的模型可以记住所有的训练数据
- 模型容量需要匹配数据择杂度,否则可能导致欠拟合和过拟合
  - 数据复杂，模型容量低，容易出现欠拟合
  - 数据简单，模型容量高，容易出现过拟合
### 估计模型容量
难以在不同的种类算法之间比较 
- 例如数模型和神经网络 

给定一个模型种类,将有两个主要因素 
- 参数的个数 
- 参数值的选择范围

### VC 维
- 统计学习理论的一个核心思想
- 统计机器学习提供数学工具来衡量模型择杂度
- 对于一个分类模型,VC等于一个最大的数据集的大小,不管如何给定标号,都存在一个模型来对它进行完美分类

### 线性分类器的 VC 维
- 2 维输入的感知机,VC 维 = 3 
  - 能够分类任何三个点,但不是4个 (xor)
- 支持 N 维输入的感知机的 VC 维是 N + 1
- 一些多层感知机的 VC 维 O(N log2 N)

### VC 维的用处
- 提供为什么一个模型好的理论依据 
  - 它可以衡量训练误差和泛化误差之间的间隔 
- 但深度学习中很少使用 
  - 衡量不是很准确 
  - 计算深度学习模型的 VC 维很困难
- 实际中一般靠观察训练误差和验证误差

### 数据复杂度
多个重要因素 
- 样本个数 
- 每个样本的元素个数 
- 时间、空间结构 
- 多样性


## 权重衰退 weight Decay
### 概念
权重衰退通过 L2 正则项使得模型参数不会过大,从而控制模型复杂度 

正则项权重是控制模型择杂度的超参数

### 使用均方范数作为硬性限制
通过限制参数值的选择范围来控制模型容量

$$
\min l(w,b) \quad \text{subject to} \quad ||w||^2 \leq \theta
$$

- 通常不限制偏移 b (限不限制都差不指) 
- 小的θ意味着更强的正则项

### 使用均方范数作为柔性限制
对每个θ,都可以找到λ使得之前的目标函数等价于

$$
\min l(w,b) + \frac{\lambda}{2} ||w||^2
$$

可以通过拉格朗日乘子来证明

超参数λ控制了正则项的重要程度

$$
\lambda = 0: \text{无作用}
$$


$$
\lambda \to \infty, \quad w^* \to 0
$$


### 参数更新法则
#### 计算梯度

$$
\frac{\partial}{\partial w} \left( l(w, b) + \frac{\lambda}{2} ||w||^2 \right) = \frac{\partial l(w, b)}{\partial w} + \lambda w
$$

#### 时间 t 更新参数

$$
w_{t+1} = (1 - \eta \lambda) w_t - \eta \frac{\partial l(w_t, b_t)}{\partial w_t}
$$

通常 ηλ<1 ,在深度学习中通常叫做权重衰退


## 丢弃法 Dropout
### 概念
- 丢弃法将一些输出项随机置0来控制模型复杂度 
- 常作用在多层感知机的隐藏层输出上 
- 丢弃概率是控制模型复杂度的超参数


### 动机
- 一个好的模型需要对输入数据的扰动鲁棒 
- 使用有噪音的数据等价于 Tikhonov 正则 
- 丢弃法:在层之间加入噪音

### 无偏差的加入噪音
- 对x加入噪音得到x',我们希望 


$$
E[x'] = x
$$

- 丢弃法对每个元素进行如下扰动


$$
x'_i = 
\begin{cases} 
0 & \text{with probability } p \\
\frac{x_i}{1-p} & \text{otherwise}
\end{cases}
$$


### 使用丢弃法
通常将丢弃法作用在隐藏全连接层的输出上

$$
h = \sigma(W_1x + b_1)
$$


$$
h' = \text{dropout}(h)
$$


$$
o = W_2h' + b_2
$$


$$
y = \text{softmax}(o)
$$


### 推理中的丢弃法
- 正则项只在训练中使用，他们影响模型参数的更新 
- 在推理过程中,丢弃法直接返回输入


$$
h' = \text{dropout}(h)
$$

这样也能变证确定性的输出


## 数值稳定性
### 神经网络的梯度
考虑如下有 d 层的神经网络

$$
h_t = f_t(h_{t-1})
$$


$$
y = l \circ f_d \circ \dots \circ f_1(x)
$$

计算损失l关于参数W_t的梯度

$$
\frac{\partial l}{\partial W_t} = \frac{\partial l}{\partial h_d} \frac{\partial h_d}{\partial h_{d-1}} \dots \frac{\partial h_{t+1}}{\partial h_t} \frac{\partial h_t}{\partial W_t}
$$

d-t 次矩阵乘法

### 数值稳定性的常见两个问题
#### 梯度爆炸
##### 值超出值域(infinity) 
对于16位浮点数尤为严重(数值区间6e-5 - 6e4)
##### 对学习率敏感 
- 如果学习率太大 -> 大参数值 -> 更大的梯度 
- 如果学习率太小 -> 训练无进展 
- 可能需要在训练过程不断调整学习率
#### 梯度消失
##### 梯度值变成0
对 16 位浮点数尤为严重
##### 训练没有进展
不管如何选择学习率 
##### 对于底部层尤为严重 
- 仅仅顶部层训练的较好 
- 无法让神经网络更深

**当数值过大或者过小时会导致数值问题**
**常发生在深度模型中,因为其会对 n 个数累乘**


## 模型初始化和激活函数
合理的权重初始值和激活函数的选取可以提升数值稳定性
### 让训练更加稳定
#### 目标：让梯度值在合理的范围内 
例如[1e-6, 1e3]
#### 将乘法变加法
ResNet, LSTM
#### 归一化 
- 梯度归一化
- 梯度裁剪
#### 合理的权重初始和激活函数


### 让每层的方差是一个常数
- 将每层的输出和梯度都看做随机变量 
- 让它们的均值和方差都保持一致

### 权重初始化
在合理值区间里随机初始参数

训练开始的时候更容易有数值不稳定 
- 远离最优解的地方损失函数表面可能很复杂
- 最优解附近表面会比较平 

使用N(0, 0.01)来初始可能对小网络没问题,但不能保证深度神经网络

### Xavier 初始化
难以需要满足

$$
n_{t-1} \gamma_t = 1
$$

和

$$
n_t \gamma_t = 1
$$

Xavier 使得

$$
\frac{\gamma_t (n_{t-1} + n_t)}{2} = 1 \quad \Rightarrow \quad \gamma_t = 2(n_{t-1} + n_t)
$$

- 正态分布


$$
N\left(0, \sqrt{\frac{2}{n_{t-1} + n_t}}\right)
$$


- 均匀分布


$$
u\left(-\sqrt{\frac{6}{n_{t-1} + n_t}}, \sqrt{\frac{6}{n_{t-1} + n_t}}\right)
$$


分布u[-a, a]和方差是 a^2/3

适配权重形状变换,特别是 n_t


# 深度学习硬件
## CPU和GPU
### 提升CPU利用率
在计算a+b之前,需要准备数据 

主内存 -> L3 -> L2 -> L1 -> 寄存器 
- L1 访问延时:0.5 ns 
- L2 访问延时:7 ns (14 x L1) 
- 主内存访问延时:100ns (200 x L1) 
提升空间和时间的内存本地性 
- 时间
重用数据使得变持它们在缓存里 
- 空间
按序读写数据使得可以预读取

高端 CPU 有几十个核 
- EC2 P3.16xlarge: 2 Intel Xeon CPUs, 32 物理核 

并行来利用所有核 
- 超线程不一定提升性能，因为它们共享寄存器

### 样例分析
如果一个矩阵是按列存储,访问一行会比访问一列要快 
- CPU一次读取 64 字节(缓存线) 
- CPU会“聪明的”提前读取下一个(缓存线)

代码A比代码B慢(python)
代码A：
```
for i in range(len(a)):
	c[i] = a[i] + b[i]
```
代码B：
```
c = a + b
```
代码A调用 n 次函数,每次调用有开销 

代码B很容易被并行(例如下面C++实现)
```
#pragma omp for
for (i=0; i<a.size(); i++) {
	c[i] = a[i] + b[i]
}
```
### 提升GPU利用率
#### 并行 
使用数千光线程 
#### 内存本地性 
缓存更小,架构更加简单 
#### 少用控制语句 
- 支持有限 
- 同步开销很大

**不要频繁在CPU和GPU之前传数据：带宽限制，同步开销**

### 更多的 CPUs 和 GPUs
- CPU
  - AMD
  - ARM 
- GPU
  - NVIDIA
  - AMD
  - Intel
  - ARM
  - Qualcomm
  - …

### CPU/GPU高性能计算编程
- CPU
  - C++ 或者任何高性能语言 
  - 编译器成熟 
- GPU 
  - Nvidia 上用 CUDA 
    - 编译器和驱动成熟 
  - 其他用 OpenCL 
    - 质量取决于硬件厂商

### CPU/GPU比较
- CPU  
可以处理通用计算。性能优化考虑数据读写效率和多线程 
- GPU  
使用更多的小核和更好的内存带宽,适合能大规模并行的计算任务

## 专有硬件
### DSP----数字信号处理
- 为数字信号处理算法设计
  - 点积
  - 卷积
  - FFT 
- 低功耗、高性能 
  - 比移动GPU快5x,功耗更低 
- VLIW: Very long instruction word 
  - 一条指令计算上百次乘累加 
- 编程和调试困难 
- 编译器质量良莠不齐

### 可编程阵列 (FPGA)
- 有大量可以编程逻辑单元和可配置的连接 
- 可以配置成计算复杂函数 
  - 编程语言:VHDL,Verilog 
- 通常比通用硬件更高效 
- 工具链质量良莠不齐 
- 一次“编译”需要数小时

### AI ASIC
- 深度学习的热门领域 
  - 大公司都在造自己的芯片 (Intel, Qualcomm, Google, Amazon, Facebook, …) 
- Google TPU 是标志性芯片 
  - 能够媲美Nvidia GPU性能 
  - 在Google大量部署 
  - 核心是 systolic array

### Systolic Array
- 计算单元(PE)阵列 
- 特别适合做矩阵乘法 
- 设计和制造相对简单
- 对于一般的矩阵内法，通过切开和填充来匹配SA大小 
- 批量输入来降低延时 
- 通常有其他硬件单元来处理别的 NN 操作子，例如激活层

## 多GPU并行
### 单机多卡并行
- 一台机器可以安装多个GPU(1-16) 
- 在训练和预测时,我们将一个小批量计算切分到多个GPU上来达到加速目的 
### 常用切分方案有 
- 数据并行 
- 模型并行 
- 通道并行(数据+模型并行)

### 数据并行 vs 模型并行
#### 数据并行
- 将小批量分成n块，每个GPU拿到完整参数计算一块数据的梯度
- 通常性能更好
#### 模型并行
- 将模型分成n块，每个GPU拿到一块模型计算它的前向和反向结果 
- 通常用于模型大到单GPU放不下

#### 数据并行步骤
- 读一个数据块
- 拿回参数
- 计算梯度
- 发出梯度
- 更新梯度


当一个模型能用单卡计算时,通常使用数据并行拓展到多卡上 

模型并行则用在超大模型上


## 分布式计算
### 分布式计算架构
- 数据放在分布式文件系统上
- 通过网络读取数据
- 多个worker
- 通过网络发送
- 多个参数服务器

### GPU机器架构
- 交换机
- CPU
- PCle交换
- GPU

### 计算一个小批量
- 每个计算服务器读取小批量中的一块
- 进一步将数据切分到每个GPU上
- 每个worker从参数服务器那里获取模型
- 复制参数到每个GPU上
- 每个GPU计算梯度
- 将所有GPU上的梯度求和
- 梯度传回服务器
- 每个服务器对梯度求和,并更新参数

### 同步 SGD
- 这里每个worker都是同步计算一个批量,称为同步SGD 
- 假设有n个GPU,每个GPU每次处理b个样本,那么同步SGD等价于在单 GPU 运行批量大小为nb的SGD 
- 在理想情况下, n个GPU可以得到相对单个GPU的n倍加速

### 性能
- t_1 = 在单GPU上计算b个样本梯度时间 
- 假设有m个参数,一个 worker 每次发送和接收m个参数、梯度 
  - t2 = 发送和接收所用时间 
- 每个批量的计算时间为 max(t_1, t_2)
  - 选取足够大的 b 使得 t_1 > t_2
  - 增加b或n导致更大的批量大小，导致需要更多计算来得到给定的模型精度

### 性能的权衡
- 系统性能----每epoch时间
- 训练有效性--需要多个epoch

### 实践时的建议
- 使用一个大数据集 
- 需要好的GPU-GPU和机器-机器带宽 
- 高效的数据读取和预处理 
- 模型需要有好的计算(FLOP)通讯(model size)比 
  - Inception > ResNet > AlexNet 
- 使用足够大的批量大小来得到好的系统性能 
- 使用高效的优化算法对对应大批量大小

### 分布式计算注意
- 分布式同步数据并行是多GPU数据并行在多机器上的拓展 
- 网络通讯通常是瓶颈 
- 需要注意使用特别大的批量大小时收敛效率 
- 更复杂的分布式有异步、模型并行




# 卷积神经网络
## 从全连接层到卷积层
对全连接层使用平移不变性和局部性得到卷积层
### 重新考察全连接层
- 将输入和输出变形为矩阵(宽度,高度)
- 将权重变形为4-D张量(h, w)到(h', w')


$$
h_{i,j} = \sum_{k,l} (w_{i,j,k,l} x_{k,l}) = \sum_{a,b} (v_{i,j,a,b} x_{i+a,j+b})
$$


- V 是 W 的重新索引


$$
v_{i,j,a,b} = w_{i,j,i+a,j+b}
$$


### 原则 #1 - 平移不变性
x 的平移导致 h 的平移

$$
h_{i,j} = \sum_{a,b} v_{i,j,a,b} x_{i+a,j+b}
$$

v不应该依赖于(i,j) 

解决方案

$$
v_{i,j,a,b} = v_{a,b}
$$


$$
h_{i,j} = \sum_{a,b} v_{a,b} x_{i+a,j+b}
$$

这就是2维交叉相关,即2维卷积

### 原则 #2 - 局部性

$$
h_{i,j} = \sum_{a,b} v_{a,b} x_{i+a,j+b}
$$

#### 当评估h_i,j时,我们不应该用远离x_i,j的参数
#### 解决方案

$$
\text{When } |a|, |b| > \Delta, \text{ set } v_{a,b} = 0
$$


$$
h_{i,j} = \sum_{a,b} v_{a,b} x_{i+a,j+b}
$$

 
## 图像卷积
### 二维交叉相关

### 二维卷积层
输入

$$
X: n_h \times n_w
$$

核 

$$
W: k_h \times k_w
$$

偏差 

$$
b \in \mathbb{R}
$$

输出

$$
Y: (n_h - k_h + 1) \times (n_w - k_w + 1)
$$


$$
Y = X \star W + b
$$

W 和 b 是可学习的参数

### 交叉相关 vs 卷积
二维交叉相关

$$
y_{i,j} = \sum \sum w_{a,b} x_{i+a,j+b}
$$

二维卷积

$$
y_{i,j} = \sum \sum w_{-a,-b} x_{i+a,j+b}
$$

由于对称性,在实际使用中没有区别

### 一维和三维交叉相关
一维

$$
y_i = \sum w_a x_{i+a}
$$

应用
- 文本
- 语言
- 时序序列


三维

$$
y_{i,j,k} = \sum \sum \sum w_{a,b,c} x_{i+a,j+b,k+c}
$$

应用
- 视频
- 医学图像
- 气象地图

### 图像卷积特点
- 卷积层将输入和核矩阵进行交叉相关,加上偏移后得到输出 
- 核矩阵和偏移是可学习的参数 
- 核矩阵的大小是超参数


## 填充和步幅
### 概念
- 填充和步幅是卷积层的超参数 
- 填充在输入周围添加额外的行/列,来控制输出形状的减少量 
- 步幅是每次滑动核窗口时的行/列的步长,可以成倍的减少输出形状

### 填充
- 给定(32 × 32)输入图像 
- 应用 5 × 5 大小的 卷积核
  - 第1层得到输出大小 28 x 28 
  - 第7层得到输出大小4 x 4 
- 更大的卷积核可以更快地减小输出大小 
  - 形状从n_h × n_w减少到


$$
(n_h - k_h + 1) \times (n_w - k_w + 1)
$$


- 在输入周围添加额外的行 / 列
- 填充p_h行和p_w列,输出形状为


$$
(n_h - k_h + p_h + 1) \times (n_w - k_w + p_w + 1)
$$


- 通常取


$$
p_h = k_h - 1, \quad p_w = k_w - 1
$$


  - 当k_h为奇数:在上下两侧填充p_h/2
  - 当k_h为偶数:在上侧填充「p_h/2|，在下侧填充 |ph/2」


$$
\text{Top padding} = \left\lceil \frac{p_h}{2} \right\rceil, \quad \text{Bottom padding} = \left\lfloor \frac{p_h}{2} \right\rfloor
$$



### 步幅
填充减小的输出大小与层数线性相关 
- 给定输入大小 224 × 224,在使用 5 × 5 卷积核的情况下,需要 44 层将输出降低到 4 × 4 
- 需要大量计算才能得到较小输出
- 步幅是指行/列的滑动步长 
  - 例:高度3 宽度2 的步幅

给定高度s_h和宽度s_w的步幅,输出形状是

$$
\left\lfloor \frac{n_h - k_h + p_h + s_h}{s_h} \right\rfloor \times \left\lfloor \frac{n_w - k_w + p_w + s_w}{s_w} \right\rfloor
$$


如果

$$
p_h = k_h - 1, \quad p_w = k_w - 1
$$


$$
\left\lfloor \frac{n_h + s_h - 1}{s_h} \right\rfloor \times \left\lfloor \frac{n_w + s_w - 1}{s_w} \right\rfloor
$$


如果输入高度和宽度可以被步幅整除

$$
\frac{n_h}{s_h} \times \frac{n_w}{s_w}
$$



## 多个输入和输出通道
### 概念
- 输出通道数是卷积层的超参数 
- 每个输入通道有独立的二维卷积核,所有通道结果相加得到一个输出通道结果 
- 每个输出通道有独立的三维卷积核


### 多个输入通道
- 彩色图像可能有 RGB 三个通道
- 转换为灰度会丢失信息
- 每个通道都有一个卷积核,结果是所有通道卷积结果的和

输入

$$
X: c_i \times n_h \times n_w
$$

核

$$
W: c_i \times k_h \times k_w
$$

输出

$$
Y: m_h \times m_w
$$


$$
Y = \sum X_{i,:,:} \star W_{i,: ,:}
$$


### 多个输出通道
无论有多少输入通道,到目前为止我们只用到单输出通道

我们可以有多个三维卷积核,每个核生成一个输出通道 

输入

$$
X: c_i \times n_h \times n_w
$$

核

$$
W: c_o \times c_i \times k_h \times k_w
$$

输出

$$
Y: c_o \times m_h \times m_w
$$


$$
Y = X \star W_{i,:,:} \quad \text{for} \quad i = 1, \dots, C_o
$$


### 多个输入和输出通道
- 每个输出通道可以识别特定模式
- 输入通道核识别并组合输入中的模式

### 1 × 1 卷积层

$$
k_h = k_w = 1
$$

是一个受欢迎的选择。它不识别空间模式,只是融合通道

相当于输入形状为

$$
n_h \times n_w \times c_i
$$

权重为

$$
c_o \times c_i
$$

的全连接层


## 池化层
### 池化层
卷积对位置敏感

需要一定程度的平移不变性

照明,物体位置,比例,外观等等因图像而异

### 池化层特征
- 池化层返回窗口中最大或平均值 
- 缓解卷积层对位置的敏感性 
- 同样有窗口大小、填充、和步幅作为超参数
- 没有可学习的参数

### 二维最大池化
返回滑动窗口中的最大值

### 填充,步幅和多个通道
- 池化层与卷积层类似,都具有填充和步幅 
- 在每个输入通道应用池化层以获得相应的输出通道
- 输出通道数 = 输入通道数

### 平均池化层
- 最大池化层  
每个窗口中最强的模式信号
- 平均池化层  
将最大池化层中的“最大”操作替换为“平均”


## 批量归一化
要解决的问题
- 损失出现在最后,后面的层训练较快 
- 数据在最底部 
  - 底部的层训练较慢 
  - 底部层一变化,所有都得跟着变 
  - 最后的那些层需要重新学习多次 
  - 导致收敛变慢 

*我们可以在学习底部层的时候避免变化顶部层吗？*

### 批量归一化算法
固定小批量里面的均值和方差

$$
\mu_B = \frac{1}{|B|} \sum x_i
$$


$$
(\sigma_B)^2 = \frac{1}{|B|} \sum (x_i - \mu_B)^2 + \epsilon
$$

然后再做额外的调整

$$
x_{i+1} = \gamma \frac{x_i - \mu_B}{\sigma_B} + \beta
$$

可学习的参数
- 方差γ
- 均值β

### 批量归一化层
- 作用在 
  - 全连接层和卷积层输出上,激活函数前 
  - 全连接层和卷积层输入上
- 对全连接层,作用在特征维 
- 对于卷积层,作用在通道维

### 批量归一化本质上是在做什么
最初论文是想用它来减少内部协变量转移 

后续有论文指出它可能就是通过在每个小批量里加入噪音来控制模型复杂度

$$
x_{i+1} = \gamma \frac{x_i - \hat{\mu}_B}{\hat{\sigma}_B} + \beta
$$


- μ_hat_B是随机偏移
- σ_hat_B是随机缩放
**因此批量归一化没必要跟丢弃法混合使用**

### 批量归一化特点
- 批量归一化固定小批量中的均值和方差，然后学习出适合的偏移和缩放 
- 可以加速收敛速度,但一般不改变模型精度


## 现代卷积神经网络
### LeNet
#### MNIST数据集
- 手写数字的黑白图片
- 样本数 60K
- 50,000 个训练数据
- 10,000 个测试数据
- 图像大小 28 × 28 
- 10类
#### LeNet架构
       Dense(10)
          ↑
       Dense(84)
          ↑
       Dense(120)
          ↑
    2×2 AvgPool, stride 2
          ↑
    5×5 Conv(6), pad 2
          ↑
    2×2 AvgPool, stride 2
          ↑
    5×5 Conv(6), pad 2
          ↑
      image(32×32)


LeNet是早期成功的神经网络 

- 先使用卷积层来学习图片空间信息 
- 然后使用全连接层来转换到类别空间

### AlexNet
#### 90年代的机器学习特点
- 特征提取 
- 选择核函数来计算相似性 
- 凸优化问题 
- 漂亮的定理
#### 几何学
- 抽取特征 
- 描述几何(例如多相机) 
- (非)凸优化 
- 漂亮定理 

如果假设满足了,效果很好
#### 特征工程
- 特征工程是关键 
- 特征描述子:SIFT,SURF 
- 视觉词袋(聚类) 
- 最后用 SVM

#### ImageNet (2010)数据集
- 自然物体的彩色图片
- 样本数 1.2M
- 图像大小 469 × 387 
- 1000类

#### AlexNet特点
- AlexNet 赢了 2012 年 ImageNet 竞赛,标志着新的一轮神经网络热潮的开始 
- 更深更大的 LeNet,10x 参数个数,260x 计算复杂度 
- 主要改进 
  - 丢弃法 
  - ReLu 
  - MaxPooling 
- 计算机视觉方法论的改变


#### AlexNet 架构
       Dense(1000)
          ↑
       Dense(4096)
          ↑
       Dense(4096)
          ↑
    3×3 MaxPool, stride 2
          ↑
    3×3 Conv(384), pad 1
          ↑
    3×3 Conv(384), pad 1
          ↑
    3×3 Conv(384), pad 1
          ↑
    3×3 MaxPool, stride 2
          ↑
    5×5 Conv(256), pad 2
          ↑
    3×3 MaxPool, stride 2
          ↑
    11×11 Conv(96), stride 4
          ↑
      image(3×224×224)


#### AlexNet细节
- 更大的池化窗口，使用最大池化层
- 更大的核窗口和步长，因为图片更大了
- 激活函数从 sigmoid 变到了 ReLu (减缓梯度消失) 
- 隐藏全连接层后加入了丢弃层 
- 数据增强

### 使用块的网络VGG
#### 为解决的问题
- AlexNet 比 LeNet 更深更大来得到更好的精度 
- 能不能更深和更大? 
- 选项 
  - 更多的全连接层(太贵) 
  - 更多的卷积层 
  - 将卷积层组合成块

#### VGG块
##### 深 vs. 宽? 
- 5×5 卷积 
- 3×3 卷积 
- 深但窄效果更好 
##### VGG 块 
- 3×3 卷积(填充 1) (n 层, m 通道) 
- 2×2 最大池化层 (步幅 2)

#### VGG 架构
- 多个VGG块后接全连接层 
- 不同次数的重复块得到不同的架构 VGG-16, VGG-19,...

#### LeNet和AlexNet和VGG
##### LeNet (1995) 
- 2 卷积 + 池化层 
- 2 全连接层 
##### AlexNet 
- 更大更深 
- ReLu, Dropout, 数据增强 
##### VGG 
- 更大更深的 AlexNet(重复的 VGG 块)

#### VGG特点
- VGG使用可重复使用的卷积块来构建深度卷积神经网络 
- 不同的卷积块个数和超参数可以得到不同复杂度的变种

### 网络中的网络(NiN)
#### 全连接层的问题
##### 卷积层需要较少的参数

$$
c_i \times c_o \times k^2
$$

##### 但卷积层后的第一个全连接层的参数
###### LeNet
16×5×5×120 = 48k 
###### AlexNet
256×5×5×4096 = 26M 
###### VGG
512×7×7×4096 = 102M

#### NiN 块
- 一个卷积层后跟两个全连接层 
  - 步幅 1,无填充,输出形状跟卷积层输出一样 
  - 起到全连接层的作用

#### NiN架构
- 无全连接层 
- 交替使用NiN块和步幅为2的最大池化层 
  - 逐步减小高宽和增大通道数 
- 最后使用全局平均池化层得到输出 
  - 其输入通道数是类别数

#### NiN特点
- NiN块使用卷积层加两个1×1卷积层
  - 后者对每个像素增加了非线性性 
- NiN使用全局平均池化层来替代VGG和AlexNet中的全连接层 
  - 不容易过拟合,更少的参数个数

### 含并行连结的网络(GoogLeNet)
#### Inception块
Inception块用4条有不同超参数的卷积层和池化层的路来抽取不同的信息，然后在输出通道维合并
- 使用不同窗口大小的卷积层
- 使用池化层
- 输出跟输入等同高宽

跟单3×3或5×5卷积层比,Inception块有更少的参数个数和计算复杂度

它的一个主要优点是模型参数小,计算复杂度低

#### GoogLeNet架构
GoogleNet使用了9个Inception块,是第一个达到上百层的网络
##### Stage 1 & 2
更小的宽口，更多的通道
##### Stage 3
- 通道分配不同
- 输出通道增加
##### Stage 4 & 5
- 增加通道数
- 1024维特征输出

#### Inception 有各种后续变种
##### Inception-BN (v2)
使用 batch normalization
##### Inception-V3
修改了Inception块 
- 替换 5×5 为多个 3×3 卷积层 
- 替换 5×5 为 1×7 和 7×1 卷积层 
- 替换 3×3 为 1×3 和 3×1 卷积层 
- 更深 
##### Inception-V4
使用残差连接


### 残差网络(ResNet)
#### 残差块
- 串联一个层改变函数类,我们希望能扩大函数类 
- 残差块加入快速通道来得到 f(x) = x + g(x) 的结构

#### ResNet 块
- 高宽减半ResNet块(步幅 2) 
- 后接指个高宽不变ResNet块

#### ResNet 架构
- 类似 VGG 和 GoogleNet 的总体架构 
- 但替换成了ResNet 块

#### 残差网络特点
- 残差块使得很深的网络更加容易训练 
  - 甚至可以训练一千层的网络 
- 残差网络对随后的深层神经网络设计出问了深远影响,无论是卷积类网络还是全连接类网络



# 循环神经网络
## 序列模型
时序模型中,当前数据跟之前观察到的数据相关
### 序列数据
实际中很多数据是有时序结构的 
- 电影的评价随时间变化而变化 
  - 拿奖后评分上升,直到奖项被忘记 
  - 看了很多好电影后,人们的期望变高 
  - 季节性:贺岁片、暑期档 
  - 导演、演员的负面报道导致评分变低
- 音乐、语言、文本、和视频都是连续的 
  - 标题“狗咬人”远没有“人咬狗”那么令人惊讶 
  - 大地震发问后,很可能会有几次较小的余震 
  - 人的互动是连续的,从网上吵架可以看出 
  - 预测明天的股价要比填补昨天遗失的股价的更困难

### 统计工具
- 在时间 观察到x_t,那么得到T个不独立的随机变量 

$$
(x_1, \ldots, x_T) \sim p(x)
$$


- 使用条件概率展开 


$$
p(a, b) = p(a)\,p(b \mid a) = p(b)\,p(a \mid b)
$$


链式法则（Chain Rule of Probability）公式

$$
p(x) = p(x_1) \cdot p(x_2 \mid x_1) \cdot p(x_3 \mid x_1, x_2) \cdot \ldots \cdot p(x_T \mid x_1, \ldots, x_{T-1})
$$


链式法则的反向展开形式

$$
p(x) = p(x_T) \cdot p(x_{T-1} \mid x_T) \cdot p(x_{T-2} \mid x_{T-1}, x_T) \cdot \ldots \cdot p(x_1 \mid x_2, \ldots, x_T)
$$


对条件概率建模

$$
p(x_t \mid x_1, \ldots, x_{t-1}) = p(x_t \mid f(x_1, \ldots, x_{t-1}))
$$

对见过的数据建模,也称自回归模型

#### 方案 A - 马尔可夫假设
马尔科夫模型假设当前只跟最近少数数据相关,从而简化模型

假设当前当前数据只跟τ个过去数据点相关

$$
p(x_t \mid x_1, \ldots, x_{t-1}) = p(x_t \mid x_{t-\tau}, \ldots, x_{t-1}) = p(x_t \mid f(x_{t-\tau}, \ldots, x_{t-1}))
$$


#### 方案 B - 潜变量模型
潜变量模型使用潜变量来概括历史信息

引人潜变量h_t来表示过去信息

$$
h_t = f(x_1, \ldots, x_{t-1})
$$

这样

$$
x_t = p(x_t \mid h_t)
$$


## 语言模型
给定文本序列,

$$
x_1, x_2, \ldots, x_T
$$

语言模型的目标是估计联合概率

$$
p(x_1, \ldots, x_T)
$$

### 它的应用包括 
- 做预训练模型(eg BERT,GPT-3) 
- 生成文本,给定前面几个词,不断的使用


$$
x_t \sim p(x_t \mid x_1, \ldots, x_{t-1})
$$

来生成后续文本 

- 判断多个序列中哪个更常见,e.g.“to recognize speech” vs “to wreck a nice beach

### 使用计数来建模
假设序列长度为2,我们预测

$$
p(x, x') = p(x) p(x' \mid x) = \frac{n(x, x')}{n(x)}
$$

这里 n 是总词数, 

$$
n(x) \quad \text{and} \quad n(x, x')
$$

是单个单词和连续单词对的出现次数

很容易拓展到长为3的情况

$$
p(x, x', x'') = p(x) p(x' \mid x) p(x'' \mid x, x') = \frac{n(x, x', x'')}{n(x)} = \frac{n(x, x')}{n(x)} \cdot \frac{n(x, x', x'')}{n(x, x')}
$$

### N元语法
当序列很长时,因为文本量不够大,很可能

$$
n(x_1, \ldots, x_T) \leq 1
$$

使用马尔科夫假设可以缓解这个问题

一元语法

$$
p(x_1, x_2, x_3, x_4) = p(x_1) p(x_2) p(x_3) p(x_4) = \frac{n(x_1)}{n} \cdot \frac{n(x_2)}{n} \cdot \frac{n(x_3)}{n} \cdot \frac{n(x_4)}{n}
$$

二元语法

$$
p(x_1, x_2, x_3, x_4) = p(x_1) p(x_2 \mid x_1) p(x_3 \mid x_2) p(x_4 \mid x_3) = \frac{n(x_1)}{n} \cdot \frac{n(x_1, x_2)}{n(x_1)} \cdot \frac{n(x_2, x_3)}{n(x_2)} \cdot \frac{n(x_3, x_4)}{n(x_3)}
$$

三元语法

$$
p(x_1, x_2, x_3, x_4) = p(x_1) p(x_2 \mid x_1) p(x_3 \mid x_1, x_2) p(x_4 \mid x_2, x_3)
$$


## 循环神经网络
循环神经网络的输出取决于当下输入和前一时间的隐变量
应用到语言模型中时,循环神经网络根据当前词预测下—次时刻词
通常使用困惑度来衡量语言模型的好坏
### 潜变量自回归模型
使用潜变量 h_t 总结过去信息


更新隐藏状态:

$$
h_t = \phi(W_{hh} h_{t-1} + W_{hx} x_{t-1} + b_h)
$$


输出:

$$
o_t = \phi(W_{ho} h_t + b_o)
$$


### 困惑度(perplexity)
衡量一个语言模型的好坏可以用平均交叉熵：

$$
\pi = \frac{1}{n} \sum_{i=1}^{n} -\log p(x_t \mid x_{t-1}, \dots)
$$

p 是语言模型的预测概率, x_t 是真实词

历史原因NLP使用困惑度 exp(π) 来衡量, 是平均每次可能选项
- 1表示完美,无穷大是最差情况


### 梯度裁剪
迭代中计算这 T 个时间步上的梯度,在反向传播过程中产生长度为 O(T) 的矩阵乘法链,导致数值不稳定

梯度裁剪能有效预防梯度爆炸

如果梯度长度超过 θ ,那么拖影影长度θ

$$
g \leftarrow \min \left( 1, \frac{\theta}{\|g\|} \right) g
$$

### 更多的应用 RNNs
- ⽂本⽣成
- ⽂本分类
- 问答、机器翻译
- Tag⽣成



## 门控循环单元 GRU
关注一个序列
- 不是每个观察值都是同等重要
- 想只记住相关的观察需要: 
  - 能关注的机制(更新门) 
  - 能遗忘的机制(重置门)

### 门

$$
R_t = \sigma(X_t W_{xr} + H_{t-1} W_{hr} + b_r)
$$

$$
Z_t = \sigma(X_t W_{xz} + H_{t-1} W_{hz} + b_z)
$$

### 候选隐状态

$$
\tilde{H}_t = \tanh(X_t W_{xh} + (R_t \odot H_{t-1}) W_{hh} + b_h)
$$

### 隐状态

$$
H_t = Z_t \odot H_{t-1} + (1 - Z_t) \odot \tilde{H}_t
$$



## 长短期记忆网络(LSTM)
### 构成组件
#### 输入门
决定不是忽略掉输入数据 

$$
I_t = \sigma(X_t W_{xi} + H_{t-1} W_{hi} + b_i)
$$

#### 忘记门
将值朝0减少

$$
F_t = \sigma(X_t W_{xf} + H_{t-1} W_{hf} + b_f)
$$

#### 输出门
决定是不是使用隐状态

$$
O_t = \sigma(X_t W_{xo} + H_{t-1} W_{ho} + b_o)
$$


### 候选记忆单元

$$
\tilde{C}_t = \tanh(X_t W_{xc} + H_{t-1} W_{hc} + b_c)
$$


### 记忆单元

$$
C_t = F_t \odot C_{t-1} + I_t \odot \tilde{C}_t
$$


### 隐状态

$$
H_t = O_t \odot \tanh(C_t)
$$


## 深度循环神经网络
深度循环神经网络使用多个隐藏层来获得更多的非线性性

$$
H_t = f(H_{t-1}, X_t)
$$


$$
O_t = g(H_t)
$$


$$
H^1_t = f_1(H^1_{t-1}, X_t)
$$


$$
H^j_t = f_j(H^{j-1}_t, H^{j-1}_{t-1})
$$


$$
O_t = g(H^L_t)
$$


## 双向循环神经网络
未来很重要
I am _____ 
I am _____ very hungry, 
I am _____ very hungry, I could eat half a pig.

I am **happy**. 
I am **not** very hungry, 
I am **very** very hungry, I could eat half a pig.


取决于过去和未来的上下文,可以填很不—样的词

在填空的时候,我们也可以看未来

### 双向 RNN 架构
- 一个前向RNN隐层 
- 一个方向RNN隐层 
- 合并两个隐状态得到输出


$$
H_t = \varphi(X_t W_{xh}^{(f)} + H_{t-1} W_{hh}^{(f)} + b_h^{(f)})
$$


$$
H_t = \varphi(X_t W_{xh}^{(b)} + H_{t+1} W_{hh}^{(b)} + b_h^{(b)})
$$


$$
H_t = [H_t^{(f)}, H_t^{(b)}]
$$


$$
O_t = H_t W_h^q + b_q
$$


### 双向 RNN 的用途
- 双向循环神经网络通过反向更新的隐藏层来利用方向时间信息
- 通常用来对序列抽取特征、填空,而不是预测未来



## 编码器-解码器
### 概念
- 编码器:将输入编程成中间表达形式(特征) 
- 解码器:将中间表示解码成输出

### CNN架构
- 编码器：特征提取层
- 解码器：Softmax 回归

### RNN架构
- 编码器：将文本表示成向量
- 解码器：向量表示成输出

### 编码器-解码器架构
一个模型被分为两块: 
- 编码器处理输出 
- 解码器生成输出



## 序列到序列学习(seq2seq)
Seq2seq从一个句子生成另一个句子
### 机器翻译
- 给定一个源语言的句子,自动翻译成目标语言 
- 这两个句子可以有不同的长度

### seq2seq 架构
编码器和解码器都是RNN
- 编码器是一个RNN,读取输入句子 
  - 可以是双向 
- 解码器使用另外一个RNN来输出

### 编码器-解码器细节
- 编码器是没有输出传递到RNN 
- 编码器最后时间步的隐状态用作解码器的初始隐状态


### 训练
训练时解码器使用目标句子作为输入

### 衡量生成序列的好坏的 BLEU
p_n 是预测中所有 n-gram 的精度
- 标签序列A B C D E F 和预测序列A B B C D,有


$$
p_1 = \frac{4}{5}, \quad p_2 = \frac{3}{4}, \quad p_3 = \frac{1}{3}, \quad p_4 = 0
$$


#### BLEU定义

$$
\exp \left( \min \left( 0, 1 - \frac{\text{len}_{\text{label}}}{\text{len}_{\text{pred}}} \right) \right) \prod_{n=1}^{k} p_n^{\frac{1}{2n}}
$$

惩罚过短的预测
长匹配有高权重

## 束搜索
### 贪心搜索
在seq2seq中我们使用了贪心搜索来预测序列 
- 将当前时刻预测概率最大的词输出

但贪心很可能不是最优的

### 穷举搜索
最优算法:对所有可能的序列,计算它的概率,然后选取最好的那个 

如果输出字典大小为 n,序列最长为 T,那么我们需要考察 n^T 个序列

$$
n = 10000, T = 10: n^T = 10^{40}
$$

计算上不可行

### 束搜索
保存最好的 k 个候选

在每个时刻,对每个候选新加一项( n 种可能),在 kn 个选项中选出最好的 k 个

时间复杂度

$$
O(knT)
$$

每个候选的最终分数是:

$$
\frac{1}{L^\alpha} \log p(y_1, \dots, y_L) = \frac{1}{L^\alpha} \sum_{t'=1}^{L} \log p(y_{t'} \mid y_1, \dots, y_{t'-1}, c)
$$

通常 α = 0.75


### 束搜索与贪心搜索、穷举搜索
束搜索在每次搜索时保存 k 个最好的候选 
- k = 1 时是贪心搜索 
- k = n 时是穷举搜索


# 注意力机制
## 注意力机制
从心理学来讲，动物需要在复杂环境下有效关注值得关注的点。

心理学框架：
人会主动、有意识的去选择注意点。注意点可以理解为值得关注的点、引人注意的点
### 动机
卷积、全连接、池化层都只考虑“不随意线索”

例如池化：最大池化层只考虑窗口上的最大值，只要是最大值就行

注意力机制则显式的考虑随意线索
- 随意线索被称为查询（query）
- 每个输入是一个值（value）和不随意线索（key）的对
- 通过注意力池化层来有偏向性的选择某些输入


首先“随意线索”就是query，就是你想查询的物品。结合之前内容，query就是想读书。

其它的物品就是key-value pair，即“不随意线索-值”对。结合之前内容，key就是红色杯子、报纸。value可以一样也可以不一样。以key是红色杯子举例，value就可以理解为杯子的价值，也就是有什么用。

注意力机制也可以叫注意力池化(attention pooling)，会根据query有偏向性的选择某些key-value pair。

总结注意力池化(attention pooling)和之前的池化(pooling)不一样的地方是：attention显示的加入了query，即“随意线索”，然后根据query去找到感兴趣的key-value pair

### 非参注意力池化层
给定数据key-value pair：

$$
(x_{i}, y_{i}), i=1, 2, ..., n
$$

最简单的池化方案是平均池化：

$$
f(x)=\frac{1}{n}\sum_{i}y_{i}
$$

更好的池化方案是Nadaraya-Watson核回归：

$$
f(x)=\sum_{i=1}^{n}\frac{K(x-x_{i})}{\sum_{j=1}^{n}K(x-x_j)}y_{i}
$$

其中，
- x是query；
- x_{i}是key；
- K是衡量x和x_{i}之间距离的一个函数(kernel)，比如这个值越大距离就越近，越小就距离越远；
- 公式中的分式，就是概率，每一项是一个相对重要性。对这项加权对y_{i}求和，意思是将和x相近那些的x_{i}和y_{i}选出来
- 可以这么理解，找出和query相近的key-value pair，别的就不管了

非参的意思是不需要学任何东西。拿一个新值去求其近似值，有点像KNN

### Nadaraya-Watson核回归
使用高斯核

$$
K(u)=\frac{1}{\sqrt{2\pi}}exp(-\frac{u^2}{2})
$$

将其代入之前的f(x)。得到的式子中softmax就是在做权重

$$
\hat{y}(x) = \frac{\sum_{i=1}^{n} \exp\left(-\frac{(x - x_i)^2}{2h^2}\right) \cdot y_i}{\sum_{i=1}^{n} \exp\left(-\frac{(x - x_i)^2}{2h^2}\right)}
$$

这个高斯核和注意力机制非常像

### 参数化的注意力机制
参数化就是加入一个可以学的w。每次迭代可以学习。这里的w是一元的(因为是标量不是向量)

$$
f(x) = \sum_{i=1}^{n} \text{softmax}\left(-\frac{1}{2} ((x - x_i)w)^2\right) y_i
$$


之前的都是用的不随意线索(就是key)，在注意力机制中加入了随意线索(就是query)

## 注意力分数

$$
f(x) = \sum_{i} \alpha (x, x_i) y_i = \sum_{i=1}^{n} \text{softmax}\left(-\frac{1}{2} (x - x_i)^2\right) y_i
$$


- α（x,xi）：注意力权重（权重一般是一组大于等于零，相加和为 1 的数）
- 注意力分数：高斯核的指数部分（相当于是注意力权重归一化之前的版本）
- 假设已知一些 key-value 对和一个 query，首先将 query 和每一个 key 通过注意力分数函数 a 和 softmax 运算得到注意力权重（与 key 对应的值的概率分布），将这些注意力权重再与已知的 value 进行加权求和，最终就得到了输出 

### 拓展到更高的维度
假设 query 是一个长为 q 的向量，k_i 是长为 k 的向量，v_i 是长为 v 的向量（这里 key 和 value 的长度可以不同）
其中 query 和 ki 的注意力权重（标量）是通过注意力评分函数 a 将两个向量映射成标量，再经过 softmax 运算得到的

#### 注意力池化层

$$
f\left(q, (k_1, v_1), \dots, (k_m, v_m)\right) = \sum_{i=1}^m \alpha(q, k_i) v_i \in \mathbb{R}^v
$$


$$
\alpha(q, k_i) = \text{softmax}(a(q, k_i)) = \frac{\exp(a(q, k_i))}{\sum_{j=1}^{m} \exp(a(q, k_j))} \in \mathbb{R}
$$


### 掩蔽 softmax 操作（masked softmax operation）
softmax 操作用于输出一个概率分布作为注意力权重，但是在某些情况下，并非所有的值都应该被纳入到注意力汇聚中

在处理文本数据集的时候，为了提高计算效率，可能会采用填充的方式使每个文本序列具有相同的长度，便于以相同形状的小批量进行加载，因此可能会存在一些文本序列被填充了没有意义的特殊词源（比如“<pad>”词元）
因此，为了仅仅将有意义的词元作为值来获取注意力汇聚，可以指定一个有效序列长度（即词元的个数），任何超出有效长度的位置都被掩蔽并置于 0，便于在计算 softmax 的时候过滤掉超出指定范围的位置，这也就是掩蔽 softmax 操作


### 注意力分数函数 α 的设计
#### 加性注意力 Additive Attention
当 query 和 key 是不同长度的矢量时，可以使用加性注意力作为注意力分数

可学参数（3 个）：

$$
W_k \in \mathbb{R}^{h \times k}, W_q \in \mathbb{R}^{h \times q}, v \in \mathbb{R}^{h}
$$

则注意力打分函数为：

$$
a(k, q) = v^\top \tanh(W_k k + W_q q)
$$


- h：超参数
- Wk：key 从 k map 到 h（将 key 向量的长度从 k 转化为 h）
- Wq：query 从q map 到 h（将 query 向量的长度从 q 转化为 h）
- Wk、Wq 都是矩阵，v 是向量
- tanh：激活函数
- 上式中，k 是长为 k 的向量，q 是长为 q 的向量
- 等价于将 query 和 key 合并起来变成一个长度为 k+q 的向量，然后将其输入到一个隐藏层大小为 h （ h 是一个超参数），输出大小为 1 的但隐藏层的 MLP（没有偏置项），最终得到输出
- 优点是 key、value 向量可以是任意的长度，可以不同

#### 缩放点积注意力 Scaled Dot-Product Attention
使用点积可以得到计算效率更高i的评分函数，但是点积操作要求 query 和 key 具有相同的长度

如果 key 和 query 都是同样的长度

$$
q, k_i \in \mathbb{R}^{d}
$$

那么可以

$$
a(q, k_i) = \frac{\langle q, k_i \rangle}{\sqrt{d}} = \frac{q^\top k_i}{\sqrt{d}}
$$

假设 query 和 key 的所有元素都是独立的随机变量，并且都满足零均值和单位方差，那么两个向量的点积的均值为 0 ，方差为 d
这里不需要学习任何东西，直接利用 <q,ki> 将 q 和 ki 做内积然后除以根号 d （除以根号 d 的目的是为了降低对 ki 的长度的敏感度，使得无论向量的长度如何，点积的方差在不考虑向量长度的情况下仍然是 1 ）


### 注意力分数总结
1. 注意力分数是 query 和 key 的相似度（没有经过 normalize ），注意力权重是注意力分数的 softmax 结果（ 0 到 1 之间的数）

2. 两种常见的注意力分数的计算
  - 有参数的版本：将 query 和 key 合并起来进入一个单隐藏层单输出的 MLP（在 query 和 key 向量长度不同的情况下）
  - 无参数的版本：直接将 query 和 key 做内积（在 query 和 key 向量长度一定的情况下），效率更高



## 使用注意力机制的seq2seq
注意力机制在 NLP 中的应用，也是最早的工作之一

### 动机
在机器翻译的时候，每个生成的词可能相关于源句子中不同的词

在语言翻译的时候，中文和英文之间的翻译可能会存在倒装，但是可能在西方语言之间，相同意思的句子中的词的位置可能近似地是对应的，所以在翻译句子的某个部位的时候，只需要去看源句子中对应的位置就可以了

然而，Seq2Seq 模型中不能对此直接建模。Seq2Seq 模型中编码器向解码器中传递的信息是编码器最后时刻的隐藏状态，解码器只用到了编码器最后时刻的隐藏状态作为初始化，从而进行预测，所以解码器看不到编码器最后时刻的隐藏状态之前的其他隐藏状态

源句子中的所有信息虽然都包含在这个隐藏状态中，但是要想在翻译某个词的时候，每个解码步骤使用编码相同的上下文变量，但是并非所有输入（源）词元都对解码某个词元有用。将注意力关注在源句子中的对应位置，这也是将注意力机制应用在Seq2Seq 模型中的动机

### 加入注意力
编码器对每次词的输出（隐藏状态）作为 key 和 value，序列中有多少个词元，就有多少个 key-value 对，它们是等价的，都是第 i 个词元的 RNN 的输出

解码器 RNN 对上一个词的预测输出（隐藏状态）是 query（假设 RNN 的输出都是在同一个语义空间中，所以在解码器中对某个词元进行解码的时候，需要用到的是 RNN 的输出，而不能使用词嵌入之后的输入，因为  key 和 value 也是 RNN 的输出，所以 key 和 query 做匹配的时候，最好都使用 RNN 的输出，这样能够保证它们差不多在同一个语义空间）

注意力的输出和下一个词的词嵌入合并进入 RNN 解码器 

对 Seq2Seq 的改进之处在于：之前 Seq2Seq 的 RNN 解码器的输入是 RNN 编码器最后时刻的隐藏状态，加入注意力机制之后的模型相当于是对所有的词进行了加权平均，根据翻译的词的不同使用不同时刻的 RNN 编码器输出的隐藏状态

### 总结
1. Seq2Seq 中通过编码器最后时刻的隐藏状态在编码器和解码器中传递信息
2. 注意力机制可以根据解码器 RNN 的输出来匹配到合适的编码器 RNN 的输出来更有效地传递信息
3. 在预测词元时，如果不是所有输入词元都是相关的，加入注意力机制能够使 RNN 编码器-解码器有选择地统计输入序列的不同部分（通过将上下文变量视为加性注意力池化的输出来实现）



## 自注意力 Self-attention
复杂输入
- 输入是一个向量，输出是一个标量或类别
- 输入是一组向量，输出是多个标量或类别

### 向量集作为输入 Vector Set as Input
- 自然语言
  - 独热编码 One-hot Encoding
  - 词嵌入 Word Embedding
- 声音
  - 400 个采样点 (16KHz)
  - 39 维 MFCC
  - 80 维滤波器组输出
- 图 Graph
  - 将每个节点视为一个向量

### 输出
- 每个向量都有一个标签
- 整个序列有一个标签
- 模型自行决定标签数量（seq2seq）

### 公式
给定序列

$$
x_1, \dots, x_n, \quad \forall x_i \in \mathbb{R}^d
$$

自注意力池化层将x_i当做key, value, query来对序列抽取特征得到y_1,...,y_n，这里

$$
y_i = f\left(x_i, (x_1, x_1), \dots, (x_n, x_n)\right) \in \mathbb{R}^d
$$


### 跟CNN以及RNN对比
| 指标       | CNN       | RNN      | 自注意力 |
|------------|-----------|----------|-----------|
| 计算复杂度 | O(knd²)   | O(nd²)   | O(n²d)    |
| 并行度     | O(n)      | O(1)     | O(n)      |
| 最长路径   | O(n/k)    | O(n)     | O(1)      |


CNN
- 只能关注感受野的自注意力机制
  - CNN 是简化的自注意力机制

自注意力机制
- 具有可学习感受野的 CNN
  - 自注意力机制是 CNN 的复杂版本

### 位置编码
跟CNN/RNN不同,自注意力并没有记录位置信息 

每个位置都有一个唯一的位置向量𝑒_𝑖
- 手工制作
- 从数据中学习

位置编码将位置信息注入到输入里
假设长度为 n 的序列是

$$
X \in \mathbb{R}^{n \times d}
$$

那么使用位置编码矩阵

$$
P \in \mathbb{R}^{n \times d}
$$

来输出 X + P 作为自编码输入


P的元素如下计算:

$$
p_{i,\,2j} = \sin\left( \frac{i}{10000^{2jd}} \right), \quad
p_{i,\,2j+1} = \cos\left( \frac{i}{10000^{2jd}} \right)
$$

#### 位置编码矩阵

$$
P \in \mathbb{R}^{n \times d}: p_{i,\,2j} = \sin\left( \frac{i}{10000^{2jd}} \right), \quad
p_{i,\,2j+1} = \cos\left( \frac{i}{10000^{2jd}} \right)
$$


#### 绝对位置信息
#### 相对位置信息
位置于 i+δ 处的位置编码可以线性投影位置 i 处的位置编码来表示

记

$$
\omega_j = \frac{1}{10000^{\frac{2j}{d}}}
$$

那么

$$
\begin{bmatrix}
\cos(\delta \, \omega_j) & \sin(\delta \, \omega_j) \\
-\sin(\delta \, \omega_j) & \cos(\delta \, \omega_j) \end{bmatrix} \begin{bmatrix} p_{i,\,2j} \\
p_{i,\,2j+1} \end{bmatrix} = \begin{bmatrix} p_{i+\delta,\,2j} \\
p_{i+\delta,\,2j+1} \end{bmatrix}
$$


投影矩阵跟 i 无关

### 自注意力总结
- 根据注意力分数提取信息
- 自注意力池化层将x_i当做key,value, query来对序列抽取特征 
- 完全并行、最长序列为1、但对长序列计算复杂度高 
- 位置编码在输入中加入位置信息,使得自注意力能够记忆位置信息



## Transformer
Transformer是一个纯使用注意力的编码-解码器
- 编码器和解码器都有n个transformer块 
- 每个块里使用多头(自)注意力,基于位置的前馈网络,和层归一化
### Transformer 架构
- 基于编码器-解码器架构来处理序列对 
- 跟使用注意力的seq2seq不同, Transformer是纯基于注意力

### 多头自注意力 Multi-head Self-attention
- 对同一key, value, query,希望抽取不同的信息
  - 例如短距离关系和长距离关系 
- 多头注意力使用 k 个独立的注意力池化 
  - 合并各个头(head)输出得到最终输出



query, kwy, value
$$
q \in \mathbb{R}^{d_q}, k \in \mathbb{R}^{d_k}, v \in \mathbb{R}^{d_v}
$$

头 i 的可学习参数

$$
W^{(q)}_i \in \mathbb{R}^{p_q \times d_q}, \quad
W^{(k)}_i \in \mathbb{R}^{p_k \times d_k}, \quad
W^{(v)}_i \in \mathbb{R}^{p_v \times d_v}
$$

头 i 的输出

$$
h_i = f\left( W^{(i)}_q q, W^{(i)}_k k, W^{(i)}_v v \right) \in \mathbb{R}^{p_v}
$$

输出的可学习参数

$$
W_o \in \mathbb{R}^{p_o \times hp_v}
$$

多头注意力的输出

$$
W_o \begin{bmatrix}
h_1 \\
\vdots \\
h_h \end{bmatrix} \in \mathbb{R}^{p_o}
$$

### 有掩码的多头注意力
解码器对序列中一个元素输出时,不应该考虑该元素之后的元素

可以通过掩码来实现
- 也就是计算 x_i 输出时,假装当前序列长度为 i

### 基于位置的前馈网络
- 将输入形状由 (b, n, d) 变换成 (bn, d)
- 作用两个全连接层 
- 输出形状由 (bn, d) 变化回 (b, n, d)
- 等价于两层核窗口为1的一维卷积层
 

### 层归一化
批量归一化对每个特征/通道里元素进行归一化
- 不适合序列长度会变的NLP应用

层归一化对每个样本里的元素进行归一化

### 信息传递
编码器中的输出 y_1, ..., y_n

将其作为解码中第 i 个Transformer块中多头注意力的 key 和 value 
- 它的query来自目标序列 

意味着编码器和解码器中块的个数和输出维度都是一样的

### 预测
预测第 t + 1 个输出时:
- 解码器中输入前 t 个预测值
  - 在自注意力中,前 t 个预测值作为key和value,第 t 个预测值还作为query



## BERT
### 概念
- BERT针对微调设计 
- 基于Transformer的编码器做了如下修改 
  - 模型更大,训练数据更多 
  - 输入句子对,片段嵌入,可学习的位置编码 
  - 训练时使用两个任务: 
    - 带掩码的语言模型 
    - 下一个句子预测

### NLP里的迁移学习
- 使用预训练好的模型来抽取词、句子的特征
  - 例如 word2vec 或语言模型
- 不更新预训练好的模型
- 需要构建新的网络来抓取新任务需要的信息
  - Word2vec 忽略了时序信息, 语言模型只看了一个方向

### BERT的动机
- 基于微调的NLP模型
- 预训练的模型抽取了足够多的信息
- 新的任务只需要增加一个简单的输出层

### BERT 架构
- 只有编码器的 Transformer
- 两个版本:
  - Base: #blocks = 12, hidden size = 768, #heads = 12, #parameters = 110M 
  - Large: #blocks = 24, hidden size = 1024, #heads = 16, #parameters = 340M
- 在大规模数据上训练 > 3B 词

### 对输入的修改
- 每个样本是一个句子对 
- 加入额外的片段嵌入 
- 位置编码可学习

### 预训练任务
#### 预训练任务1: 带掩码的语言模型
- Transformer的编码器是双向’标准语言模型要求单向 
- 带掩码的语言模型每次随机(15%概率)将一些词元换成 <mask> 
- 因为微调任务中不出现<mask> 
  - 80%概率下’将选中的词元变成<mask> 
  - 10%概率下换成一个随机词元 
  - 10%概率下变持原有的词元

#### 预训练任务2:下一句子预测
- 预测一个句子对中两个句子是不是相邻 
- 训练样本中: 
  - 50%概率选择相邻句子对:<cls> this movie is great <sep> i 
like it <sep> 
  - 50%概率选择随机句子对:<cls> this movie is great <sep> 
hello world <sep> 
- 将<cls>对应的输出放到一个全连接层来预测

### BERT 微调
- BERT 对每一个词元返回抽取了上下文信息的特征向量 
- 不同的任务使用不用的特性
- 即使下游任务各有不同,使用BERT微调时均只需要增加输出层 
- 但根据任务的不同,输入的表示,和使用的BERT特征也会不—样

#### 句子分类
将 <cls> 对应的向量输入到全连接层分类

#### 命名实体识别
- 识别一个词元是不是命名实体,例如人名、机构、位置 
- 将非特殊词元放进全连接层分类

#### 问题回答
- 给定一个问题,和描述文字,找出一个片段作为回答 
- 对片段中的每个词元预测它是不是回答的开头或结束


# 优化算法
## 优化问题
一般形式

$$
\min_{x} \; f(x) \quad \text{subject to} \quad x \in \mathcal{C}
$$

目标函数

$$
f : \mathbb{R}^n \to \mathbb{R}
$$

限制集合例子

$$
\mathcal{C} = \{ x \mid h_1(x) = 0, \ldots, h_m(x) = 0, \; g_1(x) \leq 0, \ldots, g_r(x) \leq 0 \}
$$

如果

$$
\mathcal{C} = \mathbb{R}^n
$$

那就是不受限

## 局部最小 vs 全局最小
全局最小 x*

$$
f(x^*) \leq f(x), \quad \forall x \in \mathcal{C}
$$

局部最小 x*

$$
\exists \varepsilon > 0, \quad \text{s.t.} \quad f(x^*) \leq f(x), \quad \forall x : \| x - x^* \| \leq \varepsilon
$$

使用迭代优化算法来求解,—般只能保证界到局部最小值

## 凸集和凸函数
### 凸集
一个 Rn的子集 C 

$$
\mathcal{C} \subseteq \mathbb{R}^n
$$

是凸集当且仅当

$$
\alpha x + (1 - \alpha) y \in \mathcal{C}, \quad \forall \alpha \in [0,1], \; \forall x,y \in \mathcal{C}
$$


### 凸函数
函数

$$
f : \mathcal{C} \to \mathbb{R}
$$

是凸函数当且仅当

$$
f(\alpha x + (1 - \alpha) y) \leq \alpha f(x) + (1 - \alpha) f(y), \quad \forall \alpha \in [0,1], \; \forall x, y \in \mathcal{C}
$$

如果

$$
\quad \forall \alpha \in (0,1), \; \forall x \neq y \in \mathcal{C}
$$

时不等式严格成立, 那么叫严格凸函数

#### 凸函数优化
- 如果代价函数 f 是凸的,且限制集合 C 是凸的,那么就是凸优化问题,那么局部最小一定是全局最小 
- 严格凸优化问题有唯一的全局最小

### 凸和非凸例子
#### 凸
- 线性回归


$$
f(x) = \|Wx - b\|^2
$$


- Softmax 回归

#### 非凸
深度学习模型大多是非凸
MLP, CNN, RNN, attention, …


## 梯度下降 Gradient Descent
最简单的迭代求解算法 

选取开始点 X_0

对于

$$
t = 1, \ldots, T \\
x_t = x_{t-1} - \eta \nabla f(x_{t-1})
$$

η 叫做学习率


### 随机梯度下降 Stochastic gradient descent (SGD)
有 n 个样本时,计算

$$
f(x) = \frac{1}{n} \sum_{i=1}^{n} \ell_i(x)
$$

的导数太贵


随机梯度下降在时间 t 随机选项样本 t_i 来近似 f(x)

$$
x_t = x_{t-1} - \eta_t \nabla \ell_{i_t}(x_{t-1})
$$

$$
\mathbb{E} \left[ \nabla \ell_{i_t}(x) \right] = \mathbb{E} \left[ \nabla f(x) \right]
$$


### 小批量随机梯度下降 Mini-batch Stochastic gradient descent
计算单样本的梯度难完全利用硬件资源

小批量随机梯度下降是最常用的优化算法

小批量随机梯度下降在时间 t 采样一个随机子集 I_t ⊂ {1, ..., n}, 使得 |I_t| = b

$$
x_t = x_{t-1} - \frac{\eta}{b} \sum_{i \in I_t} \nabla \ell_i(x_{t-1})
$$


同样,这是一个无偏的近似,但降低了方差

$$
\mathbb{E} \left[ \frac{1}{b} \sum_{i \in I_t} \nabla \ell_i(x) \right] = \nabla f(x)
$$


## 冲量法
冲量法使用平滑过渡梯度对权重更新
冲量对梯度做平滑


$$
g_t = \frac{1}{b} \sum_{i \in I_t} \nabla \ell_i(x_{t-1})
$$


$$
v_t = \beta v_{t-1} + g_t
$$


$$
w_t = w_{t-1} - \eta v_t
$$

梯度平滑

$$
v_t = g_t + \beta g_{t-1} + \beta^2 g_{t-2} + \beta^3 g_{t-3} + \cdots
$$


常见的动量系数取值为：
$$
\beta \in \{0.5,\, 0.9,\, 0.95,\, 0.99\}
$$

## Adam
Adam对梯度做平滑,且对梯度各个维度值做重新调整


记录

$$
v_t = \beta_1 v_{t-1} + (1 - \beta_1) g_t
$$


通常

$$
\beta_1 = 0.9
$$

展开

$$
v_t = (1 - \beta_1) \left( g_t + \beta_1 g_{t-1} + \beta_1^2 g_{t-2} + \beta_1^3 g_{t-3} + \cdots \right)
$$

因为

$$
\sum_{i=0}^\infty \beta_1^i = \frac{1}{1 - \beta_1}
$$

所以权重和为1


由于

$$
v_0 = 0
$$

且

$$
\sum_{i=0}^t \beta_1^t = \frac{1 - \beta_1^{t}}{1 - \beta_1}
$$

修正

$$
\hat{v}_t = \frac{v_t}{1 - \beta_1^t}
$$



类似记录

$$
s_t = \beta_2 s_{t-1} + (1 - \beta_2) g_t^2
$$

通常

$$
\beta_2 = 0.999
$$

且修正

$$
\hat{s}_t = \frac{s_t}{1 - \beta_2^t}
$$

计算重新调整后的梯度

$$
g'_t = \frac{\hat{v}_t}{\sqrt{\hat{s}_t} + \epsilon}
$$

最后更新

$$
w_t = w_{t-1} - \eta g'_t
$$









# 计算机视觉
## 数据增强(Data Augmentation)
### 数据增强概念
增加一个已有数据集,使得有更多的多样性 
- 在语言里面加入各种不同的背景噪音 
- 改变图片的颜色和形状

数据增广通过变形数据来获取多样性，从而使得模型泛化性能更好

### 使用增强数据训练
- 原始数据
- 在线生成增强数据
- 将增强后的数据传入模型训练

### 数据增强方法
- 翻转
  - 左右翻转
  - 上下翻转

*注意：上下翻转不总是可行*
- 切割
从图片中切割一块,然后变形到固定形状 
  - 随机高宽比 (e.g. [3/4, 4/3]) 
  - 随机大小 (e.g. [8%, 100%]) 
  - 随机位置
- 颜色
改变色调,饱和度,明切度(e.g. [0.5, 1.5])
- 几十种其他的办法


## 微调Fine Tune
### 微调
- 标注一个数据集很贵
- 微调通过使用在大数据上得到的预训练好的模型来初始化模型权重，从而完成提升精度 
- 预训练模型质量很重要 
- 微调通常速度更快、精度更高

### 网络架构
- 一个神经网络一般可以分成两块 
  - 特征抽取将原始像素变成容易线性分割的特征 
  - 线性分类器来做分类
- 微调中，Output Layer不能直接使用，因为标号可能变了
- 特征抽取层可能仍然可以对我数据集做特征抽取

### 微调中的权重初始化
- Layer 1到 Layer L-1
直接copy权重

- Output Layer
Random Initialization

### 训练
是一个目标数据集上的正常训练任务，但使用更强的正则化 
- 使用更小的学习率 
- 使用更少的数据迭代

源数据集远复杂于目标数据,通常微调效果更好

### 重用分类器权重
- 源数据集可能也有目标数据中的部分标号 
- 可以使用预训练好模型分类器中对应标号对应的向量来做初始化

### 固定一些层
- 神经网络通常学习有层次的特征表示 
  - 低层次的特征更加通用 
  - 高层次的特征则更跟数据集相关 
- 可以固定底部一些层的参数，不参与更新 
  - 更强的正则

## 目标检测
### 基本概念
- 物体检测识别图片里的多个物体的类别和位置 
- 位置通常用边缘框表示
### 边缘框
一个边缘框可以通过4个数字定义
- (左上x, 左上y, 右下x, 右下y) 
- (左上x, 左上y, 宽, 高)

### 目标检测数据集
#### COCO (cocodataset.org) 
- 80物体
- 330K图片
- 1.5M 物体
##### 每行表示一个物体 
- 图片文件名, 物体类别, 边缘框 

### 锚框
#### 概念
- 一类目标检测算法基于锚框来预测 
- 首先生成大量锚框,并赋予标号,每个锚框作为一个样本进行训练 
- 在预测时,使用NMS来去掉冗余的预测

一类目标检测算法是基于锚框 
- 提出多个被称为锚框的区域(边缘框) 
- 预测每个锚框里是否含有关注的物体 
- 如果是，预测从这个锚框到真实边缘框的偏移

#### IoU - 交并比
IoU 用来计算两个框之间的相似度 
- 0 表示无重叠,1 表示重合 

这是 Jacquard 指数的一个特殊情况 
- 给定两个集合 A 和 B 


$$
J(A, B) = \frac{|A \cap B|}{|A \cup B|}
$$


#### 赋予锚框标号
每个锚框是一个训练样本 
- 将每个锚框，要么标注成背景，要么关联上一个真实边缘框 
- 我们可能会生成大量的锚框 
  - 这导致大量的负类样本

#### 使用非极大值抑制(NMS)输出
每个锚框预测一个边缘框 

NMS可以合并相似的预测 
- 选中是非背景类的最大预测值 
- 去掉所有其它和它IoU值大于 θ的预测 
- 重复上述过程直到所有预测要么被选中，要么被去掉


### 区域卷积神经网络R-CNN
#### 相关概念
- R-CNN 是最早、也是最有名的一类基于锚框和CNN的目标检测算法 
- Fast/Faster R-CNN持续提升性能 
- Faster R-CNN 和 Mask R-CNN是在最求高精度场景下的常用算法
#### R-CNN概念
- 使用启发式搜索算法来选择锚框 
- 使用预训练模型来对每个锚框抽取特征 
- 训练一个SVM来对类别分类 
- 训练一个线性回归模型来预测边缘框偏移

#### 兴趣区域(RoI)池化层
给定一个锚框,均匀分割成n×m块,输出每块里的最大值

不管锚框多大,总是输出nm个值

#### Fast RCNN
- 使用CNN对图片抽取特征 
- 使用RoI池化层对每个锚框固定长度特征

#### Faster R-CNN
使用一个区域提议网络来替代启发式搜索来获得更好的锚框

#### Mask R-CNN
如果有像素级别的标号,使用FCN来利用这些信息


### 单发多框检测(SSD)
#### SSD相关概念
- SSD通过单神经网络来检测模型 
- 以每个像素为中心的产生多个锚框 
- 在多个段的输出上进行多尺度的检测
#### 生成锚框
- 对每个像素,生成多个以它为中心的锚框 
- 给定n个大小s_1, ..., s_n和m个高宽比,那么生成 n+m-1个锚框,其大小和高宽比分别为:  


$$
(s_1, r_1), (s_2, r_1), \dots, (s_n, r_1), (s_1, r_2), \dots, (s_1, r_m)
$$


#### SSD 模型
一个基础网络来抽取特征,然后多个卷积层块来减半高宽 

在每段都生成锚框 
- 底部段来拟合小物体,顶部段来拟合大物体 

对每个锚框预测类别和边缘框


### YOLO(你只看一次)
- SSD中锚框大量重叠,因此浪费了很多计算 
- YOLO 将图片均匀分成S×S个锚框 
- 每个锚框预测B个边缘框 
- 后续版本(V2,V3,V4…)有持续改进

## 语义分割
语义分割将图片中的每个像素分类到对应的类别
### 语义分割的应用
- 背景虚化
- 路面分割

### 语义分割和实例分割

### 转置卷积
卷积不会增大输入的高宽,通常要么不变、要么减半 

转置卷积则可以用来增大输入高宽  

$$
Y[i : i + h, j : j + w] \mathrel{+}= X[i, j] \cdot K
$$


转置卷积是一种变化了输入和核的卷积,来得到上采样的目的
#### “转置”含义
对于卷积  

$$
Y = X \star W
$$


- 可以对W构造一个V,使得卷积等价于矩阵乘法


$$
Y' = V X'
$$


  - 这里Y′, X′ 是Y, X对应的向量版本 
- 转置卷积则等价于


$$
Y' = V^\top X'
$$


- 如果卷积将输入从(h,w)变成了 (h′,w′)
  - 同样超参数的转置卷积则从(h′,w′) 变成 (h,w)

#### 转置卷积是一种卷积 
- 它将输入和核进行了重新排列 
- 同卷积一般是做下采样不同，它通常用作上采样 
- 如果卷积将输入从(h,w)变成了 (h′,w′),同样超参数下它将(h′,w′) 变成 (h,w)

#### 重新排列输入和核
当填充为0,步幅为1时 
- 将输入填充k-1(k是核窗口) 
- 将核矩阵上下、左右翻转 
- 然后做正常卷积(填充0、步幅1)

当填充为p,步幅为1时 
- 将输入填充k-p-1(k是核窗口) 
- 将核矩阵上下、左右翻转 
- 然后做正常卷积(填充0、步幅1)

当填充为p,步幅为s时 
- 在行和列之间插入s-1行或列 
- 将输入填充k-p-1(k是核窗口) 
- 将核矩阵上下、左右翻转 
- 然后做正常卷积(填充0、步幅1)

#### 形状换算
输入高(宽)为n,核k,填充p,步幅s 

转置卷积 

$$
n' = s n + k - 2p - s
$$


卷积 

$$
n' = \left\lfloor \frac{n - k - 2p + s}{s} \right\rfloor \Rightarrow n \geq s n' + k - 2p - s
$$

如果让高宽成倍增加,那么

$$
k = 2p + s
$$


#### 同反卷积的关系
数学上的反卷积(deconvolution)是指卷积的逆运算
   
$$
Y = \text{conv}(X, K) \quad \Rightarrow \quad X = \text{deconv}(Y, K)
$$

反卷积很少用在深度学习中 
- 我们说的反卷积神经网络指用了转置卷积的神经网络，不等同于数学上的反卷积操作

### 全连接卷积神经网络(FCN)
- FCN是用深度神经网络来做语义分割的奠基性工作
- 它用转置卷积层来替换CNN最后的全连接层,从而可以实现每个像素的预测


## 样式迁移
将样式图片中的样式迁移到内容图片上,得到合成图片
### 基于CNN的样式迁移


# 自然语言处理





















































































































