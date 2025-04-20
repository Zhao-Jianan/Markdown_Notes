# Particular
1. 注意速度改为0，粒子会变成一条线
2. 制作粒子时一般最后要添加发光
3. 想要粒子效果好，要叠加多个粒子层，每个粒子层粒子大小、发射速度等参数不同，图层叠加样式设为相加


# ae cc2015
## 3D Channel 三维通道特效
- 3D Channel Extract--------3D通道提取
- Depth Matte---------------深度蒙板
- Depth Of Field------------景深
- Extractor-----------------提取器
- Fog 3D--------------------雾化3D
- ID Matte------------------ID蒙版
- ID Entifier---------------标识符

## Expression Controls表达式控制特效
- 3D Point Control-----------三维点控制
- Angle Control--------------角度控制
- Checkbox Control-----------复选框控制
- Color Control--------------颜色控制
- Layer Control--------------图层控制
- Point Control--------------点控制
- Slider Control-------------滑块控制

## Stylize 风格化特效
- CC Block Load--------------CC块装载（模拟3D软件渲染过程）
- CC Burn Film---------------CC胶片烧灼效果
- CC Glass-------------------CC玻璃（玻璃透视效果增加质感,与分形杂色结合制作着火后空气抖动、冲击波等）
- CC Kaleida-----------------CC万花筒（不错的万花筒效果）
- CC Mr.Smoothie-------------CC像素溶解
- CC Plastic-----------------CC塑料/整形
- CC Repetile----------------CC重复拼贴（多种方式的叠印效果，与动态拼贴类似）
- CC Threshold---------------CC阈值（简单的阈值工具）
- CC Threshold RGB-----------CC阈值RGB
- Brush Strokes--------------画笔描边
- Cartoon--------------------卡通效果（制作油画效果）
- Color Emboss---------------彩色浮雕
- Emboss---------------------浮雕（复制一份添加浮雕，提高对比度，与原图层叠加，使画面更有层次感）
- Find Edges-----------------查找边缘（结合快速模糊做素描效果）
- Glow-----------------------发光
- Mosaic---------------------马赛克
- Motion Tile----------------动态拼贴
- Posterize------------------多色调分离（将饱满的色调变得不饱满）
- Roughen Edges--------------毛边/粗糙边缘
- Scatter--------------------散布/扩散（像素随机分布）
- Strobe Light---------------闪光灯
- Texturize------------------纹理化（纹理图层选择自身可做钢印效果）
- Threshold------------------阈值（与CC Threshold--简单的阈值工具相同，但可控性低）

## Transition 过渡特效

- CC Glass Wipe--------------CC玻璃擦除（融化过渡）
- CC Grid Wipe---------------CC网格擦除（一般不用，效果太low）
- CC Image Wipe--------------CC图像擦除（类似Gradient Wipe--渐变擦拭，一般不用，效果太low）
- CC Jaws--------------------CC锯齿状过渡（一般不用，效果太low）
- CC Light Wipe--------------CC照明式擦除（边缘加光过渡，带有变形效果，一般不用，效果太low）
- CC Line Sweep--------------CC光线扫描（一般不用，效果太low）
- CC Radial Scalewipe--------CC镜像缩放擦除（带有边缘扭曲的圆孔过渡）
- CC Scale Wipe--------------CC缩放擦除（扯动变形过渡，可做拉丝效果）
- CC Twister-----------------CC龙卷风（扭曲过渡）
- CC Warpomatic--------------CC自动弯曲
- Block Dissolve-------------块溶解
- Card Wipe------------------卡片擦除（效果强大）
- Gradient Wipe--------------渐变擦除
- Iris Wipe------------------光圈擦除/星形擦拭
- Linear Wipe----------------线性擦除（常用）
- Radial Wipe----------------径向擦除（常用）
- Venetian Blinds------------百叶窗（两个百叶窗搭配使用，角度不同）

## Obsolete过时特效
- Basic 3D-------------------基本3D
- Basic Text-----------------基本文字（中文版会出错）
- Luma Key-------------------亮度键（效果差）
- Lightning------------------闪电（被高级闪电取代）
- Path Text------------------路径文本
- Color Key------------------颜色键（效果差）
- Spill Suppressor-----------溢色抑制

## Keying 键控特效
- CC Simple Wire Removal-----CC简单的去除电线去除（简单的擦威亚工具，实际上是一种线状的模糊和替换效果 ）
- Color Difference Key-------颜色差值键（不常用）
- Color Range----------------颜色范围
- Difference Matte-----------差值遮罩（已淘汰）
- Extract--------------------提取（已淘汰）
- Inner/Outer Key------------内部外部键/轮廓抠像（不常用）
- Keylight(1.2)--------------按键光（最强大,具体翻译看后面）
- Linear Color Key-----------线性颜色键（效果粗糙）
- Advanced Spill Suppressor--高级溢出抑制器（扣头发时使绿幕变成灰色）
- Key Cleaner----------------抠像清除器（抠完像去掉半透和不干净的地方）

