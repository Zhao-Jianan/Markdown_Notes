# torch
## 安装
```
conda install pytorch==2.5.1 torchvision==0.20.1 torchaudio==2.5.1 pytorch-cuda=12.1 -c pytorch -c nvidia
```
## Tensor
```torch.Tensor```是整个Pytorch框架中的核心类，可以自动求导
### 创建矩阵
```
torch.empty(5,3)
```
创建一个未初始化的5行3列的矩阵，因为未初始化，所以元素都是内存中原有的无意义的随机数值
```
torch.rand(5,3)
```
创建5行3列的高斯分布的随机数的矩阵
```
torch.zeros(5,3, dtype=torch.long)
```
创建5行3列的全0矩阵，且元素数据类型为long
```
torch.ones(5,3, dtype=torch.long)
```
创建5行3列的全1矩阵
```
torch.tensor([2.5, 3.5])
```
直接通过数据创建张量
```
Tensor.new_one(5, 3)
```
给一个Tensor重新赋值为5行3列的全1矩阵
```
torch.randn_like(Tensor1, dtype=torch.float)
```
创建一个和Tensor1形状相同的随机数的矩阵，且元素数据类型为float

### 切片
```
X[:, 1]
```
```
Tensor.argmax(dim=)
```
例如
```
tensor.argmax(1)
```
返回输入张量中某个维度上所有元素的最大值的索引
```
Tensor.shape
```
返回张量的形状
```
Tensor.size()
```
返回张量的形状
```
Tensor.device
```
查看张量所在的设备
```
.item()
```
将张量中的一个元素转化为python数值形式
### torch.Tensor和numpy.array互相转换
```torch.Tensor```和```numpy.array```共享底层的内存空间，因此改变其中一个值，另一个也会随之改变


```
Tensor.numpy()
```
- 使用```Tensor.numpy()```可以将Tensor转化为numpy.array
- 转换之后，对其中一个进行数学运算，另一个也会改变
- 所有在CPU上的Tensor，除了CharTensor之外，都可以转换为Numpy.array，并可以反向转换
```
torch.from_numpy()
```
- 使用```torch.from_numpy()```可以将```numpy.array```转化为Tensor

### autograd自动求导
```
.requires_grad
```
如果将requires_grad设置为True，Tensor将追踪在这个类上定义的所有操作，当代码要进行反向传播时，直接调用.backward()，就可以自动计算所有的梯度，在这个Tensor上的所有梯度将被累加进属性.grad中
```
.requires_grad_()
```
可以原地改变Tensor的属性requires_grad的值，如果没有主动设定，默认为False
```
.detach()
```
如果想终止一个Tensor在计算图中的追踪回溯，只需要执行.detach()就可以将该Tensor从计算图中撤下，在未来的回溯计算中也不会再计算该Tensor
- 注意，执行Y = X.detach()后，X和Y的内容相同，但是X仍然会自动求导，而Y不会进行自动求导

```
with torch.no_grad():
```
除了.detach()，还可以使用代码块```with torch.no_grad():```的方式，终止对计算图的回溯，从而不再进行方向传播求导数的过程。这种方式非常适用于对模型进行预测的时候，因为预测阶段不再需要对梯度进行计算
```
.backward()
```
反向传播
- 在Pytorch中执行反向传播的全部操作就是loss.backward()
- 在执行反向传播前，要先将梯度清零，否则梯度会在不同的批次数据之间被累加



## torch
### 数学运算
#### 加法
```
X + Y
```
```
result = torch.add(X, Y)
```
```
torch.add(X, Y, out=result)
```
```
in-place(原地置换) Y.add_(X)
```
### reshape
```
torch.reshape(input, shape) → Tensor
```
改变Tensor形状
- 注意要保证数据元素的总数量不变
- -1代表自动匹配元素数量
### view
```
Tensor.view(shape)
```
改变Tensor的形状，和reshape效果相同
- 注意要保证数据元素的总数量不变
- -1代表自动匹配元素数量
### zeros_like
```
torch.zeros_like(input, *, dtype=None, layout=None, device=None, requires_grad=False, memory_format=torch.preserve_format) → Tensor
```
传入一个tensor，返回一个相同size的所有元素填充为0的tensor

