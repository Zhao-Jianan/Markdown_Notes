# TurbulenceFD
## 特点
1. TFD是一款流体模拟插件，常用来制作烟雾、火焰类效果，不能用来模拟水、牛奶等液体效果
2. 可控性不方便，不支持C4D的各种力场
3. 和X-particle配合很好，粒子驱动就是“力”

## 插件
### TurbulenceFD Container/TFD容器
限制TFD的计算范围，超出范围不再计算
#### Container/容器
- Resolution----------------解析度
  - Voxel---------------------像素尺寸，值越大，分辨率越低，模拟速度越快
  - Grid Size-----------------网格大小，控制范围框的大小
- Cache/缓存
  - Simulation Caches---------模拟缓存位置，需要给缓存指定一个文件位置，默认为C盘
  - Cathe Temperature---------缓存温度
  - Cathe Velocity------------缓存速度，非常重要，如果不缓存速度，就无法使用粒子来驱动TFD
  - Cathe Collision-----------缓存碰撞，用的很少，一般不勾选
#### Simulation/模拟
##### Solver/解算
- Frame Sub-Steps Limit-----帧步幅限制，如果发射流体的物体运动速度很快，就需要增大这个参数，但是会降低模拟速度
- Pressure Iteration Limit--压力迭代限制，当速度使流体变形时，压力就会增大。平衡这一压力是模拟的一个基本部分。参数数值越大，模拟速度越慢。


对于具有高速或碰撞对象或封闭容器边界的模拟，一般使用介于2和10之间的值。通常不需要大于10的值。对于没有碰撞且速度通常为中等的模拟，一般使用1
- Adaptive Container--------自适应容器，如果启用，TFD将模拟容器的最小可能部分，以节省时间和内存。在速度、温度、密度、燃料和燃烧选项卡中，下行修剪参数控制TFD可能收缩容器的时间

一般都会勾选

- Advection-----------------平流，平流精度影响流体细节的清晰度，一般默认即可
  - Velocity Advection--------平流速度
    - 1st Order-----------------第一阶，流体细节会产生一些模糊的结果，涡流会更快地平滑，结算速度快，使用内存少
    - 2nd Order-----------------第二阶，流体细节会更清晰，涡流会存在更长的时间，但是结算速度慢，使用内存多
  - Channel Advection---------平流通道
    - 1st Order-----------------第一阶，流体细节会产生一些模糊的结果，涡流会更快地平滑，结算速度快，使用内存少
    - 2nd Order-----------------第二阶，流体细节会更清晰，涡流会存在更长的时间，但是结算速度慢，使用内存多
  - Adaptive Tracer-----------自适应追踪
  - Cubic Interpolation-------立方插值
- Closed container boundaries------封闭容器边界，有时会用到，勾选后会封边勾选方向的容器边界，流体到容器边界后不是消失而是产生碰撞	
##### Up-Res'ing/二次解算，让模拟的精度更高
- Up-Res Scale--------------二次结算尺寸，在使用Up-Res模式模拟时，这个参数控制模拟精度，数值越大，精度越高，模拟速度越慢
##### Timing/时间，非常重要
- Time Scale----------------时间比例，控制动画的速度，可以K关键帧，让火焰、烟雾的速度有变化
##### Velocity/速度，非常重要，在这里控制让流体驱动粒子
- Clip Below----------------下行修剪，流体低于下行修剪的速度的地方将不会影响粒子
- Damp Velocity-------------空气阻力
- Particle Velocity Scale---粒子速度比例，如果为0，则流体不会影响粒子，100%会完全影响粒子

*一般使用TFD流体驱动粒子时，勾选缓存速度，将下行修剪设为0或1，粒子速度比例设为100%，进行缓存，然后添加粒子发射器*

**TFD对驱动粒子时，本质上TFD是一个力，但是一旦使用了TFD，XP粒子带的力场就都会失效，C4D自带的力场不会失效，可以使用C4D自带的力场叠加，这一点非常重要，但是仅限于XP2.1版本，因为XP4.0版本不支持C4D自带的力场，因此XP4.0中任何力场也无法与TFD叠加**

##### Wind/风
- Wind Direction------------风向
- Wind Speed----------------风速
##### Vorticity/涡度
- Vorticity-----------------涡度,开启后流体会打卷，可以增加流体细节
##### Turbulence/湍流
让流体有躁动，增加细节
- Tub.intensity-------------湍流强度
- Smallest Size-------------湍流最小尺寸
- Largest Size--------------湍流最大尺寸
##### Temperature/温度
- Active--------------------激活温度
- Clip Below----------------下行修剪，当温度低于这里的数值时就消失，一般默认即可
- Temp.Diffusion------------温度漫射，可以理解为给温度加了个高斯模糊，在模拟蜡烛灯特殊火焰时需要用到
- Cooling-------------------冷却，温度会随时间逐渐冷却，这里控制单位时间温度下降百分比
- Half-Life-----------------半衰期，火焰消失一半的时间
- Buoyancy------------------浮力，让流体会上升
- Buoyancy Direction--------浮力方向，默认为Y+方向
##### Density/密度
- Active--------------------激活密度
- Clip Below----------------下行修剪，当密度低于这里的数值时就消失，一般默认即可
- Dens.Diffusion------------密度漫射，可以理解为给密度加了个高斯模糊
- Dissipation---------------消散，密度会随时间逐渐消散，这里控制单位时间密度下降百分比
- Half-Life-----------------半衰期，火焰消失一半的时间
- Gravity-------------------重力，让流体会下降
- Buoyancy Direction--------重力方向，默认为Y-方向

**如果温度和密度通道同时勾选，重力会和浮力共同作用于流体**
##### Fuel/燃料
燃料通道可以理解为对象是汽油或柴火等燃料，被点燃之后开始燃烧
- Active--------------------激活燃料
- Clip Below----------------下行修剪，当燃料低于这里的数值时就消失，一般默认即可
- Fuel Diffusion------------燃料漫射，可以理解为给燃料加了个高斯模糊
- Burn Rate-----------------燃烧率，燃料有多少能被燃烧，如果燃烧率很低，燃料会烧的不旺盛
- Fuel Mask Channel---------燃料蒙版通道，控制什么时候燃料开始燃烧
  - None----------------------燃料一开始就燃烧
  - Temperature---------------温度，燃料所在位置温度达到燃点开始燃烧
- Fuel Mask Smoothing-------燃料蒙版平滑，数值越大，燃点越低，越容易点燃
- Fuel Mask Mapping---------燃料蒙版映射，控制燃料蒙版的燃烧
- Exoansion-----------------扩散，燃料会扩散，好像爆炸一样
- Temp.Emission-------------温度发射，控制燃料燃烧时释放多少热量，影响燃料别的位置能否被点燃和点燃的速度，如果温度发射为0，燃料燃烧时不产生热量，就不会漫延的燃烧和持续的燃烧
- Density Emission----------密度发射，控制燃料燃烧时释放多少密度
##### Burn/燃烧
燃烧通道与温度通道类似，但是还是有很多不同，燃烧通道燃烧比较安静，一般用来模拟蜡烛等非常小的火焰

