# 欢迎界面
- Create a terrain(Graph)/创建节点工程（常用）
- Create a terrain(Layers)/创建图层工程（不常用）
- Create new sculpt/创建侵蚀雕刻工程
Gaea独特和最有亮点的功能，直接用笔刷雕刻侵蚀细节，用法是导入制作好的地形高度图，使用笔刷绘制

# 顶部菜单
## Entire terrain/导出地形
注意导出地形前需要在需要构建的节点上点击右键选择Mark for Export或按F3标记节点
### Resolution/导出尺寸
### Format/导出格式
### Additional Options/附加选项
- Resample-----------------------重采样
- ColorSpace---------------------色彩空间
- Ignore Vertical Scale----------忽略垂直尺寸
- Increase Output Scale By+1-----输出尺寸增加1像素，避免一些软件使用Gaea输出的地形图时边缘出现错误
- Save a Copy of this.TOR file---保存一个副本
### Close Gaea UI/输出后关闭Gaea
### Open folder after build/输出后打开文件夹
### Beep when done/完成提示音

## Current preview/截屏

## Preferences/首选项

# 预览视窗设置
## Viewport Preview Resolution/调整预览尺寸

## 预览模式
### Orbit/盘旋模式（最常用）
### First Person/第一人称模式
WASDQE控制前进后退向左向右向上向下
### Orthographic/顶视图模式（不常用）

## Materials/地形预览材质

## Atmosphere/大气
控制日光方向、强度等

## Water Level/海平面

## Other Settings/其他设置
### Terrain Definition/定义地形
调整地形高度等，但是地形高度一般不在这里调整，而是添加一个AutoLevel节点

## Build/生成地形

## Build Stack/打开输出文件夹

## Resource Manager/资源管理器

## Cancel running processes/取消解算（很常用）

## Suspend engine/暂停解算
激活后修改节点不会自动解算，取消激活后再开始解算

# 节点
## 节点视窗设置
- Auto fit/自动调整节点大小
- Force refresh all nodes/强制刷新所有节点（常用）
- Mutate seeds(Randomize all nodes)/改变所有节点的随机值

## 节点右键菜单
- Rename/节点重命名（快捷键F2）
- Duplicate/复制节点（快捷键Ctrl+D）
- Refresh/刷新节点（快捷键F5）
- Show as/显示为
- Bypass/跳过（快捷键B）
点击后这个节点不参加解算
- Pin/锁定预览效果到当前节点
- Pin for Color
- Mark for Export/标记输出（快捷键F3）
- Delete/删除
- Preset/生成预设

## Primitives/基础架构节点
基础节点用来构造基础地形
### Constant/常数
生成一个等高的地形
- Height-------------------------高度
### Dunes/沙丘
### Fault/断层
用来生成裂谷断层
### File/文件
导入高度图
### Gradient/渐变
- Type---------------------------渐变类型
  - Linear-------------------------线性渐变
  - Radial-------------------------径向渐变
  - Helix--------------------------螺旋渐变
### Igneous/火山岩
### LineNoise/线状燥波
### Mountain/山
### Perlin/柏林燥波
### Plates/高原
### Resource/资源
### SlopeNoise/斜坡燥波
### Voronoi/泰森多边形
### Voronoi+/泰森多边形+

## Adjustments/调整节点
### Autolevel/自动级别
非常常用，会自动调整高度图的对比度，原理是把原来的0-X的亮度级别调整为0-1的级别，让原本很低的山变高，原本很高的山变低，使输出的灰度图是从纯黑到纯白的标准化灰度图，不会有色彩的浪费
**在调整山体时一般添加Autolevel节点，而不是在右上角的OtherSettings里面调整**
- Autolevel----------------------自动级别
  - Apply Autolevel----------------开启自动级别
  - Strength-----------------------强度
- Equalize-----------------------均衡化
  - Apply Equalize-----------------开启均衡化
  - Equalize-----------------------均衡化强度
