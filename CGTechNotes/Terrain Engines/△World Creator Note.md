# 左侧工具栏
- SYNC-Tool Export
- Toggle Heatmaps
显示热图
- Toggle Observe Tools
显示HUD
- Toggle Mannequin
- Toggle Compass
显示罗盘
- Toggle Wireframe
显示线框
- Toggle Filters
显示滤镜
- Toggle Texture
显示材质
- Toggle Objects
显示树木等对象
- Toggle Details
显示草丛等细节

# Surface/表面
## Base/基础
### Fractal Generator Properties/分形生成器
- Seed------------------------随机种子
- Area------------------------区域
  - Invert Area-----------------反转所选区域
  - Strength--------------------强度
  - Relative Height-------------区域相对高度
### Terrain Size(In Meters)/地形尺寸
- Size Locked-----------------锁定比例
- Terrain Width---------------地形宽度
- Terrain Length--------------地形长度
### Precision(In Meters)/地形精度
- Precision-------------------精度
### Soil Properties/土壤特性
- Soil------------------------激活土壤
- Depth-----------------------土壤深度
### Custom Base Shape Properties/自定义基础形状属性
- Custom Base Shape-----------勾选后可以自定义调整基础地形
- Edit Shape------------------编辑形状
  - Selection Tool--------------选择编辑工具
  - Action----------------------动作
  - Flatten Entire Terrain------把全部地形压扁
  - Reset Control Points--------重置控制点
### Seamless Properties/无缝属性
- Seamless X------------------X轴无缝
- Seamless Z------------------Z轴无缝
### Fractal Noise Properties/分形燥波属性
- General Strength------------燥波强度
- Factor----------------------因子
- Edit Curve------------------编辑曲线
  - Curve-----------------------曲线
  - Tools-----------------------曲线编辑工具
    - Smooth Curve----------------平滑曲线
    - Flatten Curve---------------压扁曲线
  - Radius----------------------半径
  - Scale-----------------------尺寸
- Edit Offset-----------------编辑偏移，勾选后可以调节X轴和Z轴的偏移，每一个控制每一层的燥波偏移
### Fractal Noise Level Strength Per Step/分形燥波每步强度级别
World Creator的滤镜系统是基于每步/每分辨率进行计算的，这意味着World Creator从生成 ```4 * 4``` 像素分辨率的随机分形开始，这是步幅1，步幅2是 ```8 * 8``` ，步幅3是```16 * 16```

## Filters/滤镜
基本上所有的滤镜都是修改器，直接影响基本地形形状，它们可以互相组合合并和进一步分组组成图层，图层可以限制到区域。滤镜属于可以放置区域的特殊层。可以使用图层、滤镜、区域的结合曲创建植物群落
### Filter Layers
#### General Filters/一般滤镜
##### Flatten/压扁
让地形趋于平缓，可以结合Relative to Ocean创建好看的沙滩
- General Strength------------强度，控制滤镜对地形影响强度
- Flatten Strength------------平滑度


##### Invert Height/反转高度
让地形高于某个高度的部分反转
- General Strength------------强度，控制滤镜对地形影响强度
- Height----------------------选择高度高于多少开始反转
- Scale-----------------------反转高度的比例系数
- Smoothness------------------平滑

##### Noise/燥波
非常强大和灵活的柏林燥波生成器，有很多种用法，比如可以增加额外的燥波地形创建陨石坑或其他不常见的类地表面
- General Strength------------强度，控制滤镜对地形影响强度
- Seed------------------------随机种子
- Scale-----------------------燥波贴图尺寸
- Height----------------------燥波影响高度的强度
- Depth-----------------------燥波贴图深度
- MinCut----------------------最小修剪
- MaxCut----------------------最大修剪
- MinValue--------------------燥波值最小值
- MaxValue--------------------燥波值最大值
- Type------------------------生成的燥波值是正的还是负的
- Height Offset---------------高度偏移
- Set Mode--------------------设置模式，如果勾选，这个燥波滤镜将覆写原始高度值
- Resize to Step--------------调整步幅，如果勾选，燥波值将调整为当前活动级别的步幅强度值