**燃烧通道没有浮力，燃烧时火焰不会向上，可以激活密度通道，在密度通道中使用重力控制**

- Active--------------------激活燃烧
- Clip Below----------------下行修剪，当燃烧低于这里的数值时就消失，一般默认即可
- Fuel Diffusion------------燃烧漫射，可以理解为给燃烧加了个高斯模糊
- Decay Mode----------------衰减模式，燃烧默认会有衰减

#### Viewport Preview/视窗预览
控制预览窗口的显示状态
- Channel-------------------选择预览窗口显示的通道

#### Rendering/渲染
##### General/一般设置
- Frame Offset--------------帧偏移，可以让调节帧偏移，让当前帧显示为第几帧
- Frame Step----------------帧步幅，控制动画速率，帧步幅为0时为静帧，帧步幅为1时是正常的模拟速率
- Step Size-----------------步幅尺寸，值越大，渲染速度越快，噪点越多，值越小，渲染速度越慢，噪点越少
- Shadow Step Size----------阴影步幅尺寸，值越大，渲染速度越快，阴影噪点越多，值越小，渲染速度越慢，阴影噪点越少
- Interpolation-------------插值
  - Fast----------------------快速，速度最快，但质量较低
  - Smooth--------------------平滑，流体有些地方比较模糊，整体很平滑
  - Sharp---------------------锐利，流体很锐利，像添加了锐化效果
- Use Distance/Opacity Mapping--使用距离/不透明度映射，根据流体距离摄像机的距离来映射它的不透明度，距离摄像机很近的流体会变得很透，制作云层穿梭时会用到
##### Smoke Shader/烟雾着色器
- Mapping-------------------映射
  - Channel-------------------通道，一般烟雾来自密度通道
  - Smoke Smoothing-----------烟雾平滑，用来对烟雾进行模糊，基本不使用，如果需要模糊，一般在后期中进行
  - Mapping-------------------映射，很重要，映射图横轴从左向右是流体最薄的地方到最厚的地方，纵轴是不透明度从0到1

**一个小技巧是把最左边透明度为0的端点稍微向右移动一点点，渲染结果和原来没有区别，但是渲染速度会加快很多**

- Separate Opacity----------分离不透明度，不常用
  - Channel-------------------通道，可以选择一个通道来和上面的映射共同影响不透明度
- Color&Opacity-------------颜色和不透明度
  - Thickness-----------------烟雾厚度，厚度值越小，烟雾越透
  - Brightness----------------烟雾亮度
  - Smoke Color---------------烟雾颜色，烟雾的密度越大，显示越靠右边的颜色，烟雾密度越小，显示越靠左边的颜色
- Sub-Grid Detail-----------子网格细节，非常重要，给烟雾添加细节
  - Velocity Displacement-----置换速度，非常重要，对速度通道进行置换，让烟雾有更多细节，需要勾选缓存速度，否则没有效果
  - Noise Intensity-----------燥波强度，给烟雾添加细节
  - Smallest Size-------------燥波最小尺寸，调节燥波的细节
  - Largest Size--------------燥波最大尺寸，调节燥波的细节
- Illumination--------------全局光照
  - Illumination--------------全局光类型
    - None----------------------没有全局光，烟雾没有投影，不常用
    - Voxelized Fast------------快速像素化，最常用，速度和质量综合起来最好的方式
    - Voxelized Smooth----------平滑像素化
    - Accurate------------------精确的
  - Multiple Scattering-------多重散射，让火焰可以照亮烟雾


##### Fire Shader/火焰着色器
- Mapping-------------------映射
  - Channel-------------------通道，一般火焰来自温度通道
  - Fire Smoothing------------火焰平滑，用来对火焰进行模糊，基本不使用，如果需要模糊，一般在后期中进行
  - Clear Smoke If Above------温度高于多少的地方不显示烟雾
- Separate Opacity----------分离不透明度，不常用
  - Channel-------------------通道，可以选择一个通道来和上面的映射共同影响不透明度
- Color---------------------颜色
  - Opacity-------------------不透明度，数值越大，火焰越透
  - Color Mode----------------颜色模式
    - Black Body----------------黑体着色，自动颜色
      - Low Temp------------------低温，温度越低，越趋近于黑色
      - High Temp-----------------高温，温度越高，越趋近于白色
      - White Point---------------白点，控制火焰整体对比度
      - Damping-------------------阻力，相当于热量衰减，数值越大，火焰亮度越小
    - Manual--------------------手动着色
  - Sub-Grid Detail-----------子网格细节，非常重要，给火焰添加细节
    - Velocity Displacement-----置换速度，非常重要，对速度通道进行置换，让火焰有更多细节，需要勾选缓存速度，否则没有效果
    - Noise Intensity-----------燥波强度，给火焰添加细节
    - Smallest Size-------------燥波最小尺寸，调节火焰的细节
    - Largest Size--------------燥波最大尺寸，调节火焰的细节


### Simulation Widows/模拟视窗
用来进行模拟计算，注意TFD必须先进行模拟，然后才能在时间轴播放
- 模拟方式
  - Cache---------------------模拟数据到缓存文件
  - Interactive---------------交互式模拟，这种方式不会生成缓存文件，但是调节参数时，会实时显示和改变当前效果，方便参数调节
  - Up-Res--------------------基于当前的缓存增加细节。会提高模拟的细节，需要有缓存文件，且缓存文件有速度通道才能进行模拟
- Render when finished------模拟结束后渲染，功能很实用，设置好渲染参数，TFD在模拟结束后会直接自动开始渲染
- Update Editor Time-line---更新预览视窗时间线，开启后在模拟时预览视窗会实时显示，如果模拟速度太慢可以关闭这个选项节省系统资源

### Start Interactive Simulation/开启交互式模拟
开启后时间轴保持不动，流体会一直模拟，主要用来进行作用力交互的模拟


### Preview Fluid Container/预览流体容器
类似一个IPR窗口，可以实时预览渲染效果


## 标签
### TurbulenceFD Emitter/发射器标签
*一般粒子驱动流体时，给粒子发射器添加TFD发射器标签*

- Emitter Active------------激活发射器
- General-------------------通用设定
  - Radius--------------------半径
  - Collision Object----------碰撞对象，开启后流体可以跟对象产生碰撞，有更多细节，但解算会变慢，如果要和一个对象碰撞，那个对象也要添加发射器标签，勾选碰撞
  - Fill Object---------------填充对象，开启后流体会填充到对象内部，如果要使用对象选集来发射流体，要取消填充对象勾选
  - Restrict to polygon selections--限制为多边形选集，只有选集发射流体
