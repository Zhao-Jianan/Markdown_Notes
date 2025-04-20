### 标题栏
#### Windows/窗口
##### Edit/编辑窗口
###### Path Manager/路径管理器
用来管理、编辑、修改资产的存放路径，支持搜索和批量移动位置

*一般使用相对路径，方便他人或客户打开使用*

```$CDIR(Content Directory)``` 文件所在路径
```$PDIR(Project Directory)``` 工程所在路径
将路径改为```$PDIR/``` 即可

#### Layout/布局

# 工作面板
## Animate/动画模块
### 3D View/3D视图面板
##### Options/设置
- Material Sampling/材质采样
  - Material Sample Count---------材质采样数
  - Diffuse Sampling Multiplier---漫射采样乘数
  - Glossy Reflection Sampling Multiplier---光泽反射采样乘数，设为0，即可关掉反射效果
##### Enable Optix Denoiser
基于英伟达核心的智能降噪
##### Create Perspective Camera from current viewport/以当前视窗创建摄像机

## Edit/编辑模块
### Attribute Editor/属性编辑器

### Tool Options/工具设置
##### Clone Stamp 3d/克隆图章工具
用来克隆对象
###### General/常规设置
- Sources-----------------------克隆源，添加要克隆的物体
- Geometry Group----------------几何体组，选择一个物体对象，在物体表面克隆，类似C4D的对象克隆
- Cloning Mode------------------克隆模式
  - Create Instances--------------创建实例，对原始物体进行操作，克隆的实例也会相应变化
  - Create Copies-----------------创建复制物体
- Clone Path--------------------克隆路径
- Opacity Threshold-------------透明度阈值
- Constrain To Surface----------约束到表面
###### Snap To Surface/表面捕捉
- Align To Normal---------------对齐法线
- Snap Default Plane------------默认对齐平面
###### Variance/变化
- Rotation Variance-------------旋转变化，旋转随机变化的角度
- Rotation Step-----------------旋转步幅，旋转变化时每一次变化多少度
- Scaling Variance--------------缩放变化
- Uniform Scaling Variance------统一缩放变化
- Translation Variance----------位置偏移变化

## Explore/资源管理模块
### Browser/资源管理器
显示当前所有场景中的内容
#### Geometry/几何体
##### Geometry/几何体
###### Box
- Kinematics/动力学
  - Translate---------------------位置
  - Ratate------------------------旋转
  - Shear-------------------------断裂，对模型进行变形
  - Scale-------------------------缩放
  - Rotation Order----------------旋转顺序
  - Parent------------------------父物体
  - Constraints-------------------约束，点击箭头进入约束编辑
  - Parent------------------------父子约束，与父物体功能相同
  - Orient------------------------方向约束
  - Target------------------------目标约束，一般用于灯光、摄像机等，和C4D的朝向功能相同

**注意：如果是多个物体，点击箭头进入的约束编辑仅是对一个物体进行编辑，要对多个物体进行编辑，可以在Search面板中搜索约束，全选后在进行编辑**
  - Inherit Transform-------------继承变换，继承父物体的变换信息
###### Deformation/变形
- Deformers---------------------变形器
  - Displacement------------------置换
###### Geometry/几何体
- Size--------------------------尺寸

##### PolyMesh/多边形网格
###### Polygrid/多边形网格
- Deformation/变形
  - Deformers-------------------- 变形器
    - Displacement------------------置换

*使用置换变形器生成地形方法：*
- 第1步：点击File-->Import-->Texture-->Map File导入高度图，Projection（贴图投射方式）设为Planar，Axis设为Y，File Color Space设为Linear，Single Channel File Behavior设为Force Luminance
- 第2步：创建平面Polygrid，分段设的高点，添加Displacement变形器，在变形器中的Texture选择导入的高度图

- Displacement/置换
  - Displacement Mode-------------置换模式
  - Displacement Tessellation Mode--置换细分模式
  - Displacement Adaptive Span Count--置换自适应细分数，控制Shader置换细分数
  - Displacement Triangulation Mode-置换三角化模式，置换时一些边缘的地方会出现三角面，这个选项用来设置这些三角面
  - Displacement Stitching Mode---置换缝合模式，修复置换出现的一些错误接缝裂缝的模式

*使用Shader置换生成地形方法：*
- 第1步：创建平面Polygrid，分段设为1或2，在Material Linker面板中点击Displacement，右键添加Displacement
- 第2步：进入添加的Displacement，在Front Value中加载高度图，并设置高度，在Bound中设置边缘高度，要大于Front Value值
- 第3步：在平面的属性中的Displacement Adaptive Span Count中设置Shader置换细分数
- Geometry/几何体
  - Size--------------------------尺寸
  - Spans-------------------------细分