### BLAS and LAPACK Operations
#### bmm
```
torch.bmm()
```
- batch matrix-matrix multiplication（批量矩阵乘法）函数，专门用于对三维张量进行批量矩阵乘法
- 典型用途是在处理批量化数据时，将每一批中的矩阵进行乘法运算
- 对存储在输入和 mat2 中的矩阵执行批量矩阵-矩阵乘积
- 输入和 mat2 必须是 3-D 张量，每个张量包含相同数量的矩阵
- 此函数不广播，需要广播可以使用torch.matmul()
- 输入: 接受两个 三维张量，形状分别为 (batch size, n, m) 和 (batch size, m, p)
- 输出: 返回一个形状为 (batch size, n, p) 的 3D 张量，每一批次的矩阵进行独立的乘法
- 功能: 专为批量处理设计，通常在 RNN、Transformer 等模型中使用，计算效率更高

#### matmul
```
torch.matmul()
```
- 两个张量的通用矩阵乘法
- 输入: 可以接受 任意维度 的张量。其行为根据输入的维度而变化：
        ◆如果是 标量或向量: 它会执行标量乘法或向量点积
        ◆如果是 2D 张量: 等同于 torch.mm()
        ◆如果是 3D 或更高维张量: 会自动进行批量矩阵乘法，并支持 广播 (broadcasting)
- 功能: 最灵活且推荐使用，因为它适用于所有场景

#### mm
```
torch.mm()
```
- 仅用于 2D 矩阵乘法
- 输入: 仅接受两个 二维 张量，形状分别为 (m,n) 和 (n,p)
- 输出: 返回一个形状为 (m,p) 的二维矩阵
- 功能: 等同于线性代数中的标准矩阵乘法


### Indexing, Slicing, Joining, Mutating Ops
#### permute
```
torch.permute(input, dims)
```
- 用于改变张量的维度顺序，而不会改变数据本身
- 它通常用于调整张量的形状，以便与不同操作兼容，尤其是在图像处理和神经网络中非常常见

#### unsqueeze
```
torch.unsqueeze()
```
- 用于在指定位置为张量添加一个新的维度，从而改变张量的形状，而不改变数据内容
- 这在需要调整张量维度以匹配特定操作（如广播、拼接、批处理等）时非常有用




### Creation Ops
#### eye
```
torch.eye()
```
- 用于生成单位矩阵（identity matrix），即对角线元素为 1，其余元素为 0 的二维张量。单位矩阵在线性代数和深度学习中经常用于初始化、线性变换以及正则化等操作

### Other Operations
#### repeat_interleave
```
torch.repeat_interleave()
```
- 用于沿指定维度重复张量中的元素
- 它可以看作是在特定维度上对元素进行“展开”或“重复”
- 这种操作常用于数据预处理、张量形状调整以及构建重复结构



### cuda
使用GPU训练

#### is_available
```
torch.cuda.is_available()
```
检测cuda是否可用
#### Tensor.cuda()
```
Tensor.cuda()
```
- 将数据、模型、损失函数发送到cuda
- 注意，只有数据、模型、损失函数可以发送到cuda
- 数据集不能发送，数据发送方式为：
```
    for data in train_loader:
        inputs, labels = data
        inputs = inputs.cuda()
        labels = labels.cuda()
```
- 模型、损失函数发送后可以不重新赋值。数据发送后必须重新赋值
#### Tensor.to(device=)
和.cuda()用法相同，更方便修改
- device
```
device = torch.device('cpu')
```
```
device = torch.device('cuda')
```
```
device = torch.device('cuda:0')
```

- 示例代码
```
device = torch.device('cuda') if torch.cuda.is_available() else torch.device('cpu')

model = model.to(device)
loss_function = loss_function.to(device)

    for data in train_loader:
        inputs, labels = data
        inputs = inputs.to(device)
        labels = labels.to(device)
```

