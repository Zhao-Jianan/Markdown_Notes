# Plexus Object Panel/对象面板
## Add Geometry/添加几何体
### Plexus Layers Object/层对象
层对象可以基于合成中的灯光或者3D图层生成点线面粒子
- Object Type------------------------对象类型
  - Lights-----------------------------基于灯光
  - 3D Layers--------------------------基于3D图层
- Light Type-------------------------灯光类型
  - Point Lights-----------------------点光源
  - Spot Lights------------------------聚光灯
- Layer Type-------------------------3D图层类型，注意使用基于3D图层类型时需要将图层的三维图层属性激活
  - Null-------------------------------基于空对象
  - AV Layers--------------------------基于调整图层
  - All 3D Layers----------------------所有3D图层
- Layer Name Begins with-------------图层名以什么开始，用来只让部分层对象生成粒子
- Get Color from Layers--------------从图层获取颜色，图层生成的点可以继承图层的颜色
- Get Opacity from Intensity---------生成点的透明度与灯光强度有关
- Get Opacity from Opacity-----------生成点的透明度与图层透明度有关
- Opacity----------------------------透明度
- Vertices Between Light-------------灯光之间的顶点，只有选择聚光灯才有此选项，激活后在两个聚光灯之间也会生成点
- Num of Vertices--------------------顶点数，两个聚光灯之间生成的点的数目
- Replication------------------------复制
  - Total No.Copies--------------------复制数量
  - Extrude Depth----------------------复制的距离
  - Replicate Direction----------------复制方向
  - Rotation Center XY-----------------X轴Y轴旋转中心
  - Rotation Center Z------------------Z轴旋转中心
  - X Rotation-------------------------控制X轴方向旋转
  - Y Rotation-------------------------控制Y轴方向旋转
  - Z Rotation-------------------------控制Z轴方向旋转
- Generate Facets--------------------生成面
- Group------------------------------组

### Plexus Path Object/遮罩对象
遮罩对象可以读取层遮罩，基于层遮罩生成点线面粒子
- Mask Name Begins with--------------遮罩名以什么开始，用来只让部分蒙版生成粒子
- Subdivide Masks--------------------细分遮罩，如果勾选会生成很多点，数量由Points on Each Mask参数控制，如果不勾选，遮罩有多少个点，就生成多少个点
- Points on Each Mask----------------每个遮罩生成的点数量
- Get Paths from Text----------------从文字获取遮罩，只对文字层有效
- Get Color from Masks---------------从遮罩获取颜色，图层生成的点可以继承遮罩的颜色
- Color------------------------------生成的点的颜色
- Get Opacity from Masks-------------生成点的透明度与遮罩透明度有关
- Opacity----------------------------透明度
- Replication------------------------复制
  - Total No.Copies--------------------复制数量
  - Extrude Depth----------------------复制的距离
  - Replicate Direction----------------复制方向
  - Rotation Center XY-----------------X轴Y轴旋转中心
  - Rotation Center Z------------------Z轴旋转中心
  - X Rotation-------------------------控制X轴方向旋转
  - Y Rotation-------------------------控制Y轴方向旋转
  - Z Rotation-------------------------控制Z轴方向旋转
  - Start Scale------------------------开始位置缩放
  - End Scale--------------------------结束位置缩放
- Generate Facets--------------------生成面
- Group------------------------------组

### Plexus OBJ Object/OBJ对象
使用导入的OBJ模型来生成粒子
- OBJ Layer--------------------------OBJ层，导入OBJ文件，把OBJ文件拖入到合成中，再在这里选择OBJ层
- After OBJ Sequence Ends------------如果是OBJ序列，在序列结束之后执行什么动作
  - Do Nothing-------------------------什么也不做
  - Loop Sequence----------------------循环序列
  - Ping Pong Sequence-----------------震荡序列，顺序播放完倒序到开头再顺序播放
  - Freeze Last Frame------------------在最后一帧冻结
