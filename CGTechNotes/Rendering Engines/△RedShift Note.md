**特别要注意：RedShift渲染器默认是sRGB流程，不是线性流程，纯黑不代表0，而纯白不代表1，因此在使用贴图控制参数时会发现结果不是想要的结果。在使用时如果贴图控制的是颜色，可以直接连接节点，如果贴图控制的是数值参数，需要先连接一个颜色校正（Color Correct）节点，再连接到数值参数端口。不连接颜色校正（Color Correct）节点也没错，但是结果会和预想的不同**

# Object/对象
## Environment/环境
用来制作体积光（丁达尔现象），模拟雾霾等
**注意开启体积光，需要在灯光的Volume选项中让Contribution值不为0，否则不会产生体积光效果**
- Volume Scattering/体积散射
**注意这里的体积与Volume对象不同，这里的体积是遍布整个场景的，在制作体积光时首先要创建一个灯光**
  - General
    - Tint--------------------------体积光颜色，注意这里的颜色也要和灯光颜色配合
    - Scattering--------------------散射数量，决定体积光散射的强度
    - Attenuation-------------------体积光衰减，控制当灯光穿透体积时有多少光线会被体积所吸收，强度越强，体积光越暗
    - Phase-------------------------相位，控制体积光各向异性，基于面向或远离摄像机对散射外观进行有偏计算。大于0是正向散射，小于0是反向散射，效果是会让体积光前的对象边缘模糊并带有光晕效果
  - Fog---------------------------雾
雾是不基于灯光的遍布整个场景的体积
**注意开启雾，需要General中的Attenuation值不为0**
    - Emission----------------------雾颜色
    - Camera Exposure Compensation--雾与摄像机曝光相关
    - Height------------------------雾高度
这里是控制雾浓度从哪里开始衰减，可以配合Environment对象的Y轴坐标来综合控制雾的高度，如要让雾从高度为500的地方开始出现，并衰减，可以将Height和Y坐标都设为500
    - Horizon Blur------------------雾边缘模糊
    - Use Transform-----------------取消勾选后将不再使用Environment对象的移动旋转缩放，可以使用下面两个参数手动对雾进行操作
    - Ground Point------------------雾旋转的基准点
    - Ground Normal-----------------地面法线，控制雾的方向，默认Y为1，是朝上
  - Ray Contribution Scales
    - Camera------------------------雾对整体亮度影响
    - Reflection--------------------雾对反射影响
    - GI----------------------------雾对GI影响
**在制作如从窗户射出的光、路灯等体积光，一般可以使用聚光灯**


## Sun&Sky Rig/日光和天空
日光创建后通常会非常亮，可以通过调节日光强度或调节摄像机曝光值来控制
### Sky/天空
- General
  - Intensity Multiplier----------日光强度
  - Use Non-Physical Intensity----使用非物理强度，开启后不符合现实物理精度，一般不开启
- Atmosphere
  - Turbidity---------------------大气浑浊度
  - Ozone-------------------------臭氧浓度，它控制太阳的黄色有多黄，默认为0.35，一般保持默认即可
  - Horizon Height----------------海平面高度
  - Horizon Blur------------------海平面模糊程度，控制天空与地面接缝处的模糊程度
  - Ground Color------------------地面颜色
  - Night Color-------------------夜晚颜色
- Color Adjustment
  - Red-Blue Shift----------------红-蓝颜色偏向，数值增大，会慢慢变红
  - Saturation--------------------饱和度
### Sun/太阳
  - Create Physical Sun-----------添加物理太阳
  - Remove Physical Sun-----------移除物理太阳
  - Sun---------------------------选择太阳对象
  - Sun Direction-----------------太阳方位
  - Sun Disk Intensity------------太阳光强度，但是调节此参数没有任何效果
  - Sun Disk Scale----------------太阳大小，控制阴影的柔和程度
  - Sun Glow Intensity------------太阳光辉光强度
### Overrides/覆盖
  - Force Alpha To Zero-----------
- Ray Type Enable
  - Background--------------------背景显示
  - Reflection--------------------影响反射
  - Reflection Intensity----------影响反射强度
  - Refraction--------------------影响反射
  - Refraction Intensity----------影响折射强度
  - GI----------------------------影响全局光照
  - GI Intensity------------------影响全局光照强度

**注意可以给Sky添加太阳标签，用时间来调节日光属性**


## Proxy/代理
用来读取RS代理文件，使用代理的好处是场景在摄像机范围外的部分不进行渲染计算，极大缩短了渲染时间，特别是使用克隆时，节约系统资源
使用方法，在导出中可以将模型导出为RedShift Proxy（*.rs）文件，使用Proxy对象导入.rs文件
- 对象
  - File--------------------------读取.rs文件
  - Display
    - Show Bounding Box-----------显示范围框
    - Preview
      - Off-----------------------不显示预览
      - Bounding Box--------------显示为边界框
      - Mesh----------------------显示为模型
    - Materials
      - Materials From
        - Proxy File----------------材质来自代理文件
        - Object--------------------材质来自对象



## Volume/体积对象
用来读取VDB文件
**注意VDB文件路径不要有中文**
**如果是Houdini生成的VDB，XZY轴的尺寸一般都要设为100倍**
- File
  - Volume------------------------静态VDB
    - Path--------------------------VDB路径
  - Animation---------------------动态VDB
    - Mode--------------------------动画模式
- Display-----------------------显示模式
  - Show Bounding Box-------------显示线框
  - Preview-----------------------预览模式
    - Off---------------------------不显示预览
    - Bounding Box------------------显示为黑箱
    - Points------------------------显示为点（可以大致看到VDB形状）
  - Maximum Points to Display-----显示的点数（数值越高，显示越接近VDB形状）
  - Prune Threshold---------------删除阈值
- Motion Blur
  - Velocity Grid X---------------调整X轴运动模糊速度
  - Velocity Grid Y---------------调整Y轴运动模糊速度
  - Velocity Grid Z---------------调整Z轴运动模糊速度
- Information
  - Channels----------------------通道信息

**需要注意的是RS灯光默认不能给VDB产生照明，导入VDB时会场景一片漆黑，需要在灯光的Volume选项中增大Contribution Scale值，数值越大，灯光照明效果越明显**



# Light/灯光
## Area Light/区域光
### General/常规
- Preview/预览
用来调节视图窗的灯光显示，不影响渲染效果
  - Wireframe---------------------视图窗中灯光形状、范围显示
  - Illumination------------------视图窗中灯光照亮显示
  - Illumination Adjustment-------视图窗中灯光亮度
- General
  - Mode--------------------------灯光模式
    - Color-------------------------使用颜色控制
    - Temperature-------------------使用色温控制
  - Texture-----------------------用贴图控制灯光颜色
  - Unit Type---------------------灯光单位类型
    - Image-------------------------类型为Image时，强度倍增一般在0-80之间调节
    - Luminous Power(lm)------------此模式灯光亮度不受光源面积和大小影响
    - Radiant Power(W)--------------此模式灯光亮度不受光源面积和大小影响
  - Intensity Multiplier----------强度倍增，控制灯光强度，区域光自带衰减
- Decay/衰减
  - Type--------------------------衰减方式
    - Inverse-square----------------平方倒数（符合物理精度），一般保持默认即可
- Area/区域
  - Shape-------------------------区域形状
    - Rectangle---------------------矩形
    - Disc--------------------------圆盘
    - Sphere------------------------球状
    - Cylinder----------------------圆柱
    - Mesh--------------------------网格，以模型创建灯光
  - Mesh--------------------------拖入模型
  - Size X------------------------X方向尺寸
  - Size Y------------------------Y方向尺寸
  - Size Z------------------------Z方向尺寸
  - Visible-----------------------光源是否可见
  - Bi-Directional----------------双面发光，要注意双面发光不能产生路径追踪
  - Normalize Intensity-----------灯光标准化，灯光照射的亮度不随灯光大小变化
  - Samples-----------------------灯光采样值
### Ray/光线
- Contribution
  - Affects Diffuse---------------影响漫射
  - Affects Specular--------------影响高光
  - Matte Shadow Illuminator------
- Scale
  - Diffuse-----------------------灯光对漫射影响程度
  - Glossy------------------------灯光对高光影响程度
*调节高光的强弱非常方便*
### Volume/体积
- Contribution Scale------------灯光照明强度
**需要注意的是RS灯光默认不能给VDB产生照明，导入VDB时会场景一片漆黑，需要在灯光的Volume选项中增大Contribution Scale值，数值越大，灯光照明效果越明显**
### Shadow/阴影
- Enable------------------------开启阴影
- Transparent-------------------控制阴影透明度
- Softness----------------------控制阴影柔和度
- Samples-----------------------阴影采样值，阴影噪点多的时候提高阴影采样值
- Softness Affects Gobo---------让点光源像区域光一样柔和
### Photon/光子
用来开启焦散，勾选Emit Caustic Photons，给焦散对象添加Object标签，在Visibility中激活Override，勾选Casts Caustic Photons，在渲染设置里取消IPR渐进式渲染（Force enabled for IPR）
- Caustics
  - Emit Caustic Photons----------激活焦散
  - Intensity Multiplier----------焦散强度，数值越高焦散效果越强
  - Number of Photons to Emit-----发射的光子数，数量越多焦散效果越强

### Project/工程
用来灯光排除

## Point Light/点光源
现实中不存在点光源，一般不使用，但是如果场景中几何体非常小，又需要光照，这时可以使用点光源来照明。因为点光源是一个点，所以阴影非常硬，如果需要制作很硬的阴影，可以使用点光源
### General/常规
- General
  - Intensity Multiplier----------强度倍增，控制灯光的衰减范围，在衰减范围中才会照亮场景

## Spot Light/聚光灯
### General/常规
- Spot
调节聚光灯外角内角，聚光灯内角到外角之间有衰减，内角内部为实心
  - Cone Angle--------------------聚光灯外角角度
  - Fall-off Angle----------------聚光灯内角角度

## Infinite Light/远光灯
远光灯没有衰减，适合给大场景打光，只有旋转的H和P值对灯光起作用，改变位置属性没有效果，远光灯有一根白线代表了照明方向，在阴影面板可以调节阴影柔和度

## Dome Light/穹顶光
用来加载HDR贴图
### General/常规
- General
  - Dome Map----------------------穹顶贴图，加载HDR贴图，直接将HDR贴图拖入Path
- Gamma
调整HDR的参数
  - Exposure----------------------曝光度,调节HDR亮度
  - Saturation--------------------饱和度，调节HDR颜色强度，如果不需要HDR有颜色，直接将饱和度调为0