## torch.Function
### 概念
- Function类是和Tensor类同等重要的一个核心类，它和Tensor共同构建了一个完整的类，每一个Tensor拥有一个.grad_fn属性，代表引用了哪个具体的Function创建该Tensor
- 如果某个张量Tensor是用户自定义的，则其对应的grad_fn is None
- ```.grad_fn```属性的类型取决于最后一步计算的方式
  - ```SumBackward```
  - ```AddBackward```
  - ```MeanBackward```


## torch.utils
### Dataset
```
torch.utils.data.Dataset
```
提供一种方式去获取数据及其label
#### 功能
- 如何获取每一个数据及其label
- 告诉我们总共有多少个数据

### Dataloader
为神经网络提供不同的数据形式
```
torch.utils.data.DataLoader
```
#### 传入参数
- dataset
加载的数据集
- batch_size
批次大小
- shuffle
是否打乱，True为打乱
- sample
- batch_sampler
- num_workers
使用多少个线程来加载数据

*注意：在Windows下，如果num_worksers>0，可能会出现BrokenPipeError错误或运行无法结束，此时将num_workers设为0*

- drop_last
最后一个批次的数据，如果不够批大小，是否丢弃，True为丢弃
#### 读取一个批次的数据
```
images, labels = next(iter(data_loader))
```

### TensorBoard
将 PyTorch 模型和指标记录到目录中，以便在 TensorBoard UI 中进行可视化
#### 导包
```
from torch.utils import tensorboard
```
#### 使用方法
创建日志文件
```
writer = SummaryWriter('log')
```
记录图片文件
```
writer.add_image('标签名', img)
```
记录标量
```
writer.add_scalar('标签名', i,i)
```
记录模型架构
```
writer.add_graph(model,input)
```
记录词嵌入
```
writer.add_embedding(mat, metadata)
```
- mat
一个Tensor来记录word embedding的形状
- metadata
list类型的数据列表

关闭writer
```
writer.close()
```
#### 查看可视化日志结果
命令行中
```
tensorboard --logdir=日志路径
```

## torch.nn
torch.nn中提供了各种不同的神经网络
注意：
- torch.nn构建的神经网络只支持mini-batches的输入，不支持单一样本的输入

- 例如：nn.Conv2d需要一个4D的Tensor,形状为(nSamples, nChannels, Height, Width)。如果输入只有单一样本形式，则需要执行input.unsqueeze(0)，主动将3D的Tensor扩充成4D的Tensor


### 基本API
#### Parameter
```
torch.nn.parameter.Parameter(data=None, requires_grad=True)
```
一种被视为模块参数的 Tensor，包含模型中所有的可训练参数，可以通过net.parameters()来获得

##### 示例代码
示例1
```
W = nn.Parameter(torch.rand(num_inputs,num_outputs,requires_grad=True))
```
示例2
```
params = list(net.parameters())
print(len(params))
```
#### torch.nn.init
```
torch.nn.init
```
用来初始化参数
##### normal_()
```
normal_()
```
初始化为正态分布
- 使用方法
```
def init_normal(m):
    if type(m) == nn.Linear:
        nn.init.normal_(m.weight, mean=0, std=0.01)
        nn.init.zeros_(m.bias)
net.apply(self.init_normal)
```
##### constant_()
```
constant_()
```
初始化为常数
- 使用方法
```
def init_constant(m):
    if type(m) == nn.Linear:
        nn.init.constant_(m.weight, 1)
        nn.init.zeros_(m.bias)
net.apply(self.init_constant)
```
##### xavier_uniform_()
```
xavier_uniform_()
```
使用Xavier 均匀分布初始化
- 使用方法
```
def init_xavier(m):
    if type(m) == nn.Linear:
        nn.init.xavier_uniform_(m.weight)
net.apply(self.init_xavier)
```
##### xavier_normal_()
```
xavier_normal_()
```
使用Xavier 正态分布初始化