- OBJ Resolution---------------------分辨率，降低分辨率类似于减面效果
- Transform OBJ----------------------OBJ变换
  - OBJ XY Location--------------------OBJ的X轴Y轴中心
  - OBJ Z Location---------------------OBJ的Z轴中心
  - Invert X---------------------------X轴反向
  - Invert Y---------------------------Y轴反向，因为C4D的Y轴方向与AE相反，所以从C4D导出的OBJ文件通常要勾选Y轴反向
  - Invert Z---------------------------Z轴反向
  - Uniform Scale----------------------统一尺寸
  - X Scale----------------------------X轴尺寸
  - Y Scale----------------------------Y轴尺寸
  - Z Scale----------------------------Z轴尺寸
  - X Rotate---------------------------X轴旋转
  - Y Rotate---------------------------Y轴旋转
  - Z Rotate---------------------------Z轴旋转
- Color------------------------------颜色
- Opacity----------------------------透明度
- Import Facets----------------------输出面
- Texture Coordinates----------------贴图纹理坐标
  - Import from OBJ--------------------从OBJ文件中导出
  - Generate based on Position---------根据位置生成
  - Generate based on ID---------------根据ID生成
- Group------------------------------组


### Plexus Primitives Object/原始对象
生成一个立方体状或球状的粒子云
- Primitive Type---------------------原始对象类型
  - Cube-------------------------------立方体
  - Sphere-----------------------------球体
- Cube
  - X Points---------------------------X轴点数量
  - Y Points---------------------------Y轴点数量
  - Z Points---------------------------Z轴点数量
  - Cube Width-------------------------立方体宽度
  - Cube Height------------------------立方体高度
  - Cube Depth-------------------------立方体深度
- Sphere
  - Sphere Radius----------------------球体半径
  - Sphere Slices----------------------纬线点数量
  - Sphere Stacks----------------------经线点数量
  - Sphere Layers----------------------深度点数量
- Generate Faces---------------------生成面的方向
- Transform--------------------------变换
  - Center XY--------------------------X轴Y轴中心
  - Center Z---------------------------Z轴中心
  - X Rotate---------------------------控制X轴方向旋转
  - Y Rotate---------------------------控制Y轴方向旋转
  - Z Rotate---------------------------控制Z轴方向旋转
- Color------------------------------颜色
- Opacity----------------------------透明度
- Group------------------------------组

### Plexus Instances Object/实例对象
从另一个使用了Plexus的图层生成实例，可以实例很多份，类似C4D中的根据对象克隆的功能
- Instance Layer---------------------实例图层源
- Num of Instances-------------------实例数量，功能相当于克隆数量
- Get Color From Vertices------------从源图层获取颜色
- Color------------------------------实例颜色
- Get Opacity From Vertices----------从源图层获取透明度
- Opacity----------------------------透明度
- Get Scale From Vertices------------从源图层获取生成点尺寸
- Scale------------------------------生成点尺寸
- Re-Align to Center-----------------重新对齐于中心
- Replication------------------------复制
  - Replication Depth------------------复制深度，控制复制的实例间距
  - Replicate Axis---------------------复制轴向
  - Replicate Direction----------------复制方向
  - Replication Center XY--------------X轴Y轴中心
  - Replication Center Z---------------Z轴中心
  - X Rotation-------------------------X轴旋转
  - Y Rotation-------------------------Y轴旋转
  - Z Rotation-------------------------Z轴旋转
- Echo-------------------------------如果源图层有动画，激活后控制实例对象动画提前或滞后
- Echo Delay-------------------------滞后时间
- Facet Mode-------------------------生成面模式
  - None-------------------------------不生成面
  - Import Facets----------------------导入面，会把源图层的生成面信息导入到这里生成面
  - Regenerate Facets------------------生成新的面，会在多个实例之间生成新的面
- Group------------------------------组


## Add Effector/添加效果器
### Plexus Noise Effector/燥波效果器
- Effector effects-------------------影响
  - Vertices---------------------------影响顶点
  - Faces------------------------------影响面
- Apply Noise To (Vertices)----------燥波影响顶点的什么属性
  - Position---------------------------位置
  - Scale------------------------------尺寸
  - Color------------------------------颜色
- Apply Noise To (Faces)-------------燥波影响面的什么属性
  - Position---------------------------位置
  - Rotation---------------------------旋转
  - Color------------------------------颜色
