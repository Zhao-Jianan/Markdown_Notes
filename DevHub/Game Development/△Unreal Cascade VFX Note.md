# Particle System/级联粒子系统
## 基本概念
### 模块
定义粒子的行为，并且被放置在一个发射器中。
### 发射器
为展示效果发射特定行为的粒子，任意个发射器可以被同时放置在一个粒子系统内。
### 粒子系统
作为内容浏览器中的一个资源，可以被一个发射器Actor来引用。

### 发射器Actor
是一个放置在关卡中的东西，用于定义粒子在场景中如何使用

## 创建粒子
在Content Browser中点击右键-->基础资产-->Particle System

## Details/粒子组件属性
调节粒子参数
### Particles
- Template----------------------粒子模板，选择一个创建好的粒子资产
### Lighting
- Cast Shadow-------------------投射阴影，勾选后粒子对象会投射阴影，一般发射模型的粒子组件需要勾选
### Rendering
- Visible-----------------------在场景中的可见性
- Actor Hidden In Game----------在游戏中隐藏
### Activation
- Auto Activate-----------------自动触发

## 粒子系统编辑器
### Toolbar/工具架
#### Restart Sim/重启模拟
该操作将重置视口窗口中的模拟。也可以按空格键来执行此操作
#### Restart in Level/在关卡中重启
该操作重置粒子系统以及关卡中的任意系统实例
#### Thumbnail/缩略图
将从视口窗格摄像头视点看出去的画面保存为缩略图，以在内容浏览器中用来表示该粒子系统
#### Bounds/边界
在模拟视窗显示粒子边界
#### Origin Axis/坐标轴
在模拟视窗显示坐标轴
#### Background Color/背景颜色
更换模拟视窗的背景颜色，一般不使用黑色背景，因为黑色背景不容易观察粒子细节
#### Regenerate lowest LOD duplicating highest/复制最高LOD以重新生成最低LOD
通过复制最高LOD来重新生成最低LOD
#### Regenerate lowest LOD/重新生成最低LOD
使用最高LOD值的预设百分比值重新生成最低LOD
#### Select Lowest LOD/选择最低LOD
#### Select Lower LOD/选择低一级别LOD
#### Add LOD Before Current/在当前加载的LOD前面添加新LOD
#### Current LOD Slider/当前LOD滑块
允许选择想要预览的当前LOD。可以手动输入值或拖动鼠标来编辑该数字
#### Add LOD After Current/在当前加载的LOD后面添加新LOD
#### Select Higher LOD/选择高一级别LOD
#### Select Highest LOD/选择最高LOD
#### Delete Selected LOD/删除选择的LOD

### Viewport/视口
#### 快捷键
- 鼠标左键----------------------围绕着粒子系统反转摄像机
- 鼠标中键----------------------围绕着粒子系统平移摄像机
- 鼠标右键----------------------旋转摄像机
- Alt+鼠标左键------------------环绕粒子系统
- Alt+鼠标右键------------------将摄像机靠近和远离粒子系统
- F-----------------------------聚焦粒子系统
- L+鼠标左键--------------------旋转照明。仅对使用光照材质的粒子有效。在无光照粒子（大部分火焰、火花，等等）上将看不到任何效果
#### View/视图
- View Overlays-----------------视图覆层，允许切换一系列数据读数，以提供有关当前粒子系统的各种信息
  - Particle Counts---------------粒子计数，切换粒子计数覆层的可视性，它显示从系统中的每个发射器发射出的粒子数
  - Particle Event Counts---------粒子事件计数，切换事件计数覆层的可视性，它显示每个发射器中触发的事件数
  - Particle Times----------------粒子时间，切换粒子发射器时间反馈的显示。这里显示的是每个发射器保持活动的时长
  - Particle Memory---------------粒子内存，切换粒子系统内存占用量的显示，显示的是模板和每个实例的占用量
  - System Complated--------------系统反馈
  - Emitter Tick Times------------发射计时
- View Modes--------------------视图模式
  - Wireframe---------------------线框
  - Unlit-------------------------无光照
  - Lit---------------------------光照
  - Shader Complexity-------------着色器复杂性,提供一个特定着色器需要多少条指令的反馈。绿色是最低值，越红则代表指令值越高
- Detail Modes------------------细节模式
- Significance------------------重要性
- Orbit Mode--------------------环绕模式，在环绕粒子系统和在视口窗格中任意移动之间切换摄像机行为
- Vector Fields-----------------矢量字段，切换应用于粒子系统的任意矢量字段的可视性
- Grid--------------------------网格，切换网格的可视性
- Wireframe Sphere--------------线框球体，显示一个线框球体，它表示粒子系统的球面半径
- Post Process------------------后期处理，切换全局后期处理的可视性
- Motion------------------------运动，切换粒子系统是保持静止还是围绕网格中心转动
- Motion Radius-----------------运动半径，调出输入字段，设置“运动”（Motion）的运行半径
- Geometry----------------------几何体，显示或隐藏默认测试网格体
- Geometry Properties-----------几何体属性，调出几何体属性窗口，在这里可以调整默认几何体属性，如调节放置，切换所用的网格体以及许多其他选项

### Emitters/发射器
发射器界面右侧的发射器优先级别高于左侧的，右侧的会影响左侧的。选中发射器按键盘的向左方向键和向右方向键可以调整发射器的优先级别。发射器的运算顺序是从左到右的，模块的计算按照堆栈列表从上到下。按Shift拖动模块可以复制模块，注意这样复制的模块是联动的，修改一个的参数，另一个也会修改

粒子系统中的发射器沿着发射器列表从左到右计算

单击发射器并使用左右箭头键可以调整发射器在列表中的位置

#### Particle Emitter/粒子发射器类
粒子发射器（ParticleEmitter）是可以放置在粒子系统中的一个单独粒子特效，ParticleEmitter 类包含下列公共变量（即不选择任何模块时Details栏的属性）
##### Particle
- EmitterName--------------------发射器名称
- Initial Allocation Count-------该值允许声明在发射器初始化时应该分配的粒子数量。若该值为0，则使用计算的峰值数。（因为计算值可能比所需数高，该参数可用于进行严格的内存控制）
- Quality Detail Spawn Rate Scale--当引擎以中或低细节模式运行时，该值用于降低发射器的生成速度。可在分屏模式下优化粒子绘制消耗。不在高细节模式中时，0值可有效禁用发射器。这并不影响每单位产生的粒子（Spawn Per Unit），除非该值为0
##### Cascade
- Emitter Render Mode------------渲染发射器粒子使用的方法
  - Normal-------------------------按所需方式对发射器的粒子进行渲染，如作为sprite、网格体等进行渲染
  - Point--------------------------将发射器的粒子作为 2x2 的像素块进行渲染，不执行缩放，使用Emitter Editor Color
  - Cross--------------------------将发射器的粒子作为交叉线进行渲染，根据任意尺寸的模块进行缩放，使用Emitter Editor Color
  - Lights Only--------------------仅渲染灯光
  - None---------------------------不对发射器的粒子执行渲染
- Collapsed----------------------如为true, 则Particle Emitter在级联的发射器列表中为重叠状态。双击Particle Emitter段可切换该属性
- Emitter Editor Color-----------重叠时和位于曲线编辑器和调试渲染模式中时Particle Emitter段所呈现的颜色

#### Particle Module/粒子模块类
ParticleModule 是所有模块的基础类。这意味着所有模块将包含这些属性。本类包含下列公共属性
##### Cascade
- 3DDraw Mode--------------------如为true，将显示模块的3D可视化助手，例如显示初始位置模块范围的线框几何体
- Module Editor Color------------级联图表编辑器中模块使用的颜色

#### Particle System/粒子系统类
Particle System是一个包含任何数量Particle Emitters的完整粒子特效。在一个系统中应用多个发射器后，可以创建出精美细致的粒子特效，并存放于单个系统中。使用级联完成创建后，即可将Particle System置于关卡中或创建于脚本中,Particle System类包含下列公共变量,在发射器右键-->Particle System-->Select Particle System可以选择粒子系统类，并调出粒子系统类的细节属性
##### Particle System
- System Update Mode-------------此列举说明系统更新其发射器所使用的方法。有两种模式可用
  - RealTime-----------------------实时更新发射器
  - FixedTime----------------------以固定时间步长更新发射器。它将系统锁定在游戏的更新时间上，并依赖于运行性能。帧率越低，系统更新时间则更低（即更新时间减慢）；反之，帧率越高，更新时间则更快。通常仅用于特殊情况

FixedTime将无视当前帧率为系统设置特定时间步长。该模式仅用于特效时间并非另一个系统关键因素的情况下，比如将发射器绑定到一个动画上

- Update Time FPS----------------在FixedTime中运算时所使用的时间步长
- Warmup Time--------------------粒子系统启动时所需的准备时间。它可使发射器从开始便全力发射。但运行性能将受到影响，建议不要大量使用，尤其是数值较高时。对关卡最初加载时便已开始运行的系统（如烟柱或环境特效）而言使用效果较好
- Warmup Tick Rate---------------在系统准备期间控制每个标记的时间步长。增加该数值可提升性能，减少该数值可提高精度。数值0表示默认标记时间。
- Orient ZAxis Toward Camera-----如果为true,Particle System的局部Z轴将保持对准相机
- Seconds Before Inactive--------如这段时间内（以秒为单位）没有对粒子系统进行渲染，其将进入不活动状态，不再接受标记。输入0值，防止系统被强制变为不活动状态
##### Thumbnail/缩略图
- Thumbnail Warmup---------------在Use Real-Time Thumbnail为勾选状态下，捕捉缩略图渲染之前粒子系统所需的准备时间。
- Use Real-Time Thumbnail--------如为true，将使用默认相机位置自动捕捉Particle System资源在Content Browser中显示的缩略图，并反映出Particle System的当前设置和外观，而不使用保存的缩略图