##### Smooth/平滑
平滑地形，可以使用坡度和高度范围分布设置来平滑地形中特定的部分。可以使用平滑滤镜创建沙丘
- General Strength------------强度，控制滤镜对地形影响强度
- Smooth Strength-------------平滑度

##### Smooth Ridges/平滑山脊
用来平滑地形上的山脊
- General Strength------------强度，控制滤镜对地形影响强度
- Length----------------------长度，控制山脊平滑长度

##### Voronoi/泰森多边形
泰森多边形适用于有裂缝的泥浆、大型山区和有沙丘的荒漠
- General Strength------------强度，控制滤镜对地形影响强度
- Cell Size-------------------单位尺寸
- Height Offset---------------高度偏移
- Height Scale----------------高度尺寸
- Set Mode--------------------选取模式，如果勾选，将覆盖原有高度

##### Voronoi Border/泰森多边形混合
适用于有裂缝的泥浆、大型山区和有沙丘的荒漠
- General Strength------------强度，控制滤镜对地形影响强度
- Cell Size-------------------单位尺寸
- Border Size-----------------边界尺寸
- Border Smooth---------------边界平滑度

##### Zero Edge/零边缘
沿边缘将地形归零，非常适合创建岛屿
- General Strength------------强度，控制滤镜对地形影响强度
- Smoothness------------------平滑度


#### Design Filters/设计滤镜
设计滤镜允许创建可用的自定义路径和形状，进一步手工修改地形
##### Curve/曲线
使用这个滤镜可以创建一个曲线，可以用来创建峡谷、梯田和火山
- General Strength------------强度，控制滤镜对地形影响强度
- Curve-----------------------曲线
- Min Height------------------曲线适用的最低高度
- Max Height------------------曲线适用的最高高度

##### Path/路径
可以用来创建多个路径对象来进一步设计山脉、道路、峡谷等，它也可以创建一个路径来应用纹理
- Add Path--------------------添加路径
- Path
  - Name------------------------路径名
  - Length----------------------路径长度
  - Height Offset---------------高度偏移
  - Strength--------------------强度
  - Width-----------------------宽度
  - Smoothness------------------平滑
  - Segment Offset--------------部分偏移
  - Noise Scale-----------------燥波尺寸
  - Noise Factor----------------燥波因子
  - Closed----------------------闭合路径
  - Use Level Step--------------勾选后使用步幅
  - Level Step------------------步幅级别
- Edit Path--------------------编辑路径
- Has Mesh--------------------激活网格
  - Height Offset(Mesh)---------网格高度偏移
  - Material--------------------材质类型
    - Standard--------------------标准
    - Water-----------------------水材质
  - Texture---------------------纹理

##### Shape/形状
可以创建矢量形状，用于进一步设计山脉、道路、峡谷、湖泊等，也可以在路径上创建额外的网格，进而使用纹理
- Add Shape-------------------添加形状
- Shape
  - Name------------------------形状名
  - Height Offset---------------高度偏移
  - Strength--------------------强度
  - Smoothness------------------平滑
  - Use Level Step--------------勾选后使用步幅
  - Level Step------------------步幅级别
- Edit Shape------------------编辑形状
- Has Mesh--------------------激活网格
  - Height Offset(Mesh)---------网格高度偏移
  - Material--------------------材质类型
    - Standard--------------------标准
    - Water-----------------------水材质
  - Texture---------------------纹理

#### Effect Filters/效果滤镜
可以使用扭曲、旋涡、像素化等效果
##### Balloon/膨胀
根据地形表面的孔洞使地形膨胀/收缩
- General Strength------------强度，控制滤镜对地形影响强度
- Direction-------------------方向，控制膨胀还是收缩，大于0是膨胀，小于0是收缩
- Length----------------------长度，控制膨胀和收缩的长度
- Smoothness------------------平滑

##### Deflate/收缩
根据地形表面方向收缩地形
- General Strength------------强度，控制滤镜对地形影响强度
- Length----------------------长度，控制收缩的长度