- Color Type-------------------------燥波影响颜色时可以选择影响颜色类型
- Noise Amplitude--------------------燥波强度
- Noise Details----------------------燥波细节
  - Noise X Scale----------------------X轴尺寸
  - Noise Y Scale----------------------Y轴尺寸
  - Noise Z Scale----------------------Z轴尺寸
  - Noise X Offset---------------------X轴偏移
  - Noise Y Offset---------------------Y轴偏移
  - Noise Z Offset---------------------Z轴偏移
  - Noise Evolution--------------------燥波整体变化
  - Loop Evolution---------------------循环变化
  - No. of Cycles to Loop--------------循环次数
  - Noise Values-----------------------燥波产生的方向
    - Positive---------------------------正向
    - Negative---------------------------反向
    - Both-------------------------------正向反向都产生
  - Noise Octaves----------------------燥波阶度，控制燥波复杂程度
  - Noise Seed-------------------------燥波种子
- Apply Noise to Axis----------------燥波影响位置时可以选择影响哪个轴向的坐标
- Use Lights for Noise---------------激活后用灯光定义燥波产生的区域，灯光的位置影响燥波产生的区域，灯光的属性可以影响燥波强度
- Light Name Begins with-------------选择灯光起始名字
- Get Effector Radius From-----------灯光的什么属性影响燥波半径
  - None-------------------------------无
  - Intensity--------------------------灯光强度
  - Shadow Darkness--------------------灯光阴影深度
  - Shadow Diffusion-------------------灯光阴影扩散
- Get Amplitude From-----------------灯光的什么属性影响燥波强度
- Get Fade Out From------------------灯光的什么属性影响燥波衰减
- Effect Only Group------------------只影响组

### Plexus Spherical Field/球形场
球形场像有一个球状的力，把粒子推走
- Effector effects-------------------影响
  - Vertices---------------------------影响顶点
  - Faces------------------------------影响面
- Apply Noise To (Vertices)----------球形场影响顶点的什么属性
  - Position---------------------------位置
  - Scale------------------------------尺寸
  - Color------------------------------颜色
- Apply Noise To (Faces)-------------球形场影响面的什么属性
  - Position---------------------------位置
  - Rotation---------------------------旋转
  - Color------------------------------颜色
- Field XY Location------------------球形场X轴Y轴位置
- Field Z Location-------------------球形场Z轴位置
- Field Sphere Radius----------------球形场半径
- Fade Out---------------------------球形场衰减
- Scale Factor-----------------------球形场影响顶点尺寸时控制尺寸影响的最大值
- Rotation---------------------------球形场影响面的旋转时控制旋转角度
- Color------------------------------球形场影响顶点或面的颜色时调节颜色
- Opacity----------------------------球形场影响顶点或面的颜色时调节透明度
- Apply Field to Axis----------------球形场影响位置时可以选择影响哪个轴向的坐标
- Use Lights-------------------------激活后用灯光定义球形场产生的区域，灯光的位置影响球形场产生的位置
- Light Name Begins with-------------选择灯光起始名字
- Get Field Radius From--------------灯光的什么属性影响球形场半径
  - None-------------------------------无
  - Intensity--------------------------灯光强度
  - Shadow Darkness--------------------灯光阴影深度
  - Shadow Diffusion-------------------灯光阴影扩散
- Get Fade Out From------------------灯光的什么属性影响球形场衰减
- Effect Only Group------------------只影响组


### Plexus Container/包裹器
与球形场效果相反，将粒子包裹起来，内部才会有粒子
- Container Type---------------------包裹器类型
  - None-------------------------------无
  - Cube-------------------------------立方体状
  - Sphere-----------------------------球状
  - Instance---------------------------实例
- Container XY Location--------------包裹器X轴Y轴位置
- Container Z Location---------------包裹器Z轴位置
- Transform Container----------------包裹器变换
  - Uniform Scale----------------------统一尺寸
  - X Scale----------------------------X轴尺寸
  - Y Scale----------------------------Y轴尺寸
  - Z Scale----------------------------Z轴尺寸
  - X Rotate---------------------------X轴旋转
  - Y Rotate---------------------------Y轴旋转
  - Z Rotate---------------------------Z轴旋转
- Container Cube Width---------------立方体状包裹器宽度
- Container Cube Height--------------立方体状包裹器高度
- Container Cube Depth---------------立方体状包裹器深度
- Container Sphere Radius------------球状包裹器半径
- Instance Layer---------------------实例层
- Refresh Instance-------------------刷新实例
- Effect Only Group------------------只影响组