使用实时缩略图渲染会降低Content Browser的运行性能
##### LOD
- LOD Distance Check Time--------确定系统执行一次距离检测的时间频率（以秒为单位），以明确使用的LOD级别（仅在LODMethod设为Automatic时使用）
- LOD Method---------------------系统选择适当LOD级别时所使用的方法。有两种方法可用
  - Automatic----------------------基于LOD距离和检测时间自动设置LOD级别
  - DirectSet----------------------游戏将直接为系统设置使用的LOD级别
  - ActivateAutomatic--------------激活时决定LOD级别。除非游戏代码直接设置，其将保持不变
- LOD Distances------------------确定使用LOD级别的距离阵列。（仅在 LODMethod 设为 Automatic 时使用）。这些数值将提供选择LOD级别的推荐最小距离。

3种LOD级别的粒子系统：
| LODDistanceIndex | 值      | 范围              | 所选 LOD 级别 |
|:----------------|:---------|:----------------|:--------------|
| 0                | 0.0       | 0.0 - 2499.9     | 0（最大值）   |
| 1                | 2500.0    | 2500.0 - 4999.9  | 1             |
| 2                | 5000.0    | 5000.0 - ∞        | 2             |

- LODSettings--------------------一种结构阵列，决定每个LOD使用的特定设置。当前使用指定LOD时，唯一的设置Lit用于控制Particle System是否接受光照
##### Bounds/边界
- Use Fixed Relative Bounding Box--如为true，代码将使用Fixed Relative Bounding Box作为粒子系统的边界
- Fixed Relative Bounding Box----允许为粒子系统设置边界框。移除每帧边界框更新所产生的性能消耗，代价是特效不可见时执行后台渲染/更新，或特效不在画面中时不执行渲染/更新。除非发射器有非常广的尺寸范围，通常推荐使用固定边界框，以确保运行性能稳定

右键单击级联工具栏上的“Toggle Bounds”按钮，用级联动态边界框当前所用值填充对话框，可从基础开始将其调整为所需的值
##### Delay/延迟
- Delay--------------------------执行ActivateSystem()时 Particle System在激活前的等待时间（以秒数计）。同时，当Use Delay Range为true时，该值为随机延迟值的范围上限
- Delay Low----------------------当Use Delay Range为true时，该值为随机延迟值的范围下限
- Use Delay Range----------------如为true，Delay Low和 Delay之间的随机值被选为实际延迟值使用
##### MacroUV
- Macro UV Position--------------相对于Particle System的局部空间位置作为中心点，生成Particle MacroUV材质表现的UV纹理坐标
- Macro UV Radius----------------它决定着Macro UV Position距离的全局空间半径，在此位置上生成的Particle MacroUV材质表现纹理坐标将开始铺制
##### Occlusion
- Occlusion Bounds Method--------计算Particle System遮挡时所用方法
  - None---------------------------不计算Particle System的遮挡
  - Particle Bounds----------------用于计算Particle System遮挡的Particle System Component边界
  - Custom Bounds-------------Custom Occlusion Bounds值用于计算ParticleSystem的遮挡
- Custom Occlusion Bounds--------使用CustomBounds Occlusion Bounds Method时，用于计算遮挡的边界

#### Default/默认模块
Required和Spawn这两个模块是永久模块，无法从发射器内移除。其他一些模块都可以按需删除
##### Required/粒子基本设定
这里包含了一些属性，都是对粒子系统绝对需要用到的属性，比如粒子使用的材质，发射器发射粒子的时间，以及其他
###### Emitter
- Material-----------------------选择粒子材质

使用粒子系统前要先创建一个粒子材质

创建粒子材质方法：
1. 基础节点的Blend Mode设为Translucent
2. 将粒子的基础形状贴图与Particle Color节点相乘连接到Base Color端口，将粒子的基础形状贴图的Alpha连接到Alpha端口
- Emitter Origin-----------------发射器原点，3D空间中将从该发射器发射出粒子的点，除非其他模块另有指定
- Emitter Rotation---------------发射器旋转，应用于发射器自身的局部旋转
- Screen Alignment---------------屏幕对齐模式，粒子相对于摄像头的朝向
  - PSA Facing Camera Position-----面向摄像机位置，粒子将旋转以面向摄像机位置，但将忽略摄像机旋转
  - PSA Square---------------------正方形，这个模式下，粒子面向摄像机，粒子等比例缩放，调整粒子尺寸只用调整X轴即可
  - PSA Rectangle------------------矩形，非等比缩放，面向摄像机
  - PSA Velocity-------------------速度，让粒子面向摄像机和粒子的移动方向。不允许非等分缩放
  - PSA Away from Center-----------远离中心
  - PSA Type Specific--------------类型特定，使用类型数据模块中指示的对齐方法。（仅限网格体）
  - PSA Facing Camera Distance Blend--面向摄影机距离混合
- Min Facing Camera Blend Distance--PSA Facing Camera Distance Blend模式下最小距离
- Max Facing Camera Blend Distance--PSA Facing Camera Distance Blend模式下最大距离
- Use Local Space----------------使用局部空间
- Kill on Deactivate-------------停用时终止，指示粒子发射器是否应在停用时终止所有粒子。如果为False，任何存活粒子将在发射器停用时终止其生命
- Kill on Completed--------------完成时终止，指示粒子系统组件应在完成时终止该发射器实例
- Sort Mode----------------------排序模式，用于发射器的排序模式
  - PSORTMODE None-----------------无，不执行排序
  - PSORTMODE View Proj Depth------视图投影，根据视图投影按深度对粒子排序
  - PSORTMODE Distance to View-----距离到视图，在场景空间中，按粒子到摄像机的距离对粒子排序
  - PSORTMODE Age Oldest First-----年龄最老优先，按年龄对粒子排序，最先绘制的粒子排在前面
  - PSORTMODE Age Newest First-----年龄最新优先，按年龄对粒子排序，最新绘制的粒子排在前面
- Use Legacy Emitter Time--------使用传统发射器时间，如果为True，则发射器的Emitter Time将通过用Emitter Duration调制Seconds Since Creation来计算。由于这对循环和可变持续时间会导致问题，因此实现了一种新方法。如果为False，将使用这种新方法，Emitter Time只需要在每个Tick增加Delta Time。当发射器循环时，它按当前Emitter Duration调整Emitter Time，产生正确的循环/延迟行为
- Remove HMD Roll----------------如果为True，移除HMD中的滚动，VR中使用
- Orbit Module Affects Velocity Alignment--轨道模块影响速度调整，如果为True，则轨道模块生成的运动应用于速度一致的粒子
###### Duration/持续时间
- Emitter Duration---------------指示发射器在循环前运行的时间，以秒为单位。如果设置为0，发射器将永不循环
- Emitter Duration Low-----------发射器持续时间低端，指定允许在发射器持续时间内变化的发射器持续时间的低端
- Emitter Duration Use Range-----发射器持续时间使用范围，当为True时，发射器将在启动时从Emitter Duration Low到Emitter Duration的范围内选择持续时间
- Duration Recalc Each Loop------每次循环重新计算持续时间，当为True时，发射器将在循环时从Emitter Duration Low到Emitter Duration的范围内选择一个新的持续时间
- Emitters Loops-----------------循环发射次数，设置发射器发射几次，0为一直发射
###### Delay/延迟
- Emitter Delay------------------发射器延迟，延迟启动发射器的时间。允许在单个粒子系统内“交错”发射器。这也相当于使用范围时选择随机延迟值的上限
- Emitter Delay Low--------------发射器延迟低端，使用范围时选择随机延迟值的下限
- Emitter Delay Use Range--------发射器延迟使用范围，如果为True，发射器的有效延迟值将是从范围[Emitter Delay Low, Emitter Delay]中选择的随机值
- Delay First Loop Only----------仅第一个循环延迟，当为True时，Emitter Delay大于0、Emitter Loops大于1的发射器将仅在第一次循环时执行延迟
###### Sub UV/子图像UV
当粒子贴图为图片序列时，在这里设定读取的序列图和序列方式等，这对于在粒子上实现简单动画十分有用

切记当粒子贴图为图片序列时，在这里设置完后，要添加一个SubImage Index设置序列读取的序列索引才能正确显示

- Interpolation Method-----------插值方法，指示用来在子图之间插值的方法的列举
  - None---------------------------无，不对该发射器应用子UV模块
  - Linear-------------------------线性，按给定顺序，平滑地在子图之间过渡，而不混合当前子图和下一个子图
  - Linaer Blend-------------------线性混合，按给定顺序，平滑地在子图之间过渡，混合当前子图和下一个子图
  - Random-------------------------随机，随机选取下一个图像，不混合当前图像和下一个图像
  - Random Blend-------------------随机混合，随机选取下一个图像，混合当前图像和下一个图像
- Sub Images Horizontal----------子图水平，纹理水平轴（x）上的纹理中的子图数量
- Sub Images Vertical------------子图垂直，纹理垂直轴（y）上的纹理中的子图数量
- Scale UV-----------------------缩放UV，指示应缩放UV值以正确适应子图尺寸。这仅用于网格体发射器
- Random Image Changes-----------随机图像更改，在插值方法设置为随机时，在粒子生命周期内更改图像的次数
###### Macro UV/宏UV
宏UV分段指示发射器应利用宏UV，允许单个图像连续地映射到多个粒子，而不是每个粒子单独映射。注意，要利用这个功能，应用于粒子的材质必须利用ParticleMacroUV材质表达式节点
- Override System Macro UV-------覆盖系统宏UV，如果为True，这里的设置将覆盖系统宏UV设置，可以通过取消选择级联发射器列表中的所有发射器和模块来查看
- Macro UVPosition---------------宏UV位置，局部空间位置，所有宏UV计算都始于这个位置
- Macro UVRadius-----------------宏UV半径，场景半径，超过这个半径的所有宏UV材质将开始平铺
###### Rendering/渲染
- Use Max Draw Count-------------使用最大绘制数量，当为True时，发射器永远不会绘制超过“最大绘制计数”数量的粒子。所有粒子在Tick时仍会更新
- Max Draw Count-----------------最大绘制数量，限制渲染到的粒子数量
- UVFlipping Mode----------------UV翻转模式，以多种不同的方式启用Sprite和GPU粒子UV翻转
  - None---------------------------无，不发生UV翻转。这是默认值
  - Flip UV------------------------翻转UV，翻转U和V纹理坐标
  - Flip UOnly---------------------仅U，仅翻转U纹理坐标
  - Flip VOnly---------------------仅V，仅翻转V纹理坐标
  - Random Flip UV-----------------随机翻转UV，在产生时间同时随机翻转U和V
  - Random Flip UOnly--------------仅随机翻转U，在产生时间仅随机翻转U
  - Random Flip VOnly--------------仅随机翻转V，在产生时间仅随机翻转V
  - Random Flip UVIndependent------独立随即翻转UV，在产生时间单独随机翻转U和V