- Texture-------------------基于纹理发射流体
  - Volume Texture------------基于体积纹理，使用这种方式可以勾选Fill Object/填充对象，但这种方式不如Surface Texture Channel直观
  - Surface Texture Channel---基于表面纹理通道，需要给发射器对象一个材质，在纹理通道里加载黑白贴图或黑白贴图序列，在这里选择对应的纹理通道，就会只在白色区域发射流体。

**这里要注意，发射器对象必须转化为可编辑对象才能基于纹理发射，并且不能勾选Fill Object/填充对象，否则不起作用**

- Use Vertex Maps-----------使用顶点贴图，非常重要，基于对象的顶点贴图进行发射，可以使用碰撞变形器配合张力标签制作碰撞交互生成流体的效果。还可以使用XP4.0版本的基于速度的动态顶点贴图，XP2.1可以使用NitroVertex插件的动态顶点贴图，来实现动态交互生成流体，进而驱动粒子。XP4.0发射器选集支持顶点贴图，可以直接将顶点贴图拖入，XP2.1发射器选集不支持顶点贴图，但支持纹理贴图，可以添加材质，使用效果中的顶点贴图，然后烘焙纹理，再导入烘焙后的黑白纹理序列，实现顶点贴图驱动动态交互

- Particle emission intensity--粒子发射强度
  - Particle property---------粒子属性，用来将流体发射强度和粒子属性关联起来
  - Intensity-----------------强度
- Force---------------------力
TFD不支持C4D自带的各种力场，但是可以通过这里的参数近似地模拟力场作用
  - Velocity Weight-----------速度权重,可以理解为粒子对于流体的碰撞，数值比较敏感
**如果使用粒子碰撞产生流体，需要开启速度权重**
  - Normal Force--------------法线力，让流体在基于发射器对象的法线方向有一个力
  - Directional Force---------方向力
  - Pressure------------------压力，对流体产生排斥的力，如果为负值，就是引力

- Channels------------------通道
  - Temperature Emission Mode-温度发射模式
    - Set-----------------------设置，温度为固定值
    - Add-----------------------相加，越燃烧温度越高
  - Temperature Value---------温度值，TFD需要有温度值才能点燃火焰，才能有效果，流体碰撞对象不需要有温度值
**温度越低，浮力越小，上升越慢**
  - Density Emission Mode-----密度发射模式
    - Set-----------------------设置，密度为固定值
    - Add-----------------------相加，密度越来越高
  - Density Value-------------密度值，TFD需要有密度值才能模拟烟雾，才能有效果
  - Fuel Emission Mode--------燃料发射模式
    - Set-----------------------设置，燃料为固定值
    - Add-----------------------相加，燃料越来越多
  - Fuel Value----------------燃料值
  - Burn Emission Mode--------燃烧发射模式
    - Set-----------------------设置，燃烧为固定值
    - Add-----------------------相加，燃烧越来越多
  - Burn Value----------------燃烧值

# X-Particles
## 插件
### System/系统

### Emitter/发射器
#### 对象
控制发射器的参数
- Emitter Parameters
  - Draw Emitter--------------显示发射器范围框
  - Emitter Shape-------------发射器形状
    - Rectangle-----------------矩形
      - Emitter Plane---------------发射方向
      - Width-----------------------发射器宽度
      - Height----------------------发射器高度
      - H Angle---------------------水平发射角度
      - V Angle---------------------垂直发射角度
      - 3D--------------------------勾选后发射器变为立方体
      - Emitter Length--------------3D发射器长度
      - Offset X&Y------------------如果不勾选，只有发射器最中间的一个点发射粒子
      - Offset Origin---------------Z轴偏移
    - Circle--------------------圆形
      - Disc Radius-----------------发射器半径
      - Cone Angle------------------锥形发射角度
      - Ring Only-------------------勾选后，只有圆形边缘发射粒子
      - Variation-------------------边缘发射粒子的角度
    - Sphere--------------------球体
      - Offset Origin---------------发射原点偏移
      - Radius----------------------发射器半径
      - Direction-------------------发射方向
    - Object--------------------对象
      - Object----------------------将模型拖入
**如果需要多个完全相同的发射器，一个个控制和调整参数太繁琐，可以创建多个平面或其他对象，对这些对象添加连接，再把连接拖入这里，非常实用**
    - Selection-------------------将模型选集拖入
    - Emit From-------------------发射来自
      - Polygon Centre--------------多边形中心
      - Polygon Area----------------多边形区域
      - Points----------------------多边形顶点
      - Edges-----------------------多边形边
      - Object Position-------------对象位置
      - Object Volume---------------对象体积（对象内部发射）
      - Voxel Grid------------------铁丝网格，也是对象体积发射，但是粒子位置很规整
    - Particle Direction----------粒子发射方向
      - Phong Normal----------------表面法线方向，是视觉上的法线方向，受平滑着色标签影响，绝大多数情况下都使用Phong Normal，而不是用Normal
      - Normal----------------------真正法线方向，方向是模型表面的面的真正的法线方向，不受平滑着色标签影响
    - Emit from Alternate Source--
    - Use Child Objects-----------使用子物体
    - Stick Particle to Source Object--粒子发射后粘在模型表面
    - Emit One Particle Per Point-每个点发射一个粒子
    - Texture Use-----------------使用对象的纹理来控制粒子，注意纹理可以使用贴图序列，来制作创意效果
      - Texture Tag-----------------将对象的纹理标签拖入
      - Emit Chanel-----------------基于纹理的什么通道发射
      - Color Channel---------------粒子颜色基于什么通道，当纹理是贴图序列时粒子颜色必须和Emit Chanel一致，否则粒子没有出声的过程，
      - Threshold-------------------临界值，默认为白色，一般使用时改成黑色
      - Mode------------------------发射模式
        - Texture Color>=Threshold--如果纹理颜色值大于临界值，就发射粒子，注意一般要将临界值改为黑色

- HUD Display
  - Show HUD--------------------激活HUD
  - Show Particle Index---------显示粒子ID，注意激活后会非常卡
  - Text Color------------------HUD字体颜色
  - Background Color------------HUD背景颜色
  - Opacity---------------------HUD透明度
  - X Position------------------HUD位置偏移
- Commands
  - Save Options----------------存储当前发射器设置
  - Reset Options to Default----恢复默认设置

#### Emission
- Max.Particles---------------最大粒子数，最大支持10亿
- Count from Object-----------将对象拖入，对象有多少个点，最大粒子数就是多少
- Emission Mode---------------发射模式
  - Rate------------------------速度模式
  - Pulse-----------------------脉冲模式
  - Trigger---------------------触发模式