- Gamma--------------------------Gamma调整
  - Apply Gamma--------------------开启Gamma调整
  - Auto Gamma---------------------自动Gamma
  - Gamma--------------------------Gamma调整
### BiasGain/增益
### Blur/模糊
### Clamp/钳制
### Combine/合并
### Denoise/去掉燥波
用来减少燥波
### Displace/置换
### Flip/反转
### Gamma
### Heal/修复
导入的地形有时可能有问题，使用Heal节点修复错误
### Invert/反相
### Sharpen/锐化
### Sine/三角函数
### Threshold/最高最低
### Transform/变化
### Zero Borders/边缘模糊

## Filters/过滤器
### Aperture/孔径
会把山脊尖的地方加厚
### Apex/尖顶
让山变尖
**Constant节点添加Transform节点，再添加Apex节点，会变成金字塔形状**
### Bomber/炸裂
会把现有地形克隆很多份，位置尺寸旋转随机放置
**一般不直接连接地形，因为出来的效果不好看，使用时一般是连接到局部细节，把局部细节克隆多份**
### Cells/细胞
效果类似Stratify
### Noise/燥波
增加细节
### Origami/折纸
把地形变成折纸风格
### Polar/极坐标
把地形从四周向中间挤压
### Recurve/反向弯曲
会让所有粗犷的地方尖锐化，制作被风刮过的效果
### Repulse/反向推动
效果类似极坐标
### Rocks/岩石化
效果类似Noise，这个节点效果不是很好，没有岩石的效果
### Subterrace/次级梯田
### Swirl/旋转
从正中间形成一个大的旋涡
### Terrace/梯田
### Whorl/涡轮
依据地形形成多个小漩涡

## Erosion/侵蚀细节
### Alluvium/冲积层
会让地势低的地方产生冲积的效果
### Breaker/断层
### Buildup/聚积
会在地形表面聚积一层
### Coast/海岸线
模拟海岸的侵蚀
### Convector/对流器
用来制作雪山的雪堆积效果
### Deposits/沉着物
用来制作沙丘效果
### Erosion/侵蚀
### Fluvial/河流
用来制作河流冲刷效果
### Fold/对折
不常用，效果类似大理石断层
### Hydro/水流
### Landform/地形侵蚀
很常用，在一大片区域比较平整时，可以使用地形侵蚀增加细节
### MicroErosion/微小侵蚀
非常实用，在制作完形态后再加一个微小侵蚀，效果非常好
### RockSlide/岩石滑坡
### Sediment/沉积
可以给地形添加薄薄的一层沙、雪等效果
### Snow/积雪
### Stratify/分层
把地形转成类似Minecraft风格的块状形态
### Thermal/

## Data Maps/数据图
生成各种数据遮罩
### Distribution/分布图
不常用，用来导出分布到别的软件，图中只有最高和最低
### Flow/河流图
### Growth/植被图
### Soil/土壤图
### Surfacer/
### Velocity/

## Selectors/选择器
### Angle/角度选择
通过设置光照角度来生成黑白贴图
### Curvature/曲率选择
### Height/高度选择
这个节点通过读取高度图可以选择高度范围
### Mask/遮罩
可以用笔刷手绘遮罩
### Slope/坡度选择
这个节点通过读取高度图可以选择坡度范围

## Color/颜色
### Biome/自动赋予颜色
### CLUTer/
### ColorFx/调色
用来调整HSL、Gamma等
### Mixer/颜色混合
### Normal Map/法线图
### RGBMix/RGB混合
分别将不同的节点连接到RGBMix的R、G、B端口，输入到R、G、B通道
### RGBSplit/RGB分裂
将RGB通道分开输出
### SatMaps/按地形着色
### Synth/颜色合成器
## Output/输出
### Mesher/输出为模型
### Output/输出为贴图
## Organize/
### Portal/