###### Normals/法线
- Emitter Normals Mode-----------发射器法线模式，用于为该发射器LOD生成法线的模式
  - ENM Camera Facing--------------面向摄像机，默认模式，法线基于面向摄像机的几何体
  - ENM Spherical------------------球体，从以法线球体中心为中心的球体生成法线
  - ENM Cylindrical----------------圆柱体，从圆柱体生成法线，穿过法线球体中心，沿着法线圆柱体方向
- Normals Sphere Center----------法线球体中心，当Emitter Normals Mode设置为ENM Spherical，则创建的粒子法线是背对法线球体中心远离。该值位于局部空间
- Normals Cylinder Direction-----法线圆柱体方向，当Emitter Normals Mode为ENM Cylindrical时，则创建的粒子法线是背对圆柱体远离，穿过法线球体中心，沿着法线圆柱体方向移动。该值位于局部空间

##### Spawn/产卵
这个模块控制粒子从发射器生成的速度，它们是否以Burst生成，以及其他和粒子发生时机有关的属性
###### Spawn/产卵
- Rate---------------------------发射速度，给定时间发射器的粒子产生速度（每秒粒子数）
- Rate Scale---------------------发射尺寸，实际发射的粒子数是Rate乘以Rate Scale
- Apply Global Spawn Rate Scale--应用全局产卵发射尺寸
- Process Spawn Rate-------------处理产生速度，如果为True，将处理速度。如果有多个产生模块“堆叠”在发射器中，并且有任何一个模块禁用了这个属性，则不会处理发射器的速度
###### Burst/爆发
爆发数据指示发射器应在设定的时间强制发射指定数量的粒子，瞬间发射粒子，通常制作爆炸、火花以及只需要发射一次的粒子如法阵等
- Particle Burst Method----------粒子爆发方法，通过爆发发射粒子时所用的方法。当前忽略
- Burst List---------------------爆发列表，一个整数数组，包括“计数”、“计数低”和浮点时间值，用于确定所需的粒子爆发。在发射器生命周期内，时间位于[0..1]范围内。如果“计数低”设置为-1，发射且将在给定时间爆发出“计数”数量的粒子。否则，发射器将在给定时间在范围[计数低..计数]范围内爆发出随机数量的粒子
  - Count--------------------------瞬间爆发的粒子数
- Burst Scale--------------------爆发比例，按这个数量调节所有爆发条目
- Process Burst List-------------处理爆发列表，如果为True，将处理Burst List。如果有多个产生模块“堆叠”在发射器中，并且有任何一个模块禁用了这个属性，则不会处理发射器的Burst List

##### Lifetime/生命期
控制粒子从出生到死亡的生命期长度，如果没有这个模块，粒子则会一直持续下去
###### Lifetime
- Lifetime-----------------------确定粒子生命周期（以秒为单位）的浮点Distribution。基于粒子生成的Emitter Time获取数值

Lifetime设为0，粒子会一直存在，不会消失

##### Initial Size/初始尺寸
控制粒子刚出生时的尺寸

##### Initial Velocity/初始速度
对粒子生成时的移动进行控制
###### Velocity
- Start Velocity-----------------开始速度，粒子生成时应用的速度
- Start Velocity Radial----------径向开始速度，粒子沿径向应用的速度。在生成时从发射器位置减去粒子位置即可确定方向
- In World Space-----------------如为True，速度将被假定于全局空间中
- Apply Owner Scale--------------如为True，可通过Particle System Component的缩放对速度值进行调整

##### Color Over Life/生命期颜色
控制粒子整个生命期的颜色和透明度的改变
###### Color
- Start Color--------------------确定粒子颜色的矢量 Distribution。基于粒子生成的Emitter Time获取数值
- Start Alpha--------------------确定粒子Alpha组件的浮点 Distribution。基于粒子生成的Emitter Time获取数值
- Clamp Alpha--------------------如为True，Alpha值将被锁定在 0-1的范围内

颜色由该模块设置。这意味着之前所有颜色模块的数值均会被覆盖


#### TypeData/发射器类型数据
控制发射器的类型，需要注意的是，无论什么类型，发射器默认都是面片发射器。可以添加不同的类型数据模块，改变发射器的类型。如果不添加发射器类型数据，默认为Sprite Emitters
##### Sprite Emitters/精灵发射器
这是发射器的基本类型，也是用的最广泛的类型。使用始终朝向摄像机的多边形化的面片（2 个多变形组成）作为单个粒子发射。可以用来做烟雾、火焰特效，以及其他各种种类的效果

##### AnimTrail Data/动画拖尾数据
用于创建动画的拖尾效果

##### Beam Data/光束数据
Beam类型数据模块使发射器产生光束 - 连接粒子形成源点（如发射器）和目标点（如一个粒子或Actor）之间的一个流。用于创建光束效果，比如镭射光、闪电等类似的效果
###### Beam/光束
- Beam Method--------------------光束生成方法
  - Distance-----------------------使用距离属性沿发射器X轴发射光束
  - Target-------------------------从发射器源点向设定的目标发射光束
  - Branch-------------------------当前未使用
- Texture Tile-------------------沿光束平铺贴图的次数。该功能当前尚未添加
- Texture Tile Distance----------沿着光束代表源贴图一个切片的距离
- Sheets-------------------------沿光束渲染的面片数量。面片在光束路径周围均匀分布。例如，从上向下观察光束穿行所沿的轴时，2 个面片将形成一个十字
- Max Beam Count-----------------允许发射器拥有存活光束的最大数量
- Speed--------------------------光束发出时从源点到目标的移动速度。如该值设为0，光束将从源点瞬时跳至目标
- Interpolation Points-----------确定光束是否应使用源点和目标切线沿光束内插曲线。如该值小于等于零，光束即为源点和目标之间的一条直线（无插值）。如该值大于零，光束将在源点和目标各自切线值之间进行插值，以决定两者之间的路径。此过程中所用步骤数量为本属性中所设的值
- Always On----------------------如为True，发射器将始终拥有一个存活粒子
- Up Vector Step Size------------决定光束向上矢量所使用的方法
  - 0------------------------------在光束各点处计算向上矢量
  - 1------------------------------在光束起点计算向上矢量，然后用于各点
  - 其他值N------------------------每隔N个点计算向上矢量，并在它们之间插值，当前不支持此方法
###### Branching/分枝
当前未使用
###### Distance/距离
- Distance-----------------------Beam Method设为Distance时，浮点Distribution将提供光束沿X轴行进的距离
###### Taper/锥化
- Taper Method-------------------光束沿其延伸方向锥化的方法
  - None---------------------------光束未应用锥化
  - Full---------------------------无视当前光束长度，相对源点到目标对光束进行锥化
  - Partial------------------------当前未使用
- Taper Factor-------------------提供光束锥化量的Distribution。使用常量曲线时，时间值0.0表示在光束源点锥化，时间值1.0表示在目标处锥化
- Taper Scale--------------------缩放锥化量。最终使用的锥化值Taper =(TaperFactor*TaperScale)。它主要用作粒子参数分配器，允许游戏代码根据其用途设置光束锥化缩放系数
###### Rendering/渲染
- Render Geometry----------------渲染几何体，如为True，将对光束的实际几何体执行渲染。通常情况下皆会启用该项，否则尾迹为不可见
- Render Direct Line-------------渲染径向线条，如为True，将对光束源点和目标之间的直线执行渲染。用于级联中的调试
- Render Lines-------------------渲染线条，如为True，将对沿光束各部分的线条执行渲染。用于级联中的调试
- Render Tessellation------------渲染细分，如为True，将对源点和目标之间的曲面细分路径执行渲染。用于级联中的调试

##### GPU Sprites/GPU精灵
这是特殊类型的粒子，在运行时大量计算交给 GPU 执行。这将 CPU 的粒子特效计算从几千的数量级提高到 GPU 计算特效的几十万的数量级，取决于具体的目标系统上 GPU 的类型

注意在使用GPU Sprites时，要在工具架中的Bounds中点击Set Fixed Bounds，设置GPU粒子的边界，GPU粒子才能正常使用

GPU粒子不支持传统CPU粒子的所有功能，但它们拥有一些独特功能，可使效率得到极大提高。粒子发射仍在CPU上发生，以确定生成粒子的位置、时间和数量。CPU也可使用传统CPU粒子方法对大小和速度等初始属性进行指定
###### Particle Module Type Data Gpu
- Camera Motion Blur Amount------相机动态模糊量，基于摄像机动态模糊设置sprites的拉伸程度

GPU粒子支持以下属性：
- 初始位置（Initial Location）
- 初始速度（Initial Velocity）
- 加速度（Acceleration）
- 阻力（Drag）
- 生命周期（Lifetime）
- 颜色（Color）
- 大小（Size）
- 旋转（Rotation）
- 自转速率（RotationRate）
- 子图像索引（SubImageIndex）

##### Mesh Data/模型数据
不再发射一系列的面片，这个类型的发射器将会发射多边形模型。用于创建岩石块，废墟等类似的效果
###### Mesh/网格
- Mesh---------------------------网格体，在发射器的粒子位置处所渲染的静态网格体
- Use Static Mesh LODs-----------使用静态网格体的LOD
- LODSize Scale------------------静态LOD尺寸缩放
- Mesh Alignment-----------------网格体对齐，渲染网格体时所使用的对齐方式。 Required Module（必须模块）的Screen Alignment（屏幕对齐）属性必须设置为PSA_Type Specific，这个属性才能有效
  - Face Camera With Roll----------面向相机，使其可绕由网格体到相机间的向量来旋转（旋转量由标准平面粒子旋转量提供）
  - Face Camera With Spin----------面向相机，使网格体可绕切线轴旋转
  - Face Camera With Locked-Axis---面向相机并保持向上的向量以作为锁定的方向