### Containers
容器，是构建神经网络的架构
#### Module
为所有神经网络模块提供的基础类
- 方法
```
Module.apply()
```
传入一个函数，遍历Module中所有sub_Module，并对其应用这个函数
```
Module.train()
```
设定模型在训练状态，注意此方法功能不强，仅对某些模块有影响，例如Dropout、BatchNorm 等
```
Module.eval()
```
设定模型在评估状态，注意此方法功能不强，仅对某些模块有影响，例如Dropout、BatchNorm 等
```
Module.state_dict()
```
返回Module当前参数
##### 用法
```
nn.Module[layer_index].state_dict()
```
```
Module.named_parameters()
```
可以一次性访问所有参数

#### Sequential
顺序容器，让代码更简洁
- 功能
  - 模块将按照在构造函数中传递的顺序添加到其中。Sequential 的 forward() 方法接受任何输入并将其转发到它包含的第一个模块。然后，它将输出按顺序“链接”到每个后续模块的输入，最后返回最后一个模块的输出
  - 与手动调用模块序列相比，Sequential 提供的价值在于它允许将整个容器视为单个模块，这样对 Sequential 执行转换将应用于它存储的每个模块（每个模块都是 Sequential 的注册子模块）



### Convolution Layers
#### nn.Conv2d
二维卷积层，图片任务一般都使用2d卷积
```
torch.nn.Conv2d(in_channels, out_channels, kernel_size, stride=1, padding=0, dilation=1, groups=1, bias=True, padding_mode='zeros', device=None, dtype=None)
```
- 传入参数
  - in_channels
输入的通道数
  - out_channels
输出的通道数。一般高宽减半的时候，把输出通道数翻倍
  - kernel_size
卷积核尺寸，最重要的超参数，卷积核边长一般选奇数，方便对称，通常取值3*3
  - stride
卷积步长，可以是单个数字或一个元组，默认值为0。如果是单个数字，向右移动和向下移动步长相同。如果是元组，可以分别设置向右移动和向下移动的步长。通常取值为1，如果计算量太大，可以取别的值（通常取2）
  - padding
填充，输入填充的维数，默认值为0，通常取值为kernel_size-1，这样计算方便
  - dilation
空洞卷积。在空洞卷积中，input在进行卷积计算时，会间隔几个元素，这里设置间隔的元素数
  - groups
分组卷积，一般不使用
  - bias
给输出添加一个可学习的偏差，默认为True
  - padding_mode
填充的模式，为字符串类型
    - zeros
0填充，默认值
    - reflect
    - repliccate
    - circular

### Pooling Layers
#### nn.MaxPool2d
```
torch.nn.MaxPool2d(kernel_size, stride=None, padding=0, dilation=1, return_indices=False, ceil_mode=False)
```
- 传入参数
  - kernel_size
池化核数
  - stride
池化步长
  - ceil_mode
如果池化层在边缘不够kernel_size，会根据此参数做决定，此值为True时，保留，并对有数值的元素做池化，如果为False，则丢弃

### Padding Layers
用来填充，和Conv层中的padding功能相同，Padding Layers不常用

### Non-linear Activations(weighted sum, nonlinearity)
非线性激活层
#### ReLU
```
nn.ReLU
```
- 传入参数
  - inplace
bool类型值，设置返回数据是否覆盖传入数据，一般保持默认值False
#### Sigmoid
```
nn.Sigmoid
```
#### Tanh
```
nn.Tanh
```

### Non-linear Activations(other)
#### Softmax
```
nn.Softmax
```
### Normalization Layers
标准化(归一化)层
#### nn.BatchNorm1d
批量归一化，全连接层用1d
#### nn.BatchNorm2d
批量归一化，卷积层用2d

##### 要解决的问题
- 损失出现在最后,后面的层训练较快 
- 数据在最底部 
  - 底部的层训练较慢 
  - 底部层一变化,所有都得跟着变 
  - 最后的那些层需要重新学习多次 
  - 导致收敛变慢
- 如果数据集中不同的特征数据不在同一个数量级，会导致梯度图为椭圆，导致梯度下降速度慢
##### 原理
- 固定小批量里面的均值和方差
$$
\mu_B = \frac{1}{|B|} \sum x_i
$$

$$
\sigma_B^2 = \frac{1}{|B|} \sum (x_i - \mu_B)^2 + \epsilon
$$