- Environment/环境
  - Enable Background-------------启用背景,取消勾选后HDR隐藏
  - Alpha Channel Replace---------勾选后产生Alpha通道
- Back-Plate
  - Enable------------------------勾选后加载一张贴图，贴图会作为场景的背景
- Gamma
调整背景图片的参数

## IES Light/IES光
### General/常规
- General
  - IES Profile-------------------载入IES文件

## Portal Sun/门户光
一般搭建房屋等半封闭场景时，在开窗的地方放置门户光，作用是告诉渲染器这个地方需要更多的光子，从而更好地照亮场景
**注意门户光没有打光的效果，不添加别的灯光不会照亮场景**
**注意门户光要和日光或Dome Light配合使用，将日光或Dome Light拖入Environment Shader中，才会起作用**

## Physical Sun/日光
### General/常规
- General
  - Intensity Multiplier----------日光强度
  - Use Non-Physical Intensity----使用非物理强度，开启后不符合现实物理精度，一般不开启
  - Sun Disk Scale----------------太阳大小，控制阴影的柔和程度
- Atmosphere
  - Turbidity---------------------大气浑浊度
  - Ozone-------------------------臭氧浓度，它控制太阳的黄色有多黄，默认为0.35，一般保持默认即可
  - Horizon Height----------------海平面高度
- Color Adjustment
  - Red-Blue Shift----------------颜色偏向
  - Saturation--------------------饱和度
**一般不直接使用Physical Sun而是使用Sun&Sky Rig，会有物理天空配合日光**

# 摄像机
## Standard/标准摄像机
### 标签
  - Motion Blur-------------------激活运动模糊
  - Camera Type-------------------摄像机类型
- Environment
  - Environment-------------------环境，可以贴HDR贴图或背景图片
具体用法是新建一个材质球，进入节点编辑器，添加Environment节点，连接到Output节点的Environment端口，在Environment节点中加载图片，再将材质拖入摄像机标签的Environment中
### Exposure/曝光
**一般都在后期调整，而不是在这里调整**
调整这里的参数来控制运动模糊或景深时，并没有真正改变摄像机的快门时间，只是用来平衡场景中的光线的
- Enable------------------------激活
- Film Settings
  - Film Speed(ISO)---------------ISO,值越大，画面越亮
  - Shutter Time Ratio------------快门速度，值越大，画面越暗
  - f-Stop Number-----------------光圈级数，值越大，画面越暗
  - Whitepoint--------------------白平衡基准
  - Vignetting--------------------暗角
- Tone Mapping------------------色调映射
  - Allowed Overexposure----------限制曝光，用来限制最大亮度，数值越高，画面中最亮的地方越亮，如果场景有过曝，可以把限制曝光值调小
  - Allow Overexposure Desaturation--勾选后调节Allowed Overexposure时，也会针对相同的数值进行去饱和度处理
  - Black Crush Threshold---------暗部范围，数值越大，暗部范围越大
  - Black Crush Amount------------数值越大，暗部越暗，类似增加画面对比度效果
  - Saturation--------------------饱和度
### Bokeh/散景，控制景深效果
  - Enable------------------------激活
- Focus Settings
  - Derive Focus Distance from Camera--使用C4D摄像机自带焦距
  - Focus Distance----------------焦距（一般激活使用C4D摄像机自带焦距，便于控制）
  - CoC Radius--------------------虚化强度，和Power配合调节，数值越高，模糊的地方越多
  - Power-------------------------也可以控制虚化强度，但是Power值越高，亮部会趋于环状
  - Aspect------------------------虚化方向，小于1时上下方向虚化，大于1时左右方向虚化
- Shutter Blades
  - Blade Count-------------------控制高亮的形状，0为圆形，3为三角形，4为四边形，5为五边形...，一般用5或6效果最好
  - Blade Angle-------------------亮部旋转
- Image
一般不使用此功能，但是使用此功能可以制作一些创意效果
  - Use Bokeh Image---------------激活用图片控制景深
  - Normalization Mode------------控制模式
  - Image-------------------------用图片来控制景深，会影响景深模糊地方的颜色和高亮区域的形状
一般使用两种类型的图片：
一种是黑白贴图，来控制高亮区域形状，比如白色五角星周围黑色，这时画面会变暗，将Normalization Mode改为Unit Intensity模式，贴图就只控制高亮形状
一种是方形贴图，周围黑色，中间为圆形，圆形是一种颜色到白再到另一种颜色的渐变，如蓝-白-红渐变（使用PS制作），将Normalization Mode改为White Color Sun模式，这个渐变颜色会影响整个画面的景深的颜色，效果很好
### Distortion/扭曲
  - Enable------------------------激活
  - Distortion Image--------------用一张图片来进行画面扭曲

## Fisheye/鱼眼摄像机
鱼眼摄像机会自动忽略默认的焦距
### 标签
- Fisheye Camera
  - Horizontal Scale--------------横向比例，用来让横向占满屏幕
  - Vertical Scale----------------纵向比例，用来让横向占满屏幕
根据勾股定理，如果画面比为1：1，要满屏横向纵向比例均为1.414，如果画面比为16：9，要满屏横向纵向比例均为1.145

## Spherical/球形摄像机
可以用来制作HDR全景图片和视频，要注意HDRI宽高比为2:1
## Cylindrical/圆柱形摄像机
与球形摄像机类似
## Stereo-Spherical/立体球体摄像机
用于一些球状的VR渲染


# 材质
## Material材质
最常用材质
### Base Properties/基本属性
- Preset-----------------------材质预设
  - Custom-----------------------自定义
  - Glass------------------------玻璃
  - Tinted Glass-----------------有色玻璃
  - Water------------------------水
  - Plastic----------------------塑料
  - Aluminum---------------------铝
  - Copper-----------------------铜
  - Gold-------------------------金
预设的金材质比较亮，且比较光滑，是金属金，而制作中一般要把亮度提高一点，增加粗糙度，加一个凹凸或法线贴图，让黄金更有质感
  - Iron-------------------------铁
  - Lead-------------------------铅
  - Platinum---------------------铂金
  - Silver-----------------------银
  - Milky Coffee-----------------牛奶咖啡
  - Jade-------------------------翡翠
  - Paper------------------------纸
#### Diffuse/漫射
  - Color------------------------调节颜色
  - Weight-----------------------颜色权重，类似于透明度，0为没有颜色，1为完全有颜色
  - Roughness--------------------漫射粗糙度，不常用
  - Back-lighting/Translucency---调节背光，让对象可以透光，可以简单模拟纸张、树叶等简单透光和简单的SSS效果，使用时一般和Diffuse中的Color一致
#### Reflection/反射
**RS的反射自带菲涅尔效应**
  - Color------------------------反射颜色
**绝大多数非金属反射颜色均为白色，金属要将漫射权重调为0**
  - Weight-----------------------反射权重，类似于透明度，0为没有反射，1为完全有反射
  - Roughness--------------------反射粗糙度，反射模糊，与OC不同的是RS粗糙度调很大效果才比较明显
  - Samples----------------------采样率
  - BRDF-------------------------反射类型（三种都符合物理精度）
    - Beckmann---------------------默认常用类型，这是用于模拟常规物体表面反射类型，适用于大部分情况，更适合塑料
    - GGX--------------------------高光与暗部区域的衰减看起来像云雾一般的效果，它模拟的是一种微相分布，实现金属上常见的高光衰减效果，这种高光衰减效果称作拖尾（Trail），它的算法最适合描述金属一类的反射现象，但是GGX的各向异性表现不太好，制作拉丝金属时不使用GGX
    - Ashikhmin-Shirley------------与Beckmann效果差不多，周围会多一圈类似毛玻璃效果，优点是噪点比较少，各向异性表现最好，制作拉丝金属时一般使用Ashikhmin-Shirley
  - Anisotropy-------------------各向异性，各向异性就是根据旋转的方向，在反射面将反射拉长，用于制作金属拉丝效果，Ashikhmin-Shirley各向异性表现最好，制作拉丝金属时一般使用Ashikhmin-Shirley
  - Rotation---------------------各向异性旋转
  - Fresnel Type-----------------菲涅尔反射类型
    - IOR(Advanced)----------------高级折射率，通过分别定义RGB三个通道的反射强度和吸光系数来控制反射强度
      - IOR--------------------------分别为RGB三个通道的反射强度
      - Absorption（k）--------------吸光系数
    - Color+Edge Tint--------------一个颜色控制金属菲涅尔正面的颜色，一个颜色控制金属菲涅尔边缘的颜色
**此模式不符合物理规律，但是效果很好，在制作一些创意效果时使用的很多**
      - Reflectivity-----------------调节金属正面颜色
      - Metalness--------------------调节金属边缘面颜色
    - Metalness--------------------使用颜色来控制金属颜色，同时控制反射强度
      - Reflectivity-----------------调节金属颜色，注意颜色亮度会同时控制反射强度,一般HSV中V值不要高于40%
      - Metalness--------------------金属度，辅助Reflectivity调节，在不改变反射强度的前提下，淡化金属颜色，值越高越偏向金属，值越低，越偏向非金属，可以使用贴图控制让场景中有的是绝缘体有的是金属
    - IOR--------------------------仅用一个IOR值来控制反射强度
      - IOR--------------------------IOR值越大，反射越强，IOR为0时为镜面反射，塑料一般为0.3左右，，玻璃在1.52左右，金属一般为7-8
#### Refraction/Transmission------折射，一般把Diffuse关掉
  - Color------------------------折射颜色
  - Weight-----------------------折射权重，类似于透明度，0为没有折射，1为完全有折射
  - Samples----------------------采样率
  - Link to Reflection-----------链接到反射的粗糙度和折射率，一般保持勾选
  - Dispersion-------------------色散
  - Thin Walled------------------薄壁，勾选后为空心玻璃，不勾选为实心玻璃
  **很重要，使用很方便**
#### Sub-Surface------------------次表面散射
**在做SSS效果时要在渲染设置中把Force enabled for IPR（IPR渐进式渲染）关掉**
**Redshift中的散射效果可控性很大，不用像OC中一样必须是以玻璃为基础材质，可以是漫射材质，漫射颜色也可以影响最终效果**
  - Attenuation Units------------衰减模式
    - Transmittance----------------透射比模式，定义什么光可以透过物体
      - Transmittance Color----------透射颜色，控制物体可以透过什么颜色的光，颜色越深，物体密度越大，越不透光
      - Absorption Scale-------------吸收能量大小，数值越大，越不透光
    - Extinction-------------------消失模式，定义什么光无法透过物体，会出现类似反向的效果（不常用）
      - Extinction Coeff-------------不能透过的颜色，物体呈现反向颜色
