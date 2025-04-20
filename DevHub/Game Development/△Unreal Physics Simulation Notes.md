# Apex Destruction/Apex破坏模拟
开启方式-->在插件中查找Apex Destruction并勾选Enable

## 破碎效果使用方法
- 第1步：在Content Browser中导入要破碎的资产；
- 第2步：右键选择Create Destructible Mesh创建Apex Destruction资产；
- 第3步：双击打开创建的Apex Destruction资产，进入Apex Destruction编辑器界面；
- 第4步：设置破碎参数，然后点击Fracture Mesh生成破碎。

## Apex Destruction编辑器
### Toolbar/工具栏
#### Fracture Mesh/破碎网格
将模型生成破碎的网格体
#### Import FBX Chunks/导入FBX碎块
将碎块形态在三维软件中制作好，把未破碎的形态导入虚幻的Content Browser，创建Apex Destruction资产，使用Import FBX Chunks导入破碎形态，这样破碎的效果更好更可控
#### Preview Depth X/预览深度
预览X层深度的破碎效果
### Fracture Settings/碎片设置
#### Voronoi
- Cell Site Count------------------破裂碎片数量
#### General
- Fracture Material Desc-----------碎片材质描述
### Destructible Settings/可破坏设置
控制在场景中如子弹击中、碰撞等交互的破坏
#### Damage/破坏
- Damage Threshold-----------------破坏阈值
- Damage Spread--------------------破坏传递
- Enable Impact Damage-------------影响碰撞
- Impact Damage--------------------影响碰撞强度
- Default Impact Damage Depth------默认影响碰撞深度
- Custom Impact Resistance---------自定义碰撞抵抗
- Impact Resistance----------------碰撞抵抗强度
- ---->>>
- Damage Cap-----------------------碰撞帽
#### Debris/碎片
- Debris Lifetime Min--------------碎片最小生命值
- Debris Lifetime Max--------------碎片最大生命值
- Debris Max Separation Min--------
- Debris Min Separation Max--------
#### Flags/
- Accumulate Damage----------------累计伤害
- Asset Defined Support------------资产定义支持
- World Support--------------------世界支持
- Debris Timeout-------------------碎片超时
#### Hierarchy Depth/层级深度
#### Effects/特效
用来添加破碎时的交互特效，如击中墙壁的爆炸特效和声效

# 布料
## 布料流程
以制作迎风飘扬的旗帜为例
- 第1步：在三维软件中制作旗杆和旗面，分别赋予材质，旗面要有足够的细分；
- 第2步：将旗杆和旗面转为可编辑对象，并合并成一个模型；
- 第3步：创建关节，一个在旗杆底部，一个在旗杆顶部（虚幻中制作布料，导入的模型必须是Skeletal Mesh）；
- 第4步：给合并后的模型添加蒙皮；
- 第5步：导出为Fbx格式模型，在虚幻的Content Browser中导入模型，导入时勾选Skeletal Mesh；
- 第6步：调整材质，旗面要勾选双面材质；
- 第7步：打开PhysicsAsset,进入Physics页面，调整碰撞体大小，使其包裹旗杆；
- 第8步：进入Mesh页面，打开Window中的Clothing；
- 第9步：点击ToolBar中的Section Selection，选择旗面，右键点击Create Colthing Data from Section,设置布料名称，选择资产，点击Create创建布料；
- 第10步：选择旗面，右键点击Apply Clothing Data,选择刚才创建的布料应用；
- 第11步：点击ToolBar中的Deactivate Cloth Paint，调整笔刷大小，对旗面进行权重绘制，白色为100%，红色为0%，旗面绘制为100%，固定到旗杆上的部分绘制为0%，中间绘制好过渡部分；
- 第12步：将PhysicsAsset放置到场景中，取消Simulate Physics勾选，使其不受动力学影响；
第13步：放置风场使旗面飘动。

## Mesh编辑器
## Clothing
#### Config
- Cloth Configs
  - Cloth Config
    - Clothing Wind Method-------------风对布料的影响方式，决定如何处理风，精确调节阻力和升力来让布料做出不同的反应。旧有系统使用类似的力作用于所有布料上，但没有阻力和升力（类似APEX），一般保持默认的Legacy
      - Legacy-------------------------旧版，使用旧版风模式，将通过模拟直接修改加速度值，无视阻力或升力
    - Vertical Constraint--------------垂直方向约束，用来限制布料垂直方向状态和运动等
      - Stiffness------------------------刚度，控制布料的硬度，此属性值影响与目标位置的接近度
      - Stiffness Multiplier-------------刚度乘数，影响所使用刚度值的乘数
      - Stretch Limit--------------------拉伸限制，有关此约束伸展距离的硬性限制
      - Compression Limit----------------压缩限制，有关此约束压缩距离的硬性限制
    - Horizontal Constraint------------水平方向约束，用来限制布料水平方向状态和运动等
    - Bend Constraint------------------弯曲约束，控制布料产生褶皱的强度和状态
    - Shear Constraint-----------------剪切变形约束
    - Self Collision Radius------------自碰撞半径，以每个顶点为中心的自碰撞球体的大小
    - Self Collision Stiffness---------自碰撞刚度，用于解算自碰撞的弹簧力的刚度
    - Self Collision Cull Scale--------自碰撞剔除状态，自碰撞剔除检测所用的半径比例。在此检测半径内的任何其他自碰撞体都将被剔除。此属性通过降低布料中的碰撞体数量来提升高分辨率网格体的性能。降低该值将对性能带来负面影响
    - Damping--------------------------阻尼，每轴向上粒子运动的衰减值
    - Friction-------------------------摩擦力，碰撞时的表面摩擦力
    - Wind Drag Coefficient------------风阻系数，用于风计算风的阻力系数，值越高意味着风对布料产生的侧向效果越明显，可以控制角色走路停止后衣服摆动的时间，数值越大，衣服停止摆动的越快
    - Wind Lift Coefficient------------风升系数，数值越大，风对布料的升力越大，布料越容易在风中上扬
    - Linear Drag----------------------线性阻力，应用到每轴向上线性粒子运动上的阻力
    - Angular Drag---------------------角阻力，粒子角运动的阻力，值越大，则材质越不容易弯曲（每轴向）
    - Linear Inertia Scale-------------线性惯性比例，线性粒子惯性的比例值，或者说有多少运动应该转化为线性运动（每轴向）
    - Angular Inertia Scale------------角度惯性比例，角粒子惯性的比例值，或者说多少运动应该转化为角向运动（每轴向）
    - Centrifugal Inertia Scale--------离心惯性比例，离心粒子惯性的比例值，或者说多少运动应转化为离心运动（每轴向）
    - Solver Frequency-----------------解算器频率，位置解算器的频率，值越低，则布料越容易伸展和活动
    - Stiffness Frequency--------------刚性频率，刚度计算的频率，值越低，则越容易降低约束的刚度
    - Gravity Scale--------------------重力强度，布料粒子模拟重力效果的比例值
    - Tether Stiffness-----------------系链刚度，点彼此之间的系链刚度比例值
    - Tether Limit---------------------系链限制，粒子系链限制比例值（点的最远分离距离）
    - Collision Limit------------------碰撞限制，所模拟布料的“厚度”，控制布料与其他对象碰撞的限制，数值大可能会有穿插
    - Anim Drive Spring Thickness------动画驱动弹簧厚度，使用动画驱动后，默认的弹簧厚度
    - Anim Drive Damper Thickness------动画驱动阻尼厚度，使用动画驱动后，默认的阻尼厚度