- Length(F)-------------------一次发射时长（脉冲模式使用）
- Interval(F)-----------------发射间隔时间（脉冲模式使用）
- Emit all Frames-------------所有帧都发射
- Start Emit(F)---------------开始发射
- End Emit(F)-----------------结束发射
- Full Lifespan---------------勾选后粒子始终存活
- Lifespan--------------------粒子生命
- Variation-------------------生命变化
- No Intersection-------------勾选后粒子无交叉，勾选后粒子没有穿插，但是会变得稀疏
- Radius----------------------粒子距离，控制粒子之间距离，勾选粒子无交叉后才起作用
- Speed-----------------------粒子速度
- Variation-------------------速度变化
- Radius----------------------粒子半径，默认状态无效果，因为粒子显示为点，可以在Display中让它显示为圆，在使用Generator基于粒子生成模型时可以控制大小
- Variation-------------------粒子半径变化
- Mass------------------------粒子质量（与动力学相关）
- Variation-------------------质量变化
- Birthrate-------------------发射速率，控制粒子密度，最大粒子数控制发射的总粒子数，粒子出生率越大，粒子越快发射完，粒子发射完后就不再发射
- Variation-------------------发射速率变化
- Groups
如果把粒子看做学生，发射器整个是学校，组就相当于一个个班级，可以分别赋予力场，也可以分别使用生成器
  - Groups to Use---------------用来将粒子分组
  - Mode------------------------分组模式
  - Creat and Add Group---------创建组

#### Display
控制预览窗口粒子状态，不影响最后渲染结果
- Show Particles--------------显示粒子
- Display Constraints---------显示动力学约束
- Fast Mode-------------------快速模式
- Editor Display--------------粒子显示模式
- Use Gradient----------------使用渐变来映射粒子的某种信息（很重要）
- Mode------------------------选择要映射的粒子信息

#### Collisions
控制粒子与对象的碰撞和粒子之间的碰撞
- Collisions with Scene Objects--粒子与对象碰撞
  - Enable Collisions--------------激活粒子与对象碰撞
- Particle-Particle Collisions---粒子之间碰撞（不常用）
  - Enable Particle Collisions-----激活粒子碰撞
  - Enable Self Collisions---------激活同一发射器发射的粒子间的碰撞
  - With---------------------------不同发射器间粒子碰撞把发射器拖入这里
  - Bounce-------------------------反弹力
  - Friction-----------------------摩擦力
  - Scatter------------------------散布
  - Spawn on Collision-------------碰撞产卵
  - Spawning Emitter---------------拖入产卵发射器
  - Number to Spawn----------------产卵数
  - Group--------------------------拖入粒子组
  - Spawn Once Only----------------只产卵一次
  - Kill Particles on Collision----碰撞产卵后杀掉源粒子

#### Dynamics/动力学
- Time Steps------------------计算精度，每帧计算多少次
- Fluids----------------------流体，XP高版本的流体动力学值得研究，2.1版本的流体动力学效果太差，很少用
  - Enable Fluids---------------激活流体，激活后粒子之间会有作用力，变现为粒子形态像液体一样
  - Density---------------------密度，1000为水的密度，密度越小，粒子越扩散，越趋近于空气
  - Viscosity-------------------黏性
  - Tension---------------------表面张力
  - Sources---------------------将另一个发射器拖进来，两个发射器流体可以产生碰撞等交互
  - Advanced--------------------高级选项
    - Smooth Radius---------------平滑半径，参数越大，粒子之间的吸附力越强
    - Stiffness-------------------硬度
    - Iterations------------------迭代次数
    - Max N'bors------------------一个粒子最大能和多少粒子产生相互作用力
- Constraints-----------------约束，相当于在粒子之间加了弹簧，互相都有力约束
  - Enable Constraints----------激活约束
  - Collider Forces-------------碰撞力
  - Connect at Birth------------出生时就有约束
    - Only Born-------------------仅出生时有约束
    - Only Same Group-------------仅相同组粒子有约束
    - Connection Limit------------连接限制，限定每个约束绑定几个粒子
    - Radius----------------------半径，以半径为多少内都产生约束，半径如果太小，约束就没有什么意义了
    - Stiffness-------------------硬度
    - Break-----------------------硬度超过多少时断裂
  - Connect on Collision--------碰撞时产生约束
  - Connect Within Distance-----根据距离产生约束
  - Particle Forces-------------粒子之间的作用力，调节吸引力和排斥力，配合粒子半径，会得到吹泡泡等效果
    - Attraction------------------吸引力
    - Radius----------------------吸引力半径，增加吸引力半径可以制作吐泡泡效果
    - Repulsion-------------------排斥力
    - Radius----------------------排斥力半径
  - Iterations------------------迭代，数值越大，精度越高，渲染速度越慢

#### Questions/问题
让粒子满足在一定条件后执行某些动作，与Action配合使用，点击Add Question后生成Question对象，设置Action的发生条件，具体参数见Question对象

#### Modifiers/修改器
用来排除或包括各种力场、变形器、效果器
**注意使用TFD来驱动粒子时，本质上X-Particles是把TFD当成了力，可以进行包括或排除**
- Particle Modifiers----------将力场拖入来进行包括或排除
- Deformers/Effectors---------将变形器或效果器拖入来进行包括或排除
**注意X-Particles的粒子可以受C4D自带的变形器和效果器影响,有些效果搭配起来效果很好**

#### Editing/编辑
- Editable--------------------勾选后，可以在点模式下框选粒子来移动旋转缩放，会自动记录点级别动画关键帧，还可以删除框选的粒子
- Range-----------------------如果对粒子进行了移动旋转缩放，这里设置粒子从初始状态到移动旋转缩放后的状态的动画时长
- Blend-----------------------曲线控制从初始状态到移动旋转缩放后的状态的动画曲线

#### Advanced/高级
- Random Seed-----------------随机种子



### Generator/生成器
通过粒子转化为模型，与默认粒子的显示对象功能类似，使用时将模型作为Generator的子物体

### Skinner/包裹
将粒子形态直接包裹转化为模型
#### 对象
- Surface
  - Surface---------------------表面算法
  - Surface Level---------------包裹强度
  - Polygon Size----------------多边形尺寸，尺寸越小精度越大
  - Render Polygon Size---------渲染多边形尺寸
- Sources
  - Objects---------------------拖入发射器

### Sprites/精灵

### Trail/路径追踪
与运动图形中的路径追踪类似
- Emitter---------------------将发射器拖入
- Algorithm-------------------算法，相当于路径追踪的模式
#### No Connections/不连接
粒子之间不连接，只跟踪粒子运动的路径
- Trail Length(Frames)--------追踪长度
- Variation-------------------变化
- Frame Sampling--------------帧采样
#### Straight Sequence/直线序列
粒子按索引数从头连到尾
#### All Points to all Points/所有点到所有点
所有的点之间都互相连接
#### Nearest by Index/按最近的索引连接
- Maximum Connections---------最大连接数
- Skip Particles--------------忽略粒子数