- Override Material--------------覆盖材质，如果该值为Ture，网格体将使用发射器中的材质（在Required Module（必须模块）中分配的材质）而不是使用这些应用到静态网格体模型上的材质进行渲染。 除非网格体上有多个需要分配材质的UV通道，才使用这项来覆盖MeshMaterial（网格体材质）模块，否则需要在代码中用参数进行材质分配
- Override Default Motion Blur Settings--覆盖默认运动模糊设置
###### Orientation/方向
###### Camera Facing/摄像机朝向
- Camera Facing------------------摄像机朝向，如果该项为True，那么网格体的X轴将总是指向相机。 当设置该项时，将忽略Axis Lock Option（坐标轴锁定选项）和其他的锁定坐标轴/屏幕对齐设置
- Camera Facing Option-----------摄像机朝向选项，该项决定了当启用Camera Facing（摄像机方向）时，网格体的朝向
- Apply Particle Rotation As Spin--应用粒子旋转为旋转值，如果该项为True，那么“平面粒子”的旋转量将会被应用到与方向坐标轴有关的网格体上（网格体指向的方向）。否则，“平面粒子”旋转值将被应用到相机面向坐标轴的网格体上
- Face Camera Direction Rather Than Position--如果该项为True，所有摄像机面向选项都会使网格体面向摄像机的视角方向，而不是指向摄像机的位置


##### Ribbon Data/条带数据
Ribbon类型数据模块意味着发射器将会产生一串粒子附属到一个点上，能在一个移动的发射器后形成一个色带。粒子按其生成顺序连接。因此，粒子初始速度模式越不稳定，条带便越无序
###### Trail/尾迹
- Sheets Per Trail---------------围绕尾迹延伸方向旋转进行渲染的面片数量
- Max Trail Count----------------允许存活尾迹的数量
- Max Particle in Trail Count----尾迹可同时包含的最大粒子数量
- Dead Trails on Deactivate------如为True，Particle System停用时尾迹将被标记为死亡状态。尾迹仍将渲染，但即使重新启用Particle System，也不会产生新粒子
- Dead Trails on Source Loss-----如为True，当尾迹源头“丢失”（即源粒子死亡）时该尾迹将被标记为死亡状态
- Clip Source Segement-----------如为True，尾迹将不会与源点位置连接
- Enable Previous Tangent Recalculation--如为True，每次产生新粒子时都将对上一切线进行重新计算
- Tangent Recalculation Every Frame--如为True，每帧都将重新计算所有切线，以便应用速度和加速度
- Spawn Initial Particle---------如为True，条带首次开始移动时将产生一个粒子
- Render Axis--------------------尾迹的“渲染”轴（即尾迹延伸方向的轴）
  - Camera Up----------------------面向相机的传统尾迹
  - Source Up----------------------使用源点的向上轴作为每个粒子的生成方向
  - World Up-----------------------使用世界场景的向上轴
###### Spawn/产卵
- Tangent Spawning Scalar--------粒子生成的切线标量。切线A和切线B之间的角度被映射为[0.0f .. 1.0f]。然后，该值与Tangent Spawning Scalar相乘，以得出将生成粒子的数量
###### Rendering/渲染
- Render Geometry----------------渲染几何体，如为True，将对尾迹几何体执行渲染。通常情况下皆会启用该项，否则尾迹为不可见
- Render Spawn Points------------渲染产卵点，如为True，将在尾迹中每个粒子生成点上渲染星星。用于级联中的调试
- Render Tangents----------------渲染切线，如为True，将使用一条线渲染尾迹中每个粒子生成点上的切线。用于级联中的调试
- Render Tessellation------------渲染细分，如为True，将渲染各个生成粒子之间的曲面细分路径。用于级联中的调试
- Tiling Distance----------------平铺距离，平铺第2个 UV 集合的（预计）覆盖距离。如该值为0.0，将不会传入第2个 UV 集合
- Distance Tessellation Step Size--尾迹曲面细分点之间的距离，其用于确定尾迹所拥有的曲面细分点数量和尾迹的平滑度
- Enable Tangent Diff Interp Scale-如启用该标记，系统将基于相邻粒子切线的差异对插值顶点的数量进行调整。每对相邻粒子将计算下列CheckTangent值：如Check Tangent值小于0.5，将根据结果对Distance Tessellation Step Size进行调整。它将进行映射，在0到1之间从平行到垂直（0到90度）进行调整。如大于90度，则值将锁定为1
- Tangent Tessellation Scalar----曲面细分的切线标量。切线A和切线B之间的角度映射为0到1。然后，该值与Tangent Tessellation Scalar相乘，得出需要细分的点数量


#### Acceleration/加速
用于处理粒子加速行为的模块，在粒子上应用加速度，或随时间变化改变粒子的速度,比如通过定义阻力等
##### Acceleration/加速
Acceleration模块设置粒子的初始加速度。该数值存储于每个粒子中，在更新调用中应用于每一帧
该模块将为粒子荷载数据Used Acceleration添加一个矢量参数。该数值用于保留每个粒子生命周期中的加速度
在每一帧中，粒子当前的基础速度值使用公式（速度+=加速度乘以DeltaTime）进行更新。此公式中的DeltaTime是上一帧后流逝的时间
###### Acceleration
- Acceleration-------------------确定加速度数值的矢量 Distribution。基于粒子生成的EmitterTime获取该数值
- Apply Owner Scale--------------如为true，加速度数值将乘以Particle System Component的大小
- Always In World Space----------如为 true，加速度矢量将被假定位于全局空间坐标中。否则，它将相对Particle System Component被假定位于局部空间中
##### Const Acceleration/常量加速
Const Acceleration模块与Acceleration模块十分相似，在其中为粒子应用了初始加速度。然而关键的不同点在于Const Acceleration模块不接受Distribution属性

Const Acceleration是GPU Sprite粒子唯一可用的加速度类型
##### Drag/阻力
Drag为每个粒子的运动应用恒定阻力。系数值在生成时计算，应用于每一帧的粒子
###### Drag
- Drag Coefficient Raw-----------一个浮点Distribution，用于定义每个粒子的阻力系数或运动抵力大小
##### Drag Scale/Life/生命期阻力乘数
Drag Scale/Life是和现有阻力模块共用的一个乘数值，可在粒子生命周期中利用曲线对阻力大小进行调整

Drag Scale/Life仅限用于GPU Sprite粒子
##### Acceleration/Life/生命期加速
Acceleration Over Life设定粒子生命周期中的加速度
###### Acceleration
- Accel Over Life----------------确定加速度数值的矢量Distribution。基于粒子更新的RelativeTime获取该数值
- Always In World Space----------如为true，加速度矢量将被假定位于全局空间坐标中。否则，它将相对ParticleSystemComponent被假定位于局部空间中

#### Attraction/引力
这些模块包含将粒子向空间中特定位置吸引的方法。这个特定位置可被定义为以下形式：一个点、一条线、或另一个粒子的位置。甚至可以将它们组合起来，创造出复杂的特效

使用一个点引力器（Point Attractor）结合一个线引力器（Line Attractor），并将其强度设为随粒子生命周期中不断变化，即可生成旋流特效
##### Line Attractor/线引力场
Line Attractor 可将粒子在 3D 空间中绘制成一条线
###### Attractor
- End Point 0--------------------指定线的一个终点，以便向该点吸引粒子
- End Point 1--------------------指定线的另一个终点，以便向该点吸引粒子
- Range--------------------------一个浮点 distribution，为线周围的吸引设定半径范围。与粒子生命周期相关
- Strength-----------------------吸引强度（负值则产生排斥效果）。与粒子生命周期相关

##### Particle Attractor/粒子引力场
Particle Attractor将把粒子向系统中其他发射器发射的粒子吸引
###### Attractor
- Emitter Name-------------------吸引源发射器的名称
- Range--------------------------一个浮点Distribution，为源粒子周围的吸引设定半径范围。与粒子生命周期相关
- Strength by Distance-----------如为true，将使用以下数值获取强度曲线中的值：(AttractorRange-DistanceToParticle)/AttractorRange。否则将使用源粒子RelativeTime获取强度
- Strength-----------------------吸引强度（负值则产生排斥效果）。如Strength By Distance为false，则其与粒子生命周期相关
- After Base Velocity------------如为true，将在基本速度上应用速度调整
- Renew Source-------------------如为true，源粒子失效后将选择一个新粒子。否则粒子将不会被吸引到另一个粒子
- Inherit Source Vel-------------如为true，源失效后其速度将被粒子继承

##### Point Attractor/点引力场
Point Attractor可定义粒子被吸引至的点，以及其效果半径
###### Attractor
- Position-----------------------一个矢量Distribution，指明粒子发射器相关点的位置。利用Emitter Time获取该数值
- Range--------------------------一个浮点Distribution，为源粒子周围的吸引设定半径范围。与粒子生命周期相关
- Strength-----------------------点引力器的强度。利用 EmitterTime获取该数值
- Strength by Distance-----------如为True，强度将沿半径均衡分布
- After Base Velocity------------如为True，将在基本速度上应用速度调整，以保持引力器的牵引力
- Override Velocity--------------覆盖速度
- Use World Space Position-------如为True，位置将被假定位于全局空间坐标中

##### Point Gravity/点重力
Point Gravity模块利用特定强度值将粒子吸引至3D空间中单一的点。它和 Maya粒子系统的Newton场原理相似。它可用于向源牵引粒子，或围绕一个点创建轨道效果

点重力是GPU Sprites唯一可用的引力器模块，且仅用于GPU Sprites
###### Point Gravity Source
- Position-----------------------在3D空间中提供一个重力发生的点
- Radius-------------------------重力牵引效果的半径范围
- Strength Raw-------------------该浮点Distribution将决定重力点对粒子的影响强度


#### Beam/光束
仅用于Beam TypeData模块，这些模块用于对发射器行为进行配置或修改
##### Beam Modifier/光束修改器
Beam Modifier模块可对光束的源点或目标进行修改
###### Modifier/修改器
- Modifier Type------------------指定需要修改的模块
  - Source-------------------------模块修改光束的源点
  - Target-------------------------模块修改光束的目标
