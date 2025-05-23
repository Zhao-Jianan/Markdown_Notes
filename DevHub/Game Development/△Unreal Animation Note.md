# Animation/动画
## Animation/动画资产
### Aim Offset/射击偏移
与混合空间功能类似，是一个特殊的混合空间，专门用来做朝不同方向射击的动画过渡，可以被混合空间替代

使用Aim Offset需要把动画资源的坐标系改成模型坐标系，默认是本地坐标系
### Animation Blueprint/动画蓝图
动画系统的核心，用来添加动画和控制动画

动画蓝图一般命名规则是加后缀_AnimBP

动画蓝图从本质上讲是个专有蓝图，它的图表可以控制骨骼网格物体的动画。它可以执行动画混合，直接控制骨架的骨骼，并在每一帧对骨骼网格体输出最终姿势

-------->>Animation Blueprint编辑器见后面Persona编辑器-->Blueprint

### Animation Montage/动画蒙太奇
动画蒙太奇（简称蒙太奇）是一种多功能工具，通过它可以实现多种动画效果，主要与公开代码或蓝图可视脚本中的动画控件相关。它也可用于创造各种动画效果，包括动画的智能循环，基于逻辑的动画切换等。可用来添加开火、瞄准等按下按键后切换到的动画

蒙太奇是可以创建并存在于内容浏览器中的动画资产。可在运行时将这些资产直接插入动画图中，并修改它的任何状态。例如可以跳转到不同片段，也可以重新链接不同的片段。这主要用于代码驱动的动画或一次性动画（例如近身攻击），可以通过动画蒙太奇控制触发器，在需要的时候停止，或者变换状态（循环或不循环）
如果动画启用了根运动，蒙太奇还提供了一种在互联的游戏之间复制根运动的方法
实际上就是对现有动画资源进行整理，方便使用 

注意：要在做好的状态机上添加蒙太奇，使用插槽

蒙太奇的部分其他用途包括：
1. 能够从动画蓝图的事件图中播放动画
2. 将复杂的一系列动画串联起来，让它们成为一个动画
3. 根据代码或蓝图脚本仅循环一个或多个动画中的特定部分
4. 根据代码或蓝图脚本处理多个动画的基于事件的切换
5. 能够将复杂的动画序列分配到可在代码或蓝图中切换的指定槽中
6. 根据代码或蓝图脚本在各种动画序列之间精确切换

制作开火特效
1. 新建AnimMontage对象，选择基础角色
2. 双击对象进入动画蓝图编辑器的动画编辑界面，在资源浏览器中选择开火动画，拖动到Montage的第二行
3. 点击Sections中Preview右侧的Default，再点击上面Preview上面的Default,此时Preview右侧的Default底色变成浅蓝色
4. 进入动画蓝图编辑器的蓝图编辑界面，在动画图表中添加插槽DefaultSlot节点，放置在最终动画姿势前，不做这一步最后不起效果
5. 在项目设置-->输入-->Bindings中添加一个Action Mappings，名称设为Fire，绑定鼠标左键
6. 在蓝图编辑器中的事件图表里，添加刚才绑定的输入节点Fire，添加一个Play Anim Montage节点和一个Stop Anim Montage节点，分别连接到输入节点Fire的Pressed输出端口和Released输出端口，Anim Montage都选择为刚才创建的动画蒙太奇

### Blend Space/混合空间
只有循环动画才能用混合空间制作，不然会出问题

用来创建两个动画中间的过渡，比如行走的轻微晃动到奔跑的快速晃动

Blendspaces(混合空间)是可以在AnimGraphs（动画图表）中进行采样的特殊资源，它可以基于两个输入值混合多个动画。基于一个输入值简单地混合两个动画可以使用动画蓝图内其中一个标准的混合节点来实现。混合空间提供了基于多个值(目前限定为2个值)对多个动画进行复杂混合的方法

混合空间的目的是减少创建一个独立的、硬编码的节点来执行基于多个特定属性或条件的混合的需要。通过允许动画师或程序员指定输入值、动画及如何使用输入值混合动画的方法，使得通过这个通用的混合空间几乎可以执行任何类型的动画混合

可以把混合空间想象成一个二维图表，其中每个输入值沿着一个坐标轴进行显示，动画散布在 图表上的各个位置点处。混合后的动画是通过基于当前输入值指定的位置 混合图表上的多个动画计算而来


制作两个动画之间的过渡动画的操作
1. 新建Blend Space对象，选择基础角色
2. 双击对象进入动画蓝图编辑器的动画编辑界面，在资源浏览器中选择两个动画分别拖动到时间线的开始点和结束点，在Axis Settings中设置参数
3. 进入动画蓝图编辑器的蓝图编辑界面，在资源管理器中找到混合空间资源，拖入动画图表，连接到Result
4. 在我的蓝图中新建Float类型的变量，拖入动画图表，连接到混合空间资源的输入端口
5. 进入事件图表，将创建的Float类型变量拖入事件图表，将事件Bliuprint Update Animation的箭头输出连接到Float类型变量的箭头输入
6. 添加Try Get Pawn Owner节点，读取蓝图角色信息
7. 连接一个Get Velocity节点，获取角色速度，这个节点输出的是Vector类型数据
8. 连接一个VectorLength节点，获取Get Velocity节点输出的Vector类型数据的向量长度，再输出到Float类型变量的输入端口