**如果把最大连接数和忽略粒子数都调到最大，会让第一个粒子和所有粒子连接**
#### Nearest by Distance/按最近的距离连接
- Distance Mode---------------距离模式
  - Nearest Only----------------仅连接最近距离
  - All Within Distance---------连接所有设定距离内的
  - Max.Number Within Distance--连接设定距离内的最大数目
- Distance--------------------设定距离
- Max.Number------------------设定最大数目
#### Cluster/簇
- Cluster Distance------------簇距离
- Min.Particles in Cluster----每个簇里最少粒子数

**可以配合运动样条制作粒子样条生长效果，使用Trail制作好粒子拖尾效果的形态后转化为多边形变为普通样条，添加运动样条，模式设置为样条，生长模式设为独立的分段，在样条中把Trail拖入源样条即可**


### Action/动作
与Question配合使用，让粒子满足在一定条件后执行某些动作
- Action Type-----------------动作类型
- Create Modifier-------------创建力场
#### Control Gravity Modifier/控制重力
- Gravity Modifier------------将重力场拖入
- Effect on Particle----------力场对粒子的影响（用来K关键帧）
  - Modifier Will Affect Particle--------力场影响粒子
  - Modifier Will NOT Affect Particle----力场不影响粒子
- Change Modifier Settings----激活改变力场设置
#### Freeze Particles/冻结粒子



### Question/问题
让粒子满足在一定条件后执行某些动作，与Action配合使用
- Actions---------------------拖入动作
- Add Action------------------添加动作
- Test Sub-Questions Mode-----子问题模式
- Create Sub-Question---------创建子问题
#### Particle Age/粒子年龄
- Mode------------------------条件模式
  - Is Greater Than-------------大于第几帧
  - Equals----------------------等于第几帧
  - Is Less Than----------------小于第几帧
  - Is Within Frames of Death---倒数第几帧
- Frames----------------------第几帧
- Range-----------------------范围
#### Particle Speed/粒子速度
- Mode------------------------条件模式
  - Is Greater Than-------------大于
  - Is Less Than----------------小于
- Speed-----------------------速度
- Range-----------------------范围
#### Particle Count/粒子数
- Mode------------------------条件模式
  - Exceeds---------------------超过
  - Is Less Than----------------少于
- Particle Count--------------粒子数
- Range-----------------------范围
#### Particle Index/粒子索引
- Mode------------------------条件模式
  - Equals----------------------等于
  - Is Greater Than-------------大于
  - Is in Range-----------------在设定范围内
  - Is Not in Range-------------在设定范围外
  - Even-Numbered Particles-----偶数粒子
- Particle Index--------------粒子索引
- Range-----------------------范围
#### Distance to Camera/与摄像机的距离
- Mode------------------------条件模式
  - Is Greater Than-------------距离大于多少
  - Is Less Than----------------距离小于多少
- Distance--------------------距离
- Range-----------------------范围
#### Distance to Object/与对象的距离
- Mode------------------------条件模式
  - Is Greater Than-------------距离大于多少
  - Is Less Than----------------距离小于多少
- Object----------------------将对象拖入
- Distance--------------------距离
- Range-----------------------范围
#### Particle Collided/粒子碰撞
当粒子发生碰撞时激发动作
#### Random Probability/随机概率
动作根据发生概率随机发生
- Rondom Seed-----------------随机种子
- Probability-----------------概率，概率为100%时会一直执行动作


### Modifiers/力场
XP2.1支持C4D自带的力场，但是4.0不支持C4D自带的力场
#### Attractor/吸引力

#### Cover/Target/追随/目标
- Target Object---------------将追随的目标对象拖入
- Mode------------------------激活方式
  - Independent-----------------独立的，添加后就生效
  - Action-Controlled-----------受到Action的控制
- Enabled---------------------激活追随
- Acuteness of Turn-----------追随准确度，如果粒子追不上目标，可以提高追随准确度，如果追随准确度到100%还是追不上目标，还可以提高粒子发射速度
- Tolerance-------------------容差
- Stick Point Offset----------吸附偏移
- Variation-------------------偏移变化

#### Direction/方向
- Mode------------------------激活方式
  - Independent-----------------独立的，添加后就生效
  - Action-Controlled-----------受到Action的控制
- Enabled---------------------激活方向
- Groups Affected-------------影响组
- Operation-------------------运算模式
  - Network---------------------网络
**Network模式可以制作很酷的网状效果**
- Change in(Frames)-----------过多少帧改变一次方向
- Change Angle(Heading)-------最小改变多少度
- Change Angle(Pitch)---------最大改变多少度
*注意如果发射器是以对象发射，则发射器中默认的粒子方向是随机的，所以这里力场影响方向，需要时要在发射器中修改粒子方向*

#### Freeze/冻结

#### Gravity/重力

#### Rotator/螺旋
注意XP2.1的螺旋有bug，点击会导致工程崩溃，4.0版本可以使用，2.1版本可以使用C4D自带的螺旋

#### Spawn/产卵
可以理解为一个个粒子是一个老母鸡，使用产卵发射器让老母鸡下蛋，类似于AE中的Particular粒子的子粒子系统

使用时新建一个发射器，将这个新建的发射器拖入Spawning Emitter,会发现这个发射器的Emission标签中Spawn Only会自动勾选，说明这个发射器已经成为了产卵发射器

**子粒子默认会排除Spawn影响，但仍会受到其他力场的影响，如果不想让子粒子受力场影响，将力场拖入产卵发射器的力场排除**

**子粒子也会再产生子粒子，具体方法是再新建一个Spawn和一个发射器**

- Spawning Emitter------------拖入产卵发射器
- Mode------------------------激活方式
    - Independent-----------------独立的，添加后就生效
    - Action-Controlled-----------受到Action的控制
- Enabled---------------------激活产卵
- Groups Affected-------------产卵的粒子组，只有该粒子组才产卵
- Spawned Particle Position---产卵的粒子位置
  - Source Particle-------------基于源粒子的位置
  - Determined by Emitter-------基于发射器位置（不常用）
- Direction-------------------产卵粒子发射方向
  - Random(Spherical)-----------球形随机
  - Relative to Source Particle-相对于源粒子（默认跟随源粒子，可以使用下面4个参数调节方向）
  - Custom(Absolute)------------自定义（不常用）
- Heading---------------------横向
- Pitch-----------------------纵向
- Spread----------------------散开
- Reverse---------------------反向
- Spawned Particle Speed------产卵粒子的速度，默认由产卵发射器的发射速度控制
  - Absolute--------------------不受约束，由产卵发射器的发射速度控制
  - Relative to Source Particle-相对于源粒子，与源粒子发射速度相同
  - Inherit---------------------继承，使用Speed Multiplier来控制继承源粒子速度的倍数