###### Position/位置
- Position Options---------------和Position属性相关的选项
  - Modify-------------------------如为True，源点/目标的位置将会被修改。否则位置将不受影响
  - Scale--------------------------如为True，可利用修改器模块的Position值对源点/目标位置进行调整。否则将重叠源点/目标位置
  - Lock---------------------------如为True，源点/目标的位置在粒子生命周期中将被锁定
- Position-----------------------该位置值用于修改源点/目标的位置
###### Tangent/切线
- Tangent Options---------------和Tangent属性相关的选项
  - Modify-------------------------如为True，源点/目标的切线将会被修改。否则切线将不受影响
  - Scale--------------------------如为 true，可利用修改器模块的Tangent值对源点/目标切线进行调整。否则将重叠源点/目标切线
  - Lock---------------------------如为 true，源点/目标的切线在粒子生命周期中将被锁定
- Tangent------------------------该切线值用于修改源点/目标的切线
- Absolute Tangent---------------如为True，将切线作为整体空间中的一条绝对切线（即不会将其改变）
###### Strength/强度
- Strength Options---------------和Strength属性相关的选项
  - Modify-------------------------如为True，源点/目标的强度将会被修改。否则强度将不受影响
  - Scale--------------------------如为True，可利用修改器模块的Strength值对源点/目标强度进行调整。否则将重叠源点/目标强度
  - Lock---------------------------如为 true，源点/目标的强度在粒子生命周期中将被锁定
- Strength-----------------------该强度值用于修改源点/目标的强度

##### Noise/燥波
Beam Noise模块可沿光束发射噪点
###### Low Freq/低频噪点
- Low Freq Enabled---------------如为 true，则启用低频噪点
*低频噪点是当前唯一支持的噪点*
- Frequency----------------------沿光束噪点的频率
- Frequency Low Range------------如大于零，该值为频率的范围下限。粒子生成时，将在```[Frequency_LowRange..Frequency]```范围内设置其频率
- Noise Range--------------------提供噪点位置范围的 Distribution。如使用的是常量曲线，首个频率点的映射时间为0.0f，目标点的时间为1.0。剩余的点使用公式 (CurrentFrequencyPoint*(1.0/TotalFrequencyPoints))进行查阅
- Noise Range Scale--------------该Distribution提供在发射器时间上调整噪点范围的方法
- NRScale Emitter Time-----------如为True，将使用发射器时间获取Noise Range Scale结果。如为False，将使用粒子时间获取 Noise Range Scale结果
- Noise Speed--------------------提供噪点移动速度的矢量Distribution
- Smooth-------------------------如为True，将尝试在噪点之间平顺地移动
- Noise Lock Radius--------------噪点周围的代表锁定的球体半径
- Oscillate----------------------如为True，噪点将弹回并向前穿过光束直线
- Noise Lock Time----------------选取新的噪点前噪点被锁定的时间
- Noise Tension------------------应用至细分噪点线的张力
- Use Noise Tangents-------------如为True，将在每个噪点上计算切线
- Noise Tangent Strength---------在沿光束插值中应用到噪点切线的强度
- Noise Tessellation-------------在噪点之间进行插值的点
- Target Noise-------------------如为True，将把噪点应用到目标点
- Frequency Distance-------------放置噪点的距离。如该值为0.0，则使用标准Frequency/Frequency_LowRange对确定噪点的频率。如该值不为0.0，噪点将分布在指定的距离上，由静态频率值决定。因此在较短光束上的噪点数量较少，将随光束的延长自动增加噪点
- Apply Noise Scale--------------如为True，将把NoiseScale应用至光束
- Noise Scale--------------------Apply Noise Scale为 True时应用至噪点范围的缩放因子。该Distribution查找值的算法：出现的噪点数量除以噪点的最大数量（即频率）

##### Source/源点
Beam Source模块为一个光束发射器应用单个源点。如光束发射器中不存在源点模块，发射器位置将代替源点
###### Source
- Source Method------------------此列举可对光束源点位置的获取方法进行设置
  - Default------------------------使用源点Distribution
  - User Set-----------------------使用用户设置的数值
  - Emitter------------------------将发射器位置作为源点使用
  - Particle-----------------------当前未使用
  - Actor--------------------------使用命名Actor的位置
- Source Name--------------------作为源点使用的Actor的名称（仅在Source Method设为Actor时使用）。如未找到Actor，备用方案为使用源点Distribution
- Source Absolute----------------如为True，将源点作为整体空间中的一个绝对位置（即不会将其改变）
- Source-------------------------对源点位置进行设置的矢量Distribution。方法设为默认、或使用其他方法无法确定源点时使用该 Distribution。使用当前的发射器时间从Distribution获取数值
- Lock Source--------------------如为True，仅在生成时才可对源点位置进行设置
- Source Tangent Method----------此列举可对光束源点切线的获取方法进行设置
  - Direct-------------------------在源点和目标之间使用一条直线
  - User Set-----------------------使用用户设置的数值
  - Distribution-------------------使用来自源点切线Distribution的数值
  - Emitter------------------------使用发射器所面对的方向
- Source Tangent-----------------对源点切线进行设置的矢量Distribution。Source Tangent Method设为Distribution时使用。使用当前的发射器时间获取数值
- Lock Source Tangent------------如为True，仅在生成时才可对源点切线进行设置
- Source Strength----------------一个浮点Distribution，用于定义每条光束源点切线的强度。使用当前的发射器时间获取数值。该强度的使用无视用于获取源点/源点切线的方法
- Lock Source Strength-----------如为True，仅在生成时才可对源点强度进行设置

##### Target/目标
Beam Target模块为一个光束发射器应用单个目标。如光束发射器中不存在目标模块，发射器假定光束将被定向使用
###### Target
- Target Method------------------此列举可对光束目标位置的获取方法进行设置
  - Default------------------------使用目标Distribution
  - User Set-----------------------使用用户设置的数值
  - Emitter------------------------当前不支持
  - Particle-----------------------当前不支持
  - Actor--------------------------使用命名Actor的位置

如将目标设为发射器或粒子，它将使用来自 distribution 的数值
- Target Name--------------------作为目标使用的Actor的名称。仅在Target Method设为Actor时使用。如未找到Actor，备用方案为使用目标Distribution
- Target-------------------------对目标位置进行设置的矢量Distribution。方法设为默认、或使用其他方法无法确定目标时使用该Distribution。使用当前的发射器时间从Distribution获取数值
- Target Absolute----------------如为True，将目标作为整体空间中的一个绝对位置（即不会将其改变）
- Lock Target--------------------如为True，仅在生成时才可对目标位置进行设置
- Target Tangent Method----------此列举可对光束目标切线的获取方法进行设置
  - Direct-------------------------在源点和目标之间使用一条直线
  - User Set-----------------------使用用户设置的数值
  - Distribution-------------------使用来自源点切线Distribution的数值
  - Emitter------------------------使用发射器所面对的方向
- Target Tangent-----------------对目标切线进行设置的矢量Distribution。Target Tangent Method设为Distribution时使用。使用当前的发射器时间获取数值
- Lock Target Tangent------------如为True，仅在生成时才可对目标切线进行设置
- Target Strength----------------一个浮点Distribution，用于定义每条光束目标切线的强度。使用当前的发射器时间获取数值。该强度的使用无视用于获取目标/目标切线的方法
- Lock Target Strength-----------如为True，仅在生成时才可对目标强度进行设置
- Lock Radius--------------------当前光束端所在的球体半径，被视为目标点锁定。在应用含速度值集的光束时使用

#### Camera/摄像机
这些模块对摄像机相关的发射器行为进行修改，用于管理如何在摄像机空间来移动粒子的模块，能够处理粒子是靠近还是远离摄像机
##### Camera Offset/摄像机偏移
Camera Offset 模块使 sprite 粒子的位置相对于相机之间存在偏移。究其本质，它将粒子向摄像机拉近或推远
###### Camera
- Camera Offset------------------应用至Sprite粒子位置的摄像机相对偏移
- Spawn Time Only----------------如为True，该模块的偏移将只在粒子最初生成时出现
- Update Method------------------指定从此模块更新偏移的方法
  - Direct Set---------------------使用Camera Offset值直接设置偏移，覆盖之前存在的偏移
  - Additive-----------------------将Camera Offset值从该模块添加到之前的偏移中
  - Scalar-------------------------利用Camera Offset值对现有的偏移进行调整

#### Collision/碰撞
用于管理粒子如何和其他Actor碰撞的模块
##### Actor Collision/角色碰撞
###### Collision
- Damping Factor-----------------确定碰撞后粒子“减慢”程度的矢量Distribution。基于粒子生成的Emitter Time获取该数值，并将其保存在粒子中
- Damping Factor Rotation--------确定碰撞后粒子旋转“减慢”程度的矢量Distribution。基于粒子生成的Emitter Time获取该数值，并将其保存在粒子中
- Max Collisions-----------------确定一个粒子所拥有最大碰撞数的浮点Distribution。基于粒子生成的Emitter Time获取该数值
- Collision Completion Option----此列举说明达到最大碰撞数后粒子将出现的情况
  - Kill---------------------------达到Max Collisions时销毁粒子，默认行为
  - Freeze-------------------------就地冻结粒子
  - Halt Collisions----------------停止碰撞检测，但保持更新。这可能会导致粒子下坠并穿过对象
  - Freeze Translation-------------停止粒子平移，但保持其他所有更新
    - Freeze Rotation----------------停止粒子旋转，但保持其他所有更新
  - Freeze Movement----------------停止粒子平移/旋转，但保持其他所有更新
- Collision Types----------------碰撞类型
- Apply Physics------------------确定粒子和碰撞对象之间是否应用物理的布尔值

