# UE4的渲染管线
可以理解为渲染原理或渲染流程。即一帧的画面是如何呈现出来的
## 技术原理
3D场景中通过摄像机将显示效果转换到2D坐标系中展现的过程

## 渲染流程阶段
应用阶段-->几何阶段-->光栅化阶段-->逐片元操作-->后处理

整个渲染是由CPU和GPU交互得到的结果

### 应用阶段
由CPU负责，渲染设置、获取渲染状态、准备基本数据、输出到几何阶段

### 几何阶段
顶点着色器、曲面细分、几何着色器、顶点裁剪、屏幕映射

### 光栅化阶段
三角形设置、三角形遍历、片元着色器

### 逐片元操作
裁剪测试、透明度测试、深度测试、模板测试、混合

透明度测试、深度测试、模板测试合称为三大测试

### 后处理
渲染最后的准备工作


## CPU-->GPU的通信过程
这是应用阶段过渡到集合阶段的过程，也是CPU过渡到GPU的过程，也是内存过渡到显存的过程
由CPU发出指令，通知GPU去渲染，GPU的渲染永远是一个被动的过程
### 准备基本场景数据
准备场景中的物体
摄像机确定了渲染场景哪个部分
场景中的光源和阴影
其他全局数据，如雾化效果
### 加速算法
渲染之前应该剔除一些东西，如碰撞检测、遮挡剔除
### 粗粒度剔除
优化渲染效果的方式，根据光源剔除、根据场景模型剔除
### 设置渲染状态
决定谁先渲染，谁后渲染，以及渲染模式
### 准备渲染参数
顶点信息（位置、法线、切线、UV坐标）
### 调用DrawCall
DrawCall每调用一次，代表CPU通知GPU进行一次渲染，执行底层图形编程接口（DirectX OpenGL）

DrawCall是CPU调用的，优化要尽量减少DrawCall调用次数，优化DrawCall优化的是CPU
因为每次DrawCall，CPU都要准备大量的数据

游戏出现卡顿通常原因都是CPU给GPU发消息时发慢了

### 输出渲染图元到显存
前面的步骤准备好后，显存拿到的数据就是图元，包括顶点位置、顶点颜色、顶点法线、顶点UV、模型矩阵


## 几何阶段
从几何阶段开始，都是GPU负责
### 视图转换
在顶点着色器阶段完成MVP矩阵变换，目的是完成三维到二维的屏幕映射的转换（经过三次变换：模型变换-->观察变换-->投影）
#### 模型变换
把模型从本地空间坐标系转换到世界空间坐标系
#### 观察变换
以相机作为世界空间原点
#### 投影
投影本质是缩放过程，把世界空间坐标系转为屏幕空间坐标系
### 顶点着色
### 曲面细分（可选配置）
### 几何着色器（可选配置）
基于图元计算每一个三角面
### 投影
正交或透视
### 裁剪
正面与背面剔除
三角面如果整个在屏幕范围内，就保留，如果整个都在屏幕范围外，就剔除，如果有部分在屏幕范围内，需要进行裁剪。裁剪多生成两个点，重新计算面，把面变为三角形

OpenGL坐标系左下角（0,0），右上角（512,512），DirectX坐标系左上角（0,0），右下角（512,512）
### 屏幕映射
根据不同的底层图形编程接口来转换坐标系

## 光栅化阶段
绘制颜色

将模型点点投射在画面的片元信息，进行渐变连线，绘制出三角形，抗锯齿处理（MSAA、FXAA、SMAA），片元着色器执行shader代码，绘制效果

## 逐片元操作
逐片元进行三大测试，没有通过测试的片元不会显示
深度测试是必须做的测试，它决定遮挡关系
模板测试是自由的测试，由技术美术控制


# 游戏优化
基本理念：空间换取时间
## 纹理
尽量使用2的n次幂大小的贴图 生成MipMap技术 增加内存 根据相机距离选择不同分辨率
的纹理进行渲染
纹理都是有压缩的 透明通道该不要的尽量不要
BC3/DXTC5 记录透明
BC1/DXTC1 不记录透明
## 剔除优化
UE4的4种剔除：距离剔除 预计算剔除 视锥剔除 遮挡剔除
距离剔除：distanceCulling
遮挡剔除：CPU的遮挡裁剪 把一个大mesh拆分成多个小的mesh 看不见的部分被剔除出
渲染队列
## DrawCall优化
核心思路：把很多小的drawcall合并成一个大的drawcall
  ### 合并图集
优化UI 把很多小的贴图合并到一张大纹理 在满足相同mesh 相同材质 和贴图
的基础上 合并drawcall
  ### 网格的合批
合并网格对象 多个mesh和合并成一个大的新mesh 
## 模型面数和物理优化
不需要的情况下关闭掉所有物理
## LOD
对于需要展示细节的物体 设置LOD 如果距离较近 选用LOD0层级的模型 如果距
离较远 选用LOD1层级的模型
## 灯光优化
光照贴图 静态光照 计算快速 也是预计算 光照阴影信息存储在纹理中 增加内存
提升渲染效率