## Blur & Sharpen 模糊与锐化特效
- CC Cross Blur--------------CC交叉模糊(类似方向模糊，把X和Y方向分开）
- CC Radial Blur-------------CC径向模糊（类似镜像模糊，可在镜头推拉时使用，也可模拟眩晕感）
- CC Radial Fast Blur--------CC径向快速模糊（可模拟具有层次的体积光）
- CC Vector Blur-------------CC矢量模糊（常用，让图像变得更抽象，可用来制作光效）
- Bilateral Blur-------------双向模糊（类似美图秀秀磨皮，不常用）
- Box Blur-------------------方框模糊/盒状模糊（完全用不到）
- Camera Lens Blur-----------摄像机镜头模糊（功能强大但速度较慢，不常用，被FL Depth Of Field替代）
- Camera-Shake Deblur effect-摄像机抖动去模糊
- Channel Blur---------------通道模糊（用不到）
- Compound Blur--------------复合模糊（不常用，模拟玻璃透过感觉）
- Directional Blur-----------定向模糊（可用来模拟炫光）
- Fast Blur------------------快速模糊（非常常用）
- Gaussian Blur--------------高斯模糊（与快速模糊相似，但一般使用快速模糊）
- Radial Blur----------------径向模糊（类似CC放射状模糊，可在镜头推拉时使用，也可模拟眩晕感）
- Reduce Interlace Flicker---降低隔行扫描闪烁
- Sharpen--------------------锐化（常用，数值不宜太大，水泥金属等使用后质感很好，人物使用时数值要慎重）
- Smart Blur-----------------特殊模糊/智能模糊（用不到）
- Unsharp Mask---------------钝化蒙版（钝化作用）

## Simulation 模拟特效
- CC Ball Action-------------CC滚珠效果（小球状粒子化，效果还可以，但一般使用C4D模拟）
- CC Bubbles-----------------CC气泡效果（不常用，效果太low）
- CC Drizzle-----------------CC细雨滴/雨打水面效果（不常用，可用来做三维置换贴图，置换生成立体涟漪）
- CC Hair--------------------CC毛发效果/毛发生成器（较慢，但效果较好，可制作一些创意效果）
- CC Mr.Mercury--------------CC水银滴落效果（偶尔用到，模仿水银流动）
- CC Particle Systems II-----CC粒子仿真系统II效果（二维粒子运动，用不到）
- CC Particle World----------CC粒子仿真环境效果（三维粒子运动用不到，优于Particle Playground--粒子运动场）
- CC Pixel Polly-------------CC像素多边形效果（画面破碎效果，效果太low）
- CC Rainfall----------------CC下雨效果（效果还可以，速度快）
- CC Scatterize--------------CC散射效果（发散粒子化，不常用，类似于Stylize>Scatter--扩散）
- CC Snowfall----------------CC飘雪效果（效果还可以，速度快）
- CC Star Burst--------------CC星爆效果（不常用，模拟星团，粒子颜色基于图层颜色，操作简单）
- Card Dance-----------------卡片动画（不常用，类似C4D中的阵列、过渡>卡片擦除，通过一个图层控制，一般用C4D制作）
- Caustics-------------------焦散（偶尔使用，模拟阳光透过水面）
- Foam-----------------------泡沫（不常用）
- Particle Playground--------粒子运动场（老特效，已被淘汰，效果太low）
- Shatter--------------------碎片（效果还可以，但一般通过C4D制作）
- Wave World-----------------波形环境（比较实用，效果讨巧，可用来做三维置换贴图）

## Distort扭曲特效
- CC Bend It-----------------CC区域弯曲效果（通常和骨骼插件中的回弹效果结合使用做文字）
- CC Bender------------------CC层卷曲效果
- CC Blobbylize--------------CC融化效果
- CC Flo Motion--------------CC折叠运动效果（两点收缩变形）
- CC Griddler----------------CC方格效果（网格状变形，将图像切成块放大缩小旋转）
- CC Lens--------------------CC镜头效果（鱼眼镜头，正常镜头变成鱼眼，鱼眼镜头变成正常，不如Pan Lens Flare Pro）
- CC Page Turn---------------CC翻页效果
- CC Power Pin---------------CC四角扯动效果（带有透视效果的四角扯动工具，类似扭曲>边角定位，功能更强大，做摄像机跟踪时常用）
- CC Ripple Pulse------------CC波纹脉冲效果（扩散波纹变形，必需打关键帧才有效果）
- CC Slant-------------------CC倾斜效果（倾斜变形）
- CC Smear-------------------CC旋涡条纹效果（涂抹变形）
- CC Split-------------------CC胀裂效果（简单的胀裂效果，不常用，类似剪刀裁开）
- CC Split 2-----------------CC胀裂2效果（不对称的胀裂效果）
- CC Tiler-------------------CC平铺效果（电视墙）
- Bezier warp----------------贝赛尔曲线变形（比较实用）
- Bulge----------------------凸出（模拟放大镜）
- Corner Pin-----------------边角定位
- Displacement Map-----------置换图（非常常用，画面的置换，可模拟热浪，制作贴图等）
- Liquify--------------------液化/像素溶解变换
- Magnify--------------------保留细节放大/像素无损放大
- Mesh Warp------------------网格变形/液态变形（常用）
- Mirror---------------------镜像（制作创意MV时会用到）
- Offset---------------------偏移（不常用）
- Optics Compensation--------光学补偿/镜头变形（可用于修正鱼眼镜头的畸变，常用于添加鱼眼效果或消除鱼眼效果）
- Polar Coordinates----------极坐标转换
- Reshape--------------------改变形状（通过3个遮罩控制）
- Ripple---------------------波纹（不常用）
- Rolling Shutter Repair-----果冻效应效果（用于修复单反拍视频中一卡一卡的果冻效应）
- Smear----------------------旋涡条纹/涂抹（两个遮罩控制）
- Spherize-------------------球面化
- Transform------------------变换
- Turbulent Displace---------湍流置换（非常常用，用于模拟热浪、飘旗等）
- Twirl----------------------旋转扭曲/扭转
- Warp-----------------------变形/歪曲边框（常用,类似PS的自由变换 ）
- Warp Stabilizer VFX--------变形稳定器VFX（使用频率非常高，对视频做稳定，一般右键>变形稳定器VFX）
- Wave Warp------------------波浪变形/波形变形

## Generate 生成特效

- CC Glue Gun----------------CC胶水喷枪效果（效果不错，可用wiggle控制位置结合使用）
- CC Light Burst 2.5---------CC光线缩放效果2.5（可模拟速度感）
- CC Light Rays--------------CC光束效果（光芒放射，加有变形效果，可模拟舞台光或太阳光穿过云层）
- CC Light Sweep-------------CC扫光效果
- CC Threads-----------------CC线状效果/螺纹（编织物纹理）
- 4-Color Gradient-----------四色渐变（通常做背景或做蒙版给文字上色）
- Advanced Lightning---------高级闪电（效果不错）
- Audio Spectrum-------------音频频谱
- Audio Waveform-------------音频波形（通常和Particular结合使用）
- Beam-----------------------光束效果（效果简单但是非常实用）
- Cell Pattern---------------单元格图案（可用来生成贴图）
- Checkerboard---------------棋盘效果
- Circle---------------------圆形（非常常用）
- Ellipse--------------------椭圆（不常用）
- Eyedropper Fill------------吸管填充（不常用）
- Fill-----------------------填充
- Fractal--------------------分形效果（不常用，分形有专门的软件形）
- Grid-----------------------网格
- Lens Flare-----------------镜头光晕（通常使用光效工厂）
- Paint Bucket---------------油漆桶
- Radio Waves----------------无线电波（不常用）
- Ramp-----------------------梯度渐变
- Scribble-------------------涂写（不常用，模拟手绘）
- Stroke---------------------描边
- Vegas----------------------勾画（蒙版路径中使用频繁，配合蒙版使用）
- write-on-------------------写入/手写效果（可以用于观察表达式实现的效果）

## Time 时间特效
- CC Force Motion Blur-------CC强制运动模糊(默认的运动模糊只支持移动旋转缩放和Particular、E3D等插件，其他特效如果添加运动模糊就添加合成然后使用本特效)
- CC Time Blend--------------CC时间混合（带有动态模糊的帧融合）
- CC Time Blend FX-----------CC时间混合FX（可自定义的帧融合）
- CC Wide Time---------------CC宽泛时间（多重的帧融合效果）
- Echo-----------------------残影
- Posterize Time-------------色调分离时间
- Time Difference------------时间差异
- Time Displacement----------时间置换
- Timewarp-------------------时间扭曲/时间收缩

## Utility 实用工具特效

- CC Overbrights-------------CC过于鲜亮效果（32位模式下对hdr图像过曝部分进行还原）
- Apply Color LUT------------应用颜色LUT（颜色空间中，LOG模式记录色彩信息很全，但呈现效果很灰，REC模式接近人眼识别色彩，但记录色彩信息不全，通常拍摄时使用LOG模式，再用LUT进行调色，此特效需要加载预设）
- Cineon Converter-----------Cineon转换器（LOG模式和正常模式互换，对数到线性>把LOG模式的图像转化为正常模式的图像）
- Color Profile Converter----颜色配置文件转换器
- Grow Bounds----------------范围扩散（32位模式下对让图像扭曲时还原边缘被裁切部分）
- HDR Compander--------------HDR压缩扩展（32位模式下对hdr图像过曝部分进行还原）
- HDR Highlight Compression--HDR高光压缩（32位模式下对hdr图像过曝部分进行还原）

## Channel 通道特效
- CC Composite---------------CC合成效果（合成与自己进行混合）
- Arithmetic-----------------算术/通道运算（强制性加入红绿蓝三个值）
- Blend----------------------混合（不常用）
- Calculations---------------计算/融合计算（两个通道信息进行计算）
- Channel Combiner-----------通道合成器（某图层的某通道当做当前图层的某通道）
- Compound Arithmetic--------复合运算（与图层混合模式功能相同）
- Invert---------------------反转/反相（255-当前颜色）
- Minimax--------------------最小值最大值/扩亮扩暗（使画面没有层次颜色均匀）
- Remove Color Matting-------移除颜色遮罩
- Set Channels---------------设置通道（不常用）
- Set Matte------------------设置遮罩（使用某图层的某信息当做当前图层的遮罩）
- Shift Channels-------------转换通道
- Solid Composite------------固态层合成（原图层与一个固态层混合，不常用）

## Perspective 透视特效
- CC Cylinder----------------CC圆柱体效果（把画面变成圆柱，支持摄像机，不常用，一般用3D制作）
- CC Environment-------------CC环境效果（把画面变成球形，不常用，一般用E3D制作）
- CC Sphere------------------CC球面效果（一般用E3D制作,可以把世界地图变为地球，简单效果可用）
- CC Spotlight---------------CC点光源效果（模拟聚光灯照射）
- 3D Camera Tracker----------3D摄像机追踪（跟踪摄像机）
- 3D Glasses-----------------3D眼镜（用两个摄像机拍摄3D视频）
- Bevel Alpha----------------斜面Alpha
- Bevel Edges----------------斜面边缘（与斜面Alpha类似，但是只针对图层边缘）
- Drop Shadow----------------投影
- Radial Shadow--------------径向阴影

## Text 文字特效
- Numbers--------------------数字
- Timecode-------------------时间码

## Color correction 颜色校正特效
- CC Color Neutralizer-------CC颜色中和剂效果（分开调节阴影中间调高光）
- CC Color Offset------------CC色彩偏移
- CC Kernel------------------CC内核效果
- CC Toner-------------------CC调色剂/碳化（比较常用，与三色调、色调特效类似）
- Auto Color-----------------自动颜色（自动化的效果都不太好）
- Auto Contrast--------------自动对比度（自动化的效果都不太好）
- Auto Levels----------------自动色阶（自动化的效果都不太好）
- Black & White--------------黑白（将图像变为黑白，并精确控制）
- Brightness & Contrast------亮度与对比度
- Broadcast Colors-----------广播级颜色（老特效，用于适配老机器，基本不用）
- Change Color---------------更改颜色（不常用）
- Change to Color------------更改为颜色（把一种颜色换成另一种颜色，一般与抠像配合）
- Channel Mixer--------------通道混合器（把一种通道转化为另一种通道，不常用）
- Color Balance--------------色彩平衡
- Color Balance(HLS)---------色彩平衡(HLS)
- Color Link-----------------颜色链接（不常用）
- Color Stabilizer-----------颜色稳定器
- Colorama-------------------色光（把亮度或饱和度或单个通道映射为颜色）
- Curves---------------------曲线调整
- Equalize-------------------色调均化/均衡效果（效果提升了饱和度和对比度）
- Exposure-------------------曝光度/多次曝光（亮度的调整会影响饱和度，曝光度只调节亮度，不会影响饱和度）
- Gamma/Pedestal/Gain--------灰度系数（伽马值）/基值/增益（不常用，被曲线、色阶替代）
- Hue/Saturation-------------色相/饱和度（调整饱和度可能会导致颜色溢出，可用自然饱和度）
- Leave Color----------------保留颜色/退色（保留一种颜色，去掉其他颜色）
- Levels---------------------色阶
- Levels (Individual Controls)--色阶(单独控件/个体控制)
- Photo Filter---------------照片滤镜（把一种颜色和当前图层混合）
- PS Arbitrary Map-----------PS任意映射/映像遮罩
- Selective Color------------可选颜色（不常用）
- Shadow/Highlight-----------阴影/高光
- Tint-----------------------色调/色度（CC Toner效果涵盖色调/色度效果）
- Tritone--------------------三色调（CC Toner效果涵盖三色调效果）
- Vibrance-------------------自然饱和度（很实用，在调整饱和度时不会有颜色溢出）

## Audio 音频特效
- Backwards------------------倒放
- Bass & Treble--------------低音和高音
- Delay----------------------延迟
- Flange & Chorus------------变调与和声(干输出>原始音量输出，湿输出>变调后的音量输出）
- High-Low Pass--------------高通/低通（高低音过滤）
- Modulator------------------调制器
- Parametric EQ--------------参数均衡
- Reverb---------------------混响
- Stereo Mixer---------------立体声混合器
- Tone-----------------------音调

## Noise & Grain 杂色和颗粒特效
- Add Grain------------------添加颗粒（直接添加杂色，也可以用来 制作杂色贴图）
- Dust & Scratches-----------蒙尘与划痕
- Fractal Noise--------------分型杂色/分形燥波
- Match Grain----------------匹配颗粒（用杂色贴图把三维制作的素材模拟成实拍的）
- Median---------------------中间值
- Noise----------------------杂色
- Noise Alpha----------------Alpha通道杂点
- Noise HLS------------------HLS通道杂点
- Noise HLS Auto-------------自动生成HLS通道杂点
- Remove Grain---------------移除颗粒（快速高效移除三维制作的素材的噪点）
- Turbulent Noise------------湍流杂色/动荡噪波（与分形杂色相同）

## Matte 遮罩特效
- Matte Choker---------------遮罩阻塞工具（抠图时让比较虚的画面变实）
- Mocha Shape----------------蒙版形状
- Refine Matte---------------优化遮罩
- Simple Choker--------------简单阻塞工具（加在调节图层上可以让下面的图层有融合效果）
Synthetic Aperture
- SA Color Finesse 3---------

# 大型特效/插件中英文对照
## Keylight
- View-------------------------视图模式
  - Source----------------显示原始图像（用不到）
  - Source Alpha----------显示原始图像的Alpha（用不到）
  - Corrected Source------（用不到）
  - Colour Correction Edges---颜色校正的边缘效果（偶尔用）
  - Screen Matte----------抠出蓝绿背景后的通道效果（常用）
  - Inside Mask-----------内部遮罩效果（用不到）
  - Outside Mask----------外部遮罩效果（用不到）
  - Combined Matte--------合并后的遮罩效果（用不到）
  - Status----------------抠像后的状态（常用，当前景有透明的地方，直接看Alpha通道不容易看出来，用此模式检查Alpha通道是否完美）
  - Intermediate Result---中间效果（偶尔用到）
  - Final Result----------最终效果（常用）
- Unpremultiply Result---------非预乘效果
- Screen Colour--------------吸取屏幕颜色（非常常用）
- Screen Gain----------------屏幕增益（非常常用）
- Screen Balance-------------屏幕平衡（非常常用）
- Despill Bias---------------溢出影响（用不到）
- Alpha Bias-----------------Alpha影响（用不到）
- Lock Biases Together-------锁定两种影响（用不到）
- Screen Pre-blur------------屏幕预模糊（偶尔用）
- Screen Matte---------------屏幕蒙版（常用）
  - Clip Black-------------限制黑色（常用）
  - Clip White-------------限制白色（常用）
  - Clip Rollback----------滚动操作（不常用，弱化Alpha黑白通道处理）
  - Screen Shrink/Glow-----收缩/扩展（不常用）
  - Screen Softness--------羽化（不常用）
  - Screen Despot Black----填充黑色（不常用）
  - Screen Despot White----填充白色（不常用）
  - Replace Method---------替换方式（不常用）
    - None------------无
    - Souce-----------原始图像效果
    - Hard Colour-----硬颜色
    - Soft Colour-----柔和颜色
  - Replace Colour---------替换颜色（不常用）
- Inside Mask----------------内部蒙版(用不到)
  - Inside Mask------------内部蒙版
  - Inside Mask Softness---内部蒙版羽化
  - Invert-----------------反向
  - Replace Method---------替换方式
  - Replace Colour---------替换颜色
  - Source Alpha-----------原始图像Alpha
- Outside Mask---------------外部蒙版(用不到)
  - Outside Mask-----------外部蒙版
  - Outside Mask Softness--外部蒙版羽化
  - Invert-----------------反向
- Foreground Colour Correction---前景颜色校正(用不到)
  - Enable Colour Correction---激活颜色校正
  - Saturation-----------------饱和度
  - Contrast-------------------对比度
  - Brightness-----------------亮度
  - Colour Suppression---------颜色抑制
  - Colour Balancing-----------色彩平衡
- Edge Colour Correction-------------边缘颜色校正（偶尔会用）
  - Enable Edge Colour Correction--激活边缘颜色校正
  - Edge Hardness------------------边缘锐化
  - Edge Softness------------------边缘柔化
  - Edge Grow----------------------边缘扩张
  - Saturation---------------------饱和度
  - Contrast-----------------------对比度
  - Brightness---------------------亮度
  - Edge Colour Suppression--------边缘色抑制
  - Colour Balancing---------------色彩平衡
- Source Crops-------------源修剪(用不到)
  - X Method-------------X轴
  - Y Method-------------Y轴
  - Edge Colour----------边缘色
  - Edge Colour Alpha----边缘色Alpha

## Magic Bullet Suite 红巨星调色套装
- Magic Bullet Cosmo----------润肤磨皮滤镜
- Magic Bullet InstantHD------视频转换滤镜
- Magic Bullet Colorista------调色师滤镜
- Magic Bullet Denoiser-------降噪滤镜
- Magic Bullet Frames---------去隔行扫描滤镜
- Magic Bullet Mojo-----------快速调色滤镜
- Magic Bullet MisFire--------特殊效果滤镜
- Magic Bullet Looks----------胶片级调色滤镜
  - Subject-----------------物体（拍摄的物体人或者物）
    - Exposure----------------曝光
    - Spot Exposure-----------局部增加曝光量
    - Grad Exposure-----------渐变改变曝光（可以更改颜色，有点像镜头上的渐变滤镜）
    - Contrast----------------对比
    - Color Contrast----------颜色对比（有点类似通道混合器，但是它有明度对比的概念，实际上就是改变RGB通道的数值和组合来影响颜色）
    - Crush-------------------RGB通道混合改变颜色（RGB通道混合改变颜色，但它没有明度对比，颜色过于明显，略显不自然）
    - Saturation--------------饱和度
    - Ranged Saturation-------局部改变饱和度（把饱和度分为高光阴影中间调来分别改变饱和度，牛逼！）
    - Colorista 3-way---------改变阴影高光中间调三者的明度（可以近似理解为色阶的调整）
    - Color Ranges------------可以改变阴影高光和中间调三者的颜色并且可以调整明度！（可以理解为色阶还可以调整每个场的颜色，有点类似PS中色阶加上色彩平衡的整合功能）
    - Chromatlc Aberratlon----色相差（可以理解为一种镜头滤镜眩晕的效果）
    - Warm/Cool---------------冷暖颜色改变
    - Fill Light--------------增加明度
    - Spot Fill---------------局部增加明度
    - Curves------------------曲线
    - Pop---------------------活跃色
    - Hue/Saturation----------色相/饱和度
    - Cosmo-------------------磨皮
    - 预置
        - Minus One Stop----------降低曝光的预置
        - Plus One Stop-----------增加曝光的预置
  - Matte-------------------蒙版（在镜头上所加的滤镜，如灰镜、偏色镜等等）
    - Exposure----------------曝光（与Subject中效果相同）
    - Spot Exposure-----------局部增加曝光量（与Subject中效果相同）
    - Grad Exposure-----------渐变改变曝光（与Subject中效果相同）
    - Diffusion---------------柔光
    - Color Filter------------颜色滤镜（类似于PS中的颜色滤镜）
    - Sky Filter--------------天空滤镜（实际也可以改变颜色不一定非得是蓝色，有渐变效果）
    - Gradient----------------渐变滤镜
    - Lightflex---------------灯光滤镜（实际就是增加了明度概念的带颜色的滤镜，可调节明度）
    - Warm/Cool---------------冷暖颜色改变（与Subject中效果相同）
    - Star Filter-------------高光星星滤镜（高光的地方出现星星的光斑）
    - 预置
  - Lens--------------------镜头（可以通过镜头的变化实现的效果，比如暗角，比如色相差比如虚化等等）
    - Exposure----------------曝光（与Subject中效果相同）
    - Spot Exposure-----------局部增加曝光量（与Subject中效果相同）
    - Grad Exposure-----------渐变改变曝光（与Subject中效果相同）
    - Vignette----------------暗角
    - Anamorphic Flare--------变形的闪光（高光区域有些类似高光星星滤镜 但形状和可调节性更强）
    - Deflare-----------------去高光（可以理解为增加自然对比，比较实用）
    - Chromatlc Aberratlon----色相差（与Subject中效果相同）
    - Edge Softness-----------圆形虚化
        - Swing-Tilt--------------十字型虚化
    - Lens Distortion---------镜头畸变扭曲
    - Haze/Flare--------------阴霾/耀斑
  - Camera------------------相机（调节相机内部的设置实现的效果如遮光条纹、饱和度、白平衡等）
    - Exposure----------------曝光（与Subject中效果相同）
    - Spot Exposure-----------局部增加曝光量（与Subject中效果相同）
    - Grad Exposure-----------渐变改变曝光（与Subject中效果相同）
    - Neg Bleach Bypass-------漂白特效（实际就是往画面里加白，配合曝光，可以理解为降低自然饱和度）
    - Contrast----------------对比
    - Color Contrast----------颜色对比
    - Shutter Streak----------遮光条纹（挺好看的比较适合lomo这种幻境的效果！）
    - Crush-------------------RGB通道混合改变颜色（与Subject中效果相同）
    - Color Reversal----------颜色倒转（提升画面中阴影的数量，整体降低明度,增加对比）
    - Black&White-------------黑白
    - Saturation--------------饱和度（与Subject中效果相同）
    - Ranged Saturation-------局部改变饱和度（与Subject中效果相同）
    - Shoulder----------------改变高光区域的明度
    - 2-Strip Process---------原色之间混合改变颜色（有点像用LAB模式或者通道混合器出来的效果）
    - 3-Strip Process---------同上面一样（但是似乎加入了明度的功能，不是很常用）
    - Warm/Cool---------------冷暖颜色改变（与Subject中效果相同）
    - Film Grain--------------电影颗粒
    - Curves------------------曲线
  - Post--------------------最终快速调整（对于画面最终的调整，是对画面色彩整体的色相、饱和度、明度的调节，使之最终可以呈现在屏幕上。实际上就是对之前一些单向工具的重复调节，使之达到更好的效果。）
    - Exposure----------------曝光（与Subject中效果相同）
    - Spot Exposure-----------局部增加曝光量（与Subject中效果相同）
    - Grad Exposure-----------渐变改变曝光（与Subject中效果相同）
    - Contrast----------------对比
    - Color Contrast----------颜色对比
    - Neg Bleach Bypass-------增加漂白特效（增加高光区域亮度，增强对比）
    - Telecine Net------------电视电影网（增加对比，增加饱和度，使得画面更加柔和! 不错)
    - Crush-------------------RGB通道混合改变颜色（与Subject中效果相同）
    - Saturation--------------饱和度（与Subject中效果相同）
    - Ranged Saturation-------局部改变饱和度（与Subject中效果相同）
    - Colorista 3-way---------改变阴影高光中间调三者的明度（与Subject中效果相同）
    - Color Ranges------------可以改变阴影高光和中间调三者的颜色并且可以调整明度！（与Subject中效果相同）
    - Chromatlc Aberratlon----色相差（与Subject中效果相同）
    - Warm/Cool---------------冷暖颜色改变（与Subject中效果相同）
    - Film Grain--------------电影颗粒（与Camera中效果相同）
    - Curves------------------曲线
    - Auto Shoulder-----------自动匹配图像明度信息
    - Pop---------------------活跃色
    - Ranged HSL--------------深度修改
    - Hue/Saturation----------色相/饱和度
    - Cosmo-------------------磨皮
（虽然它是按照五个步骤来区分的,但是实际上没有明显的差别,比如曝光你加在subject里和加在post里都一样，没有明显的区别，所以记住功能就好。但需要注意的是步骤虽然没有区别，但是单向工具所加的前后顺序是有区别的，你先加饱和度在加曝光，就是先让画面增加了饱和度之后再加大了曝光量，如果你先加曝光再加饱和度，那就是你先加大了曝光量之后再加的饱和度，两者所能实现的效果是完全不同的！）



# AE菜单英文翻译
Color Grad（颜色渐变）
Defocus （散焦）
Faux Flim（模仿胶片效果）
Fluorescent （荧光）
Fog（雾）
Infra-red （在红色下面）
Mist（薄雾）
ND Grad（渐变）
Night Vision（夜视）
Selective Soft Focus（选择性的软焦点）
Skin Smoother（外表面平整）
Tint（偏色）
Warm/Cool（暖色/冷色）
Blur（模糊）
DirBlur（方向模糊）
Diffuse（扩散）

# 外部插件翻译
## TinderBox 1
1.4 T_Etch（蚀刻）
1.6 T_Qube（方格状）
1.7 T_Rays（体积光）
1.8 T_Starburst（星放射状）
1.9 T_Stutter（扫描残迹） 
1.10 T_Beam（光柱） 
1.11 T_Caustic（腐蚀性）
1.12 T_Grad（渐变） 
1.13 T_Sky（天空） 
1.14 T_Deflicker（降低闪烁） 
1.15 T_Degrain（去除颗粒） 
1.16 T_Dilate（扩大） 
1.17 T_Pattern（图案） 
1.18 T_Tile（重复） 
1.19 T_Distorto（定位镜像） 
1.20 T_Droplet（波纹） 
1.21 T_Lens（鱼眼）

## TinderBox 2
2.1 T_BlurMasked（模糊遮罩） 
2.2 T_LensBlur（镜头模糊） 
2.3 T_RadialBlur（放射状模糊） 
2.4 T_Bandlimit（镶边） 
2.5 T_Chromatic（彩色的） 
2.6 T_Contour（轮廓线） 
2.7 T_Glass（玻璃） 
2.8 T_Glow（辉光） 
2.9 T_Kaleid（幻觉） 
2.10 T_Newsprint（新闻纸） 
2.11 T_Paint（油画） 
2.12 T_PseudoColour（变色） 
2.13 T_Trail（轨迹） 
2.14 T_Bars（彩条） 
2.16 T_LensFlare（镜头光斑） 
2.17 T_NightSky（夜空） 
2.18 T_Grain（颗粒） 
2.19 T_Wobble（摇晃） 
2.20 T_Ripple（波纹） 
2.21 T_Swirl（旋涡）

## TinderBox 3
3.1 T_CircularBlur（圆形模糊） 
3.2 T_GradientBlur（梯度模糊） 
3.3 T_Silk（去除皱纹） 
3.4 T_BadTV（不良的电视信号） 
3.5 T_BumpShade（变阴暗） 
3.6 T_Condensation（蒸气凝结成为水） 
3.7 T_DiffusionFilter（漫射过滤器） 
3.8 T_EdgeDetect（边探测器） 
3.9 T_MeltTime（融化时间） 
3.10 T_MotionDetect（运动探测器） 
3.11 T_OldFilm（老电影） 
3.12 T_RomanMosaic（马赛克） 
3.13 T_Turner（车工） 
3.14 T_Lightning（闪电） 
3.15 T_Plasma（血浆） 
3.16 T_Sparks（焰火发射器） 
3.17 T_Starfield（星空） 
3.18 T_Deband（带状模糊） 
3.19 T_Defield（转制工具） 
3.20 T_MatteTool（剪影工具）

## Trapcode
1 Shine（体积光） 
2 3D Stroke （三维描边） 
3 Sound Key （声音基调）

## Digital Film Tools
1 CS Color Correct（颜色修正） 
2 CS Composite（合成） 
3 CS Defocus（散焦） 
4 CS Fast Blur（快速模糊） 
5 CS Frame Averager（画面中和器） 
6 CS Grain（增加颗粒） 
7 CS Holdout Composite（持续合成） 
8 CS Light Composite（灯光合成） 
9 CS Math Composite（数学合成） 
10 CS Matte Generator（无光发生器） 
11 CS Matte Repair（剪影修理） 
12 CS Non-Additive Mix（非附加混合） 
13 CS Paste Color（粘贴颜色） 
14 CS Selective Color Correct（选择颜色修正） 
15 CS Selective Soft Focus（选择软焦点）

## Final Effects Complete Complete Final Effects（简称Fe）
1.1 FE Ball Action（球状运动） 
1.2 FE Bubbles（泡沫） 
1.3 FE Color Offset（颜色位移） 
1.4 FE Composite（合成） 
1.5 FE Flo Motion（失真运动） 
1.6 FE Griddler（矿筛） 
1.7 FE Image Wipe（图像擦除） 
1.8 FE Kaleida（发音体） 
1.9 FE Lens（透镜） 
1.10 FE Light Burst 2.5（灯光爆裂） 
1.11 FE Light Sweep（扫光） 
1.12 FE Page Turn（翻页） 
1.13 FE Particle Systems（粒子系统） 
1.14 FE Particle Systems II（粒子系统2）
1.15 FE Particle Systems LE（粒子系统LE）
1.16 FE Pixel Polly（像素剥离） 
1.17 FE Radial ScaleWipe（反射状的缩放擦拭） 
1.18 FE Rain（下雨） 
1.19 FE Scale Wipe（缩放擦除） 
1.20 FE Scatterize（分散） 
1.21 FE Slant（倾斜） 
1.22 FE Slant Matte（倾斜剪影） 
1.23 FE Snow（下雪） 
1.24 FE Sphere（球体） 
1.25 FE Star Burst（星爆式） 
1.26 FE Threshold（阀值） 
1.27 FE Threshold RGB（RGB阀值）
1.28 FE Tiler（瓦盖） 
1.29 FE Twister（缠绕）

## Next Effect（简称Ne）
2.1 FE Advanced 3D（高级三维） 
2.2 FE Bend It（弯曲） 
2.3 FE Cylinder（圆柱体） 
2.4 FE Drizzle（毛毛雨） 
2.5 FE Force Motion Blur（强大的运动模糊） 
2.6 FE Hair（毛发） 
2.7 FE Light Rays（体积光） 
2.8 FE Mr. Smoothie（圆滑） 
2.9 FE Power Pin（透视点） 
2.10 FE RepeTile（放射状模糊） 
2.11 FE Simple Wire Removal（擦除金属丝） 
2.12 FE Wide Time（放慢）

## 3 Studio Effects（简称Se）
3.1 FE Alpha Map（Alpha贴图） 
3.2 FE Bender（弯曲） 
3.3 FE Blobbylize（滴状斑点） 
3.4 FE Burn Film（燃烧的胶片） 
3.5 FE Glass（玻璃） 
3.6 FE Glass Wipe（擦拭玻璃） 
3.7 FE Glue Gun（喷胶枪） 
3.8 FE Grid Wipe（删格擦拭） 
3.9 FE Jaws（狭口） 
3.10 FE Light Wipe（扫光） 
3.11 FE Mr. Mercury（水银先生） 
3.12 FE Particle World（粒子世界） 
3.13 FE Ripple Pulse（涟漪发生器） 
3.14 FE Smear（涂污） 
3.15 FE Split（切开） 
3.16 FE Spotlight（聚光灯） 
3.17 FE Time Blend（时间混合） 
3.18 FE Time Blend FX（时间混合FX）
3.19 FE Toner（调色剂）

## Boris
1 Boris Fire（火焰效果）
2 Boris FX 3 
2.1 Boris Artist's Poster（艺术海报） 
2.2 Boris Blur （模糊） 
2.3 Boris Directional Blur （方向模糊） 
2.4 Boris Gaussian Blur （高斯模糊） 
2.5 Boris Unsharp Mask （锐利的遮罩） 
2.6 Boris Brightness-Contrast （亮度-对比度）
2.7 Boris Color Balance （颜色平衡） 
2.8 Boris Color Correction （颜色修正） 
2.9 Boris Composite （合成） 
2.10 Boris Correct Selected Color （修改选择的颜色） 
2.11 Boris Hue-Sat-Lightness （色调-饱和度-亮度） 
2.12 Boris Invert Solarize （反转曝光） 
2.13 Boris Levels Gamma （标准的伽马值） 
2.14 Boris MultiTone Mix （多通道混合） 
2.15 Boris Posterize （多色调分色）
2.16 Boris RGB Blend （RGB混和）
2.17 Boris Tint-Tritone （以三种颜色替换） 
2.18 Boris Bulge （凸出） 
2.19 Boris Displacement Map （置换贴图） 
2.20 Boris Fast Flipper （自动翻转） ，
2.21 Boris Polar Displacement （两极置换） 
2.22 Boris Ripple （波纹） 
2.23 Boris Vector Displacement （矢量置换） 
2.24 Boris Wave （波浪） 
2.25 Boris Alpha Process （Alpha通道处理）
2.26 Boris Chroma Key （色度抠像） 
2.27 Boris Composite Choker （令人窒息的合成） 
2.28 Boris Linear Color Key （线性颜色抠像） 
2.29 Boris Linear Luma Key （线性亮度抠像） 
2.30 Boris Make Alpha Key （制作新的Alpha通道）
2.31 Boris Matte Choker （令人窒息的剪影） 
2.32 Boris Matte Cleanup（清除剪影） 
2.33 Boris Two Way Key（两种路线的抠像） 
2.34 Boris Alpha Spotlight（以Apha通道的方式设定聚光灯）
2.35 Boris Edge Lighting（边缘亮光） 
2.36 Boris Light Sweep（扫光） 
2.37 Boris Reverse Spotlight（相反的聚光灯） 
2.38 Boris Spotlight（聚光灯） 
2.39 Boris 2D Particles（二维粒子） 
2.40 Boris 3D Image Shatter（模拟三维图像破碎效果） 
2.41 Boris Cube（模拟三维立方体） 
2.42 Boris Cylinder（模拟三维圆柱体） 
2.43 Boris DVE（模拟三维效果） 
2.44 Boris Page Turn（翻页） 
2.45 Boris Sphere（模拟三维球形） 
2.46 Boris Clouds（流动的云） 
2.47 Boris Noise Map（噪点地图） 
2.48 Boris Alpha Pixel Noise（通道像素噪点） 
2.49 Boris RGB Edges（RGB边缘） 
2.50 Boris RGB Pixel Noise（RGB像素噪声）
2.51 Boris Scatterize（模拟毛玻璃的效果） 
2.52 Boris Spray Paint Noise（喷漆噪点） 
2.53 Boris Flat 3D Text（扁平的三维字体[不支持中文]） 
2.54 Boris 3D Text（三维字体[不支持中文]）

## 3 Boris Continuum
3.1 BC 3D Text（三维文字） 
3.2 BC Boost Blend（推进混合） 
3.3 BC Burnt Film（燃烧的电影） 
3.4 BC Clouds（流动的云） 
3.5 BC Comet（彗星） 
3.6 BC Composite（合成） 
3.7 BC DVE（模拟三维效果） 
3.8 BC Fire（火） 
3.9 BC Jitter（频谱曲线抖动） 
3.10 BC Looper（循环） 
3.11 BC Particle System（粒子系统） 
3.12 BC Posterize Time（相片时间） 
3.13 BC Rain（下雨） 
3.14 BC Sequencer（音序器） 
3.15 BC Snow（下雪） 
3.16 BC Sparks（火花） 
3.17 BC Stars（星星） 
3.18 BC Super Blend（超级混合） 
3.19 BC Temporal Blur（时间模糊） 
3.20 BC Trails（轨迹） 
3.21 BC Velocity Remap（速度测试图） 
3.22 BC Z Space I（Z空间1） ，
3.23 BC Z Space I I（Z空间2）

project 窗 ，comp 窗，time layout 窗，lay 窗，file 菜单

新建 ← New
New Project → 新建项目
New Folder →新建文件夹
打开项目 ← Open Project
打开最近项目 ← Open Recent Projects
在Bridge内浏览 ← Browse in Bridge
浏览模板 ← Browse Template Projects
关闭 ← Close
关闭项目 ← Close Project
保存 ← Save  
另存为 ← Save As...
保存副本 ← Save a Copy...
另存为XML格式← Save a Copy As XML
增量保存 ← Increment and Save
恢复 ← Revert
导入 ← Import
File...     → 文件
Multiple Files...    →多个文件
Capture in Adobe Premiere Pro →Premiere Pro采集
Adobe Clip Notes Comments.. →Adobe 剪辑注释评论
Adobe Premiere Pro Project… →Premiere Pro项目…
Vanishing Point  (vpe)… → PS消失点 （.vpe）…
Placeholder... →输入占位符
Solid...  →实色
导入最近素材 ← Import Recent Footage
Adobe Dynamic Link Adobe ← 动态链接
输出 ← Export
查找 ← Find...
再次查找 ← Find Next
添加素材到合成 ← Add Footage to Comp
选定脚本建立合成 ← New Comp From Selection...
整理素材 ← Consolidate All Footage
删除未用素材 ← Remove Unused Footage



Ctrl+Alt+F使素材满屏



# AE表达式
## 循环 
``` 
loopOut(type = "pingpong", numKeyframes = 0)  
```
## 抖动
```  
wiggle(5,100)
```
## 时间 
``` 
time*30
```

## 弹性 
``` 
amp = .1; 
freq = 2.0; 
decay = 2.0; 
n = 0; 
if (numKeys > 0){ 
n = nearestKey(time).index; 
if (key(n).time > time){n--;} 
} 
if (n == 0){ t = 0;} 
else{t = time - key(n).time;} 
if (n > 0){ 
v = velocityAtTime(key(n).time - thisComp.frameDuration/10); 
value + v*amp*Math.sin(freq*t*2*Math.PI)/Math.exp(decay*t); 
} 
else{value}
```

## 透明过渡效果
```
transition = 20; 
if (marker.numKeys<2){ 
tSecs = transition / ( 1 / thisComp.frameDuration); 
linear(time, inPoint, inPoint + tSecs, 0, 100) - linear(time, outPoint - tSecs, outPoint, 0, 100) 
}else{ 
linear(time, inPoint, marker.key(1).time, 0, 100) - linear(time, marker.key(2).time, outPoint, 0, 100) 
}  
``` 
## index的简单应用（仿3D字体）
```
[transform.position[0], transform.position[1],index*3]
// 该层Z轴的值等于该层的序号*3；X轴、Y轴值为它本身
```
```
[transform.position[0], transform.position[1],index*thisComp.layer("Control").effect("Slider Control")("Slider")]
// 该层X轴、Y轴值为它本身，Z轴的值等于该层的序号*本合成里的控制层 效果 大小控制的系数。这个比上面一个更为好用 可以根据效果调节疏密。
```
```
thisComp.layer("Control").effect("Color Control")("Color")
// 该层的信息 被本合成里的控制层（Control） 效果（Color Control）色彩 控制。这里设置被控制的是字体的填充色，最外慢一层除外。
```

*在做3D字体需要反复修改颜色的时候毋须一条一条的修改，修改效率更高*