##### Directional Balloon/方向性膨胀
根据地形表面的孔洞和给定的角度值来使地形膨胀/收缩
- General Strength------------强度，控制滤镜对地形影响强度
- Direction-------------------方向，控制膨胀还是收缩，大于0是膨胀，小于0是收缩
- Horizontal Angle------------水平角
- Vertical Angle--------------垂直角
- Affected Steepness----------影响陡度
- Length----------------------长度，控制膨胀和收缩的长度
- Smoothness------------------平滑

##### Distort/扭曲
水平扭曲地形
- General Strength------------强度，控制滤镜对地形影响强度
- Length----------------------长度，控制扭曲变形的长度
- Scale-----------------------缩放

##### Inflate/膨胀
根据地形表面方向使地形膨胀
- General Strength------------强度，控制滤镜对地形影响强度
- Length----------------------长度，控制膨胀的长度

##### Magnify/放大
由内而外放大地形
- General Strength------------强度，控制滤镜对地形影响强度
- Magnify Strength------------放大强度

##### Normal Map/法线贴图
加载一张法线贴图来增强细节
- General Strength------------强度，控制滤镜对地形影响强度
- Length----------------------长度，控制法线贴图的长度
- Scale-----------------------缩放，控制法线贴图的缩放
- Scale with Level------------根据级别缩放
- Normal Map------------------导入法线贴图

##### Pixelate/像素化
把地形像素化
- General Strength------------强度，控制滤镜对地形影响强度
- Pixel Size------------------像素块尺寸

##### Rugged/崎岖
根据地形表面角度改变地形，创建崎岖的地形外观
- General Strength------------强度，控制滤镜对地形影响强度
- Angle-----------------------角度
- Length----------------------长度，控制崎岖的长度

##### Swirl/旋涡
从内到外旋转地形
- General Strength------------强度，控制滤镜对地形影响强度
- Swirl Strength--------------旋涡强度


#### Alien Filters/异形滤镜
可以用来制作陨石坑和外星球的地形等
##### Cratered Cliffs/坑坑洼洼的悬崖
可以用来生成类似月球表面的布满火山口和又深又硬的悬崖的景观，可也创造一些外星陨石坑的世界
- General Strength------------强度，控制滤镜对地形影响强度
- Fine Strength---------------微调，可以增加附加强度值
- Rough Strength--------------粗调，可以增加小火山口和坚硬悬崖的数量
- Min Angle-------------------最小角，控制地形中应用此滤镜的最小角度
- Max Angle-------------------最大角，控制地形中应用此滤镜的最大角度

##### Cratered Plates/坑坑洼洼的平坦地面
这个滤镜创造了一个坑坑洼洼的，含金属的，包含了互相叠加的平原和高原的景观
- General Strength------------强度，控制滤镜对地形影响强度


#### Canyon Filters/峡谷滤镜
可以用来制作峡谷
##### Canyon/峡谷
峡谷滤镜用来创建典型的西方风格的景观，有陡峭的悬崖和小高原，也可以通过路径和形状滤镜创建典型的峡谷走廊
- General Strength------------强度，控制滤镜对地形影响强度
- Sharpness-------------------陡度，控制峭壁的陡峭级别
- Sharpness Strength----------陡峭强度，控制峭壁的陡峭强度

##### Canyon Sand Covered/峡谷沙地
峡谷沙地滤镜用来创建典型的沙漠风格的景观，有陡峭的悬崖和非常小的高原，实际上它是在标准峡谷滤镜上覆盖了沙子沉积，它也可以用来创建积雪覆盖悬崖的景观
- General Strength------------强度，控制滤镜对地形影响强度
- Sharpness-------------------陡度，控制峭壁的陡峭级别
- Sharpness Strength----------陡峭强度，控制峭壁的陡峭强度

##### Canyon Rocky Cliffs/峡谷岩石悬崖
峡谷岩石悬崖滤镜用来创建岩石岩壁，而不是陡峭的崖壁。额外的沙子沉积让这个滤镜在创建另一种
- General Strength------------强度，控制滤镜对地形影响强度
- Min Count-------------------周围高度样本的最小数量
- Max Count-------------------周围高度样本的最大数量
- Min Angle-------------------最小角，控制地形中应用此滤镜的最小角度
- Max Angle-------------------最大角，控制地形中应用此滤镜的最大角度