### Blend Space1D/混合空间1D
简化版的混合空间，将多个有共性参数的动画进行混合，自动生成中间的平滑混合过渡，例如从站立到行走到奔跑



## Persona编辑器
Persona是虚幻引擎中的一组动画编辑工具集。这是一个强大的系统，可用来编辑骨架，骨架网格体，动画蓝图以及多种其它动画资源。在虚幻引擎中，大部分（即时不是全部）动画处理工作都在这个编辑器中进行。这是一款多功能的工具，包含了用于编辑骨架插槽 、预览动画序列、设置动画混合空间以及蒙太奇、编辑动画蓝图等的面板
通过在内容浏览器中双击一个动画资源可以打开角色编辑器，比如双击以下这样的动画资源：
动画蓝图、骨架、骨架网格体、动画序列、混合空间、动画蒙太奇
### Skeleton/骨架模式
显示和修改模型全部的骨骼，骨架模式能够可视化的控制角色或者骨骼网格物体，包括控制单个骨骼或者关节继承关系。比如可以做的事情包括：
1. 在骨骼网格物体上新建插槽Socket用于外挂其他物体
2. 为每个插槽Socket编辑相对位置和相对角度
3. 建立动画数据和骨骼数据的绑定关系

在大部分3D应用程序中，骨架是一个数字化的层次架构，用于定义角色中的骨骼或关节，并且在很多方面都模仿真实的生物骨骼。一个主要的区别是骨架资源和骨架网格物体中的骨骼层次结构不是同一个东西。在UE4中，骨架资源不太像是实际骨架的三维呈现，更像是一个列表，存放了一种特定类型的角色或骨架网格物体的骨骼和层次结构信息。动画通过这个列表来进行关联。至于它在动画系统中的定位，最好把它想成处于骨架网格物体和动画之间的中间物。多个骨架网格物体可以使用同样的骨架资源，且任何使用相同骨架资源的网格物体都可以共享动画

关于骨架资源的基本知识：
1. 每个骨架网格物体需要一个相关的骨架资源
2. 可以在导入骨架网格物体时为它创建一个新的骨架资源，或者选择一个已有的骨架资源
3. 骨架的初始部分是由根据其创建该骨架的骨架网格物体定义的。当进行重定向时注意到这点是非常重要的
4. 要想共享动画，那么骨架网格物体必须使用同样的骨架资源
5. 共享同样的骨架资源要求不要破坏骨架网格物体中的骨骼层次结构的命名顺序

#### Toolbar/工具架
##### Retarget Manager/重定向管理器
可以将一个模型的骨骼赋予到另一个模型，从而可以将这个模型的动画蓝图迁移到另一个模型上，使其具有动画蓝图

动画重定向方法：
1. 分别进入两个模型的Skleton界面，点击Retarget Manager，将Set up Rig中的Select Rig选择为Humanoid,点击保存
2. 在内容浏览器中找到第一个模型的动画蓝图，点击右键Retarget Anim Blueprints,进入动画重定向界面
3. 选择目标模型，点击Retarget，会将第一个模型的动画蓝图全部重定向到第二个模型

### Mesh/网格模式
模型和材质编辑，能够对骨骼网格物体上的多面体模型做改动。比如可以做的事情包括：
1. 为骨骼网格物体设置材质
2. 添加布料元素
3. 对骨骼网格物体做 LOD 设置
4. 测试 Morph Target

### Animation/动画模式
动画编辑，能够为骨骼网格模型很容易的访问各类动画资源，包括动画序列，混合空间，动画蒙太奇。比如可以做的事情包括：
1. 预览动画资源（动画序列，混合空间，动画蒙太奇）
2. 对资源进行修改（混合空间，动画蒙太奇）
3. 为材质或者Morph Target的变化添加或编辑曲线
4. 新建或编辑动画通知（Animation Notification）

使用插槽给角色添加武器的操作
1. 在动画蓝图编辑器的动画编辑中切换到骨架树，找到拿武器的手的关节，右键添加插槽
2. 在生成的插槽上右键添加预览资源，将武器添加到插槽
3. 旋转插槽，让武器匹配手臂（注意这里只是预览）
4. 在骨架和动画中分别点击保存
5. 在蓝图编辑器的组件中添加SkeletalMesh组件，将SkeletalMesh组件作为Mesh组件的子物体
6. 在插槽选项的插槽-->父项插槽中选择设定的插槽，将位置和旋转归零

### BluePrints/动画蓝图模式
主要是用来创建并编辑动画蓝图，以及动画状态机。比如可以做的事情包括：
1. 设置并编辑动画蓝图
2. 新建并编辑状态机
3. 在动画蓝图的事件图中播放动画蒙太奇
4. 使用AnimGraph混合不同的姿势以及其他动画计算的结果数据