- 然后再做额外的调整(可学习的参数)
$$
x_{i+1} = \gamma \frac{x_i - \mu_B}{\sigma_B} + \beta
$$

其中γ是方差，β是均值

##### 使用方法
- 可学习的参数为γ和β 
- 作用在 
  - 全连接层和卷积层输出上,激活函数前 
  - 全连接层和卷积层输入上 
- 对全连接层,作用在特征维 
- 对于卷积层,作用在通道维

批量归一化的本质是通过在每个小批量里加入噪音来控制模型择杂度

批量归一化没必要跟丢弃法混合使用

批量归—化固定小批量免的均值和竞差,然后学习出适合的偏移和缩放

##### 批量归—化的作用
- 可以加速收敛速度,但—般不改变模型精度
- 可以减少训练时间，并使非常深的网络变的可以训练
  - 因为可以减少协变量（covariate）偏移，从而使用较大的学习率
  - 避免梯度消失和梯度爆炸，对Sigmoid和Tanh效果尤为显著
- 学习会更少的被参数初始化所影响
- 降低对正则化的要求

### Recurrent Layers
#### nn.RNN
#### nn.LSTM
#### nn.GRU

### Transformer Layers
#### nn.Transformer

### Linear Layers
#### nn.Linear

### Dropout Layers
#### nn.Dropout
- 正则化方式，在层之间加入噪音
- Dropout法将—些输出项随机置0来控制模型择杂度
- 通常将Dropout法作用在指层感知机的隐藏层的输出上
- 丢弃概率是控制模型择杂度的超参数，一般尝试3个值：0.1， 0.5， 0.9
- 正则项只在训练中使用:他们影响模型参数的更新
- Dropout是给全连接层用的，不能给卷积层用


### Loss Functions
#### 损失函数相关概念
损失函数的输入是一个pair:(output, target)，然后计算出一个数值来评估output和target之间的差距大小
#### nn.L1Loss
L1Loss,对每个元素真实值和预测值相减求绝对值，再求平均

传入参数
- reduction
- mean

对output求平均
- sum

对output求和
#### nn.MSELoss
差值平方Loss，对每个元素，真实值和预测值相减求平方，再求平均
#### nn.CrossEntropyLoss
交叉熵Loss，一般对多类别分类问题使用
##### shape
- input
input的shape是(C)或(N,C)或(N,C,d1,d2,...,dk)
  - C是分类数
  - N是batch size
  - dk是k-dimensional loss
- target
target的shape ()或(N)或(N,d1,d2,...,dk)
- output
output的shape ()或(N)或(N,d1,d2,...,dk)
##### 调用方法
```
output = loss(input, target)
```
### Utilities
#### nn.Flatten
将多维tensor压平成1维
- 使用方法
可以直接调用
```
torch.flatten()
```


## torch.nn.functional
提供了一些函数式的单层神经网络和一些工具
### Convolution functions
#### conv2d
```
torch.nn.functional.conv2d(input, weight, bias=None, stride=1, padding=0, dilation=1, groups=1) → Tensor
```
### Sparse functions/稀疏函数
#### one_hot
one hot编码
```
torch.nn.functional.one_hot(tensor, num_classes=-1) → LongTensor
```

## torch.optim
优化器
### 优化器算法
#### SGD
随机梯度下降
```
torch.optim.SGD(params, lr=0.001, momentum=0, dampening=0, weight_decay=0, nesterov=False, *, maximize=False, foreach=None, differentiable=False, fused=None)
```
##### 算法公式
weight = weight - learning_rate * gradient
##### 手动实现
```
learning_rate = 0.01
for param in net.parameters():
	param.data.sub_(param.grad.data * learning_rate)
```

传入参数
- params
模型参数，一般传入 ```net.parameters()```
- weight_decay
  - 权重衰退，正则化最常用的方法，它的功能是使用均方范数来限制模型参数值的选择范围，从而控制模型容量
  - 用来避免过拟合，是一个惩罚项，值越大，拟合越慢。通常不限制偏移b
  - 取值一般是e-2，e-3或e-4
  - 只在训练中使用，推理中不使用
#### Adam