### Plexus Transform/变换效果器
用来对粒子进行移动旋转缩放等基本变换
- Center XY--------------------------X轴Y轴中心
- Center Z---------------------------Z轴中心
- X Rotation-------------------------X轴旋转
- Y Rotation-------------------------Y轴旋转
- Z Rotation-------------------------Z轴旋转
- X Translate------------------------X轴偏移
- Y Translate------------------------Y轴偏移
- Z Translate------------------------Z轴偏移
- Uniform Scale----------------------统一尺寸
- Scale------------------------------尺寸
- X Scale----------------------------X轴尺寸
- Y Scale----------------------------Y轴尺寸
- Z Scale----------------------------Z轴尺寸

### Plexus Color Map/颜色映射
效果很强大，使用很频繁，可以用贴图来赋予粒子颜色
- Effector effects-------------------影响
  - Vertices---------------------------影响顶点
  - Faces------------------------------影响面
- Map Amplitude----------------------映射强度
- Apply Map To (Vertices)------------映射到点什么属性
  - Position---------------------------位置，可以使用贴图映射位置，产生置换效果
  - Scale------------------------------尺寸
  - Color------------------------------颜色
- Apply Map To (Faces)---------------映射到面的什么属性
  - Position---------------------------位置
  - Rotation---------------------------旋转
  - Color------------------------------颜色
- Apply To Axis----------------------映射到位置或旋转时应用到哪个坐标轴
- Color Map--------------------------颜色贴图，选择颜色映射的源贴图层
- Flip X-----------------------------反转X轴
- Flip Y-----------------------------反转Y轴
- Map Over Plane---------------------映射平面
- Effect Only Group------------------只影响组

### Plexus Shade Effector/明暗效果器
让粒子像三维模型一样可以被灯光照亮，并受灯光颜色影响，原理是让粒子有明暗变化，但是不能让粒子之间有阴影关系
- Light Name Begins with-------------选择灯光起始名字
- Ambience---------------------------环境光强度
- Effect Only Group------------------只影响组

### Plexus Sound Effector/声音效果器
类似C4D运动图形的声音效果器，用声音来控制粒子移动缩放和颜色
- Sound Layer------------------------选择声音层
- Sound Start Amplitude--------------声音开始振幅
- Sound End Amplitude----------------声音结束振幅
- Frequency Begin--------------------开始频率
- Frequency End----------------------结束频率
- Sample Duration(ms)----------------持续采样时间
- Echo Time Delay--------------------滞后延迟时间
- Affect Position--------------------影响位置
- Affect Scale-----------------------影响缩放
- Affect Color-----------------------影响颜色
- Position---------------------------位置
  - Position Factor--------------------位置系数，影响位置的强度
  - Apply Sound to Axis----------------声音影响哪个轴向
- Scale------------------------------缩放
  - Scale Factor-----------------------缩放系数，影响缩放的强度
- Color------------------------------颜色
  - Color Factor-----------------------颜色系数，影响颜色的强度
  - Color Gradient---------------------颜色渐变
- Effect Only Group------------------只影响组


## Add Renderer/添加渲染器
### Plexus Points Renderer/点渲染
- Points Size------------------------点大小
- Get Scale From Vertices------------从生成器生成的点中获取缩放
- Offset-----------------------------偏移
  - X Offset---------------------------X轴偏移
  - Y Offset---------------------------Y轴偏移
  - Z Offset---------------------------Z轴偏移
- Get Color From Vertices------------从生成器生成的点中获取颜色
- Points Color-----------------------点颜色
- Get Opacity From Vertices----------从生成器生成的点中获取透明度
- Points Opacity---------------------点透明度
- Textured Sprite--------------------贴图精灵，用来进行粒子替代，把粒子替换成选择的层
- Sprite Controls--------------------精灵控制
  - Time Sampling----------------------时间采样
    - Current Time-----------------------当前时间
    - Random Still-----------------------随机固定
    - Random Loop------------------------随机循环
  - Loop Type--------------------------循环模式
  - Random Seed------------------------随机种子
  - Max No. of Samples-----------------最大采样值，如果贴图层很多，需要提高最大采样值，否则有些层可能采样不到