当前情况为单向：粒子到对象。粒子本身并未应用物理，它只会产生一个应用于碰撞对象上的冲量
- Ignore Trigger Volumes---------
- Particle Mass------------------确定粒子质量的浮点 Distribution，在Apply Physics为True时使用。基于粒子生成的Emitter Time获取该数值
- Dir Scalar---------------------一个浮点值，用于调整粒子边界，防止出现相互穿插或较大间隙
- Pawns Do Not Decrement Count---如为True，与Pawns之间的碰撞仍将存在效果，但不计入Max Collisions的次数。这将使粒子在碰撞后从Pawn上弹开，而不会停留在空中
- Only Vertical Normals Decrement Count--如为True，无垂直碰撞法线的碰撞仍存在效果，但不计入Max Collisions的次数。这将使粒子在碰撞后从墙上弹开，落到地上
- Vertical Fuage Factor----------用于确定垂直与否的浮点值。真正垂直的条件是Hit.Normal.Z==1.0f。这将使[1.0-VerticalFudgeFactor..1.0]范围内的Z组件被算作垂直碰撞
- Delay Amount-------------------粒子碰撞检查的延迟量。利用Emitter Time获取该数值。在更新中，粒子标记Ignore Collisions将被设置，直至粒子Relative Time超过Delay Amount
- Ignore Source Actor------------忽略初始角色
###### Performance
- Drop Detail--------------------如为True，且World Settings 的Drop Detail属性也为True，模块将被无视
- Collide Only if Visible--------如为True，只有粒子系统被渲染的情况下才会产生碰撞
- Max Collision Distance---------粒子碰撞产生的最大距离

#### Color/颜色
该分类模块用于改变粒子的颜色

Color模块要求发射器材质使用粒子颜色材质表现，将颜色从模块传递到材质上

颜色在一个全浮点范围上进行计算。大于1的数值通常会呈现出发光效果
##### Initial Color/初始颜色
Initial Color模块在生成时设置粒子颜色。粒子在其生命周期中将保持该颜色，除非被另一颜色模块所覆盖
###### Color
- Start Color--------------------确定粒子颜色的矢量 Distribution。基于粒子生成的Emitter Time获取数值
- Start Alpha--------------------确定粒子Alpha组件的浮点 Distribution。基于粒子生成的Emitter Time获取数值
- Clamp Alpha--------------------如为True，Alpha值将被锁定在 0-1的范围内

##### Init Color(Seed)/初始颜色（种子）
Init Color(Seed)模块与生成时设置粒子初始颜色的Initial Color模块相同；然而此模块可对种子信息进行指定。该种子信息用于选择Distribution值，从发射器每次使用的模块获得更稳定的效果
###### Random Seed
- Random Seed Info---------------为该模块属性选择“随机”值而使用的随机种子
  - Get Seed from Instance---------如为True，则模块将尝试从实例所有者处获得种子（Seed）。如获取失败，将返回从Random Seeds阵列中获得种子
  - Instance Seed Is Index---------如为True，从实例中恢复的种子值即为Random Seeds阵列中的索引
  - Reset Seed on Emitter Looping--如为True，每次发射器循环时将重新设置该种子
  - Randomly Select Seed Array-----随机选择种子数组
  - Random Seeds-------------------本模块应用的随机种子值。如多个值被指定，实例将随机选取一个值

##### Color Over Life/生命期颜色

##### Scale Color/Life/生命期颜色级别
Scale Color/Life模块用于调整粒子在其生命周期中的颜色


#### Event/事件
事件模块允许基于粒子自身间、不同粒子之间、或者粒子和世界之间的相互作用来产生事件，然后监听这些事件并在一个交互的粒子系统关卡中导致一系列的反应。 一个很好的例子是当一个粒子和世界中其它物体产生碰撞时，会触发指定的碰撞事件，然后在那些碰撞发生的地方产生粒子
##### Event Generator/时间生成器
Event Generator模块将根据指定的条件生成一个(或多个)事件。这个模块有一个单独的事件数组，它包含了想让发射器生成的一系列事件

#### Kill/销毁
该分类模块用于处理单个粒子的删除行为，如果某个给定粒子满足了特定的规则，那么销毁模块将销毁它
##### Kill Box/销毁盒
Kill Box模块用于在粒子移动到所定义的盒体外部时销毁它们
###### Kill
- Lower Left Corner---------------左下边界，一个定义盒体的左下边界的向量分布
- Upper Right Corner--------------右上边界，一个定义盒体的右上边界的向量分布
- Absolute------------------------绝对位置，如果为True，边界设置将被认为是世界坐标空间值并在测试时保持不变。 如果为False，盒体将被转换为发射器的世界坐标空间
- Kill Inside---------------------销毁边界盒内粒子，如果为 True，落在边界盒内的粒子将会被销毁。 如果为Talse(默认)，边界盒外的粒子将会被销毁
- Axis Aligned and Fixed Size-----坐标轴对齐和固定尺寸，如果此值为True，盒体将总会与轴对齐且无法缩放。 就实际效果来说，这会造成盒体忽略发射器尺寸

##### Kill Height/销毁高度
Kill Height模块在粒子移动到所定义的高度之上时用来销毁该粒子
###### Kill
- Height--------------------------高度，一个定义了高度的浮点分布，当粒子在此高度或者高于此高度时将被销毁
- Absolute------------------------绝对位置，如果为True，高度值将被认为是世界坐标空间的值并且在测试时保持不变。 如果为False，高度值将被转换为发射器的世界坐标空间
- Floor---------------------------值下限，如果为True，当粒子下降到低于高度值的位置时，该粒子被销毁。 如果为False(默认)，当粒子上升到高于高度值的位置时将被销毁
- Apply PSys Scale----------------如果设置为True, 定义的尺寸会考虑发射器的比例

#### Lifetime/存活时间
该分类模块用于处理粒子存在的时间
##### Lifetime/存活时间

##### Lifetime(Seeded)/存活时间（种子）
Lifetime(Seeded)模块与生成时设置粒子生命周期的Lifetime模块相同；然而此模块可对种子信息进行指定。该种子信息用于选择Distribution值，从发射器每次使用的模块获得更稳定的效果

#### Light/灯光
这些模块管理粒子的光照特性，附加到各个粒子的光源来渲染CPU粒子发射器（CPU Particle Emitters）。这对火花或火焰等特效很有用，在这种情况下它可以发出足够的光，在周围环境中引人注目
##### Light/灯光
用来使粒子照亮周围场景，使粒子特效与场景融合的更好

光源（Light）模块仅可用于CPU粒子上，因此任何GPU粒子都无法使用该模块。将模块添加到GPU发射器不会破坏系统，但是它不会执行任何操作，并且在列表中模块上方会显示一个巨大的红色X
###### Light
- Use Inverse Squared Falloff----使用平方反比衰减，如果启用，光源指数（Light Exponent）将被忽略，以便基于光源半径获得更逼真的衰减
- Affects Translucency-----------影响半透明，启用后，每个粒子光源都将影响照明半透明度。这可用于表现火箭穿过烟雾的发射轨迹。此属性会为以此方式渲染的每个粒子增加大量成本，因此建议仅对少数粒子启用此设置
- Preview Light Radius-----------预览光源半径，在预览（Preview）窗口中，这将显示光源在线框球体内的半径
- Spawn Fraction-----------------生成分数，定义要附加光源的粒子的百分比。1.0表示所有粒子，0.5表示一半粒子，0.1为10%的粒子。优化时，可用此设置降低成本
- Color Scale Over Life----------粒子生命期照亮场景的颜色强度，XYZ分别对应RGB通道
- Brightness Over Life-----------粒子生命期照亮场景的亮度
- Radius Scale-------------------半径比例，照亮场景的半径，这是一个乘数，它根据粒子的大小定义光源的范围。X轴上比例为1的粒子将具有与半径比例（Radius Scale）相等的半径，而X轴上比例为10的粒子则将具有10倍于半径比例（Radius Scale）的半径
- Light Exponent-----------------光源指数，如果禁用使用平方反比衰减（Use Inverse Squared Falloff），则这将控制光源的衰减，较大数值会导致更平缓的衰减，因为光源接近光源半径，而较小数值将导致接近光源半径的光源突然衰减
- Volumetric Scattering Intensity--体积散射密度，扥光的体积散射密度，影响密度和灯光颜色
- High Quality Lights------------高质量灯光
- Shadow Casting Lights----------灯光投射阴影，控制粒子灯光是否投射阴影，需要在高质量灯光开启才能生效
*这个属性开启后非常占用GPU资源*
- Lighting Channels--------------灯光通道

#### Location/位置
这些模块定义了相对于发射器位置的粒子生成位置的信息，影响粒子在其生命周期中多个时间的所在位置
##### Initial Location/初始位置
控制粒子产生的位置
###### Location
- Start Location-----------------确定粒子发射位置（与发射器相关）的浮点Distribution。基于粒子生成的Emitter Time获取数值
- Distribute Over NPoints--------当此属性被设为非零的数值时，它沿发射粒子的等分Distribution生成多个均衡分布的点。例如，如一个Distribution的最小和最大值将一条线的长度定义为100个单位，将该值设为2则会造成只在实际的最大和最小位置发射粒子，两者之间不存在发射的位置
- Distribute Threshold-----------当Distribute Over NPoints被设为任何非零数字时，将获得这些平均分布的点上粒子发射量的百分点。例如，数值1将使所有粒子从这些点发射。数值0.5将使一半的粒子从这些点发射，另外一半从随机位置发射
##### Initial Location(Seed)/初始位置（种子）
Initial Location(Seeded)模块与生成时设置粒子初始位置的Initial Location模块相同；然而此模块可对种子信息进行指定。该种子信息用于选择Distribution值，从发射器每次使用的模块获得更稳定的效果
##### Bone/Socket Location/骨骼/插槽位置
Bone/Socket Location 模块允许粒子从骨骼网格体的骨骼或插槽的所在位置直接发射
###### Bone Socket
- Source Type--------------------指定源点位置是骨骼或插槽
  - Sockets------------------------生成粒子的Source Locations是插槽
  - Bones--------------------------生成粒子的Source Locations是骨骼