### 优化器使用步骤
1. 定义优化器
```
optimizer = torch.optim.SGD(model.parameters(), lr=0.01)
```
2. 在每轮循环中梯度清零
```
optimizer.zero_grad()
```
3. 对损失值执行反向传播
```
loss.backward()
```
4. 在每次的backward()之后优化模型参数
```
optimizer.step()
```

# torchvision
## transforms
是一个包含多种工具的工具箱
```
from torchvision import transforms
```
### 使用方法
#### 创建工具
```
transform = transforms.ToTensor()
```
#### 使用工具
```
result = transform(input)
```

### 类型转换
#### ToTensor
- 把PIL.Image或numpy.ndarray类型转为torch.tensor
- 此方法非常常用，因为只有tensor才可以加入到计算图中进行反向传播
#### ToPILImage
把torch.tensor或numpy.ndarray类型转为PIL.Image
#### PILToTensor

### 调整尺寸
#### Resize
传入一个PIL Image,给定一个尺寸，调整Image尺寸为给定的尺寸

### 归一化
#### Normalize
归一化，给定一个平均值和一个标准差，对tensor进行归一化

### Compose
将多个transform操作合起来
```
Compose([transforms参数1, transforms参数2,...])
```

### 数据增强
#### RandomHorizontalFlip
随机概率水平翻转
#### RandomVerticalFlip
随机概率垂直翻转
#### RandomCrop
随机裁剪
#### RandomResizedCrop
```
RandomResizedCrop(size=(),scale=(),ratio=())
```
随机裁剪，并调整尺寸

#### ColorJitter
```
ColorJitter(brightness=0.5, contrast=0.5, saturation=0.5, hue=0)
```
调整颜色，饱和度对比度色相等

## datasets
### CIFAR10
```
CLASStorchvision.datasets.CIFAR10(root: Union[str, Path], train: bool = True, transform: Optional[Callable] = None, target_transform: Optional[Callable] = None, download: bool = False)
```
#### 传入参数
- root
数据集路径
- train
True为训练数据，False为测试数据
- transform
传入一个transform来处理数据，通常会传一个ToTensor的transform
- download
True为下载数据集到root路径，False不下载，直接使用root路径的数据集

## models
### 使用方法(以vgg为例)
#### 使用模型
- 使用随机参数模型
```
vgg = torchvision.models.vgg16(weights=None)
```
- 使用预训练模型
```
vgg = torchvision.models.vgg16(weights='ImageNet')
```
#### 修改模型
- 添加模型module
```
vgg.add_module(name='linear', module=nn.Linear(in_features=1000, out_features=10))
```
- 为模型module添加层
```
vgg.classifier.add_module(name='linear', module=nn.Linear(in_features=1000, out_features=10))
```
#### 查看模型架构
```
print(vgg)
```
#### 保存模型
- 保存方式1----保存模型架构+模型参数
```
torch.save(vgg16,'vgg16.pth')
```
- 保存方式2----仅保存模型参数（官方推荐方式）
```
torch.save(vgg16.state_dict(),'vgg16_param.pth')
```

#### 读取模型
- 读取方式1----读取模型架构+模型参数
```
model1 = torch.load('vgg16.pth')
```
- 读取方式2----读取模型参数（官方推荐方式）
```
saved_features = torch.load('vgg16_param.pth')
model2 = torchvision.models.vgg16(weights=None)
model2.load_state_dict(saved_features)
```
*注意*
- *如果是自己定义的模型，使用方式1保存的模型，在读取时需要引入模型架构，否则会报错找不到模型*
- *如果在CPU设备上读取GPU训练的模型，需要设置```map_location```*
```
saved_features = torch.load('vgg16_param.pth', map_location=torch.device('cpu'))
```
### Classification
#### VGG


## torchvision.utils
### make_grid()
制作图像网格，返回一个包含图像网格的Tensor

## Tricks
1.在迁移学习的微调中，可以把最后一层的学习率调为其他层的10倍，让其参数学习的更快