**可以建一个合成，在里面用不同的文字，一个字一帧，在Time Sampling中选择Random Still，可以让粒子随机显示文字，如果选择Random Loop可以让粒子随机显示文字并循环播放动画**

- Points Perspective Aware-----------顶点是否有透视变换，默认勾选，勾选后有顶点有近大远小的透视关系
- Draw Only Connectes Points---------仅显示连接的点，需要配合线渲染器使用，勾选后，如果点没有参与连接线，那么点就不会显示
- Effect Only Group------------------只影响组

### Plexus Lines Renderer/线渲染
- Max No. of Vertices to Sea---------生成线的点的数量，一个点会和周围多少个点发生关联生成线
- Maximum Distance-------------------生成线的两个点的最大距离
- Get Color From Vertices------------从生成器生成的点中获取颜色
- Lines Color------------------------线颜色
- Get Opacity From Vertices----------从生成器生成的点中获取透明度
- Lines Opacity----------------------线透明度
- Opacity over Distance--------------不同距离上透明度变化
- Line Thickness---------------------线宽度
- Thickness over Distance------------不同距离上线宽度变化
- Get Scale From Points--------------从点中获取缩放，线会根据点的缩放进行相应的缩放
- Lines Perspective Aware------------线是否有透视变换，默认勾选，勾选后有线有近大远小的透视关系
- Calc Lines Distance----------------计算点之间距离生成线的方式
  - Every Frame------------------------每一帧都重新计算，会根据点之间的距离，线会实时变化
  - Only One Frame---------------------只计算一帧的点之间距离，每一帧都以这一帧的距离为准
  - Over Time Interval-----------------随时间间隔，每几秒计算一次
- Calc Lines based on this Frame-----Only One Frame方式下，选择以当前帧计算点之间的距离
- Calc Time Interval-----------------Over Time Interval方式下，设置计算的时间间隔
- Draw Lines Between-----------------选择哪些组之间可以生成线

### Plexus Facets Renderer/面渲染
- Get Color From Vertices------------从生成器生成的点中获取颜色
- Color Mode-------------------------颜色模式
  - Interpolate Between Vertices-------顶点颜色插值
  - Average of Vertices----------------顶点平均颜色
  - Color of Vertices------------------顶点颜色
- Facets Color-----------------------面颜色
- Get Opacity From Vertices----------从生成器生成的点中获取透明度
- Facets Opacity---------------------面透明度
- Limit Opacity by Distance----------距离影响透明度
- Opacity over Distance--------------不同距离上透明度变化
- Maximum Distance-------------------生成面的点的最大距离
- Effect Only Group------------------只影响组

### Plexus Triangulation Renderer/三角面渲染
- Render Mode------------------------渲染模式
  - Nearest Triangles------------------最近的三角面
  - Outer Surface----------------------外表面，把点的外框连接生成三角面，把整个Plexus粒子包裹起来
  - Mesh Triangulation-----------------把点当成网格对象生成三角面，和Nearest Triangles模式差不多
- Max No. of Triangles Per Vertex----每个顶点最多参与多少个三角面生成
- Maximum Distance-------------------能生成三角面的点的最大间距
- Get Color From Vertices------------从生成器生成的点中获取颜色
- Color Mode-------------------------颜色模式
  - Interpolate Between Vertices-------顶点颜色插值
  - Average of Vertices----------------顶点平均颜色
  - Color of Vertices------------------顶点颜色
- Triangles Color--------------------三角面颜色
- Get Opacity From Vertices----------从生成器生成的点中获取透明度
- Triangles Opacity------------------三角面透明度
- Opacity over Distance--------------不同距离上透明度变化
- Calc Triangles Distance------------计算点之间距离生成三角面的方式
  - Every Frame------------------------每一帧都重新计算，会根据点之间的距离，三角面会实时变化
  - Only One Frame---------------------只计算一帧的点之间距离，每一帧都以这一帧的距离为准
  - Over Time Interval-----------------随时间间隔，每几秒计算一次
- Calc Triangles based on this Frame-Only One Frame方式下，选择以当前帧计算点之间的距离
- Calc Time Interval-----------------Over Time Interval方式下，设置计算的时间间隔
- Draw Triangles Between-------------选择哪些组的顶点之间可以生成三角面