##### Canyon Smooth/峡谷平滑
峡谷平滑滤镜用来创建典型的西方风格的景观，有陡峭的悬崖和小高原，也可以通过路径和形状滤镜创建典型的峡谷走廊
- General Strength------------强度，控制滤镜对地形影响强度
- Bottom Height---------------底部高度
- Bottom Smoothness-----------底部平滑
- Bottom Border---------------底部边缘
- Top Height------------------顶部高度
- Top Smoothness--------------顶部平滑
- Top Border------------------顶部边缘

#### Erosion Filters/侵蚀滤镜
对地形进行侵蚀、风化等特定操作
##### Erosion/侵蚀
用来对地形进行侵蚀
- General Strength------------强度，控制滤镜对地形影响强度
- Reduce Flow Amount----------减少河流冲刷痕迹数量，数值越低，河流冲刷痕迹越多越明显
- Depth Reduction-------------减小河流冲刷痕迹深度
- Wideness--------------------河流冲刷痕迹宽度
- Sharpness-------------------河流冲刷痕迹锐利度
- Deepness--------------------河流冲刷痕迹深度
- Smoothness------------------河流冲刷痕迹平滑度
- Min Height------------------最小高度
- Max Height------------------最大高度

##### Erosion Fluvial/侵蚀河流
使用这个滤镜来侵蚀地形，可以创建被侵蚀后的河流、沙子和雪
- General Strength------------强度，控制滤镜对地形影响强度
- Depth-----------------------侵蚀深度
- Max Length------------------侵蚀最大长度
- Slope Start Min-------------开始侵蚀的最小坡度
- Slope Start Max-------------开始侵蚀的最大坡度
- Slope Min-------------------侵蚀雕刻的最小坡度
- Slope Max-------------------侵蚀雕刻的最大坡度
- Noise-----------------------侵蚀燥波
- Precision-------------------精确度

##### Erosion Deep/深度侵蚀
这个滤镜在侵蚀地形时会造成很深的侵蚀雕刻效果
- General Strength------------强度，控制滤镜对地形影响强度
- Depth-----------------------侵蚀深度
- Max Length------------------侵蚀最大长度
- Slope-----------------------坡度为多少的地方开始侵蚀
- Slope Strength--------------坡度强度，侵蚀强度取决于地形坡度
- Min Height------------------最小高度
- Max Height------------------最大高度

##### Erosion Soft/软侵蚀
这个滤镜在侵蚀地形时会造成软侵蚀雕刻效果
- General Strength------------强度，控制滤镜对地形影响强度
- Depth-----------------------侵蚀深度
- Max Length------------------侵蚀最大长度
- Slope Min-------------------侵蚀雕刻的最小坡度
- Slope Max-------------------侵蚀雕刻的最大坡度
- Noise-----------------------侵蚀燥波
- Precision-------------------精确度

##### Wind/风
对地形应用类似风的方向失真
- General Strength------------强度，控制滤镜对地形影响强度
- Length----------------------长度，控制风的影响时间长度
- Direction-------------------方向，控制风的方向


#### Sediment Filters/沉积滤镜
对地形进行沉积等特定操作
##### Sediment/沉积
通过用物质填满山谷来模拟沉积
- General Strength------------强度，控制滤镜对地形影响强度
- Length----------------------长度，控制填满山谷的尺寸
- Quality---------------------尺寸，控制沉积质量，更大的尺寸需要更好的电脑性能

##### Sediment Complex/沉积混合
通过用物质填满山谷来模拟沉积
- General Strength------------强度，控制滤镜对地形影响强度
- Length----------------------长度，控制填满山谷的尺寸
- Quality---------------------尺寸，控制沉积质量，更大的尺寸需要更好的电脑性能