- Speed Multiplier------------继承倍数，产卵粒子是源粒子速度的多少倍
- Number to Spawn-------------产卵数
- Number Variation(+/-)-------产卵数变化
- Spawned Particle Life-------产卵粒子的生命值，默认由产卵发射器的粒子生命值控制
  - Absolute--------------------不受约束，由产卵发射器的粒子生命值控制
  - Relative to Source Particle-相对于源粒子，与源粒子生命值相同
  - Inherit---------------------继承，使用Life Variation(+/-)来控制继承源粒子的生命值变化
- Life Variation(+/-)---------生命值变化
- Group-----------------------让产卵的粒子属于某个粒子组
- Spawn Once Only-------------仅产卵1次
- Min.Interval Between Spawns-最短间隔几帧产卵一次
- Max.Interval Between Spawns-最长间隔几帧产卵一次
- Don't Spawn from Frozen Particles------冰冻的粒子不会产卵
- Kill Original Particle After Spawning--产卵后杀死源粒子
*产卵一个非常重要的用法是让源粒子驱动TFD流体，再用流体驱动产卵粒子*

**XP2.1版本产卵粒子无法继承源粒子的颜色，4.0版本可以继承源粒子的颜色**

#### Turbulence/湍流



## 标签
### Colliser/碰撞
给对象添加，让粒子可以和对象发生碰撞
  - Enable Collisions-----------激活碰撞
  - Bounce on Collision
    - Normals---------------------法线，选择对象的正面碰撞还是背面碰撞
      - Outside---------------------对象正面碰撞
      - Inside----------------------对象背面碰撞
      - Any-------------------------对象双面碰撞
    - Bounce----------------------反弹力
    - Bounce Variation------------反弹力变化
    - Friction--------------------摩擦力
    - Friction Variation----------摩擦力变化
    - Scatter---------------------分散，让粒子碰撞后分散开
    - Expand----------------------扩散，控制碰撞间隙，非常重要。碰撞间隙与粒子半径有关，默认粒子半径为5，碰撞时会发现粒子与碰撞物体中间有间隙，将这里改为-5，粒子就完美的碰撞在碰撞物体表面。即让扩散值等于负的粒子半径
  - Forces----------------------力
**注意如果要使这里的力起作用，要在发射器的Dynamics里勾选Enable Constrains和Collider Forces,否则不起作用**
    - Attraction------------------吸引力
    - Radius----------------------吸引力半径
    - Falloff---------------------衰减，拖入顶点贴图，用顶点贴图控制吸引力哪里强哪里弱

*吸引力可以和产卵力场结合制作粒子在对象表面游走，具体做法：*
1. 创建一个发射器，对着对象发射粒子，粒子少一些，仅发射几帧
2. 给对象添加碰撞标签，给一定的吸引力，同时发射器开启Enable Constrains和Collider Forces
3. 添加产卵力场，添加产卵发射器，产卵发射器粒子速度设为0

    - Repulsion-------------------排斥力
    - Radius----------------------排斥力半径
    - Falloff---------------------衰减，拖入顶点贴图，用顶点贴图控制排斥力哪里强哪里弱
  - Connect on Collision--------碰撞时连接对象和粒子
粒子碰到对象后会粘在对象表面，如果对象有动画，粒子会跟着对象运动

**注意如果要使这里的力起作用，要在发射器的Dynamics里勾选Enable Constrains和Collider Forces,否则不起作用**

- Connect on Collision--------激活连接
- Stiffness-------------------硬度
- Break-----------------------断开
- Reaction on Collision-------碰撞时对象的反应（不常用）
    - Reaction--------------------反应
      - None------------------------无反应
      - Translate-------------------转化，粒子会推着对象前进
    - Initial Velocity------------对象初速度
    - Mass------------------------对象质量，质量越大，粒子越难推动对象
  - Actions on Collision--------碰撞时激发动作
    - Action----------------------拖入动作
  - Spawn on Collision----------碰撞产卵
    - Enabled---------------------激活碰撞产卵
    - Spawning Emitter------------拖入产卵发射器
    - Spawned Particle Position---产卵粒子产生的位置
      - Collision Point-------------碰撞点
      - Determined by Emitter-------基于发射器（不常用）
    - Direction-------------------产卵方向
      - Random(Spherical)-----------球状随机
      - Source Particle-------------基于源粒子方向
      - Face Normal-----------------表面法线方向
    - Spawned Particle Speed------产卵粒子速度
      - Absolute--------------------绝对
      - Relative--------------------相对
    - Spawn Once Only-------------只产卵一次
    - Kill Original Particle After Spawning--产卵后杀掉源粒子






# Krakatoa渲染器
## 特点
1. 只能渲染粒子
2. 使用CPU渲染，内存越大，读取速度越快
3. 支持默认粒子、TP粒子、XP粒子、TFD


## 渲染出粒子的几个条件
1. 场景中要有粒子
2. 场景中要有灯光
3. 渲染设置中选择Krakatoa
4. 如果渲染默认粒子，添加Krakatoa Emitter Source,并将粒子发射器拖入Object中，来告诉KK渲染器渲染什么。也可以选中发射器，点击Krakatoa Emitter Source添加
5. 如果渲染TP粒子，添加Krakatoa TP Source
6. 若果渲染XP粒子，添加Krakatoa X-Particles Source,并将Emitter拖入Object中，来告诉KK渲染器渲染什么。也可以选中发射器，点击Krakatoa X-Particles Source添加


## 插件
### Krakatoa PRT Loader
用来读取粒子缓存，非常常用
*可以将PRT Loader的一个轴向尺寸调的非常大，制作拉丝的效果*

- Setup
  - Override Color------------颜色覆写，用一个颜色覆盖掉粒子原来的颜色
  - Override Emission---------自发光覆写
  - Override Absorption-------吸收覆写
  - Override Density----------密度覆写，1为保持原来的密度不变，一般不作调整
  - Reduce Number Of Particles--减少粒子数量，不常用
  - Particle Percentage-------减少的百分比，不常用
- Particle Files
  - File Path-----------------选择要读取的prt格式缓存
  - Sequence------------------读取prt序列
  - Keep Velocity Channel-----保留速度通道，如果不勾选，就没有速度通道，无法根据粒子速度着色，也无法添加运动模糊
  - Load Additional Partitions--读取多个序列（读取分区缓存时使用）
  - Partitions to Load--------当前读取哪个粒子分区
  - Partitions Found----------共找到几个粒子分区序列
  - Enable Playback Graph-----激活回放图
  - Playback Graph------------回放步幅
  - Frame Offset--------------时间偏移
  - Use Custim Range----------使用自定义帧范围
  - Available Channels--------查看可以使用哪些通道
- Display
设置预览视图粒子形态
  - Percent Of Render Count---显示粒子数量百分比，调低后播放会非常流畅，且不影响渲染结果
- Render
设置粒子能有多少被渲染，这里的设置影响渲染结果