Controller（控制器）根据玩家输入或者基于游戏环境作出的决定指示其Pawn(或角色)进行移动。每个Pawn有一个骨骼网格物体组件(引用要产生动画的骨架网格物体)和一个动画蓝图实例。动画蓝图通过它的两个图表，可以访问它所具有的Pawn的属性，可以计算进行动画混合、状态变换或驱动动画蒙太奇所使用的值，可以根据动画序列的混合计算骨架网格物体的当前姿势、还可以通过骨架控制器指示骨骼进行变换

动画蓝图通过动画图表和事件图表两个图表，可以访问与它绑定的Pawn的属性，可以计算进行动画混合、状态变换或驱动动画蒙太奇所使用的值，可以根据动画序列的混合计算骨架网格物体的当前姿势、还可以通过骨架控制器指示骨骼_进行变换

在动画蓝图中，有两个主要部分相互协作来创建每帧的最终姿势。EventGraph(事件图表)可以更新值，然后可以在AnimGraph（动画图表）中使用这些值来驱动状态机、混合空间、可以混合多个动画序列的其他混合节点、或者驱动那些可以触发到其他系统的通知，从而发生动态动画效果的姿势

#### AnimGraph/动画图表
用于计算当前帧上骨架网格体的最终姿势。默认情况下，每个动画蓝图有一个动画图表，在该动画图表内可以放置动画节点，以便对动画序列进行采样、执行动画混合或者通过使用骨架控制器来控制骨骼变换。然后,在每帧中将最终的姿势应用到骨架网格物体上

**动画图表中只能调用纯函数**

动画图表中只Get变量，不要Set，否则会出现线程安全警告，因为UE4为了场景和渲染的流畅性，默认将与渲染直接没有关联的操作放在独立的工作子线程中。例如：Animation Blueprint（动画蓝图）中的：动画更新、混合、蒙太奇以及其他资源更新放到工作线程（worker thread）。如果在子线程中调用渲染线程的对象等数据，就会有线程不安全问题

解决办法：
- 方法1：关闭UE4默认的优化
ClassSettings ——> Optimization ——>Use Multi Threaded Animation Up勾选取消,再编译
- 方法2: 使用线程安全的调用
基本类型的变量可以认为是线程安全的
将先前不安全的数据获取分解为：在渲染线程（Event Graph）中对变量进行set操作，在工作子线程中进行get操作
#### State Machine/状态机
状态是承载动画的载体，在状态机中可以设置角色的多种状态，如站立、奔跑、跳跃、攻击，并设置状态切换的条件
#### Slot/插槽
可以理解为一种标签，为动画蒙太奇等动画资源准备的，UE在状态机输出角色姿态之前，会先检查插槽中有没有绑定的蒙太奇动画，如果有，就执行，作用就是把动画蒙太奇等动画资源绑定到动画蓝图上

#### 特有节点
##### Asset（角色蓝图名）
- Current Time(状态机绑定的动画资源名)/当前时间
动画当前运行时间
- Current Time(ratio)(状态机绑定的动画资源名)/当前时间（比率）
动画当前运行的比率
- Length(状态机绑定的动画资源名)/长度
动画长度
- Time Remaining(状态机绑定的动画资源名)/剩余时间
动画剩余播放时间
- Time Remaining(Ratio)(状态机绑定的动画资源名)/剩余时间（比率）
动画剩余播放的比率
##### Blends
- Apply Additive/应用添加
可以用这个节点把状态机和混合空间混合叠加
- Blend Poses by in/通过一个整数混合
相当于Switch，Index为0，播放第一个动画，Index为1，播放第二个动画。例如：两个不同的武器，Idle动画不同，可以使用这个节点，通过Index来切换Idle动画

注意，它只支持需要循环播放的动画，如果不是需要循环播放，如换子弹等，使用这个节点混合，动画会出现多余动作

#### EventGraph/事件图表
每个动画蓝图有一个单独的事件图表，且该事件图表是个标准的图表，它使用了一组动画相关的专用事件来初始化节点序列。事件图表的最常见用途是更新混合空间和其他混合节点使用的值来驱动动画图表中的动画

注意动画蓝图资源不能拖到场景中，只要和角色蓝图绑定之后，不管角色是否已经实例化，动画蓝图中的事件是一定会运行的，所以一般要加一个Is Valid来判断角色是否实例化真实存在，再执行

动画蓝图大部分节点与Pawn蓝图相同
#### 特有节点
##### Add Anim Notify Event/动画通知时间
在动画资源中，时间线上可以添加通知标记，动画资源与动画蓝图绑定后，可以在动画蓝图中调用，即当动画播放到通知标记处时，触发的事件
##### Add Event
- Event Blueprint Begin Play/蓝图开始运行事件
- Event Blueprint Update Animation/蓝图更新动画事件

### Physics/物理模式
查看和编辑角色的碰撞盒