#### Hills Filters/山滤镜
生成丘陵、山脉等
##### Hills/丘陵
用来创建一些丘陵小山
- General Strength------------强度，控制滤镜对地形影响强度
- Ridge Strength--------------山脊强度，调节山脊的陡度和落差
- Min Count-------------------周围高度样本的最小数量
- Max Count-------------------周围高度样本的最大数量
- Min Angle-------------------最小角，控制地形中应用此滤镜的最小角度
- Max Angle-------------------最大角，控制地形中应用此滤镜的最大角度

##### Ridged and Crossed Hills/有山脊和交叉的小山
这个滤镜创建非常陡峭的小山和高角度山脊的景观
- General Strength------------强度，控制滤镜对地形影响强度
- Min Count-------------------周围高度样本的最小数量
- Max Count-------------------周围高度样本的最大数量
- Min Angle-------------------最小角，控制地形中应用此滤镜的最小角度
- Max Angle-------------------最大角，控制地形中应用此滤镜的最大角度

##### Rocky Bumpy Hills/崎岖不平的岩石小山
这个滤镜创建有岩石和崎岖不平的表面的小山
- General Strength------------强度，控制滤镜对地形影响强度
- Hills Strength--------------山强度，调节山的高度
- Min Count-------------------周围高度样本的最小数量
- Max Count-------------------周围高度样本的最大数量
- Angle-----------------------角度，控制地形中应用此滤镜的角度

##### Rocky Hills/岩石小山
这个滤镜创建其他类型的岩石表面的小山
- General Strength------------强度，控制滤镜对地形影响强度
- Hills Strength--------------山强度，调节山的高度
- Min Count-------------------周围高度样本的最小数量
- Max Count-------------------周围高度样本的最大数量
- Angle-----------------------角度，控制地形中应用此滤镜的角度

##### Mountains/山脉
创建山脉
- General Strength------------强度，控制滤镜对地形影响强度
- Layer Strength--------------层强度，调节山的高度
- Min Count-------------------周围高度样本的最小数量
- Max Count-------------------周围高度样本的最大数量
- Min Angle-------------------最小角，控制地形中应用此滤镜的最小角度
- Max Angle-------------------最大角，控制地形中应用此滤镜的最大角度

##### Rocky Deep Hills/很深的岩石小山
创建有着很深的多岩石小山丘的景观
- General Strength------------强度，控制滤镜对地形影响强度
- Fine Strength---------------微调
- Rough Strength--------------粗调
- Min Count-------------------周围高度样本的最小数量
- Max Count-------------------周围高度样本的最大数量
- Min Angle-------------------最小角，控制地形中应用此滤镜的最小角度
- Max Angle-------------------最大角，控制地形中应用此滤镜的最大角度


#### Plateaus Filters/高原滤镜
##### Rocky Plateaus/多岩石的高原
创建多岩石的高原地形
- General Strength------------强度，控制滤镜对地形影响强度
- Min Count-------------------周围高度样本的最小数量
- Max Count-------------------周围高度样本的最大数量
- Min Angle-------------------最小角，控制地形中应用此滤镜的最小角度
- Max Angle-------------------最大角，控制地形中应用此滤镜的最大角度

##### Clean Plateaus/干净的高原
创建一个干净的高原
- General Strength------------强度，控制滤镜对地形影响强度
- Fine Strength---------------微调
- Rough Strength--------------粗调
- Min Count-------------------周围高度样本的最小数量
- Max Count-------------------周围高度样本的最大数量
- Min Angle-------------------最小角，控制地形中应用此滤镜的最小角度
- Max Angle-------------------最大角，控制地形中应用此滤镜的最大角度

#### Ridged Filters/山脊滤镜
##### Ridged/山脊
创建山脊
- General Strength------------强度，控制滤镜对地形影响强度
- Ridge Strength--------------山脊强度
- Min Count-------------------周围高度样本的最小数量
- Max Count-------------------周围高度样本的最大数量
- Min Angle-------------------最小角，控制地形中应用此滤镜的最小角度
- Max Angle-------------------最大角，控制地形中应用此滤镜的最大角度