- Universal Offset---------------应用至每个骨骼或插槽的偏移
- Source Locations---------------骨骼网格图上的源骨骼或插槽，从此处生成粒子
- Selection Method---------------从Source Locations阵列选择骨骼或插槽的方法
  - BONESOCKETSEL_Sequential-------按顺序次序选择Source Locations阵列中的项目
  - BONESOCKETSEL_Random-----------随机选择Source Locations阵列中的项目
  - BONESOCKETSEL_RandomExhaustive-随机选择Source Locations中的项目，但在所有源点均被使用前不会出现选择两个相同项目的情况
- Update Position Each Frame-----如为True，粒子位置将被更新至每帧中骨骼或套接字的位置
- Inherit Bone Velocity----------继承骨骼速度
- Inherit Velocity Scale---------继承速度倍数
- Skel Mesh Actor Param Name-----范例参数的名称，指定为游戏提供Skeletal Mesh Component的Skeletal Mesh Actor
- Num Pre Selected Indices-------预选索引数
- Editor Skel Mesh---------------指定在编辑器中用于预览的骨骼网格体

##### Direct Location/直接位置
Direct Location 模块用于直接设置粒子的位置
###### Location
- Location-----------------------确定特定时间粒子位置的矢量Distribution。基于粒子的Relative Time获取该数值。请注意，粒子位置设为此数值，因此复写任意之前的模块均会产生影响
- Location Offset----------------一个矢量Distribution，确定从Location计算所获取的位置而进行应用的偏移。利用Emitter Time获取偏移。它在以下情况十分实用：通过对Actor或其他资源进行脚本代码编写使用Location场集时，或使用随机Location Offset在对象周围产生偏移时。偏移将在粒子生命周期中将保持恒定
- Scale Factor-------------------一个矢量Distribution，用于在时间线特定的点上对对象的速度进行调整。它将使粒子变形，与跟随的路径相吻合
- Direction----------------------当前未使用

##### Emitter Initial Location/发射器初始位置
Emitter Initial Location模块将粒子的初始位置设为来自在同一个粒子系统中另一个发射器的粒子位置
###### Location
- Emitter Name-------------------发射器的名称，用作位置粒子的源点
- Selection Method---------------此列举说明从源发射器选择粒子的方法
  - ELESM Random-------------------从源发射器随机选择一个粒子
  - ELESM Sequential---------------从源发射器按顺序依次逐句通过每个粒子
- Inherit Source Velocity--------用于确定生成的粒子继承源粒子速度的布尔值
- Inherit Source Velocity Scale--继承时源速度的调整量
- Inherit Source Rotation--------用于确定生成的粒子继承源粒子旋转的布尔值
- Inherit Source Rotation Scale--继承时源旋转的调整量

##### Emitter Direct Location/发射器直接位置
Emitter Direct Location模块将粒子在整个生命周期中的位置设为来自在同一个粒子系统中另一个发射器的粒子位置

##### Cylinder/圆柱体
用一个圆柱体来限制发射位置
###### Location
- Start Radius-------------------开始半径，控制圆柱体半径
- Start Height-------------------开始高度，控制圆柱体高度
- Height Axis--------------------高度坐标系，控制圆柱体朝向
- Surface Only-------------------仅表面，只在圆柱体表面发射
###### Cascade
- B 3DDraw Mode------------------在预览窗口显示圆柱框

##### Cylinder(Seed)/圆柱体（种子）
Cylinder(Seeded)模块与在圆柱体中设置粒子初始位置的Cylinder模块相同；然而此模块可对种子信息进行指定。该种子信息用于选择Distribution 值，从发射器每次使用的模块获得更稳定的效果

##### Sphere/球体
在球体中产生粒子

##### Sphere(Seed)/球体（种子）
Sphere(Seed)模块与在球体中设置粒子初始位置的Sphere模块相同；然而此模块可对种子信息进行指定。该种子信息用于选择Distribution 值，从发射器每次使用的模块获得更稳定的效果

##### Triangle/三角形
Triangle模块允许用户定义三角形的形状和位置，粒子将从该三角形的2D和3D区域发射（取决于是否应用了厚度）
###### Location
- Start Offset-------------------定义三角形位置偏移的矢量Distribution
- Height-------------------------定义三角形边长的浮点Distribution
- Angle--------------------------确定斜边和对边之间角度的浮点Distribution
- Thickness----------------------一个浮点Distribution，确定三角形的厚度，将其转为3D楔形物。粒子将从三维区域中进行发射

##### Skel Vert/Surf Location(Skeletal Mesh Vertex/Surface Location)/骨骼网格顶点/曲面位置
Skel Vert/Surf Location模块允许粒子从骨骼网格体的顶点或多边形表面发射

##### World Offset/世界偏移
World Offset模块用于偏移粒子生成时的初始位置。偏移位于全局空间中，但在粒子的生命周期中将遵守Use Local Space标记。这意味着粒子将无视发射器方向在全局空间中生成偏移，但在其生命周期中将相对于发射器保持该偏移
###### Location
- Start Location-----------------一个矢量Distribution，用于确定粒子所使用的全局空间偏移。基于粒子生成的Emitter Time获取数值
- Distribute Over NPoints--------当此属性被设为非零的数值时，它沿发射粒子的等分Distribution生成多个均衡分布的点。例如，如一个Distribution的最小和最大值将一条线的长度定义为100个单位，将该值设为2则会造成只在实际的最大和最小位置发射粒子，两者之间不存在发射的位置
- Distribute Threshold-----------当Distribute Over NPoints被设为任何非零数字时，将获得这些平均分布的点上粒子发射量的百分点。例如，数值1将使所有粒子从这些点发射。数值0.5将使一半的粒子从这些点发射，另外一半从随机位置发射

##### World Offset(Seed)/世界偏移（种子）
World Offset(Seed)模块与在球体中设置粒子初始位置的World Offset模块相同；然而此模块可对种子信息进行指定。该种子信息用于选择Distribution值，从发射器每次使用的模块获得更稳定的效果

##### Pivot Offset/枢轴偏移

##### Source Movement/源移动
Source Movement模块基于源点（即发射器）的移动设置粒子位置的偏移
###### Source Movement
- Source Movement----------------一个矢量Distribution，指定添加到粒子位置前应用至源点移动的缩放因子。使用粒子相对时间获取该数值

#### Material/材质
这些模块定义了粒子上应用的材质信息

#### Rotation/旋转
这些模块用于控制粒子的旋转
##### Initial Mesh Rotation/初始模型旋转
Initial Mesh Rotation模块为以网格体数据发射器创建的网格体粒子赋予初始旋转

##### Initial Mesh Rotation(Seed)/初始模型旋转（种子）
Initial Mesh Rotation(Seed)模块为以网格体数据发射器创建的网格体粒子赋予初始旋转，额外添加了随机性

##### Initial Rotation/初始旋转
控制粒子产生时的旋转值，一般设为Float Uniform模式，0-1即为0度到360度

##### Initial Rotation(Seed)/初始旋转（种子）
Initial Rotation(Seeded)模块与设置初始旋转或粒子的Initial Rotation模块相同；然而此模块可对种子信息进行指定。该种子信息用于选择Distribution 值，从发射器每次使用的模块获得更稳定的效果

##### Rotation/Life/生命期旋转
控制粒子在从出生到死亡中间的旋转

#### RotationRate/旋转速率
这些模块管理旋转速度的变化
##### Initial Mesh Rotation Rate/初始模型旋转速率
Initial Mesh RotationRate模块用于设置网格体粒子被发射时的旋转速率

##### Initial Mesh Rotation Rate(Seed)/初始模型旋转速率（种子）
Initial Mesh RotationRate(Seed)模块与发射时设置网格体粒子旋转速率的Initial Mesh RotationRate模块相同；然而此模块可对种子信息进行指定。该种子信息用于选择Distribution值，从发射器每次使用的模块获得更稳定的效果

##### Mesh Rotation Rate*Life/粒子生命期模型旋转速率
Mesh RotationRate*Life模块用于调整网格体粒子在其生命周期中的旋转速率
##### Mesh Rotation Rate Over Life/粒子生命期模型旋转速率
Mesh RotationRate Over Life模块用于调整网格体粒子在其生命周期中的旋转速率

##### Initial Rotation Rate/初始旋转速率
Initial RotationRate模块用于设置粒子被发射时的旋转速率

只发射一次的粒子如法阵等，要让它自身旋转，使用Initial Rotation Rate模块即可

##### Initial Rotation Rate (Seeded)/初始旋转速率（种子）
Initial RotationRate(Seeded)模块与发射时设置粒子旋转速率的 Initial RotationRate模块相同；然而此模块可对种子信息进行指定。该种子信息用于选择Distribution值，从发射器每次使用的模块获得更稳定的效果

##### Rotation Rate*Life/生命期旋转速率
Rotation Rate*Life模块用于调整粒子在其生命周期中的旋转速率

#### Orbit/轨迹
这些模块能够定义屏幕空间的行为轨迹，为效果添加额外的运动特性，可实现粒子Sprites从实际粒子中心偏移/向外旋转的渲染
##### Orbit/轨迹
这是添加的唯一Orbit模块。它可实现从实际粒子位置发生的Sprite偏移和旋转。数个轨道组件可以多种方式链接起来
###### Chaining/链接
- Chain Mode---------------------此列举描述该模块与发射器中的其他模块之间的链接方式。设置该数值可定义模式与之前模式的组合
  - Add----------------------------将之前结果和模块值相加
  - Scale--------------------------将之前结果和模块值相乘
  - Link---------------------------“断开”链接并应用之前结果的数值
###### Offset/偏移
- Offset Amount------------------偏移量，确定Sprite与粒子“中心”之间偏移程度的矢量Distribution
- Offset Options-----------------偏移设置，与Offset Amount相关的选项
- Process During Spawn------------如为True，将在粒子生成过程中对数据相关部分进行处理
- Process During Update-----------如为True，将在粒子更新过程中对数据相关部分进行处理
- Use Emitter Time----------------如为True，获取数据相关部分时将使用Emitter Time。如为False，将使用粒子Relative Time
###### Rotation/旋转
- Rotation Amount-----------------确定粒子位置旋转偏移程度的矢量Distribution。它为“轮流型”，0等于无旋转、0.5等于180度旋转、1.0等于360度旋转
###### Rotation Rate/旋转速率