# jieba
## 分词模式
### 分词
#### 分词概念
分词就是将连续的字序列按照一定的规范重新组合成词序列的过程。在中文中，词没有形式上的分界符，分词就是找到分界符的过程
#### 分词的作用
词作为语言语义理解的最小单元，是人类理解文本语言的基础，也是NLP中的自动问答、机器翻译、文本生成等任务的重要基础环节
### 精准模式分词
试图将句子最精确地切开，适合文本分析
#### API
```
jieba.cut(content, cut_all=False)
```
返回一个生成器对象
```
jieba.lcut(content, cut_all=False)
```
返回分词后的列表内容

### 全模式分词
把句子中所有的可以成词的句子都扫描出来，速度非常快，但是不能消除歧义
#### API
```
jieba.cut(content, cut_all=True)
```
返回一个生成器对象
```
jieba.lcut(content, cut_all=True)
```
返回分词后的列表内容

### 搜索引擎模式分词
在精准模式的基础上，对长词再次切分，提高召回率，适合用于搜索引擎分词
#### API
```
jieba.cut_for_search(content)
```
返回一个生成器对象
```
jieba.lcut_for_search(content)
```
返回分词后的列表内容

### 中文繁体分词

### 用户自定义词典
#### 添加自定义词典后，jieba能够准确识别词典中出现的词汇，提升整体的识别准确率
#### 词典格式
每一行分三部分，用空格隔开，顺序不可颠倒
- 词语
- 词频（可省略）
- 词性（可省略）

## 命名实体识别
### 概念
#### 通常将人名、地名、机构名等专有名词统称为命名实体
#### 命名实体识别（Named Entity Recognition, 简称NER）就是识别出一段文本中可能存在的命名实体
### 命名实体的作用
同词汇一样，命名实体也是人类理解文本的基础单元，因此也是AI解决NLP领域高阶任务的重要基础环节

## 词性标注
### 概念
#### 词性
语言中对词的一种分类方法，以语法特征为主要依据，兼顾词汇意义对词进行划分的结果，常见的词性有14种，如：名词、动词、形容词等
#### 词性标注(Part of Speech Tagging, POS)就是标注出一段文本中每个词汇的词性
### 词性标注的作用
#### 词性标注以分词为基础，是对文本语言的另一个角度的理解，因此也常常成为AI解决NLP领域高阶任务的重要基础环节
### 语法
#### 导包
```
import jieba.posseg as pseg
```
#### API
```
pseg.lcut(content)
```

## 文本张量表示方法
### one-hot编码
#### 定义
又称独热编码，将每个词表示成具有n个元素的向量，这个词向量中只有一个元素是1，其他元素都是0，不同词汇元素为0的位置不同，其中n的大小是整个语料中不同词汇的总数
#### 优点
操作简单，容易理解
#### 缺点
完全割裂了词与词之间的联系。且在大语料集下，每个向量长度过大，占据大量内存
#### 由于one-hot编码明显的劣势，这种编码方式被应用的地方越来越少，取而代之的是稠密向量的表示方法word2vec和word embedding
### Word2vec
#### 定义
word2vec是一种流行的，将词汇表示成向量的无监督训练方法，该过程将构建神经网络模型，将网络参数作为词汇的向量表示，它包含CBOW和skipgram两种训练模式
#### CBOW(Continuous bag of words)模式
给定一段用于训练的文本语料，再选定某段长度（窗口）作为研究对象，使用上下文词汇预测目标词汇

#### skipgram模式
### Word Embedding/词嵌入
#### 定义
- 通过一定的方式将词汇映射到指定维度（一般是更高维度）的空间
- 广义的word embedding包括所有密集词汇向量的表示方法，如word2vec，即可认为是word embedding的一种
- 狭义的word embedding是指在神经网络中加入的embedding层，对整个网络进行训练的同时产生的embedding矩阵（emdedding层的参数），这个embedding矩阵就是训练过程中所有输入词汇的向量表示组成的矩阵


## 文本数据分析
### 作用
文本数据分析能够帮助我们理解数据语料，快速检查出语料可能存在的问题，并指导之后模型训练过程中的一些超参数选择
### 常用文本数据分析方法
#### 标签数量分布
#### 句子长度分布
#### 词频统计与关键词词云