##### Volume/体积
可以制作灯光雾、云、火焰等，添加Volume后一般要添加Volume材质并赋予给体积
###### Box/盒状体积

###### Surface/表面体积
通过场景中现有的模型生成体积

##### Particle/粒子
###### Point Array/点阵
由粒子组成的阵列，效果简单，灵活性不强

###### Point Cloud/点云
可以根据几何体生成粒子点云，效果好，很常用
- Scattering/散布
  - Use Density-------------------使用密度控制，使用密度控制更方便，缩放几何体时，粒子会随之变化
  - Density-----------------------密度，控制粒子数
  - Point Count-------------------粒子数量，使用数量控制粒子
  - Geometry----------------------几何体，选择生成点云的几何体



#### Light/灯光
##### Physical/物理灯光
###### Ambient Light/环境光
用来整体提升场景亮度

###### Distant Light/定向光
模拟日光灯平行光源
- Lighting/灯光
  - Shadow Color------------------阴影颜色
  - Color-------------------------灯光颜色
  - Exposure----------------------曝光值
  - Angle-------------------------角度，控制阴影柔和度，早晨和傍晚值比较大，中午值比较小

###### Point Light/点光源
- Lighting/灯光
  - Shadow Color------------------阴影颜色
  - Color-------------------------灯光颜色
  - Exposure----------------------曝光值
  - Radius------------------------灯光半径，半径增大，会产生衰减，灯光半径控制衰减距离
- Attenuation/衰减
  - Attenuation Mode--------------衰减模式
    - None--------------------------无衰减
    - Near Only---------------------仅近处衰减
    - Far Only----------------------仅远处衰减
    - Near&Far----------------------近处远处都产生衰减
    - Curve-------------------------曲线控制衰减
  - Attenuation Near Start--------近处衰减开始点
  - Attenuation Near End----------近处衰减结束点
  - Attenuation Far Start---------远处衰减开始点
  - Attenuation Far End-----------远处衰减结束点

###### Spot Light/聚光灯
模拟太阳穿过叶片的效果或舞台效果使用
- Lighting/灯光
  - Cone Angle--------------------锥角
  - Falloff Angle-----------------衰减度数，控制聚光灯边缘衰减强度
  - Radius------------------------灯光半径，半径越大，阴影越虚

###### Area Light/面光源
- Lighting/灯光
  - Shape-------------------------形状，有方形和圆形两种
  - Radius------------------------灯光半径，半径越大，阴影越虚
  - Direction---------------------方向，可以选择单面发光或双面发光
  - Cone Angle--------------------锥角

###### Environment Light/环境光
用来加载HDR贴图，进行环境光照明

*显示HDR场景的方法：*
- 第1步：使用导入Map File将HDR图导入工程
- 第2步：添加Environment Light，在Color中加载HDR贴图
- 第3步：添加一个Sphere对象和Matte材质，将Matte材质赋予Sphere
- 第4步，将Sphere对象作为Environment Light的父对象
- 第5步：勾选Sphere对象的Visibility-->Unseen By Rays,关掉HDR产生的GI，解决HDR的间接照明产生的噪点

###### Image Based Lighting/基于图片的光照
与Environment Light功能相同，快速创建HDR环境光


#### Material/材质
材质可以按鼠标中键直接拖到视口中的对象上
##### Physical/物理材质
物理材质使用PBR材质，基于Arnold内核
###### Standard/标准材质
最常使用的材质，它涉及基于Specular的PBR材质
- Geometry/几何体
  - Normal Input------------------法线输入，输入法线贴图
  - Sidedness---------------------选择材质赋予几何体的正面还是反面还是双面

*注意使用双面要在Diffuse Backlight中开启Diffuse Back Strength*

- Diffuse/漫射
  - Diffuse Front Color-----------漫射颜色
  - Diffuse Front Strength--------漫射强度
  - Diffuse Roughness-------------漫射粗糙度
- Diffuse Backlight/漫射背光
给树叶、纸张等材质添加背光，让树叶有透光效果
  - Diffuse Back Color------------背光颜色
  - Diffuse Back Strength---------背光强度
- Diffuse SSS
SSS效果
  - Diffuse SSS Mix---------------SSS强度
  - Diffuse SSS Mode--------------SSS模式
    - Gaussian----------------------高斯模糊模式
    - Cubic-------------------------立方体模式
    - Empirical---------------------经验模式，效果最好，但需要更多采样
  - Diffuse SSS Density Scale-----SSS范围大小
  - Diffuse SSS Color 1-----------SSS层1颜色
  - Diffuse SSS Distance 1--------SSS层1距离，距离越小，颜色越明显
  - Diffuse SSS Weight 1----------SSS层1权重