#### Orientation/定向
这些模块能够锁定粒子的旋转轴，控制粒子的方向，阻止旋转在特定的轴上发生
##### Lock Axis/锁定坐标轴
Axis Lock模块可将粒子锁定朝向固定的轴。这当下只是一个基于Sprite的模块，可以用于改变粒子朝向，如将法阵改为朝上就是锁定到Z轴
###### Orientation/定向
- Lock Axis Flags-----------------确定粒子锁定的轴
  - None----------------------------无锁定轴
  - X-------------------------------锁定Sprite朝向+X轴
  - Rotate X------------------------锁定Sprite在X轴上旋转

#### Parameter/参数化
这些模块能够被参数化，将数据从粒子系统中传出，可以使用外部系统来对粒子进行控制，比如蓝图、材质、Matinee
##### Dynamic/动态
Dynamic模块用于向发射器使用的材质传递四个标量值，使发射器对材质效果进行控制

使用时在材质中添加Dynamic Parameter节点，在粒子系统中添加Parameter模块，即可联动
###### Particle Module Parameter Dynamic
- Dynamic Params------------------模块动态参数阵列。Dynamic Params阵列中的每个元素均有以下属性
  - Param Name----------------------材质DynamicParameter表现中相关参数的名称。该属性为只读，在粒子动态材质表现存在于此发射器应用的材质中时进行自动填入
  - Use Emitter Time----------------如为True，使用发射器时间获取参数的Distribution值。否则将使用粒子相对时间
  - Spawn Time Only-----------------如为True，粒子生成时只设置参数值。否则，该值将每帧更新
  - Value Method--------------------指定用于获得参数值的方法
    - EDPV User Set-------------------在Param Value属性中设置的值作为参数值传递到材质
    - EDPV Auto Set-------------------忽略Distribution中的值
    - EDPV Velocity X-----------------沿X轴的粒子速度作为参数值传递到材质
    - EDPV Velocity Y-----------------沿Y轴的粒子速度作为参数值传递到材质
    - EDPV Velocity Z-----------------沿Z轴的粒子速度作为参数值传递到材质
    - EDPV Velocity Mag---------------粒子速度的量级作为参数值传递到材质
  - Scale Velocity by Param Value---如为True，在Param Value distribution中设置的值将对传至材质的速度值进行调整
  - Param Value---------------------浮点Distribution，用于设置以EDPV User Set方法使用的参数值

##### Dynamic(Seed)/动态（种子）
Dynamic(Seed)模块与允许发射器传递数值到材质的Dynamic Parameter模块相同；然而此模块可对种子信息进行指定。该种子信息用于选择Distribution值，从发射器每次使用的模块获得更稳定的效果

#### Size/尺寸
这些模块控制粒子的缩放行为
##### Initial Size/初始尺寸

##### Initial Size(Seed)/初始尺寸（种子）

##### Size By Life/尺寸随生命期变化
Size By Life模块通过特定数值在粒子生命周期中对其尺寸进行缩放

##### Size Scale/尺寸缩放
Size Scale模块将粒子尺寸设为Base Size测定的固定缩放因子。请注意，该模块将覆盖之前在该帧中进行的尺寸调整

##### Size By Speed/随速度缩放尺寸
通过粒子速度的一部分对其尺寸进行缩放
###### Particle Module Size Scale By Speed
- Speed Scale---------------------这个属性用于设置Sprite在X轴和Y轴中的缩放量
- Max Scale-----------------------提供一个最大的缩放值，作用和夹具相似

#### Spawn/产卵
这些模块用来给粒子生成速率添加额外定义，比如根据距离的改变来调整粒子的生成，影响发射器粒子的数量/速率
##### Spawn Per Unit/每单位产卵
基于发射器移动的距离生成粒子。在创建类似于基于Sprite的烟雾尾迹特效时十分实用。因为烟雾尾迹在速度快慢时都需要内凝力，生成相应数量的粒子可填补空隙
###### Spawn/产卵
- Unit Scalar---------------------一个浮点值，用于确定应用至已移动距离的标量。Spawn Per Unit的值除以该数值，获得每个单位上粒子的实际数量
- Spawn Per Unit------------------确定每个单位上粒子生成数量的浮点Distribution。利用Emitter Time获取该数值
- Ignore Spawn Rate When Moving---如为True，非移动状态下将处理默认的生成速率。发射器为移动状态时，不处理默认生成速率。如为False，返回Process Spawn Rate设置
- Movement Tolerance--------------一个浮点值，用于确定关于Ignore Spawn Rate When Moving旗标的移动和非移动状态公差，即如果（Distance Moved小于(Unit Scalar乘Movement To lerance)），则判定其为非移动状态
- Max Frame Distance--------------单独一帧中最长的移动距离。如粒子在一帧中的移动超过了此距离，发射器将不会发射粒子。如数值为0，将不执行该检查。它在处理瞬移对象时十分实用
- Ignore Movement Along X---------如为True，则运动的X轴组件将被无视
- Ignore Movement Along Y---------如为True，则运动的Y轴组件将被无视
- Ignore Movement Along Z---------如为True，则运动的Z轴组件将被无视
- Process Spwan Rate--------------确认Required模块的Spawn Rate是否应被处理。在叠列的Spawn模块（同一粒子发射器上的多个Spawn模块）中，如有模块指出“默认”生成速率不应被处理，将不会对其进行处理
###### Burst
- Process Burst List--------------如为True，发射器Spawn Module的Burst List将被处理。如多个Spawn模块叠列在一个发射器中，且其中有模块将此属性设为False，将不对Spawn Module Burst List进行处理

#### SubUV/子UV
这些模块能够让粒子使用序列帧动画贴图数据，每“帧”的网格摆放在此贴图中

在Interpolation Method未被设为PSUVIM_None时，SubUV模块方可应用至发射器
##### SubImage Index/子图像索引
当粒子贴图是图片序列时，需要在Required模块的Sub UV设置好序列，再添加一个SubImage Index，Point0输出值设为0，Point1输出值设为序列的最后一个-1，如序列共有36张图，就设为35
###### Sub UV
- Sub UV Image Index--------------子UV图像索引，确定子图像索引应被应用于粒子的浮点Distribution。使用粒子更新中的RelativeTime获取该数值

因实际值为浮点型，应使用稍高的值。例如，如所需第二张图片（Image1），则值应被设为1.01
###### Realtime
- Use Real Time-------------------使用真实时间，如为True，影片将无视游戏的慢动作设置进行实时播放

##### SubUV Movie/子UV电影
SubUV Movie模块以特定帧率按顺序次序循环贴图的子图像，与Flipbook 贴图的工作方式相似
###### Flipbook
- Use Emitter Time----------------使用发射器时间，如为True，发射器时间用于获取FrameRate Distribution的值。否则将使用相对粒子时间
- Frame Rate----------------------帧率，用于指定子图像播放帧率的浮点Distribution
- Starting Frame------------------开始帧，SubUV的起始图片索引（1=第一帧）。假定顺序为从左至右、从上至下。如大于最后一帧，则锁定为最后一帧。如为0，则随机选择一个起始帧

#### Velocity/速度
这些模块处理每个粒子的移动速度
##### Intial Velocity/初始速度

##### Intial Velocity(Seed)/初始速度（种子）

##### Velocity Cone/锥形速度
Velocity Cone模块以锥形发射粒子
###### Cone/圆锥
- Angle---------------------------角度，此浮点Distribution值设置锥形的角度。如需设为Uniform，Min代表内锥形角，Max代表外锥形角。数值的最小单位为[0..1]，1代表180度，或一个完整的圆
- Velocity------------------------速度，一个浮点Distribution，用于设置粒子沿锥形发射的速度
- Direction-----------------------定义方向点的3D矢量
###### Velocity/速度
- In World Space------------------如为True，速度将被假定于全局空间中
- Apply Owner Scale---------------如为True，可通过Particle System Component的缩放对速度值进行调整

##### Inherit Parent Velocity/继承父速度
Inherit Parent Velocity在粒子生成时使其获得父项（粒子发射器本身）的速度

##### Velocity/Life/生命期速度
Velocity/Life 模块在粒子生命周期中按指定量对速度进行调整
###### Velocity/速度
- Vel Over Life-------------------一个矢量Distribution，作为调整值应用至速度。使用粒子的Relative Time获取该数值
- Absolute------------------------如为True，速度将被设为Distribution中的数值。利用该属性可在粒子生命周期中的一个特定点对粒子速度直接进行设置。

该设置将“优先于”之前影响速度的模块。它还将阻止“初始速度”模块为粒子赋予初始速度。如为False，速度将根据Distribution的值进行调整


### Distributions/分布
Distribution是一组数据类型，以特殊的方式处理数据，比如为一个数值应用一个范围，或者使用曲线来对数值做插值操作。如果粒子系统需要任何随机属性，或者粒子需要随着时间进行变化时，就需要使用一个distribution来控制属性
##### Constant/常数分布
固定值不产生随机
- Constant-----------------------常数
##### Uniform/范围分布
提供了一个最小值和一个最大值，输出这两个值之间（包含这两个值）的随机数值
##### Constant Curve/常数曲线分布
提供了一个数值的简单曲线，可以添加多个点，每个点赋予一个值，当时间或某变量到达这个点的值时，输出设定的值。在这个类型下，时间通常是指一个粒子从生成的消失的过程，或者说是粒子的起始时间和结束时间
- Point--------------------------添加点
  - In Val-------------------------输入值，范围是0-1，如时间，0为粒子出生时间，1为粒子死亡时间
  - Out Val------------------------输出值，范围是0-1，如透明度，0为透明，1为不透明
##### Uniform Curve/范围曲线分布
可以添加多个点，每个点赋予一个最小值和一个最大值，当时间或某变量到达这个点的值时，输出设定的最小值和最大值之间的一个随机值
##### Particle Parameter/使用粒子参数分布
这种类型的 Distribution 使得该属性参数化，以便于它能够被外部系统，诸如蓝图、Matinee 或者其他系统读取或改写

Distribution的每种类型对Float和Vector都单独存在。然而无论是使用Float还是Vector的版本，Distribution是由类型来决定，并不能自由选择