##### Small Sharp Ridges/小而尖的山脊
创建小而尖的山脊
- General Strength------------强度，控制滤镜对地形影响强度
- Sharpness-------------------尖锐度


#### Terrace Filters/梯田滤镜
##### Terrace/梯田
使用这个高度可定制化的梯田滤镜可以把地形转变为梯田地形
- General Strength------------强度，控制滤镜对地形影响强度
- Strength Multiplier---------强度倍增，用来提升梯田强度
- Random----------------------随机
- Min Size--------------------单个梯田的最小高度
- Max Size--------------------单个梯田的最大高度

##### Minecraft/我的世界
这个非常特别的梯田滤镜可以创建“我的世界”风格的梯田
- Min Size--------------------单个梯田的最小高度
- Max Size--------------------单个梯田的最大高度

##### Terrace Smooth/平滑梯田
可以创建没有硬边的平滑梯田
- General Strength------------强度，控制滤镜对地形影响强度
- Strength Multiplier---------强度倍增，用来提升梯田强度
- Random----------------------随机
- Min Size--------------------单个梯田的最小高度
- Max Size--------------------单个梯田的最大高度

##### Terrace Irregular/不规则梯田
可以创建没有不规则的梯田
- General Strength------------强度，控制滤镜对地形影响强度
- Random----------------------随机
- Top Smoothness--------------顶部边的平滑程度
- Irregularity Size-----------不规则的尺寸
- Irregularity Scale----------不规则的缩放
- Terrace Amount--------------梯田的数量

##### Terrace Cliffs/悬崖状梯田
可以创建没有悬崖状的梯田
- General Strength------------强度，控制滤镜对地形影响强度
- Random----------------------随机
- Scale-----------------------缩放
- Terrace Amount--------------梯田的数量
- Irregularity----------------不规则程度


#### Dunes Filters/沙丘滤镜
##### Dunes/沙丘
沙丘滤镜用来创建一些非常漂亮的沙丘，根据设置，可以创建更多的岩石和更小的沙丘，将底层景观变成干旱的
- General Strength------------强度，控制滤镜对地形影响强度

### Filter Distribution Properties/滤镜分布属性
定义滤镜应用的位置
- Operation-------------------叠加方式
  - Addition--------------------相加
  - Subtraction-----------------相减
  - Min-------------------------最小值
  - Max-------------------------最大值
- Cavity----------------------孔洞
  - None------------------------无
  - Convex----------------------凸面
  - Concave---------------------凹面
    - Steps-----------------------步幅
    - Step Size-------------------步幅尺寸
    - Strength--------------------强度
- Noise Select----------------燥波选取
  - World Size------------------尺寸
  - Scale-----------------------缩放
  - Seed------------------------种子
  - Octaves---------------------阶度
  - Depth-----------------------深度
  - Factor----------------------燥波因子
  - Factor Low------------------最低因子
  - Factor High-----------------最高因子
- Height Select---------------高度选取
  - Relative to Ocean-----------相对于海
  - Height Range----------------高度范围
  - Height Smoothness-----------高度平滑
- Slope Select----------------坡度选取
  - Slope Range-----------------坡度范围
  - Slope Smoothness------------坡度平滑
- Angle Select----------------角度选取
  - Angle-----------------------角度
  - Angle Width-----------------角度宽度，控制角度范围
  - Slope Smoothness------------角度平滑

### Filter Level Strengths/滤镜级别强度


# Textures/纹理
## Textures/纹理
### Texture Layers/纹理层
- Add Layer-------------------添加层
- Remove All------------------移除所有层
- Name------------------------层名字
- Area------------------------层区域
- Textures--------------------添加纹理
- Save Heatmap----------------储存热图，将当前纹理的分布导出为黑白遮罩

### Texture Properties/纹理属性
- Diffuse Map-----------------漫射贴图
- Normal Map------------------法线贴图
- Height Map------------------高度贴图
- Tag-------------------------标签
- Operation-------------------叠加方式
  - Default---------------------默认
  - Multiply--------------------相乘
  - Add-------------------------相加
  - Subtract--------------------相减
  - Subtractinverse-------------减法器