### Plexus Beams Renderer/光束渲染
注意与Lines Renderer的区别，光束每个点只会有一条线
- Beams Type-------------------------光束类型
  - Objects----------------------------整个对象生成
  - Groups-----------------------------组与组之间生成
- Only on Axis-----------------------整个对象生成时选择在哪个轴向生成光束
- Lines Type-------------------------组与组之间生成时选择连线的类型
  - Straight Lines---------------------直线
  - Bezier Lines-----------------------贝赛尔曲线
- First Group------------------------组与组之间生成时选择第一个组
- Second Group-----------------------组与组之间生成时选择第二个组
- Time-------------------------------时间，K关键帧可以有生长动画
- Flip Direction---------------------反转方向
- Join Ends--------------------------连接终点
- Range Selector---------------------生成范围选择
  - Range Start------------------------开始范围
  - Range End--------------------------结束范围
  - Range Offset-----------------------范围偏移
  - Randomize--------------------------随机化
  - Random Seed------------------------随机种子
- Bezier Settings--------------------贝塞尔设置
  - Bezier Points----------------------贝塞尔点个数，点个数越多，曲线越平滑
  - Start Curve------------------------起始曲率
  - End Curve--------------------------结束曲率
  - Bezier Axis------------------------贝塞尔坐标
- Start Thickness--------------------开始宽度
- End Thickness----------------------结束宽度
- Get Color From Vertices------------从生成器生成的点中获取颜色
- Beams Color------------------------光束颜色
- Get Opacity From Vertices----------从生成器生成的点中获取透明度
- Beams Opacity----------------------光束透明度
- Get Scale From Points--------------从点中获取缩放，线会根据点的缩放进行相应的缩放
- Perspective Aware------------------光束是否有透视变换，默认勾选，勾选后光束有近大远小的透视关系
- Effect Only Group------------------只影响组

## Add Group/添加组

# Plexus
- Toggle Plexus Object Panel---------打开关闭对象面板
- Shading----------------------------阴影关系
  - Use Lights for Shading-------------使用灯光来影响阴影关系
    - Light(s) Name Begins with----------灯光名字以什么开始，用来选择灯光
    - Shading Mode-----------------------阴影模式，让灯光可以对Plexus照明，注意只能给面照明
      - One Side---------------------------一边
      - Both Sides-------------------------两边
    - Shading Radius---------------------阴影半径
    - Shading Falloff--------------------阴影衰减
- Unified Rendering------------------统一渲染，勾选后可以渲染景深和运动模糊
  - Depth of Field---------------------景深
    - Depth of Field---------------------开启关闭景深
      - Off--------------------------------关闭景深
      - Camera Settings--------------------根据摄像机设置
    - Blur Factor------------------------模糊因数
  - Motion Blur------------------------运动模糊
    - Render Motion Blur-----------------渲染运动模糊
      - Off--------------------------------不渲染运动模糊
      - Comp Settings----------------------根据合成设置
      - Custom-----------------------------自定义
    - Shutter Angle----------------------快门角度
    - Shutter Phase----------------------快门想为，决定运动模糊的方向
    - Motion Blur Samples----------------运动模糊采样
  - Visibility-------------------------可见性
    - Polygon Visibility-----------------
    - Near Vanish------------------------近处修剪
    - Near Fade--------------------------近处衰减
    - Far Fade---------------------------远处衰减
    - Far Vanish-------------------------远处修剪
    - Depth Map for Occlusion------------选择深度图
    - White Pixels Depth-----------------白色像素深度
    - Dark Pixels Depth------------------黑色像素深度
  - Render Quality---------------------景深模糊质量
- Export SVG-------------------------导出SVG文件，可以在AI中打开
- Refresh Cache----------------------清空缓存


**Plexus与C4D交互的三种方法**
1. 将C4D中的模型导出成OBJ格式，如果是动画，使用插件导出成OBJ序列，在Plexus中使用OBJ Object导入，注意AE和C4D的Y轴与Z轴均是相反的，需要对Y轴和Z轴勾选反向
2. 在C4D中使用空物体克隆到物体表面顶点，然后对空物体克隆添加外部合成标签，勾选应用子集，导出成aec文件后，在Plexus中使用Layer Object导入,注意C4D的克隆不能勾选渲染实例
3. 将C4D中的灯光使用外部合成导出，在Plexus中使用Layer Object导入