**在制作有机物时可以让这里是透射颜色的补色**
      - Extinction Scale-------------控制材质的密度
  - Scatter Coeff----------------散射颜色
  - Scatter Scale----------------散射强度
  - Phase------------------------散射各向异性（默认即可），控制光从哪里进入从哪里出去，如果为负数，光线会倾向于向光散射，如果为正数，光线会倾向于背光散射
  - Samples----------------------采样

### Multi-SSS/高级SSS效果
**在做SSS效果时要在渲染设置中把Force enabled for IPR（IPR渐进式渲染）关掉**
高级SSS效果一般做皮肤等复杂的SSS效果时才使用
- General
  - Amount-----------------------SSS强度
  - Radius Scale-----------------光线可以穿过的距离
- Layer1
  - Color------------------------散射颜色
  - Weight-----------------------强度
  - Radius-----------------------半径
**注意如果要符合物理精度，三个层的Weight加起来必须等于1**

### Coating/表面涂层
在现有材质的表面涂上一层材质，可以模拟车漆或表面潮湿、划痕等
- General
  - Color------------------------涂层颜色
  - Weight-----------------------强度
  - Roughness--------------------粗糙度
  - Samples----------------------采样
- Advanced/高级
  - Transmittance----------------透射颜色，可以在不改变高光颜色的情况下模拟图层颜色
  - Thickness--------------------厚度，指图层在表面上的厚度

### Overall/整体
  - Overall Tint-----------------调节模型整体的色相，原理是让材质的所有通道乘以这个颜色
  - Opacity----------------------模型透明度
  - Emission---------------------模型发光
  - Emission Weight--------------模型发光强度

### Optimizations/优化
  - Enable Trace Depth Overrides-激活优化追踪深度，激活后可以自定义材质的反射和折射深度，即反射和折射次数
- Reflection
  - Trace Depth------------------反射深度，设置反射多少次
  - Cut-off Override Enable------激活反射阈值
  - Cut-off Threshold------------反射阈值，光子能量小于阈值后，不再计算反射，数值越大，反射计算越快，但越不精确，默认0.01即可
  - Cull Dim Internal Reflections--不计算模型内部反射，激活后不符合物理精度，但加快渲染速度，默认勾选
- Refraction
  - Trace Depth------------------折射深度，设置折射多少次
  - Cut-off Override Enable------激活折射阈值
  - Cut-off Threshold------------折射阈值，光子能量小于阈值后，不再计算折射，数值越大，反射计算越快，但越不精确，默认0.01即可
- Combined Trace Depth-----------总体的追踪深度

### Advanced/高级
- Diffuse
  - Direct Scale-----------------直接光对漫射的影响
  - Indirect Scale---------------间接光对漫射的影响
- Reflection
  - Direct Scale-----------------直接光对反射的影响
  - Indirect Scale---------------间接光对反射的影响
  - Covert From Glossiness to Roughness--粗糙度变为光滑度，勾选后在基本属性中的粗糙度变为光滑度，0为最粗糙，1为最光滑，一般不勾选
- Coating
  - Direct Scale-----------------直接光对表面涂层的影响
  - Indirect Scale---------------间接光对表面涂层的影响
  - Covert From Glossiness to Roughness--粗糙度变为光滑度，勾选后在基本属性中的粗糙度变为光滑度，0为最粗糙，1为最光滑，一般不勾选
- Refraction
  - Covert From Glossiness to Roughness--粗糙度变为光滑度，勾选后在基本属性中的粗糙度变为光滑度，0为最粗糙，1为最光滑，一般不勾选
  - Decouple IOR From Roughness--勾选后折射率与粗糙度无关，不符合物理精度，一般不勾选
  - Shadow Opacity---------------阴影透明度
  - Opacity Affects Alpha Channel--透明度影响Alpha通道，默认勾选
  - Block Volumes In Sub-Surface Mediums--
- Energy Conservation Mode-------能量守恒模式
  - RGB----------------------------用颜色影响下一层
  - Mono---------------------------用亮度影响下一层
- Overall Tint Affects Emission--勾选后发光颜色会受Overall中Overall Tint（整体色相）的影响
- Anisotropy-------------------模型表面各向异性（不常用）

## Architectural/建筑材质
功能完全被Material材质取代，以后版本可能会取消此材质

## Car Paint/车漆材质
车漆是一种高级材质，原理是分为3层，底层是基础颜色，中间层是金属颗粒或金属碎片，顶层是透明反光层，RS将复杂的车漆材质专门分出来作为材质预设，默认效果就很好
### Base Layer Diffuse/基本层漫射
- Pigment Color----------------底层颜色
- Weight-----------------------颜色强度
- Edge Falloff
  - Color------------------------菲涅尔边缘颜色，一般默认黑色
  - Curve Factor-----------------菲涅尔边缘范围
### Base Layer Specular/基本层镜面反射
- General
参数与Material材质的反射参数基本相同

  - Glossiness-------------------光滑度，与粗糙度相反，数值越大越光滑
  - Hightlights Only-------------只保留高光，一般不勾选
- Fresnel Control--------------调整菲涅尔反射
  - Facing Reflectivity----------正面反射率（正对摄像机的地方）
  - Perpendicular Reflectivity---垂直面反射率（与摄像机垂直的地方）
  - Curve Factor-----------------过渡曲线
### Metallic Flakes/金属薄片
调整中间金属颗粒或金属碎片的层
- Reflection
参数与Base Layer Specular中的参数基本相同
  - General
    - Glossiness-------------------光滑度，与粗糙度相反，数值越大越光滑
    - Hightlights Only-------------只保留高光，一般不勾选
  - Fresnel Control--------------调整菲涅尔反射，会基于金属片所面对的方向，控制它的亮度
    - Facing Reflectivity----------正面反射率（面向摄像机的金属片），值越大颗粒越明显
    - Perpendicular Reflectivity---垂直面反射率（背向摄像机的金属片），值越大颗粒越明显
    - Curve Factor-----------------过渡曲线，数值越低，权重越偏向垂直面反射率，
- Definition-------------------清晰度
  - Density----------------------金属碎片密度
  - Decay Distance---------------衰减距离，数值调大时会提高金属片整体的粗糙度，高光部分会越来越宽，在表面会看到一个更长的衰减区域
  - Variation--------------------片状分布，数值越大碎片越明显
  - Scale------------------------金属碎片大小
### Clear Coat Reflection/外层反射
参数与Base Layer Specular中的参数基本相同
- General
  - Glossiness-------------------光滑度，与粗糙度相反，数值越大越光滑
- Fresnel Control--------------调整菲涅尔反射
  - Facing Reflectivity----------正面反射率（正对摄像机的地方）
  - Perpendicular Reflectivity---垂直面反射率（与摄像机垂直的地方）
  - Curve Factor-----------------过渡曲线
### Advanced/高级选项
- Enable Trace Depth Overrides--启用覆盖最大跟踪深度
- Max Reflection Trace Depth----最大反射深度
- Cut-off Override
  - Enable------------------------激活反射阈值
  - Threshold---------------------反射阈值，光子能量小于阈值后，不再计算反射，数值越大，反射计算越快，但越不精确
- Bump
  - Disable Base Layer Bump Mapping----勾选后，凹凸贴图对底层无影响
  - Disable Clear Coat Bump Mapping----勾选后，凹凸贴图对外层无影响
  - Add Bump Input To Material Bump----此参数没有任何效果

## C4D Shader/C4D程序纹理材质
非常强大的功能，可以让RedShift直接读取C4D所有自带的程序纹理，这是RS渲染器强大的地方
**原理是C4D Shader节点连接到Texture节点，再进行输出**

## Hair/毛发材质
RS可以直接识别C4D自带的毛发材质，也可以添加一个RS的毛发材质，打开节点编辑器可以看到默认的RS Hair还是用C4D自带的毛发材质来调节毛发，相关节点已经连接好，也可以自己连接节点来调节
### General
#### Internal Reflection/内部反射
用来定义毛发基础颜色，对最终颜色表现非常大
#### Diffuse/漫反射
一般设为0，因为数值调高不符合物理精度，使用时数值尽量调低
#### Transmission/颜色传递
模拟毛发背光时半透效果
#### Primary Reflection/主要反射
主要用来调整毛发的光泽
- Angular Shift----------------调整毛发倒刺角度
- Enable Fresnel---------------勾选开启菲涅尔，毛发高光到边缘有一个过渡
### Transparency/透明
设置毛发的透明，默认即可，调整后会大大增加渲染时间

## Incandescent/自发光材质
反光板常用这种材质，会发出淡淡的白光,可以模拟电脑屏幕、霓虹灯等
### Illumination
- Color------------------------发光颜色
- Temperature------------------色温
- Mode-------------------------发光模式
  - Color------------------------使用灯光颜色
  - Temperature------------------使用色温
- Intensity Multiplier---------发光强度
- Double-Sided-----------------双面发光
- Apply Camera Exposure Compensation----使用相机曝光补偿，与摄像机曝光挂钩
### Ray Type Intensity Multipiers
- Reflection-------------------发光对反射的影响
- Refraction-------------------发光对折射的影响
- GI---------------------------是否产生GI

## Skin/皮肤材质
皮肤材质有3层散射，可以给皮肤贴图添加颜色校正来分别控制3层散射
### Scattering Layers/散射层
- Common
  - Radius Scale-----------------散射距离
  - Overall Scale----------------颜色亮度
  - Diffuse Amount---------------漫射强度，值越趋向1，越受漫射影响，越趋向0，越受SSS效果影响
  - Disable Diffuse Bump Mapping-勾选后凹凸不影响漫射，一般不勾选
  - Nomalize Diffuse Weights-----标准化能量，勾选后光线射出物体时比射入物体时能量少，遵循能量守恒，符合物理精度
- Shallow Scatter--------------浅皮层散射
影响普通的漫射
- Mid Scatter------------------中间皮层散射
一般偏黄或偏绿
- Deep Scatter-----------------深皮层散射
一般趋向于深红色
- Single Scattering------------简单散射，把颜色设为黑色，扩大散射范围，可以让整体变暗，不常用
### Reflections/反射
- Primary Reflection-----------基础反射
皮肤正常的反射
- Secondary Reflection---------二次反射
模拟汗液的反射
- General
  - Disable Reflection Bump Mapping--勾选后凹凸贴图不影响反射，一般不勾选
- Optimization-----------------优化
  - Specular Highlights Only-----只有刚
  - Enable Trace Depth Overrides-激活优化追踪深度，激活后可以自定义材质的反射和折射深度，即反射和折射次数
  - Max Trace Depth--------------最大追踪深度