- Diffuse Advanced/漫射高级选项
- Specular 1/高光
  - Specular 1 Color--------------高光颜色
  - Specular 1 Strength-----------高光强度
  - Specular 1 Roughness----------高光粗糙度
  - Specular 1 Anisotropy---------高光各向异性
  - Specular 1 Anisotropy Rotation--高光各向异性旋转
- Specular 1 Fresnel/高光菲涅尔
  - Specular 1 Fresnel Preset-----菲涅尔预设
  - Specular 1 Fresnel Mode-------菲涅尔模式
    - Dielectric--------------------绝缘体
    - Metallic----------------------金属
  - Specular 1 Index Of Refraction---物理折射率（IOR）
  - Specular 1 Fresnel Reflectivity--金属高光入射角颜色
  - Specular 1 Fresnel Edge Tint-----金属高光边缘颜色
- Specular 1 Advanced/高光高级选项
  - Specular 1 Brdf---------------高光模型
- Specular 2/高光2
注意高光1始终在高光2的上面
- Transmission/透射
模拟玻璃等半透明效果
  - Transmission 1 Color----------透射颜色
  - Transmission 1 Strength-------透射强度
  - Transmission Link To Specular-透射链接到高光，勾选后投射的IOR和粗糙度由高光控制
  - Transmission Linked To--------选择透射链接到高光1还是高光2
  - Transmission Index Of Refraction--透射IOR
  - Transmission Roughness--------透射粗糙度
- Emission/自发光
  - Emission Color----------------自发光颜色
  - Emission Strength-------------自发光强度

###### Disney_Principled/基于迪士尼原则的材质
是一种基于Metallic的PBR材质，与Substance搭配很方便


###### Volume/体积材质
给体积对象赋予的专用材质
- Shading/着色
  - Optical Mode------------------透明模式
    - Physicist---------------------物理模式，使用吸收颜色和散射颜色控制
    - Legacy------------------------遗留的旧模式，使用散射颜色和衰减颜色控制
    - Artistic----------------------艺术模式，使用衰减颜色和反照率控制
  - Absorption--------------------吸收颜色
  - Scattering--------------------散射颜色
  - Attenuation-------------------衰减颜色
  - Albedo------------------------反照率
  - Emission----------------------发光，让体积产生自发光，一般不使用，效果不够真实
  - Density Multiplier------------密度乘数，控制体积的密度
  - Forward Scattering------------向前散射，调为正值，离灯光近处较亮，离灯光远处较暗。负值相反

##### Material/特殊材质
###### Matte
一般用来给环境球赋予HDR贴图使用

#### Texture/贴图
##### Map
###### Map_file/贴图文件
- General/常规
- Projection Mode/投射模式
  - Projection--------------------UV投射方式
    - UV----------------------------自动UV，与C4D中的UVW模式相同
    - Planar------------------------平面投射
    - Cylindrical-------------------圆柱体投射
    - Spherical---------------------球形投射
    - Cubic-------------------------立方体投射
    - Camera------------------------摄像机投射
  - Axis--------------------------坐标朝向
  - Object Space------------------对象空间
    - Object------------------------对象坐标，一般制作比较精细的物体
    - World-------------------------世界坐标，设为世界坐标时，移动对象，贴图不跟随对象移动，一般制作大面积的山等
- Camera Projection/摄像机投射
投射模式设为摄像机投射时的设置
  - Camera------------------------摄像机，选择摄像机投射的摄像机
- Projcetion Transform/投射变化
  - Projection Translate----------投射偏移
  - Projection Rotate-------------投射旋转
  - Projection Scale--------------投射缩放
  - Fit To Bounding Box-----------自适应边界框，根据边界框自动调整投射。一般新建一个Combiner对象，将Combiner范围框作为自适应边界框
- UV Transform/UV变化
对UV进行调整，和投射变化配合使用
  - UV Translate------------------UV偏移
  - UV Rotate---------------------UV旋转
  - UV Scale----------------------UV缩放
- Process/工作流
  - Use Raw Data------------------使用原始数据
  - Color Space Auto Detect-------颜色空间自动检测
  - File Color Space--------------文件颜色空间

*高度图和法线贴图要使用Linear颜色空间*