### Krakatoa PRT Fractal
KK渲染器自带的分形粒子，添加灯光后，可以使用KK渲染器直接渲染，可以用来制作很随机的概念化的粒子
- Setup
  - Override Color------------颜色覆写，用一个颜色覆盖掉粒子原来的颜色
  - Override Emission---------自发光覆写
  - Override Absorption-------吸收覆写
  - Override Density----------密度覆写，1为保持原来的密度不变，一般不作调整
  - Reduce Number Of Particles--减少粒子数量，不常用
  - Particle Percentage-------减少的百分比，不常用
- Fractals
  - Number Of Particles Render----渲染的粒子数
  - Number Of Particles Viewport--预览视窗显示的粒子数
  - Use Gradient Object-----------使用渐变
  - Color Gradient----------------渐变颜色
  - Color Gradient Begin----------渐变开始颜色
  - Color Gradient End------------渐变结束颜色
  - Affine Transforms Count-------设置Params中有几列参数可以调节
  - Random Seed-------------------随机种子，调节后没有反应，需要点击一下Create Fractal Design From Random Seed
  - Create Fractal Design From Random Seed--根据随机种子创建分形粒子
  - Keyframe All Layers At Current Frame----在当前帧给所有形态层打关键帧
  - Remove All Keyframes From All Frames----清除所有关键帧
  - Remove Keyframes From Current Frame-----清除当前帧的关键帧
  - Params----------------------------------形态层，用来调整分形粒子形态，可以配合Keyframe All Layers At Current Frame做形态变化


### Krakatoa PRT Volume
由模型内直接生成填充的粒子
- Setup
  - Override Color------------颜色覆写，用一个颜色覆盖掉粒子原来的颜色
  - Override Emission---------自发光覆写
  - Override Absorption-------吸收覆写
  - Override Density----------密度覆写，1为保持原来的密度不变，一般不作调整
  - Reduce Number Of Particles--减少粒子数量，不常用
  - Particle Percentage-------减少的百分比，不常用
- Mesh
  - Mesh From-----------------设置由对象或由模型文件生成粒子
  - File Path-----------------模型文件路径，路径和文件名不能有中文
  - Object--------------------将对象拖入
  - Voxel Spacing in Renderer-渲染时粒子间隙，间隙越小粒子越多
  - Voxel Spacing in Viewport-预览视窗粒子间隙
  - Voxel Subdivisions--------粒子细分，细分越高粒子越多
  - Enable Jittering----------激活抖动，激活后粒子位置随机，不再规整
  - Enable Shell--------------激活外壳，激活后粒子会有厚度，不再只是一个点
  - Shell Start---------------外壳开始处
  - Shell Thickness-----------外壳厚度
  - Viewport Percent Limit----预览视窗粒子显示数量比例

### Krakatoa PRT Surface
基于模型表面发射粒子，不常用
- Setup
  - Override Color------------颜色覆写，用一个颜色覆盖掉粒子原来的颜色
  - Override Emission---------自发光覆写
  - Override Absorption-------吸收覆写
  - Override Density----------密度覆写，1为保持原来的密度不变，一般不作调整
  - Reduce Number Of Particles--减少粒子数量，不常用
  - Particle Percentage-------减少的百分比，不常用
- Surface
  - Surface From-----------------设置由对象或由模型文件生成粒子
  - File Path-----------------模型文件路径，路径和文件名不能有中文
  - Object--------------------将对象拖入
  - Random Seed---------------随机种子
  - Use Spacing---------------勾选使用粒子间隙来控制粒子数
  - Partile Count-------------粒子数量
  - Partile Spacing-----------粒子间隙，间隙越小，粒子数越多
  - Viewport Percent Limit----预览视窗粒子显示数量比例

### Krakatoa Emitter Source
专门用来渲染C4D默认粒子
- Emitter
  - Emitter Object------------将C4D自带的粒子发射器拖入后可以进行渲染
- Channels------------------读取粒子的通道

### Krakatoa X-Particles Source
专门用来渲染XP粒子
- Emitter
  - Emitter Object------------将XP的发射器拖入后可以进行渲染
- Channels------------------读取粒子的通道

### Krakatoa Turbulence FD Source
把TFD流体作为粒子渲染，不常用


## 标签
### Channel Copy/复制通道
把已有的通道信息复制到另一个通道
- Enable Channel Copying---------激活复制通道
- Souce Channel Selection--------选择已有的通道信息
- Destination Channel Selection--选择要复制到的通道

**一个重要用法是当粒子已经缓存了，要改变粒子的颜色时，给PRT Loader材质会发现显示的颜色不是想要的，因为粒子没有UV，贴图是乱的。这是需要给PRT一个Channel Copy标签，已有通道选择Color/颜色，复制到的通道选择TextureCoord/纹理坐标，这样贴图就会恢复正常**



### Channel Gradient/通道渐变
用渐变来将粒子的一种属性映射到一个通道
- Enable Channel Gradient---激活通道渐变
- Source Channel Name-------来源通道，最常用的是Position、Color、Velocity
- Destination Channel Name--映射通道，最常用的是Color、Emission、Density，Emission通道可以制作自发光，效果很好；Density通道可以控制粒子分布密度，渐变中白色代表粒子最密，黑色代表没有粒子
**注意如果使用Emission通道，一定要将渲染设置中使用自发光打开，否则没有效果**
- Output Data Type----------输出数据类型
- Gradient------------------渐变颜色
- Gradient Input From-------映射方式
  - Magnitude Squared---------平方衰减，最常用方式
  - Magnitude-----------------平方，没有衰减
- Normalize Gradient Input--自动计算映射范围，默认勾选



### Channel Scale/通道倍数
只对PRT Loader有效果，让某个通道的参数乘以相应的倍数，颜色通道是RGB的倍数，可以让颜色变暗或变亮，位置通道可以让粒子整体放大缩小，速度通道可以让运动模糊变的更强烈或变弱
- Enable Channel Scaling----激活通道倍数
- Channel Selection---------选择通道
- Scale---------------------倍数

### Channel Set/通道设置
强制给通道数据赋予数值，不常用
- Enable Channel Setting----激活通道设置
- Channel Selection---------选择通道
- Data Type-----------------数据类型
- Integer Value-------------整数数值
- Float Value---------------浮点数据数值
- Vector Value--------------矢量数值

### Channel Texture/通道纹理
- Enable Texture Channel Override----激活通道纹理
- Enable Texture in Viewport---------在预览视窗显示纹理
- Enable Output Channels even if Shader is Disabled--强制激活输出通道，即使着色器被禁用
- Input Channels
  - Input Position Channel Selection---选择将什么通道输入位置通道
  - Input UVW Channel Selection--------选择将什么通道输入UV通道
  - Input Normal Channel Selection-----选择将什么通道输入法线通道
  - Input Tangent Channel Selection----选择将什么通道输入切线通道
