# Paper2D
用来制作2D游戏的资产和工具集
## Paper2D/Paper2D资产
### Paper Flipbook/Paper图像序列
用多个精灵实现基于Sprite的动画,可以把它看做一种手绘动画的表现形式。原理是一系列有细微不同之处的图片快速"翻过"，从而产生动画的效果
Flipbooks由一系列关键帧组成，每帧均包含一个需要展示的Sprite和展示时长（以帧数为单位）

#### 使用方法
- 第1步 将动画序列每一帧都转换为Sprite
- 第2步 创建一个Paper Flipbook资产，将序列帧的每个Sprite按动画顺序拖到Paper Flipbook资产的时间轴上

#### 与蓝图绑定的2种方法
1. 创建角色蓝图（角色）------在资产管理器中创建蓝图，搜索选择PaperCharacter蓝图类，然后将Flipbook绑定到Sprite组件上
2. 创建Actor蓝图（开火、爆炸等特效等其他资源）-----创建Actor或Pawn蓝图，在组建中搜索添加PaperFlipbook组件，然后将Flipbook绑定到PaperFlipbook组件上
#### Details/细节面板
##### Sprite
- Frames Per Second------------每秒帧数，用来控制动画的播放速度
- Collision Source-------------碰撞源，如果发现2D角色没有碰撞，要检查这里
  - No Collision-----------------无碰撞
  - First Frame Collision--------首帧检测碰撞，如果需要有碰撞，一般选择这个
  - Each Frame Collision---------每帧检测碰撞，系统消耗较大，一般不使用

### Sprite/精灵
Paper2D游戏的核心
是一种可在游戏场景中进行渲染的纹理映射平面网格物体和相关材质，就是在UE4中迅速而简易地进行2D图像绘制。可以理解为图片到引擎里进行的一个转换，本质上是图片
拥有一套Sprite资源之后可以创建Flipbook，从而实现动画
#### 创建Sprite方法
把图片导入引擎后可以右键Sprite Actions创建Sprite资产，有两种方式
1. Create Sprite----直接把图片转换成Sprite资产
2. Extract Sprites--把图片根据像素自动分割或手动分割，转换成多个Sprite资产

Sprite不一定非要创建Flipbook才可以和蓝图绑定，Sprite资产可以通过PaperSprite组件和蓝图绑定

### Tile Map/瓦片地图
定义了长宽的2D网格（以瓦片计量）。可以有多个图层，每个图层可指定该图层的每个贴图单元中显示的瓦片
#### Toolbox/工具架
在这里选择绘制的瓦片
- Paint------------------------绘制工具，绘制地图
- Eraser-----------------------橡皮擦工具
- Fill-------------------------填充工具
#### Viewport/视口
在这里绘制地图
#### Details/细节
##### Tile Map/瓦片地图
在这里控制图层
- Tile layer list--------------瓦片图层列表，一般设三个图层，前景中景背景
##### Selected Layer/选定图层
在这里调整选择的图层属性
- Hidden in Editor-------------编辑器中隐藏
- Hidden in Game---------------游戏中隐藏
- Layer Collides---------------图层碰撞，控制图层是否有碰撞
- Layer Color------------------图层颜色
##### Setup/配置
- Map Width--------------------贴图宽度
- Map Height-------------------贴图高度
- Tile Width-------------------瓦片宽度
- Tile Height------------------瓦片高度
- Pixels Per Unreal Unit-------逐虚幻单位像素，一个虚幻单位占用多少像素，虚幻单位默认是厘米
- Separation Per Layer---------逐图层分隔


### Tile Set/瓦片集
从纹理中抽出的图片集合，用于填充瓦片地图

注意，制作瓦片集的图片要右键-->Sprite操作-->应用Paper2D纹理设置，或在压缩设置中选择用户界面2D(RGBA)
#### Details/细节面板
##### TileSet/瓦片集
- Tile Size--------------------瓦片大小，控制拆分成的瓦片大小，即在瓦片地图中绘制时的单位大小，一般设置成2的倍数
- Tile Sheet Texture-----------瓦片薄片纹理，选择瓦片的纹理图片
- Border Margin----------------边缘距离，设置能获取到瓦片的图片范围
- Per-Tile Spacing-------------逐瓦片间距，选取瓦片时，瓦片之间的间距
##### Single Tile Editor/单个瓦片编辑器
编辑单个瓦片的属性
- Collision Data---------------碰撞数据，需要有碰撞的瓦片都需要在这里逐个添加碰撞


## Sprite编辑器
### View/查看模式
用于预览Sprite和总体数据
#### Details/工具架
##### Sprite
- Pivot Mode-------------------轴心模式，可以调节Sprite的轴心
#### Sprite List
这里显示所有用同一图片生成的Sprite
### Edit Source Region/编辑源区域模式
用于显示完整源纹理和设置要显示的区域
### Edit Collision/编辑碰撞模式
用于显示和编辑碰撞形态，主要是调节碰撞盒
#### Details/工具架
##### Collision
- Sprite Collision Domain------精灵碰撞域
  - None-------------------------无碰撞
  - Use 3D Physics---------------使用3D物理效果
- Collision Geometry Type------碰撞几何体类型
  - Source Bounding Box----------源边界框
  - Tight Bounding Box-----------收紧边界框，会自动识别有像素的区域的最大范围，并形成矩形，一般使用收紧边界框，再进行微调即可
  - Shrink Wrapped---------------缩小包装，自动识别有像素的区域，作为边界框，会生成很多点，增加系统负荷
  - Fully Custom-----------------完全自定义
### Edit Render Geometry/编辑渲染几何体模式
用于显示和编辑Sprite渲染几何体