- Lock Tile Size--------------锁定尺寸比率
- Tile Size X-----------------X轴尺寸
- Tile Size Y-----------------Y轴尺寸
- Lock Tile Offset------------锁定偏移比率
- Tile Offset X---------------X轴偏移
- Tile Offset Y---------------Y轴偏移
- Use Gradient----------------使用渐变
  - Strength--------------------强度
  - Height Offset---------------高度偏移
  - Height Size-----------------高度尺寸

### Texture Distribution Properties/纹理分布属性
- Sediment Surface------------表面沉积物
- Cavity----------------------孔洞
  - None------------------------无
  - Convex----------------------凸面
  - Concave---------------------凹面
    - Steps-----------------------步幅
    - Step Size-------------------步幅尺寸
    - Strength--------------------强度
- Roughness-------------------粗糙
- Follow Sun Direction--------跟随日光方向
  - Invert----------------------反向
  - Smoothness------------------平滑度
- Noise Select----------------燥波选取
  - World Size------------------尺寸
  - Scale-----------------------缩放
  - Seed------------------------种子
  - Octaves---------------------阶度
  - Depth-----------------------深度
  - Factor----------------------燥波因子
  - Factor Low------------------最低因子
  - Factor High-----------------最高因子
- Height Select---------------高度选取
  - Relative to Ocean-----------相对于海
  - Height Range----------------高度范围
  - Height Smoothness-----------高度平滑
- Slope Select----------------坡度选取
  - Slope Range-----------------坡度范围
  - Slope Smoothness------------坡度平滑
- Angle Select----------------角度选取
  - Angle-----------------------角度
  - Angle Width-----------------角度宽度，控制角度范围
  - Slope Smoothness------------角度平滑

## General/一般设定
### Texturing Properties/纹理属性
- Height-Based----------------基于高度，激活后，置换贴图会影响高度值的采样，并使用采样去计算纹理权重。如果从地面上看，基于高度的纹理会有一个很真实的效果。但是如果从远处看，会有一个很难看的硬边。基于高度的属性还很依赖置换贴图的质量
  - Smooth Height---------------平滑高度
- Tri-Planar------------------
- Perlin-Normal Noise---------柏林法线燥波
- Eliminate Tiling------------


# Scene/景观
## Objects/对象
### Object Layers/对象层
用来添加树木、草、灌木、花、岩石、小景观等对象

### Object Properties/对象特性
- Tag-------------------------标签
- Height Offset---------------高度偏移，对象距离地面的高度
- Size Locked-----------------锁定尺寸比率
- Width Range-----------------宽度范围
- Height Range----------------高度范围
- Rotation X Range------------X轴旋转范围
- Rotation Y Range------------Y轴旋转范围
- Rotation Z Range------------Z轴旋转范围
- Align to Terrain------------与地形对齐

### Object Distribution Properties/对象分布属性
- Cavity----------------------孔洞
  - None------------------------无
  - Convex----------------------凸面
  - Concave---------------------凹面
    - Steps-----------------------步幅
    - Step Size-------------------步幅尺寸
    - Strength--------------------强度
- Follow Sun Direction--------跟随日光方向
  - Invert----------------------反向
  - Smoothness------------------平滑度
- Noise Select----------------燥波选取
  - World Size------------------尺寸
  - Scale-----------------------缩放
  - Seed------------------------种子
  - Octaves---------------------阶度
  - Depth-----------------------深度
  - Factor----------------------燥波因子
  - Factor Low------------------最低因子
  - Factor High-----------------最高因子
- Height Select---------------高度选取
  - Relative to Ocean-----------相对于海
  - Height Range----------------高度范围
  - Height Smoothness-----------高度平滑
- Slope Select----------------坡度选取
  - Slope Range-----------------坡度范围
  - Slope Smoothness------------坡度平滑
- Angle Select----------------角度选取
  - Angle-----------------------角度
  - Angle Width-----------------角度宽度，控制角度范围
  - Slope Smoothness------------角度平滑

## Details/细节
### Detail Layers/细节层
用来添加如花、草、叶片等2D细节