- Evaluation/评估
  - U Repeat Mode-----------------U向重复模式
    - Repeat------------------------重复UV
    - Edge--------------------------边缘，不重复UV，UV边缘颜色向外拉伸
    - Reset-------------------------不重复UV，UV外面是黑色

  - V Repeat Mode-----------------V向重复模式
  - Single Channel File Behavior--单通道文件行为
    - Use File Channel Name---------使用文件通道名
    - Force Luminance---------------强制灰度通道，对于灰度图，需要选择强制灰度通道


##### Group/组
将资产打组，是一种特殊的打组。组在视窗中不可见，模型、灯光、摄像机等所有的资产都可以打组
- Inclusion/包含
  - Inclusion Rule----------------包含规则，如果要包含同类型的所有物体，可以输入 *资产名相同的部分*
  - Inclusion Items---------------包含项目
  - Edit--------------------------编辑组项目
  - Add---------------------------添加资产到组
- Exclusion/排除
将资产排除出组
- Result/结果
通过包含和排除之后，最终的打组结果

##### Combiner/合并
可以将多个对象合并，它会保留原有资产的基础上，复制一份进行合并，它的复制是实例复制，不占用系统资源。Combiner就是通常三维软件中的打组



## Render/渲染模块
#### Layer Editor/层编辑器

#### Material Editor/材质编辑器
Clarisse材质的节点编辑器
##### 节点
Textures
- Color/颜色
  - Blend/混合
很常用，和SD中的混合相同
  - Blur/模糊
  - Contrast/对比度
  - Hue/色相
  - Saturation/饱和度
- Math/数学运算
  - Absolute/绝对值
  - Add/相加
  - Clamp/钳制
  - Divide/除法
  - Dot Product/点积
  - Invert/反相
  - Maximum/最大值
  - Minimum/最小值
  - Multiply/相乘
  - Normalize/标准化
  - Power/幂
  - Rescale/重映射
  - Subtract/减法
  - Vector To Scalar/矢量转为标量
- Normal/法线
  - Bump Map/凹凸贴图
  - Normal Map/法线贴图
- Procedural/程序纹理
  - Cellular Noise/细胞状燥波
  - Checker/棋盘格
  - Fractal Noise/分形燥波
可以用来制作污渍脏迹
  - Grid/网格
  - Perlin Noise/柏林燥波
最常用的燥波，可以制作水底的焦散
- Raytrace/光线追踪
  - Occlusion/光线遮蔽
    - Geometry
      - Occlusion Mode----------------遮蔽模式
        - Ambient-----------------------环境光遮蔽
        - Inner-------------------------可以选择出山脊，给山脊增加细节使用
- Utility/工具
  - Gradient/渐变
    - Input
      - Incidence---------------------入射角，可以区分物体的边缘和面对摄像机的角度
      - Slope(World)------------------坡度（世界坐标），很常用，根据坡度进行渐变，用来选取植被、积雪、悬崖、岩石等区域
      - UV Map U----------------------UV映射U向
      - UV Map V----------------------UV映射V向
      - UV Map UV---------------------UV映射UV向

  - Reorder/通道重映射
可以更改输出的RGBA通道顺序
  - Triplanar/三平面
三个轴向六个面分别连接贴图，可以调节接缝处过渡，用来解决贴图接缝
  - Utility/工具
这个节点可以获取和输出世界位置、材质ID等各种信息
  - Curvature/曲率
用来制作破损效果，或给比较硬的边缘增加质感。可以给地貌增加类似侵蚀的质感

#### Material Linker/材质链接器

#### Shading Layer Editor/着色层编辑器
根据一些规则，自动给场景中的物体赋予材质，Shading Layer流程在制作动画同一场景不同镜头时效率非常高

**使用方法：**
1. 在Browser中新建Shading Layer
2. 在Shading Layer中添加规则，一般是设置要上材质的物体的路径，设置好要上的材质
3. 在3D View中选择要使用的Shading Layer

**如果要同时使用多个Shading Layer，可以创建一个总的Shading Layer，将其他的Shading Layer作为它的子着色层**

### Preferences/偏好设置
#### Application
###### Evaluation
- Max Core Count----------------使用的最大CPU核心数
###### Rendering
- Acceleration Mode-------------加速模式
  - Full interactivity--------------以交互为主
  - Favor interactivity over speed--交互超过渲染速度
  - Favor speed over interactivity--渲染速度超过交互
  - Rotation Variance-------------以渲染速度为主
- Displacement Storage Mode-----置换贴图存储模式
  - Favor Memory------------------内存优先
  - Favor Speed-------------------速度优先，很占用系统内存，如果电脑内存大，可以选择速度优先