- Cut-off Override-------------折射阈值
  - Enable-----------------------激活折射阈值
  - Threshold--------------------折射阈值，光子能量小于阈值后，不再计算折射，数值越大，反射计算越快，但越不精确，默认0.01即可
### Bump Mapping/凹凸贴图
- Add Bump Input To Material Bump--增加凹凸贴图入口，没有作用，添加凹凸贴图直接在节点编辑器中添加

## Sprite/透明材质
一般直接在节点编辑器中使用Sprite节点，用法见Sprite节点

## SSS
**SSS材质要在渲染设置中渐进式渲染关掉，不然IPR无法预览SSS效果**
### General Parameters/通用参数
- Preset-----------------------预设
  - Skin(Brown)------------------深色皮肤
  - Skin(pink)-------------------浅色皮肤
  - Skin(Yellow)-----------------黄色皮肤
  - Milk(Skimmed)----------------脱脂牛奶
  - Milk(Whole)------------------全脂牛奶
  - Marble-----------------------大理石
  - Ketchup----------------------番茄酱
  - Cream------------------------冰激凌
  - Potato-----------------------土豆
  - Spectralon-------------------特氟龙涂料
- Scale------------------------SSS强度
- IOR--------------------------折射率
### Diffuse and Sub-Surface Scattering Layers/漫射和SSS层
- Diffuse Amount---------------漫射强度，值越趋向1，越受漫射影响，越趋向0，越受SSS效果影响
- Disable Diffuse Bump Mapping-勾选后凹凸不影响漫射，一般不勾选
- Sub-Surface
  - Sub-Surface Color------------吸收颜色
**吸收颜颜色太深散射颜色就看不出来，如果想体现散射颜色，吸收颜色设置的浅一些
  - Scatter Color----------------散射颜色
  - Scatter Radius---------------散射半径，半径越大，散射效果越明显
- Single Scattering
  - Enable-----------------------激活单一散射
  - Phase------------------------散射产生的各向异性，小于0为反相，大于0为正相
  - Override Coefficients--------覆盖系数，勾选后整体的散射由下面3个参数控制
  - Transmittance----------------透射比，设置透射颜色，颜色越深，透射效果越明显
  - Thickness--------------------厚度，参数越小，透射效果越明显，0为无效果
  - Scatter Amount---------------散射强度

## Particle/粒子材质
本质上就是给Material材质加了一个Color User Data节点，来读取粒子颜色
**注意RS只识别X-Particle 3.0以上版本**

## Volume/体积材质
### Basic/基础设置
- Scatter
  - Channel----------------------选择VDB的通道,一般选择Density通道
  - Scatter Coefficient----------散射值，值越大穿透VDB后投射出的光越强，画面越亮
  - Tint-------------------------设置散射颜色，影响VDB颜色
  - Scatter Remap Ramp-----------设置散射渐变颜色（一般不要动左侧的黑色，否则VDB边缘抠不干净）
- Absorption
  - Absorption Coefficient-------吸收值，值越大VDB吸收光能量越多，画面越暗
  - Absorption Remap Ramp--------设置吸收渐变，在中间加一个点，点越向左移动，VDB越浓厚，点越向右移动，VDB越淡（一般不要动左侧的原点，否则VDB范围框会显示出来）
- Emission
用来渲染火焰等VDB
  - Channel----------------------选择VDB的通道,一般选择Temperature通道
### Advanced/高级设置
- Shadow Density Scale---------阴影透明度
- Density Remap Range----------密度重映射
  - Old Min----------------------原本的密度最小值，一般不要调整，调高会出现像素块
  - Old Max----------------------原本的密度最大值，调整参数来控制最终的密度，值越大，VDB越稀薄
  - New Min----------------------新的密度最小值，一般不要调整，调高会出现像素块
  - New Max----------------------新的密度最大值，调整参数来控制最终的密度，值越小，VDB越稀薄



# 节点编辑器
## Materials
#### Material Blender/混合材质节点
与OCtane的混合材质类似，支持多个材质混合
- Base Color-------------基础颜色，连接基础材质
- General
  - Layer1
    - Layer Color1--------------------图层1颜色，连接混合的材质
    - Blend Color---------------------混合颜色，间接贴图控制混合方式，黑色为基础颜色，白色为图层1颜色
#### Matte-Shadow Catcher/阴影捕捉节点
制作实景合成非常重要的功能
**原理是只保留阴影，其他部分变为透明，给地面加阴影捕捉材质后，实现模型放置在HDR环境上的效果**
- General
  - Base
    - Background Is Environment-------环境作为背景，勾选后平面消失，只留下阴影
  - Illumination
    - Diffuse
      - Catch Diffuse-------------------投射漫射，勾选后会捕捉漫射光
    - Shadows
      - Catch Shadows-------------------投射阴影，勾选后会保留阴影
      - Shadows Color-------------------阴影颜色
      - Shadows Alpha-------------------阴影透明度
- Reflections
  - Catch Reflections---------------添加反射
  - Color---------------------------反射颜色
  - Alpha---------------------------反射透明度
  - Weight--------------------------反射强度
  - Attenuation---------------------衰减
    - Enable--------------------------激活衰减
    - Distance------------------------距离，距离越大，反射越明显

- Ambient Occlusion
  - Enable--------------------------添加环境吸收，让阴影效果更强烈更真实
  - Samples-------------------------环境吸收采样
**官方推荐不使用此节点，而是给平面添加一个材质，然后给平面一个Object标签，在Matte中激活Override来实现阴影捕捉，方便进行反射、折射的控制，具体见Object标签参数**

#### Sprite/Alpha通道节点
可以将灰度贴图或带Alpha通道的贴图拖入Sprite节点，让对象有Alpha通道
节点连接方法是把material主节点的OutColor连接到Sprite的输入端口，Sprite的输出端口连接到Output的Surface端口
- General
  - Stencil
    - Opacity Calculation-------------透明度计算方式
      - From Color Intensity------------来自颜色强度（灰度图使用此方式）
      - From Alpha----------------------来自贴图Alpha
    - Stencil Opacity Threshold-------不透明度阈值
    - Texture Repeats-----------------贴图重复
**使用Sprite节点渲染出的结果和使用Opacity端口渲染出的结果相比，Sprite节点渲染出的结果阴影更厚**
**一般使用Alpha通道都使用Sprite节点，而不使用材质中Overall选项卡里的Opacity端口，因为使用Sprite节点后，透明的部分不参与光的运算，大大减少了计算量**

## Textures
#### AO/环境吸收（环境光遮蔽）节点
AO的原理是从一个点出发，它的各个方向都能到达天空，那么这个点呈现纯白色，若果它的各个方向都无法到达天空，那么这个点呈现纯黑色，整体形成一张灰度图
- General
  - Samples-------------------------采样值，如果黑色区域噪点太多，可以增加采样值
  - Bright.Color--------------------白色区域颜色
  - Bright.Alpha--------------------白色区域透明度
  - Dark.Color----------------------黑色区域颜色
  - Dark.Alpha----------------------黑色区域透明度
  - Spread--------------------------扩散，数值越大，黑白过渡越柔和
  - Falloff-------------------------衰减，也会影响黑白过渡，但是影响比较小
  - Max Distance--------------------衰减距离
  - Reflective----------------------反射，开启后会使用和光线投射获取像素一样的过程，从而加深颜色深度，效果类似提高对比度
  - Invert Normal-------------------反转法线，基本不使用此功能
  - Output Mode---------------------输出模式
    - Occlusion Using Bent Normals----输出为纯黑白
    - Sampled Environment-------------颜色受环境影响，会变成不是纯黑白，而是受到HDR贴图反射影响
    - Return Bent Normals(World Space)--输出法线颜色
  - Consider Same Object Only---------只影响相同对象，光线只会光照每个对象本身的遮挡，不考虑物体之间的遮挡

#### Camera Map/摄像机贴图节点
用来进行实景合成
- General
  - Image
    - Map-----------------------------导入背景图
  - Scaling--------------------------
    - Match Render Size---------------
    - Aspect Ratio--------------------
    - Apply Camera Exposure Compensation--
  - Camera
    - Camera Picker-----------------------导入摄像机



#### Curvature/曲率节点
曲率大的地方为白色，曲率小的地方为黑色，如立方体的棱为白色，面为黑色
- General
  - Mode
  - Radius--------------------------半径，调节黑色和白色的范围

#### Noise/燥波节点
- Color
  - General
    - Color1.Color--------------------第一个颜色
    - Color1.Alpha--------------------第一个颜色透明度
    - Color2.Color--------------------第二个颜色
    - Color2.Alpha--------------------第二个颜色透明度
    - Invert--------------------------反相
  - Remap
    - Bias----------------------------颜色偏向，小于0.5更偏向颜色1，大于0.5更偏向颜色2
- Noise
  - General
    - Noise Type----------------------燥波类型
  - Fractal/Turbulence
    - Complexity----------------------复杂度，控制细节层级，使用时可以根据效果一点一点往上
    - Amplitude Gain------------------振幅增益，控制每次迭代的明亮度，反映到效果上与对比度类似，越接近0对比度越高
    - Frequency Scale-----------------燥波缩放
    - Distortion----------------------燥波细节
    - Distortion Scale----------------燥波细节缩放
  - Time
    - Source--------------------------来源
      - None----------------------------不产生效果
      - Constant------------------------恒定的，产生流动效果
      - User Time-----------------------调节数值会有流动效果，可以K关键帧，也可以用Xpresso中的时间节点连接到User Time来控制流动动画
- Coordinates
  - General
    - Source--------------------------改变燥波所在空间
    - Overall Scale-------------------整体缩放
    - Scale---------------------------各方向尺寸
    - Offset--------------------------各方向偏移值
        
#### Ramp/渐变和着色节点
有两个功能，相当于C4D自带的渐变和着色两个功能
- General
  - Input
    - Souce---------------------------源
      - UV Map--------------------------渐变功能
      - Alt-----------------------------着色功能，用Texture节点连接到Ramp的Input端口，可以用渐变颜色来映射贴图的颜色
    - Mapping-------------------------投射方式
      - Horizontal----------------------V向
      - Vertical------------------------U向
      - Diagonal------------------------斜向
      - Radial--------------------------锥形
      - Circular------------------------圆形
  - Adjust
    - Invert--------------------------反相
    - Noise Amount--------------------渐变中产生燥波
    - Noise Frequency-----------------燥波尺寸