### Detail Properties/细节特性
- Tag-------------------------标签
- Ground Tint Strength--------颜色与地形颜色混合强度
- Size Locked-----------------锁定尺寸比率
- Width Range-----------------宽度范围
- Height Range----------------高度范围
- Alpha Cut-Off---------------细节透明通道强度
- Crossed Quads---------------交叉四边形排列
- Align to Terrain------------与地形对齐

## Ocean/海洋
激活海洋，和Lumion的海洋类似
### Ocean Properties/海洋特性
- Show Ocean Plane------------显示海平面
- Ocean Height----------------海平面高度
- Diffuse Color---------------海洋漫射颜色
- Specular Color--------------海洋高光颜色
- Reflection Color------------海洋反射颜色
- Subsurface Scattering-------表面散射强度
- Water Drops Intensity-------

## Weather/天气
控制天气来影响对象和细节
### Wind Properties/风特性
- Direction-------------------风向
- Intensity-------------------风强度
- Turbulence------------------风絮乱
- Magnitude-------------------风力级数
- Frequency-------------------风频率


### Rain Properties/雨特性
- Enable Rain-----------------激活雨
- Follow Camera Z-------------跟随摄像机景深
- Fix Distance----------------固定距离
- Intensity-------------------雨强度
- Fade------------------------雨衰退值
- Size------------------------尺寸
- Speed-----------------------下雨速度
- Distortion------------------让景观产生视觉扭曲
- Storm Flash-----------------风暴闪烁频率
- Myst Color------------------雾颜色
- Myst Intensity--------------雾浓度


## Sky/天空
### General Sky Properties/天空一般特性
- Mode------------------------天空模式
  - None------------------------关闭天空
  - Default---------------------默认天空
- Time of Day-----------------时间
- Latitude--------------------纬度
- Longitude-------------------经度
- Color-----------------------颜色
- Disable Skybox Ocean--------不显示地形以外的海洋

### Haze and Fog Properties/霾和雾特性
- Thickness-------------------厚度
- Wavelengths-----------------波长
- Fog-------------------------激活雾
- Fog Type--------------------雾类型
  - Distance--------------------根据距离
  - Height----------------------根据高度
- Density---------------------密度
- Start Distance--------------开始距离
- Exclude Far Pixels----------排除远处的像素
- Use Radial Distance---------使用径向距离

### Sun and Moon Properties/太阳和月亮特性
- Sun Size--------------------太阳尺寸
- Sun Intensity---------------日光强度
- Moon Intensity--------------月光强度
- Exposure--------------------曝光度
- Mie Scattering--------------散射
- Anisotropy Factor-----------各向异性因子
- Sun Shafts------------------
- Threshold-------------------
- Max Shafts Radius-----------

### Clouds Properties/云特性
- Density---------------------密度
- Attenuation-----------------衰减，参数越大，云越稀薄
- Step Size-------------------步幅尺寸
- Alpha Saturation------------控制云边缘透明度
- Light Color Multiplier------光颜色倍增器
- Sky Color Multiplier--------天空颜色倍增器
- Scatter  Multiplier---------散射倍增器
- RotationSpeed---------------旋转速度

# Aeras/区域
## Aeras/区域
区域是一个多功能的非常强大和灵活的工具，可以用来
1.创建混合地图
2.创建生物群落
3.导入现有的高度图
3.创建自定义的高度图
5.生成水流地图
6.绘制滤镜、纹理、对象和细节
区域可以应用到基础地形生成器、滤镜层、对象层和细节层
### Aera Layers/区域层
- Name------------------------区域名
- Width-----------------------区域宽度
- Length----------------------区域长度
- Fit to Terrain Size---------适合地形尺寸
- Resolution------------------分辨率
- Overlay Image---------------覆盖图像
- Has Heightmap---------------

### Blendmap Properties/混合地图特性

### Painting and Sculpting Properties/绘制和雕刻特性

## General/一般设定
### Areas Optimization Properties/区域优化属性
- Skip Filters on Move--------移动时无视滤镜
- Skip Filters on Paint-------绘制时无视滤镜

# Post/后期