- Output Shader Channels-------------输出材质通道，给PRT Loader一个材质球，让材质球的各通道来影响粒子
  - Output Color Channel Enable--------激活输出颜色通道
  - Output Color Channel Selection-----选择将材质球的颜色通道输出到什么通道，可以给材质球颜色通道一个动画序列，可以来控制发光，也可以控制密度让粒子有一个逐渐出现的效果
- Output Mapped Channels-------------输出映射通道，让材质球的通道影响粒子
  - Mapped Position Channel Enabled----激活位置映射
  - Mapped Position Use Bump Shader----激活凹凸通道影响粒子位置
  - Mapped Position Use Displacement Shader--激活置换通道影响粒子位置

### Krakatoa Camera/KK摄像机
给摄像机添加的标签，不常用
- Override Field of View----勾选后使用这里的视野范围覆盖掉摄像机原来的视野范围
- Override f-stop-----------勾选后覆盖掉原有的光圈大小
- Override Focal Length-----勾选后覆盖掉原有焦距
- Override Focal Distance---勾选后覆盖掉原有目标距离
- Override Near Clipping----勾选后覆盖掉原有近端修剪
- Override Far Clipping-----勾选后覆盖掉原有远端修剪

### Krakatoa Light/KK灯光
给灯光添加的标签，它可以让灯光有衰减
- Override Color------------勾选后覆盖原有灯光颜色
- Color---------------------覆盖颜色
- Intensity-----------------灯光强度
- Decay Exponent------------灯光指数衰减强度
**将粒子颜色改为灰白渐变，然后用几个开启了衰减的KK灯光放置在不同位置，可以让不同地方的粒子呈现不同的颜色，制作五彩斑斓的效果**
- Attenuation Map
  - Lighting-Pass Density-----投射阴影强度
  - Attenuation Map Resolution--衰减贴图分辨率，一般保持默认即可
- Attenuation
  - Override Near Attenuation-控制衰减开始，从Start到End灯光强度从0到100
  - Override Far Attenuation--控制衰减结束，从Start到End灯光强度从100到0

### Krakatoa Mesh
给对象添加Krakatoa Mesh标签，用来让KK渲染器渲染的粒子和对象产生交互，让粒子和对象没有穿插
- Visible To Camera---------让对象和粒子产生交互
- Visible To Lights---------让对象和粒子在照明、投影产生交互，一般不勾选，否则对象会在粒子上产生投影
**注意使用Krakatoa Mesh时，要确保渲染设置中Options-->Matte Objects是激活的，否则不起作用**

### Repopulate Particles/再填充粒子
KK渲染器渲染粒子是没有近大远小的，粒子最大只能是1像素，镜头离粒子越近粒子越稀疏，粒子效果越暗。使用Repopulate Particles可以解决这个问题

**注意Repopulate Particles标签只能添加给PRT Loader才有效果，它的原理是在粒子周围生成很多的粒子，使粒子看起来变大，这样会产生近大远小的透视效果，使用Repopulate Particles时，渲染一般使用粒子叠加模式**

- Enable Particle Repopulation---------激活再填充粒子
- Fill Radius--------------------------填充半径，半径约小，填充的越密
- Subdivision--------------------------细分
- Number Of Particles Per Subdivision--每次细分的粒子数
- Density Falloff Start----------------衰减，让再填充粒子中间粒子数最多，越向外粒子数越少，效果就像羽化一样，中间很实，边缘很虚
- Random Seed--------------------------随机种子
- Enable in Viewport-------------------在预览视窗显示，激活后会很卡



## 渲染设置
### Output
- Output
  - Render To
    - Viewer--------------------渲染到图片查看器（常用）
    - File----------------------渲染到文件
    - MultiChannelEXR-----------渲染到多通道EXR文件
    - Save Particles to File Sequence--缓存粒子（常用），会输出PRT格式的缓存文件，然后使用PRT Loader来读取，在输出时在保存里面选择输出路径，注意不要有中文，格式、深度等其他选项均保持默认即可
- Save Particles
  - Export Channels-----------输出通道，注意先要在Emitter Source或X-Particles Source中勾选读取通道，才能在这里输出
**常用的有颜色通道、速度通道和年龄通道，其他的都不常用**
- Partitioning--------------分区
可以让缓存粒子分多个地方保存，每个分区之间有微弱的差距，然后进行叠加
  - Save Multiple Partitions--激活分区保存
  - Total Partitions Count----选择保存几份
**注意分区保存渲染时要点击Save Particles中的Submit Saving Job Or Partitioning Jobs来进行保存，它会自动打开渲染队列**


### Options（非常常用）
#### Global Render Values/全局参数

#### Rendering Controls/渲染控制
- Rendering Method----------渲染方式
  - Particles-----------------粒子方式
  - Voxel---------------------体积方式
粒子大小可以超过一个像素，此方式很少用
- Ignore Scene Lights-------忽略场景灯光，一般不勾选
- Force Additive Mode-------强制粒子为叠加模式，非常常用，开启后灯光就没有作用了
- Use Emission--------------使用自发光，如果使用发光通道，必须要开启使用自发光才有效果
- Use Absorption------------

#### Lighting And Drawing Pass
- Self-Shadow Filter--------
- Final Pass Density--------最终密度
- Exponent------------------指数衰减，和最终密度配合控制粒子密度和大小，数值为10的指数，-1即为10的-1次方（10分之1），-2即10的-2次方（100分之1），粒子最终的大小是最终密度*指数衰减，例如最终密度为1，指数衰减为-1，粒子大小就是1*1/10=0.1，由于粒子大小最大为1个像素，所以最终数值超过1时粒子都为1个像素

**在操作时会发现，镜头离粒子很近，粒子会很暗，镜头离粒子很远，粒子会很亮，这是因为粒子最大只能为1个像素，镜头离粒子很近时粒子间距大，单位面积粒子少；镜头离粒子很远时粒子间距小，单位面积粒子多**

#### Motion Blur/运动模糊
**运动模糊必须渲染到图片查看器才能显示效果**
- Enable Motion Blur---------激活运动模糊
- Jittered Motion Blur-------抖动运动模糊，让运动模糊更随机，效果更好
- Particle Segments----------运动模糊分段，分段数越大运动模糊越精细，效果越好，渲染速度越慢，最大不要超过20
- Shutter Angle--------------快门角度，数值越大，运动模糊效果越强烈
- Disable Camera Motion Blur-忽略摄像机的运动模糊

#### Depth Of Field/景深
- Enable Depth Of Field------激活景深
- Sample Rate----------------采样，数值越大，效果越好，光斑效果越精细，一般介于1-10之间
- Camera f-stop--------------光圈大小，数值越小光圈越大，景深效果越明显
- Camera Focal Distance------焦点距离，这里数值不够直观，可以直接将摄像机的目标距离数值复制过来，也可以将摄像机目标距离设置驱动，这里设为被驱动

#### Matte Objects/对象蒙版

### Shader
控制粒子怎样呈现
#### Shader Type/呈现类型