#### Texture/图像节点
- General
  - Image
    - Animation-----------------------导入图像序列生成动画
  - Gamma Override
    - Enable--------------------------激活调节Gamma值
    - sRGB----------------------------
    - Gamma---------------------------调节Gamma值
  - UV
    - UV Channel----------------------UV通道,可以将模型的UV标签拖进去，调整UV
    - Mirror U------------------------镜像U向
    - Mirror V------------------------镜像V向
    - Wrap U--------------------------U向包裹
  - Remap
    - Scale---------------------------贴图尺寸，贴图的重复次数
    - Offset--------------------------贴图偏移
    - Rotate--------------------------贴图旋转
- Adjust--------------------------对贴图Alpha通道进行操作
  - Color Multiplier----------------用Texture节点连接，可以用图片灰度来定义当前贴图的Alpha
  - Color Offset--------------------颜色偏移
  - Alpha Multiplier----------------
  - Alpha Offset--------------------
  - Alpha Is Luminance--------------根据贴图亮度来生成Alpha通道
  - Default/Invalid Color.Color-----
  - Default/Invalid Color.Alpha-----
- Advanced------------------------高级，控制MIP贴图
**Mip Mapping(MIP贴图)，可以理解为图像纹理的细节层级，MIP来自拉丁语Multum In Parvo，它可以让渲染器使用较少的内存和纹理采样，从而节约渲染时间。原理是在渲染时RS会生成原始图像的低分辨率版，每调一级MIP，每个贴图的质量都是原先的一半，log(贴图最大分辨率）/log(2)=MIP级数。2k分辨率以上的贴图都会影响渲染速度**
  - Filter Enable-------------------MIP过滤模式
    - None----------------------------不使用MIP
    - Magnification-------------------放大时使用MIP
    - Magnification/Minification------放大和缩小时都使用MIP 
  - Bicubic Filtering---------------双立方过滤，不够选时贴图两个像素点之间的采样是线性的，勾选后采样是曲线的，柔和了像素点的插值，过渡会更平滑
  - Prefer Sharp Filtering----------偏好锐化过滤，勾选后调节Mip Bias，会让贴图出现马赛克,不勾选调节Mip Bias，会让贴图模糊
  - Mip Bias------------------------MIP偏差，0为不使用MIP，越往负值调整，过滤使用的越小，贴图渲染的分辨率越高，图像越清晰，但是动画不能往负值调整，会使画面闪烁，越往正值调整，过滤使用的越大，图像越模糊


#### WireFrame/线框节点
用来显示模型的布线
- General
  - Polygon Color.Color-------------多边形颜色
  - Polygon Color.Alpha-------------多边形
  - Wire Color.Color----------------线颜色
  - Wire Color.Alpha----------------线Alpha
  - Wire Thickness------------------线厚度
  - Show Hidden Edges---------------显示斜线
**可以将多边形颜色设为黑色，线颜色设为白色，然后连接到Material的Opacity Color端口和Diffuse Color或Emission Color端口控Alpha和颜色或发光，来制作镂空模型线条效果**


## Utilities
#### Bump Blender/凹凸混合节点
用来将多个凹凸贴图混合，使用时将一个Bump Map节点连接到Base Input端口，将其他的Bump Map节点连接到Layer中的Bump Input端口，可以将灰度图连接到Layer中的Bump Weight端口来控制凹凸分布，最后将Bump Blender节点连接到主材质节点的Overall-->Bump
- General
  - Additive Mode-------------------相加模式，勾选后为相加模式，不勾选为覆盖模式
#### Bump Map/凹凸节点
使用时用图像节点输入，再输出到主材质节点的Overall-->Bump Input端口
**法线贴图也使用凹凸节点，使用法线贴图时如果格式为JPG或PNG等线性颜色空间的格式，需要把Gamma改为2.2**
**2.6版新增了选择凹凸还是法线**

#### C4D Shader/C4D程序纹理节点
使用时连接到Texture节点，再进行输出，可以调用C4D所有自带的程序纹理
**使用Substance流水线时在RS中调用需要使用C4D Shader节点，在Shader中选择Substance着色器，加载Substance材质**

#### Color User Data/颜色用户数据节点
可以让RS读取对象的显示颜色、运动图形效果器控制的颜色等，一般最常用的是读取运动图形效果器控制的颜色，让模型在可调节反射折射等的基础上，还保留了运动图形颜色
- General
  - Attribute name------------------读取模式
    - MoGraph
      - Color---------------------------读取运动图形颜色
      - Index Ratio---------------------读取运动图形索引
    - Object
      - Object Color--------------------读取对象颜色
      - GeomID Color--------------------每个对象会有一个ID，读取对象ID，赋予不同的颜色，如果对默认赋予的颜色不满意，可以连接一个Ramp节点，渐变模式设为Alt，可以用渐变来指定颜色
    - Particles
      - Particle Color------------------读取粒子颜色，RS的Particle材质本质上就是给Material材质加了一个Color User Data节点，来读取粒子颜色

#### Constant/常数节点
Redshift单独把Xpresso中的常数节点拿出来，非常实用
- 数据类型
  - 实数----------------------------相当于OC中的Float节点
  - 颜色----------------------------相当于OC中的Color节点
  - 矢量----------------------------可以用来颜色控制，矢量的3个数值分别代表RGB值

#### Displacement/置换节点
使用时用图像节点输入到Tex Map端口，再输出到Output节点的Displacement端口
**注意进行置换时必须给对象Object标签，在Geometry开启置换，否则没有效果**
- General
  - Texture
    - Scale-------------------------比例，比例会和Object标签中的Displacement Scale联合运作，最终置换高度是Scale乘以Displacement Scale
    - Map Encoding------------------置换模式
      - Height Field------------------高度置换模式，使用普通的灰度图进行置换
      - Vector------------------------矢量置换，使用矢量图进行置换，矢量置换不仅仅是高度置换，还有X轴和Z轴的置换
  - Remap
    - New Range Min-----------------如果这里为0，颜色值大于黑色都会往外凸，如果设为-1，颜色大于50%灰的往外凸，小于50%灰的往里凹


#### Displacement Blender/置换混合节点
用来将多个置换贴图混合，使用时将一个Displacement节点连接到Base Input端口，将其他的Displacement节点连接到Layer中的Displacement Input端口，可以将灰度图连接到Layer中的Displacement Weight端口来控制置换分布，最后将Displacement Blender节点连接到Output节点的Displacement端口，给对象添加Object标签，在Geometry中勾选Override和Displacement Enabled
- General
  - Additive Mode-------------------相加模式

#### Fresnel/菲涅尔节点
一般连到粗糙度或反射强度，也可以连到发光、透明度等端口制作非常好玩的效果
- General
  - Falloff Color
    - Use Index of Refraction---------使用折射率
    - Curve Falloff-------------------曲线衰减，调整曲线衰减会不符合物理精度但是便于调整
    - Facing Color--------------------面向摄像机的颜色
    - Perpendicular Color-------------边缘颜色
  - IOR
    - Index of Refraction-------------折射率
    - Extinction Coefficient(k)-------
    - Correct Facing Color Intensity--矫正面向颜色强度，这个功能只在开启使用折射率时才有效果
**注意金属的菲涅尔效应是很弱的**

#### Hair Position/毛发位置节点
可以重新定义毛发的UV

#### Hair Random Color/毛发随机颜色节点
可以随机毛发颜色
- General
  - Color---------------------------随机的基本颜色
- Randomization
  - Hue Amount----------------------色相随机范围
  - Saturation Amount---------------饱和度随机范围
  - Value Amount--------------------色值随机范围
**需要注意的是随机的基本颜色可以添加Texture节点，用图片来控制，但是添加图片后RS会自动将图片颜色设置为从发根到发梢渐变分布，无法起到随机颜色效果，一般直接使用C4D自带毛发材质来控制随机颜色**

#### Integer User Data/整数用户数据节点
用来读取对象、运动图形等的ID值,用来给运动图形做随机颜色非常方便，添加一个相除节点，除以克隆的物体个数，然后连接到Ramp节点，用渐变控制随机颜色，如果不想出现死黑，添加先一个相加节点，加上1，再相除
**还可以用来单独控制克隆的每个物体的材质，操作方法：**
1. 新建Integer User Data节点，Attribute name选择MoGraph-->Object
2. 新建Shader Switch节点，将Integer User Data节点的Out连接到Selector端口，多个Material节点的Out Color端口连接到Shader端口
3. 把Shader Switch节点的Out Color端口连接到Output的Surface端口

#### Normal Map/法线节点
连接到主材质节点的Overall-->Bump Input端口，如果既有凹凸贴图又有法线贴图，使用Bump Blender节点将凹凸贴图和法线贴图混合，具体混合方法是将混合强度调为1，勾选相加模式

#### Ray Switch/射线转换节点
是一个优化节点，单独将正面背面颜色、反射、折射、GI用纯色来定义，可以减少反射、折射、GI等的计算量，缩短渲染时间，在场景过于复杂，渲染速度很慢的时候可以使用Ray Switch节点进行优化。
连接方式为Material节点的Out Color端口连接到Ray Switch节点的Camera-->Camera Color端口，Ray Switch节点的Out Color端口连接到Output节点的Surface端口
- General
  - Camera
    - Enable Front/Back---------------激活正反面颜色
    - Color.Color---------------------正面颜色，一般连接到Material节点的Out Color端口
    - Color.Alpha---------------------正面颜色Alpha
    - Back-face Color.Color-----------背面颜色
    - Back-face Color.Alpha-----------背面颜色Alpha
**如果需要正反两面材质不同，就使用Ray Switch节点，将两个Material节点分别连接到Color.Color和Back-face Color.Color端口，然后将Ray Switch节点的Out Color端口连接到Output节点的Surface端口**


#### Round Corners/圆角节点
连接到Material节点的Bump Input端口，可以给模型倒角，这个倒角是假倒角，模型本身没有改变
- General
  - Radius--------------------------倒角半径

#### Scalar User Data/实数用户数据节点
可以输出带小数点的实数
- General
  - Attribute name------------------读取模式
    - MoGraph
      - Object ID Normalized------------标准化运动图形索引，与Integer User Data中读取ID再添加相加、相除后效果相同，更方便
      - Weight--------------------------权重，注意要把效果器的权重变化打开，不然没有效果
      - Clone Offset--------------------克隆偏移
      - Time Offset---------------------时间偏移


#### Shader Switch/材质转换节点
将多个材质球连接到不同的Shader端口，将Out Color端口连接到Output节点的Surface端口，可以给对象切换不同材质，可以K关键帧
- General
  - Shader Selector-----------------切换材质
  - Offset--------------------------偏移

#### State/状态节点
可输出的端口很多，可以提供模型的各种状态信息
- Normal--------------------------法线信息
- RayLength-----------------------光线长度
- Rayposition---------------------光线位置信息，将点的X,Y,Z映射到R，G，B，让点在不同的位置呈现不同的颜色，因为RGB最大值为1，一般会显示不出效果，可以添加一个Vector Div节点，除以100或1000，移动对象，颜色会进行变化，可以制作创意效果

#### TriPlanar节点
让坐标的三个轴向颜色不一样，可以给三个轴向不同的贴图

- General
  - Texture
    - Same Image On Each Axis----------三个轴向使用同一图像，一般不勾选
    - Blend Amount---------------------混合数量，用来调整边缘柔和度，数值越大边缘越柔和
    - Blend Curve----------------------混合曲线，与Blend Amount搭配调整边缘柔和度，数值越小边缘越柔和
  - Coorfinates
    - Scale----------------------------贴图尺寸
    - Offset---------------------------贴图偏移
    - Rotation-------------------------贴图旋转
**可以将贴图连接到ImageX端口，用作调整UV的节点**

#### Vector User Data/矢量用户数据节点
- General
  - Attribute name------------------读取模式
    - MoGraph
      - UVW-----------------------------控制UVW，需要把效果器中的U向偏移或V向偏移打开


#### Vertex Attribute/顶点属性节点
用来读取顶点贴图信息，将顶点贴图转化为黑白贴图使用
- General
  - Attribute Name-------------------拖入顶点贴图


## Environment
#### Environment/环境节点
使用时连接到Output节点的Environment端口，然后将材质球拖到渲染设置里基本属性中的Environment,或者将材质球拖到RS摄像机标签的Environment中，可以创建环境或者背景，效果与Dome Light相同，比Dome Light多的功能是可以单独设置背景、反射、折射、GI的贴图，一般很少用，Dome Light可以满足绝大部分场景

#### Physical Sky/物理天空节点
与Sun&Sky Rig功能相同，可以用贴图来控制日光颜色，很少用


## Light
在灯光中点击Add Shader Graph，可以给灯光创建一个灯光材质球，灯光的参数会显示在节点编辑器中，用节点来控制
#### Dome Light/穹顶光节点

#### IES Light/IES光节点

#### Physical Light/物理灯光节点
点光源、聚光灯、区域光都使用这个节点

#### Portal Light/窗口光节点

#### Sun Light/太阳光节点

## Volume
#### Volume/体积节点
使用时直接连到Output的Volume端口，将材质赋予Volume对象
- Basic
  - Scatter--------------------------散射
    - Channel--------------------------选择读取体积的什么通道
    - Scatter Coefficient--------------散射系数，数值越大，灯光可以透射的越远，体积越亮
    - Tint-----------------------------颜色，RS的体积没有吸收颜色，这里的颜色就像一层颜色裹在体积表面，效果不好
    - Scatter Remap Ramp---------------散射渐变重映射，用渐变来重映射散射颜色
  - Absorption-----------------------吸收
    - Absorption Coefficient-----------吸收系数，这个参数决定光线穿过体积时，会有多少被吸收，数值越小，体积越亮
    - Absorption Remap Ramp------------吸收渐变重映射，用渐变来重映射吸收，从而控制体积的厚度，最左边的点一般要为0，否则效果很诡异
  - Emission-------------------------发光
    - Channel--------------------------选择读取体积的什么通道
    - Tint-----------------------------发光颜色
    - Emission Remap Ramp--------------发光渐变重映射

## Math
注意RS的Math节点只能在RS中使用，无法在Xpresso中使用
#### Abs/取绝对值节点

#### Add/相加节点

#### Change Range/更改范围节点
对于操作着色器网络数据非常好用，功能与XPresso中的范围映射器非常相似
- General
  - Clamp To New Range---------------钳制到新范围


#### Cosine/余弦节点
#### Div/相除节点
#### Mul/相乘节点
#### Sine/正弦节点
#### Sub/相减节点
#### Tangent/正切节点
#### Vector Div/矢量除法节点
#### Vector To Scalars/矢量转为实数


## Color
#### Color Abs/颜色绝对值节点
一般当做常数颜色来使用

#### Color Change Range/改变颜色范围节点
不常用

#### Color Composite/颜色混合节点
将两个颜色混合，可以贴图，并设置混合模式

#### Color Correct/颜色校正节点
- General
  - Gamma---------------------------Gamma值
  - Contrast------------------------对比度
  - Hue Shift-----------------------色相
  - Saturation Scale----------------饱和度，可以提升到1以上
  - Level Scale---------------------明度
  - Use HSV Conversion--------------把颜色转化为HSV类型

#### Color Invert/颜色反相节点
用来反相颜色

#### Color Layer/颜色层节点
相当于一个高级的颜色混合节点，可以将多个颜色混合，可以理解为PS中的图层，PS中图层由下到上解算，颜色层节点由上到下解算
- General
  - Base Layer----------------------基础颜色层
  - Layer1--------------------------颜色层1
    - Enable--------------------------激活
    - Color.Color---------------------层1的颜色，可以用贴图连接
    - Mask----------------------------强度，可以用黑白贴图控制分布
    - Blend Mode----------------------混合模式
      - Normal--------------------------正常
      - Add-----------------------------相加
      - Subtract------------------------减去
      - Multiply------------------------正片叠底


#### Color Maker/颜色制作节点
可以将不同的贴图定义到红、绿、蓝通道进行融合

#### Color Mix/颜色混合节点
与OCtane中的Mix功能相同

#### Color Splitter/颜色分离节点
与Color Maker节点相反，可以将颜色的RGBA通道分离

#### Color To HSV/RGB转HSV节点

#### HSV To Color/HSV转RGB节点




# RS标签
### Object标签
#### Particles/粒子
给粒子发射器添加Object标签会出现的选项卡，用来控制粒子渲染形态
- Mode--------------------------模式
  - Disabled----------------------不渲染粒子
  - Point Instances---------------粒子渲染为点实例，如果XP发射器中设置有粒子半径变化，这里会生成不同半径的圆盘
  - Sphere Instances--------------粒子渲染为球体实例（最常用，因为为实例对象，占用系统资源少）
  - Quad Instances----------------粒子渲染为四边形实例
  - Custom Objects----------------粒子渲染为自定义模型
  - Spheres-----------------------粒子渲染为球体（占用系统资源多，一般不使用）
- Custom Objects----------------自定义模型，将要渲染成的自定义模型拖进去
- Distribution------------------分布
  - Sequential--------------------顺序分布
  - Random------------------------随机分布
- Random Seed-------------------随机种子
- Scale Multiplier--------------调整粒子大小
#### Curve/曲线
给样条线或毛发添加Object标签会出现的选项卡，用来直接渲染样条和渲染毛发
- Mode--------------------------渲染模式
  - Disabled----------------------不渲染
  - Hair Strands------------------毛发生长，以毛发形式渲染
  - Box---------------------------盒子状，2.6版新增
- Thickness---------------------厚度，渲染的毛发或样条粗细
- Scale-------------------------尺寸，控制从样条开始到结束或从毛发发根到发梢的尺寸变化
- Resample Curve----------------曲线重新采样，勾选后会激活Steps
- Steps-------------------------步幅，可以手动调整曲率的步幅数量，即控制渲染样条的点数量
#### Visibility/可见性
- Override----------------------激活后可以自定义可见性
- General-----------------------常用
  - Primary Ray Visible-----------首次光线可见，取消勾选后物体本身不可见
*制作切割物体的效果，可以新建一个平面，给玻璃材质，折射率为1，平面会完全不可见，再给物体一个Object标签，取消Primary Ray Visible勾选，再用Ray Switch节点制作反面材质即可*
  - Secondary Ray Visible---------光线二次反弹可见，取消勾选后物体不受GI影响
  - Casts Shadows-----------------投射阴影
  - Receives Shadows--------------接收阴影
  - Self-Shadows------------------投射到本体的阴影
  - Casts AO----------------------环境吸收
**制作反光板时，去掉物体本身可见、投射阴影、接收阴影、投射到本体的阴影、环境吸收的可见，注意光线二次反弹可见必须勾选**
- Reflection&Refraction/反射&折射
  - Visible in Reflection---------反射可见
  - Visible in Refraction---------折射可见
  - Casts Reflection--------------投射反射
  - Casts Refraction--------------投射折射
- Global Illumination
  - Visible to Non-Photon GI------不是辐照贴图模式的GI是否可见
  - Visible to GI Photons---------GI光子可见
  - Visible to Caustic Photons----焦散光子可见
  - Receives GI-------------------是否接收GI
  - Force Brute-Force GI----------开启暴力GI模式,勾上后强制使用Brute-Force（暴力GI）模式
  - Casts GI Photons--------------投射光子
  - Casts Caustic Photons---------投射焦散光子
用来开启焦散，勾选Emit Caustic Photons，给焦散对象添加Object标签，在Visibility中激活Override，勾选Casts Caustic Photons，在渲染设置里取消IPR渐进式渲染（Force enabled for IPR）
  - Receives GI Photons-----------接收光子
  - Receives Caustic Photons------接收焦散光子
#### Geometry/几何
用来开启细分和置换
- Override----------------------激活几何
- Tessellation------------------细分
  - Enabled-----------------------勾选后开启细分
  - Subdivision Rule--------------细分模式，两种方式仅为细分后的布线不同
    - Catmull-Clark+Loop------------CC循环细分，适用于有四边面和三角面
    - Catmull-Clark Only------------仅CC细分，适用于只有四边面
  - Screen Space Adaptive---------屏幕空间自适应细分，镜头离物体越近，细分越高，镜头离物体越远，细分越低，原理是当一条线的长度大于Minimum Edge Length时，进行细分，长度小于Minimum Edge Length时，不进行细分，会大大减少细分的工作量
  - Smooth Subdivision------------勾选后开启平滑
  - UV Smooth---------------------UV平滑的部位
    - Disabled----------------------不平滑
    - All Edges
  - Minimum Edge Length-----------最小细分长度，数值越小细分越密
  - Maximum Subdivisions----------最大细分级别，影响细分形状
  - Out of Frustum Tess. Factor---完全处在摄像机镜头外的对象的细分级别
- Displacement------------------置换
  - Enabled-----------------------勾选后开启置换
  - Maximum Displacement----------最大置换高度，在调节时最好把Enable Auto Bump Mapping关掉
  - Displacement Scale------------置换缩放，在调节时最好把Enable Auto Bump Mapping关掉
  - Enable Auto Bump Mapping------启用自动凹凸贴图，勾选后，任何一些无法放入几何体的置换细节，自动凹凸贴图都会检查一下凹凸贴图，如果想单独看一下置换效果，就取消勾选
**注意进行置换时必须在这里开启置换，否则没有效果**
#### Matte
用来实现实景合成中的阴影捕捉
**注意要给平面一个材质才有效果，反射、折射等参数可以结合材质综合调节达到更好的效果**
- Override----------------------激活后可以进行阴影捕捉
- General
  - Enable------------------------勾选后平面进行阴影捕捉
  - Show Backgound----------------显示背景，平面变为透明
  - Apply to Secondary Rays-------参与二次反射
  - Affected by Matte Lights------激活后受遮罩灯光影响
  - Include in Puzzle-Mattes------包含拼图，2.6新功能
  - Alpha-------------------------透明度
  - Reflection Scale--------------反射强度
  - Refraction Scale--------------折射强度
  - Diffuse Scale-----------------漫射强度
- Shadow
  - Enable------------------------勾选后保留阴影
  - Affects Alpha-----------------影响Alpha通道
  - Color-------------------------阴影颜色
#### Object ID/项目ID
配合AOV（多通道渲染）使用
#### Motion Blur/运动模糊
开启运动模糊，注意要在渲染设置中基本里面的Motion Blur中开启运动模糊
**注意IPR中无法显示运动模糊效果，需要渲染到图片查看器**
#### Exclusion/排除
将别的对象拖到有标签对象的排除中，该对象不会在有标签对象上产生反射、折射等效果



# 渲染设置
### 基本
#### Progressive Rendering/渐进式渲染
- Enabled----------------------启用
- Force enabled for IPR--------IPR强制启用
- Passes-----------------------传递数，只用于IPR时一般设为256，用于最终渲染时一般设为1024
- Fast Preprocessing-----------快速渐进式渲染应用于
  - All--------------------------所有渲染
  - IPR Only---------------------只有IPR
  - None-------------------------不使用快速渐进式渲染
**使用渐进式渲染的缺点**
1. 所有的采样都会失效，如渲染设置中的Unified Samping和Sample Filtering，还有灯光、材质的采样都会失效
2. 部分SSS效果失效，无法看到SSS效果
3. 渐进式渲染会强制使用Brute Force（暴力GI）的GI模式，Photons Maps（辐射贴图）和Irradiance Cache（辐照缓存）模式都会失效
#### Unified Sampling/统一采样值
RS的采样使用的是自适应采样，场景简单的地方采样值低，复杂的地方采样值高,原理是最低会给每个像素发射Samples Min次光线，而后继续不停地发射光线，直到找到一个无噪点的解决方案为止，但是如果还没有达到Samples Max次就已经满足了Adaptive Error Threshold（自适应容错阈值），就会停下来，结束这个像素的采样
**统一采样值只能控制来自摄像机的光线**
- Samples Min------------------最小采样值，最终渲染时一般设为8-16
- Samples Max------------------最大采样值，最终渲染时一般设为256-512，如果开启了运动模糊或景深，要增大最大采样值来消除运动模糊和景深产生的噪点
- Adaptive Error Threshold-----自适应容错阈值，数值越低，渲染出来的错误和噪点越少，官方建议设为0.003，一般0.01即可
- Show Samples-----------------显示采样，勾选后会渲染一张黑白图来显示采样情况，画面中越黑的地方采样值越小，越白的地方采样值越大
- Don't Automatically Reduce Samples of Other Effects--一般不勾选，勾选后渲染速度非常慢
- Randomize pattern every frame--噪点在每一帧随机跳动，做动画时一定要勾选，不然噪点会粘滞不动，看上去像蒙了一层东西

#### Sample Filtering/采样过滤器（抗锯齿）
- Filter Type------------------过滤方式，5种方式由上到下从最柔和到最锐利，一般使用第三个或第四个
- Filter Size------------------过滤尺寸，过滤结果越锐利，就要调的越大，过滤结果越柔和，就要调的越小
- Max Subsample Intensity------控制画面中最大亮度
- Max Secondary Ray Intensity--限制光噪点，如果有萤火虫现象，可以适当调低参数，但是会损失物理精度

#### Sampling Overrides/采样覆写
场景中材质、灯光等太多时，每一个调节采样太麻烦，可以直接使用采样覆写，给所有的反射、折射、AO、灯光、体积等统一调节采样值
- Override Samples-------------激活覆写采样
- Samples----------------------这里的采样除以最大采样值的结果是发射一次光线中包含几条此通道的光线，这里的数值不能小于最大采样值，且必须是最大采样值的倍数

#### Motion Blur/运动模糊
**注意IPR中无法显示运动模糊效果，需要渲染到图片查看器**
- Enable-----------------------开启运动模糊
- Enable Deformation Blur------开启变形运动模糊，在点级别动画和物体发生形变的动画中使用
- Transformations Steps--------运动模糊变化步幅，控制运动模糊细分值，数值越高计算越精确，计算速度越慢，原理是沿着动画，会有多少个步幅，然后给运动模糊一个参考。在运动为弧线等情况时，需要调高变化步幅
- Frame Duration---------------运动模糊持续时间，默认为1就是运动模糊只采样1帧，从效果上看数值越大，运动模糊强度越大
- Shutter Start----------------运动模糊开始
- Shutter End------------------运动模糊结束
- Shutter Position-------------穿梭位置，运动模糊最强的地方
- Shutter Efficiency-----------穿梭效率，相当于快门启动速度，控制运动模糊拖尾的外观

#### Photometric Units/光度单位
- Units to Meter Scale---------这里的数值要跟工程的网格间距设置统一
#### Quantization/数字化
- Quantize to 8-bit and Dither-把最大亮度限制在1.0，产生8位的效果

### AOV
用来进行多通道渲染，RS的多通道渲染比较复杂
- General
  - Mode-------------------------模式
- AOVs
  - Number of AOVs-----------------通道数
  - AOV
    - Enabled------------------------开启多通道
    - Type---------------------------选择通道
    - Ambient Occlusion--------------环境吸收
注意材质中有AO节点时，才能渲染出AO通道，不管AO节点是否起效果。如果材质没有使用AO节点，但是想渲染AO通道，可以给发光加一个AO节点，并将发光强度设为0，这样AO没起到任何作用，但是可以渲染出对象的AO通道
    - Depth--------------------------深度通道
使用深度通道会发现全是白色，并没有灰度图，那是因为RS的深度显示默认为0到1，场景中的对象离摄像机都超过1CM，所以都是白色，但是仅仅是显示，依然是有深度信息的，导出到合成软件中可以正常使用，如果想要显示正确，可以在Depth Mode中选择Z Normalized（法线化）模式
        - Depth Mode---------------------深度模式
          - Z------------------------------显示正常的深度信息
          - Z Normalized-------------------将深度信息法线化（法线化即把数值转化为0-1之间）
    - Puzzle Matte-------------------遮罩
可以渲染是对象遮罩，相当于对象缓存，在使用时给对象Object标签，在ObjectID中设置ObjectID，在Options中Mode选ObjectID，Name、RedID、GreenID、BlueID都设为与ObjectID相同
也可以用来渲染材质遮罩，使用时在材质的Output设置MaterialID，在Options中Mode选MaterialID，Name、RedID、GreenID、BlueID都设为与MaterialID相同
**一种用法是把RedID、GreenID、BlueID都与ObjectID或MaterialID设为相同值，会生成黑白遮罩，在合成软件中使用亮度通道进行分离；另一种用法是将RedID设为第一个对象的ObjectID或第一个材质的MaterialID，GreenID设为第二个对象的ObjectID或第二个材质的MaterialID，BlueID设为第三个对象的ObjectID或第三个材质的MaterialID，这样会生成一张红、绿、蓝三色的彩色遮罩，在合成软件中使用颜色通道进行分离**
    - Options------------------------通道设置
  - Multi-Pass Output--------------输出多通道，使用C4D自带的多通道系统进行渲染（常用）
  - File Output--------------------输出文件，使用RS自己的多通道系统进行渲染（不常用）
**由于AE默认的色彩空间为sRGB，渲染使用线性颜色空间的EXR会导致颜色不正确，在AE中有两种解决方法：**
1. 在项目设置中选择线性工作空间
2. 添加调整层，给调整层添加 实用工具-->颜色配置文件转换器（Color Profile Converter）效果，在输入配置文件中勾选线性化输入配置文件，在输出配置文件中选择sRGB即可（通常使用这种方法，因为这种方法渲染时出错率更低）

### Optimozation/最优化
#### Maximun Trace Depth/最大追踪深度
- Reflection------------------最大反射次数
- Refraction------------------最大折射次数
- Combined--------------------综合，在最终截止之前的最大反射折射次数

#### Hair Min Pixel Width/毛发最小像素宽度
当毛发比较细时，光线进行采样会有很多光线从毛发间隙中漏过去，只有少量光线可以采样到毛发，会导致毛发看起来有很多锯齿，解决的方法有两种，第一种是提高采样率，第二种是设置毛发最小像素宽度。
原理是将毛发变粗，让光线更好地进行采样，而变粗的部分变为透明，使最终效果看上去没有变化，但是渲染速度会变得很慢
- Enabled----------------------开启优化
- Automatic Threshold----------自动阈值，会根据毛发数量自动设置阈值，控制变粗的毛发数量,一般用自动阈值即可
- Threshold--------------------阈值，数值越大，优化效果越好，渲染速度越慢
- Trace Depth------------------厚度之内的毛发进行优化，厚度外的毛发不进行优化，是提高渲染速度的一种方法,官方推荐值4-6
#### Russian Roulette
让摄像机发出采样光线时根据对象的不同，发出数量不同的反射和折射采样光线。默认即可，调节参数可能会降低渲染质量，增加渲染时间
#### Texture Sampling/纹理采样方式
- Primary Rays------------------首次采样方式，默认即可
- Copy Pre-Converted Textures to Cache Folder--将使用的贴图复制到缓存文件夹，方便调用，会占用CPU，如果电脑配置不低，一般开启
#### Global Overrides/全局设置

### GI
全局光照是间接光照的一种算法
**一般首次反弹GI和二次反弹GI都使用Brute Force/暴力GI即可，速度会比较慢，但是参数简单且效果好。但如果一些大的表面出现噪点较多的问题时，二次反弹GI使用Irradiance Point Cloud/辐射点云，如果问题依然存在，首次反弹GI使用Irradiance Cathe/辐照缓存**
- General
这里的GI只是漫反射GI，不影响焦散效果
  - Primary GI Engine------------首次反弹GI
  - Photon Map-------------------光子映射（辐射贴图），传统GI方式，唯一一种正向GI，计算时光子由光源射出，最后反弹到摄像机。优点是速度快，但是是一种过时的计算方式，一般首次反弹GI不使用这种模式二次反弹GI可以使用，因为速度快而且效果比较干净。焦散的GI都是Photon Map模式，它可以给焦散提供光子
  - Irradiance Cathe-------------辐照缓存，是一种反向GI，计算时光子从摄像机射出，在渲染动画时可以利用上一帧的缓存信息来进行下一次计算，从而节省渲染时间。优点是图像分辨率成倍增大时，渲染时间不会随着成倍增加，速度比较快，效果比较好，最常用。分辨率越高，使用的内存越多
  - Brute Force------------------暴力GI，是一种反向GI，计算时光子从摄像机射出。优点是最符合物理精度，渲染结果最精确，做动画时不容易产生闪烁。缺点是速度慢，而且容易产生噪点。一般用于复杂场景
**如果使用Irradiance Cathe模式渲染结果出现问题，且不知道怎么解决，可以使用Brute Force模式，将光线数量调高即可，渲染速度变慢，但保证了不出问题**
  - Secondary GI Engine----------二次反弹GI，控制第二次及第二次以后的反弹GI
  - Irradiance Point Cloud-------辐射点云，这种二次反弹模式速度比较快，结果也比较干净,噪点比较少。优点是能很好地照明场景，且噪点比较少，缺点是占用内存，而且有时候需要调节下面Irradiance Point Cloud中的参数，才能达到好的效果
  - Number of GI Bounces---------光线反弹次数
#### Brute Force GI
  - Number of Rays---------------暴力GI模式下光线数量，数量越大，噪点越少，速度越慢，一般调到512或1024
#### Irradiance Point Cloud
  - Screen Radius----------------屏幕半径，指的是屏幕空间中的采样点数量。数值越高，采样点越多，渲染速度越慢，效果越好，一般显存大于2G时可以调整为8
  - Samples per Pixel------------效果类似暴力GI模式下的Number of Rays，原理是进行运算并基于初始发射去存储在场景中分布的采样点。数值直接影响渲染质量。如果屏幕中噪点很多，可以调高数值
  - Filter Size------------------过滤尺寸，辐射点云会运算并存储主要GI引擎光线何时去发现表面数值并报告，然后去寻找场景中储存的辐照点云的采样点，过滤尺寸直接控制着离主要GI引擎光线的点有多少个并运算。调大后画面会更柔和，但是一般保持默认，只调整Samples per Pixel参数，因为Samples per Pixel计算的更快，分布的也更加均匀
  - Retrace Threshold------------重追踪阈值，因为我们没有办法去计算朝向曲面或朝向彼此靠近的对象的权重，最后的结果就是屏幕中所有的采样点都是均匀分布，也就是说不会考虑类似两个很靠近的对象接缝处之类的地方的细节，就会导致一些问题出现，而Retrace Threshold/重追踪阈值会对于这一区域的采样点进行重点追踪，阈值越高，重新追踪的力度就越大。如果首次GI使用的是辐照缓存，一般阈值设为1或2，如果首次GI使用的是暴力GI，一般阈值设为2或3
#### Irradiance Cathing
  - Show Calculation-------------显示计算过程，勾选后渲染时会看到噪点一点点消失的过程
  - Separate Points for Secondary Rays--如果画面出现由反射或折射引起的闪烁，勾选此选项后会解决闪烁问题
**判断闪烁是否由反射或折射引起的方法：**
1. 在Optimization/最优化中的Maximum Trace Depth里，将Reflection调为0，渲染看是否还有闪烁，如果闪烁消失，就是由反射引起的闪烁
2. 将Refraction调为0，渲染看是否还有闪烁，如果闪烁消失，就是由折射引起的闪烁
  - Visualize Points--------------勾选后渲染可以看到采样点，用来调试
  - Preset------------------------辐照缓存预设，渲染时可以选择最高或者中等，渲染速度不会变的很慢，不要用低
  - Min Rate----------------------最小比率，控制辐照缓存的最小分辨率是当前分辨率的几倍，0为与场景分辨率相同，-1为0.5倍
  - Max Rate----------------------最大比率，控制辐照缓存最终分辨率是当前分辨率的几倍
**Min Rate和Max Rate主要控制采样点的数量和分布**
  - Color Threshold---------------颜色阈值，颜色阈值会终点关注场景中颜色对比度高的地方，颜色阈值越低，会向对比度高的地方射出更多的采样点，而对比度低的地方会射出更少的采样点
  - Distance Threshold------------距离阈值，距离阈值越高，会向离摄像机远的地方射出更多的采样点，向离摄像机近的地方射出更少的采样点
  - Normal Threshold--------------法线阈值，与表面曲率相关，法线阈值越高，会向表面曲率大的地方射出更多的采样点，向表面曲率小的地方射出更少的采样点
  - Min Detail--------------------最小细节，功能是尽量不给表面添加更多的采样点
  - Radius Factor-----------------半径因子，采样点彼此的距离有多宽，调大之后会有模糊平滑效果，会加快渲染速度，但是影响最终效果，一般不使用
  - Num Rays----------------------数量光线，效果类似于暴力GI的Number of Rays，如果噪点太多或着色不均匀，可以将数值调大。原理是给每个采样点上发射多少光线
  - Adaptive Amount---------------自适应百分比，如果Num Rays为200，Adaptive Amount为0.8，意思是给每个采样点发射40束光线，而自适应错误阈值来决定要不要发射另外的160束光线
  - Adaptive Error Threshold------自适应错误阈值，如果调大Num Rays，还是有噪点，可以降低Adaptive Error Threshold值到0.005或更低
  - Num Smoothing Passes----------数量平滑通道，与Radius Factor/半径因子类似，但是它会把半径缓存放在一块进行模糊处理，会损失很多细节，在最终渲染时不使用

### Photon
控制焦散的GI，焦散的GI都是Photon Map模式
**使用焦散时要关掉渐进式渲染**
**如果想进一步增加焦散效果，可以给对象一个Object标签，在Visibility中开启Casts Caustic Photons/投射焦散光子**
- General
  - Reflection Traing Depth------反射焦散深度，反射焦散是由反射聚焦到一个点产生的，用来调节反射焦散的强度
  - Refraction Traing Depth------折射焦散深度，折射焦散是由折射聚焦到一个点产生的，用来调节折射焦散的强度
  - Combined Traing Depth--------整体焦散深度
  - Max Num GI Photons-----------最大GI光子数（GI不为Photon Map时可以使用）
  - GI Search Radius-------------GI搜寻半径（GI不为Photon Map时可以使用）
  - Max Num Caustics Photons-----最大焦散光子数，每个像素可以看到最大有多少光子
  - Caustics Search Radius-------焦散搜寻半径，绕着每个像素的搜索半径，让它只会在每个像素周围多大半径范围内进行搜索。搜寻半径越大，会将光子之间的间隙填充，使焦散变的柔和。数值低的时候焦散会变成小噪点，效果不好，数值高的时候焦散很平滑，效果较好。但是数值高的时候会变暗，解决方法是提升灯光的光子数（在灯光的Photon选项卡中）
### SSS
- General
  - Mode-------------------------SSS计算模式
    - Rebuild----------------------每一帧都进行重新计算，并储存缓存文件
    - Load-------------------------从缓存文件中读取计算结果
    - Rebuild(Prepass Only)--------每一帧都进行重新计算，当前帧储存缓存文件，之后的帧计算时会读取第一帧储存的缓存文件
    - Rebuild(Don't Save)----------每一帧都进行重新计算，不储存缓存文件
  - Filename---------------------缓存文件名
  - Rate-------------------------抗锯齿，设置的越高SSS表面效果越好，渲染速度越慢
  - Interpolation Quality--------插值质量，一般使用Low，渲染动画时可能会出现光斑闪烁，可以使用High
  - Number of GI Rays------------GI数量，SSS效果是比较柔和的，数值不要太高，一般从130往上调至效果满意为止

### System/系统
#### Log/日志
#### Feedback Display/系统反馈
#### Material Override/材质覆写
相当于黏土渲染，覆写所有材质，且只有漫射，可以用来渲染白模效果
#### Ray Tracing Acceleration Structure
- Do Complete Construction Before Rendering--在渲染前将场景打包转换格式发送给RS渲染器（有时会提高渲染速度，有时会减慢渲染速度）
#### Hair Tessellation/毛发细分
#### Experimental Options
- Disable Shadow Ray Biasing----关闭阴影光线有偏运算，一般不勾选，勾选关闭后阴影边缘会不再平滑，可以使用Object标签中的平滑来使阴影边缘平滑。当一个对象法线数目很少且法线方向不同时，对象上的阴影可能会出问题，会有亮的地方，此时需要勾选关闭阴影光线有偏运算
- Bucket Order------------------渲染顺序
#### Bucket Rendering
- Bucket Size-------------------渲染格大小
- Bucket Order------------------渲染顺序
  - Spiral------------------------从中间向四周转圈渲染
  - Horizontal--------------------从上到下横排渲染
  - Hilbert-----------------------从左向右竖排渲染

### Memory/内存管理
- General
  - Automatic Memory Management---勾选后系统会自动分配显存
  - Percentage of GPU memory to use--显存利用率
  - Irradiance point cloud working tree reserced memory--烘培贴图占用的显存
  - Irradiance cache working tree reserced memory--烘培贴图占用的显存
  - Percentage of free memory used for texture cache--纹理占用的缓存
  - Maximum GPU Texture cache size----最大GPU占用
  - Maximum CPU Texture cache size----最大CPU占用

### Integration/集成
#### Options
- Default Light-----------------开启关闭默认灯光





# 贴图使用方法
### Color/颜色贴图
直接连接到Color端口
### AO/环境吸收贴图
使用Color Layer节点来与Color节点进行混合，混合模式为相乘（正片叠底），再连接到Color端口
### Bump/凹凸贴图
连接到Bump Map节点，再连接到Material节点的Overall-->Bump Input端口
### Normal/法线贴图
使用Normal Map节点，连接到Material节点的Overall-->Bump Input端口
**法线贴图与凹凸贴图连接的是同一个端口，如果需要同时使用Bump贴图和Normal贴图，使用Bump Blender节点进行混合**
### Roughness/粗糙贴图
直接连接到Roughness端口，如果是Glossiness贴图，需要在Advanced中勾选Convert From Glossiness tu Roughness，将粗糙度变为光滑度，再将Glossiness贴图连接到Roughness端口
### Displacement/置换贴图
连接到Displacement节点的Tex Map端口，然后连接到Output节点的Displacement端口，再给模型添加RedShift Object标签，在Geometry选项卡中勾选Override，再勾选Tessellation（细分）和Displacement（置换）才会有置换效果


# RS渲染器技巧
- 1、可以在工程设置里面把默认对象颜色设为80%灰，方便打光时判断明暗关系
