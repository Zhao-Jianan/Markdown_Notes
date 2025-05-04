# Matplotlib
## 介绍
### 概念
画二维图表的python库
#### mat
matrix矩阵
#### plot
画图
#### lib
libray库

### 用途
数据可视化，帮助理解数据，方便选择更合适的分析方法
### 导包
```
import matplotlib.pyplot as plt
```
## Matplotlib三层结构
### 容器层
#### Canvas/画板层
#### Figure/画布层
```
plt.figure(figsize=, dpi=)
```
#### 绘图区/坐标系
```
figure, axes = plt.subplots(nrows=,ncols=,figsize=,dpi=)
```
x、y轴张成的区域
### 辅助显示层
#### 修改x，y轴刻度
```
plt.xticks()
plt.yticks()
```
#### 添加描述信息
```
plt.xlabel()
plt.ylabel()
plt.title()
```
#### 添加网格
```
plt.grid()
```
#### 显示图例
```
plt.legend()
```
### 图像层
可以设置图像颜色、风格、标签等)
#### 折线图
```
plt.plot()
```
例如
```
plt.plot(x,y_Newcastle, color = 'r', linestyle='--', label='Newcastle')
```
#### 散点图
```
plt.scatter()
```
#### 柱状图
```
plt.bar()
```
例如
```
plt.bar(x, first_day, color='r', label='first_day', width=0.2)
```
#### 直方图
```
plt.hist()
```
例如
```
plt.hist(time, bins=group_num, density=True)
```
#### 饼状图
```
plt.pie()
```
例如
```
plt.pie(tickets, labels= movie_names, autopct='%1.2f%%')
```

# Numpy
## 介绍
### 概念
- Numpy(Numerical Python)是一个开源的Python科学计算库，用于快速处理任意维度的数组
- Numpy 支持常见的数组和矩阵操作。对于同样的数值计算任务，使用 Numpy 比直接使用 Python 要简洁的多
- Numpy 使用 ```ndarray``` 对象来处理多维数组，该对象是一个快速而灵活的大数据容器

## ndarray
### 概念
- Numpy使用 ```ndarray``` 对象来处理多维数组，该对象是一个快速灵活的大数据容器
- Numpy提供了一个N维数组类型的 ```Ndarray```，它描述了相同类型的 ```items``` 的集合
### 优势
#### 存储风格
##### ndarray
相同数据类型，通用性不强
##### list
不同数据类型，通用性强
#### 并行化运算
ndarray支持向量化运算
#### 底层语言
Numpy底层使用C语言编写，内部解除了GIL（全局解释锁），其对数组的操作速度不受Python解释器的限制，效率远高于纯Python代码

### 属性
数组维度的元组
```
ndarray.shape
```
数组维数
```
ndarray.ndim
```
数组中的元素数量
```
ndarray.size
```
一个数组元素的长度（字节）
```
ndarray.itemsize
```
数组元素的类型
```
ndarray.dtype
```

*在创建 ```ndarray``` 的时候，如果没有指定类型，默认：整数 ```int64/int32``` 浮点数 ```float64/float32```*

## 基本操作
### 生成数组
#### 生成 0 和 1 的数组
生成一组0
```
np.zeros(shape=, dtype=)
```
例如
```
np.zeros(shape=(3, 4), dtype="float32")
```
生成一组1
```
np.ones(shape=, dtype=)
```
例如
```
np.ones(shape=[2, 3], dtype=np.int32)
```
#### 从现有数组生成
深拷贝
```
np.array()
```
例如
```
data1 = np.array(score)
```
浅拷贝
```
np.asarray()
```
例如
```
data2 = np.asarray(score)
```
深拷贝
```
np.copy()
```
例如
```
data3 = np.copy(score)
```
#### 生成固定范围的数组
```
np.linspace()
np.linspace(0, 10, 5) # 生成[0,10]之间等距离的5个数
```
```
np.arange()
np.arange(0, 11, 5) # [0,11)，5为步长生成数组
```
#### 生成随机数组
生成均匀分布的一组数[low,high)
```
np.random.uniform(low=,high=,size=)
```
例如
```
data1 = np.random.uniform(low=-1, high=1, size=1000000)
```
生成正态分布的一组数，loc：均值；scale：标准差
```
np.random.normal(loc=, scale=, size=)
```
例如
```
data2 = np.random.normal(loc=1.75, scale=0.1, size=1000000)
```

### 数组的索引、切片
```
stock_change = np.random.normal(loc=0, scale=1, size=(8, 10))
```
```
# 获取第一个股票的前3个交易日的涨跌幅数据
print(stock_change[0, :3])
a1[1, 0, 2] = 100000
```
### 形状修改
#### ```ndarray.reshape()```
返回新的ndarray,原始数据没有改变
```
stock_change.reshape((10, 8))
```
#### ```ndarray.resize()```
没有返回值，对原始的ndarray进行了修改
```
stock_change.resize((10, 8))
```
#### ```ndarray.T```
转置,行变成列，列变成行
```
stock_change.T
```
### 类型修改
#### ndarray.astype()
类型转换
stock_change.astype("int32")
#### ndarray.tostring()
ndarray序列化到本地
stock_change.tostring()

### 数组去重
#### ```np.unique()```
```
temp = np.array([[1, 2, 3, 4],[3, 4, 5, 6]])
np.unique(temp)
set(temp.flatten())
```

## ndarray 运算
### 逻辑运算
#### 运算符
```
# 逻辑判断, 如果涨跌幅大于0.5就标记为True 否则为False
stock_change > 0.5
stock_change[stock_change > 0.5] = 1.1
```
#### 通用判断函数
```np.all()```
```
# 判断stock_change[0:2, 0:5]是否全是上涨的
np.all(stock_change[0:2, 0:5] > 0)
```
```np.any()```
```
# 判断前5只股票这段期间是否有上涨的
np.any(stock_change[:5, :] > 0)
```
#### 三元运算符
```
# np.where(布尔值，True的位置的值，False的位置的值)
np.where(temp > 0, 1, 0)

# 大于0.5且小于1
np.where(np.logical_and(temp > 0.5, temp < 1), 1, 0)

# 大于0.5或小于-0.5
np.where(np.logical_or(temp > 0.5, temp < -0.5), 11, 3)
```
### 统计运算
#### 统计指标函数
```min```
```
ndarray.min(axis=)
```
```
np.min(ndarray, axis=)
```
```max```
```
ndarray.max(axis=)
```
```
np.max(ndarray, axis=)
```
```mean(均值)```
```
ndarray.mean(axis=)
```
```
np.mean(ndarray, axis=)
```
```median(中位数)```
```
ndarray.median(axis=)
```
```
np.median(ndarray, axis=)
```
```var(方差)```
```
ndarray.var(axis=)
```
```
np.var(ndarray, axis=)
```
```std(标准差)```
```
ndarray.std(axis=)
```
```
np.std(ndarray, axis=)
```
```argmax```  
返回最大值的位置
```
np.argmax(tem,axis=)
```
```argmin```  
返回最小值的位置
```
np.argmin(tem,axis=)
```
### 数组间运算
#### 数组与数的运算
```
arr = np.array([[1, 2, 3, 2, 1, 4], [5, 6, 1, 2, 3, 1]])
arr / 10
```
#### 数组与数组的运算
广播机制broadcast
- 执行 broadcast 的前提在于，两个 nadarray 执行的是 element-wise 的运算，Broadcast 机制的功能是为了方便不同形状的 ndarray(numpy 库的核心数据结构)进行数学运算。

- 当操作两个数组时，numpy 会逐个比较它们的 shape(构成的元组 tuple)，只有在下述情况下，两个数组才能够进行数组与数组的运算。
- 广播必须满足的条件
  - 维度相等
  - shape（其中相对应的一个地方为 1）

#### 矩阵运算 ```matrix```
和 ```array``` 的区别是矩阵必须是 2 维的，但是 ```array``` 可以是多维的

##### 矩阵和二维数组的区别

```np.mat()``` 将数组转换成矩阵类型

**矩阵乘法规则```（M 行,N 列）x (N 行,L 列) = (M 行,L 列)```**

##### ndarray的矩阵乘法
```
np.dot(data,data1)
```
```
np.matmul(data,data1)
```
```
data @ data1
```
##### martix的矩阵乘法
```
data * data1
```

## 合并与分割
### 合并
#### 水平拼接
```
numpy.hstack
```
```
numpy.concatenate((a1,a2),axis=0)
```
#### 垂直拼接
```
numpy.vstack
```
```
numpy.concatenate((a1,a2),axis=1)
```
### 分割
```
numpy.split
```
```
numpy.split(x,3) # 分三份
```
```
numpy.split(x,[3,4,6,10]) # 按索引分割
```

## IO 操作与数据处理
### 读取数据
#### ```np.genfromtxt()```
```np.genfromtxt("test.csv", delimiter=",")``` 会有问题，读不出字符串

### 如何处理缺失值
两种思路：
#### 直接删除含有缺失值的样本
#### 替换/插补 （补入平均值或中位数）




# Pandas
## 介绍
### 概念
- 2008 年 WesMcKinney 开发出的库
- 专门用于数据挖掘的开源 Python 库
- 以 Numpy 为基础，借力 Numpy 模块在计算方面性能高的优势
- 基于 matplotlib，能够简便的画图
- 独特的数据结构
### 优势
- 便捷的数据处理能力
- 读取文件方便
- 封装了 Matplotlib、Numpy 的画图和计算

## 核心数据结构
### DataFrame
#### 结构
既有行索引，又有列索引的二维数组
##### 行索引(index)
表明不同行，横向索引
##### 列索引(columns)
表明不同列，纵向索引

#### 常用属性
```shape```  
维度

```index```  
行索引列表

```columns```  
列索引列表

```values```  
直接获取其中 array 的值

```T```  
行列转置

#### 常用方法
开头几行
```
head()
```
最后几行
```
tail()
```


#### 索引的设置
```
DataFrame.index = 
```
##### 修改行列索引值
```
# data.index[2] = "股票88" 不能单独修改索引
stock_ = ["股票_{}".format(i) for i in range(10)]
data.index = stock_
```
##### 重设索引
```
DataFrame.reset_index(drop=False)
```
```
data.reset_index(drop=False)
```
- drop
  - ```drop=True``` -------- 把之前的索引删除
  - ```drop=False``` ------- 保持之前的索引

##### 设置新索引
```
DataFrame.set_index("column_name", drop=)
```
```
df = pd.DataFrame({'month': [1, 4, 7, 10],
                    'year': [2012, 2014, 2013, 2014],
                    'sale':[55, 40, 84, 31]})
```
###### 以月份设置新的索引
```
df.set_index("month", drop=True)
```
###### 设置多个索引，以年和月份
```
new_df = df.set_index(["year", "month"])
```

### MultiIndex 与 Panel
#### MultiIndex
多级或分层索引对象
```index``` 属性
- names
  - levels 的名称
- levels
  - 每个 level 的元组值
```
print(new_df.index)
print(new_df.index.names)
print(new_df.index.levels)
```
#### Panel（已弃用）
```
pandas.Panel(data=None,items=None,major_axis=None,minor_axis=None,copy=False,dtype=None)
```
##### 存储 3 维数组的 Panel 结构
```
items - axis 0，每个项目对应于内部包含的数据帧(DataFrame)。
major_axis - axis 1，它是每个数据帧(DataFrame)的索引(行)。
minor_axis - axis 2，它是每个数据帧(DataFrame)的列
```
*Pandas 从版本 0.20.0 开始弃用，推荐的用于表示 3D 数据的方法是 DataFrame 上的 MultiIndex 方法*

### Series
带索引的一维数组
#### 属性
```index```  

```values```

** ```DataFrame``` 是 ```Series``` 的容器，```Panel``` 是 ```DataFrame``` 的容器**

## 基本数据操作
### 索引操作
索引操作即数据查询操作
#### 直接索引
```
data["column_name"]["index_name"]
```
**直接索引注意是先列后行**
```
data = pd.read_csv("./stock_day/stock_day.csv")
data = data.drop(["ma5","ma10","ma20","v_ma5","v_ma10","v_ma20"], axis=1) # 去掉一些不要的列
data["open"]["2018-02-26"] # 直接索引，先列后行
```
#### 按名字索引
data.loc
根据行、列的标签值查询
```
data.loc["index_name"]["column_name"] 
data.loc["index_name", "column_name"] 
```
```
data.loc["2018-02-26"]["open"] # 按名字索引
data.loc["2018-02-26", "open"]
```

##### 使用df.loc查询数据的方法
1. 使用单个`label`值查询数据
2. 使用值列表批量查询
3. 使用数值区间进行范围查询
4. 使用条件表达式查询
```
# 查询温度小于30度，大于21度，湿度大于50，小于70，累计雨量为0
df.loc[(df['气温(度)'].astype(float) < 27) & (df['气温(度)'].astype(float) > 24) & (df['相对湿度(%)'] < 60) & (df['相对湿度(%)'] > 50) & (df['累积雨量(mm)'] < 0.1),:]
```
5. 调用函数查询
```
df.loc[lambda df : (df['气温(度)'].astype(float) < 27) & (df['气温(度)'].astype(float) > 24) & (df['相对湿度(%)'] < 60) & (df['相对湿度(%)'] > 50) & (df['累积雨量(mm)'] < 0.1)]
```

#### 按数字索引
data.iloc
根据行列的数字位置查询
```
data.iloc[index_num, column_num]
```
```
data.iloc[1, 0] # 数字索引
```

#### 组合索引
```
# 获取行第1天到第4天，['open', 'close', 'high', 'low']这个四个指标的结果
data.ix[:4, ['open', 'close', 'high', 'low']] (已弃用)
data.loc[data.index[0:4], ['open', 'close', 'high', 'low']]
data.iloc[0:4, data.columns.get_indexer(['open', 'close', 'high', 'low'])]
```
### 赋值操作
```
data.open = 100
data.iloc[1, 0] = 222
```
### 排序操作
排序有两种形式，一种对内容进行排序，一种对索引进行排序
#### 内容排序
```
df.sort_values(key=,ascending=)
```
##### 对内容进行排序
单个键或者多个键进行排序，默认升序

```ascending=False```:降序 ```True``` :升序```

#### 索引排序
对索引进行排序
```
df.sort_index
```

```
data.sort_values(by="high", ascending=False) # DataFrame内容排序

data.sort_values(by=["high", "p_change"], ascending=False).head() # 多个列内容排序

data.sort_index().head()

sr = data["price_change"]

sr.sort_values(ascending=False).head()

sr.sort_index().head()
```

## DataFrame 运算
### 算术运算
#### ```add()```
#### ```sub()```
```
data["open"].add(3).head() # open统一加3  data["open"] + 3
data.sub(100).head() # 所有统一减100 data - 100
data["close"].sub(data["open"]).head() # close减open
```
### 逻辑运算
#### ```query(expr)```
```expr```
查询字符串

#### ```isin(values)```
判断是否为 ```values```


### 统计运算
#### 综合分析
```describe()```
能够直接得出很多统计结果，```count```, ```mean```, ```std```, ```min```, ```max```等

#### 累计统计函数
计算前 1/2/3/../n 个数的和
```
cumsum()
```
计算前 1/2/3/../n 个数的最大值
```
cummax()
```
计算前 1/2/3/../n 个数的最小值
```
cummin()
```
计算前 1/2/3/../n 个数的积
```
cumprod()
```


### 自定义运算
#### ```apply(func, axis=0)```
自定义函数
```
func

axis=0 默认按列运算
axis=1 按行运算
```

## Pandas 绘图
### ```pandas.DataFrame.plot```
```
DataFrame.plot(x=None, y=None, kind='line')

# x: label or position, default None
# y: label, position or list of label, positions, default None
Allows plotting of one column versus another

kind: str
"line": line plot(default)
"bar": vertical bar plot
"barh": horizontal bar plot
"hist": histogram
"pie": pie plot
"scatter": scatter plot
```
```
data.plot(x="volume", y="turnover", kind="scatter")
data.plot(x="high", y="low", kind="scatter")
```
### ```pandas.Series.plot```
```
sr.plot(kind="line")
```

## 文件读取与存储
### CSV
#### 读取
```
pd.read_csv()
```
```
pd.read_csv("./stock_day/stock_day.csv", usecols=["high", "low", "open", "close"]).head() # 读哪些列
```
```
data = pd.read_csv("stock_day2.csv", names=["open", "high", "close", "low", "volume", "price_change", "p_change", "ma5", "ma10", "ma20", "v_ma5", "v_ma10", "v_ma20", "turnover"])
# 如果列没有列名，用names传入
```
#### 保存
```
data.to_csv
```
```
data[:10].to_csv("test.csv", columns=["open"]) # 保存open列数据
```
```
data[:10].to_csv("test.csv", columns=["open"], index=False, mode="a", header=False)
# 保存opend列数据，index=False不要行索引，mode="a"追加模式|mode="w"重写，header=False不要列索引
```

### Excel
读取微软Excel文件,支持xls, xlsx, xlsm, xlsb, odf, ods和odt格式，存储到一个DataFrame中
#### 读取 
read_excel()

```
pandas.read_excel(io, sheet_name=0, *, header=0, names=None, index_col=None, usecols=None, dtype=None, engine=None, converters=None, true_values=None, false_values=None, skiprows=None, nrows=None, na_values=None, keep_default_na=True, na_filter=True, verbose=False, parse_dates=False, date_parser=<no_default>, date_format=None, thousands=None, decimal='.', comment=None, skipfooter=0, storage_options=None, dtype_backend=<no_default>, engine_kwargs=None)
```

### HDF5
HDF5 文件的读取和存储需要指定一个键，值为要存储的 ```DataFrame```
#### 读取 
read_hdf()

```
pandas.read_hdf(path_or_buf, key=None, **kwargs)
```
从 h5 文件当中读取数据
文件路径
```
path_or_buffer
```
读取的键
```
key
```
打开文件的模式
```
mode
```
The Selected object
```
return
```

#### 保存 ```to_hdf()```
```
DataFrame.to_hdf(path_or_buf, key, **kwargs)
```

### JSON
#### 读取
```read_json()```
```
pandas.read_json(path_or_buf=None,orient=None,type="frame",lines=False)
```
##### 将 JSON 格式转换成默认的 Pandas DataFrame 格式
```orient```
```
string,Indication of expected JSON string format
```
```'split'```
```
dict like {index -> [index], columns -> [columns], data -> [values]}
```
'records'
```
list like [{column -> value}, ..., {column -> value}]
```
```'index'```
```
dict like {index -> {column -> value}}
```
```'columns'```
```
dict like {column -> {index -> value}}
```
默认该格式
```'values'```
just the values array

```lines```
boolean, default False
###### 按照每行读取 json 对象
```type```   
default 'frame'，指定转换成的对象类型 series 或者 dataframe

#### 保存 ```to_json()```

### SQL
将 SQL 查询或数据库表读入 DataFrame
#### 读取
read_sql()

```
pandas.read_sql(sql, con, index_col=None, coerce_float=True, params=None, parse_dates=None, columns=None, chunksize=None, dtype_backend=<no_default>, dtype=None)
```

例如
```
import pymysql
conn = pymysql.connect(
  host='127.0.0.1',
  user='root',
  password='123456',
  database='my_database',
  charset='utf-8'
  )

mysql_page = pandas.read_sql("SELECT * FROM users", conn) 
```

此函数是对 read_sql_table 和 read_sql_query 的便捷包装（用于向后兼容）。它将根据提供的输入委托给特定的函数。SQL 查询将被路由到 read_sql_query，而数据库表名称将被路由到 read_sql_table





## 缺失值处理
### API
#### ```replace```
实现数据替换
#### ```dropna```
实现缺失值的删除
#### ```fillna```
实现缺失值的填充
#### ```isnull```
判断是否有缺失数据 NaN
#### ```get_dummies```
对于类别值或离散值，将NaN视为一个类别，使用此API处理转成one-hot编码

### 缺失值处理方法
- 删除含有缺失值的样本
- 替换/插补数据

### 缺失值处理步骤
#### 第1步--判断是否有 ```NaN```
```
pd.isnull(df)
pd.notnull(df)
```
#### 第2步--删除含有缺失值的样本
```
df.dropna(inplace=True)
```
默认按行删除  
- inplace
  - True----------修改原数据
  - False----------返回新数据，默认 False
#### 第3步--替换/插补数据
```
df.fillna(value,inplace=True)
```
- value  
替换的值
- inplace
  - True----------修改原数据
  - False----------返回新数据，默认 False

例如：
```
import pandas as pd
import numpy as np
movie = pd.read_csv("./IMDB/IMDB-Movie-Data.csv")

# 1）判断是否存在NaN类型的缺失值
np.any(pd.isnull(movie)) # 返回True，说明数据中存在缺失值
np.all(pd.notnull(movie)) # 返回False，说明数据中存在缺失值
pd.isnull(movie).any()
pd.notnull(movie).all()

# 2）缺失值处理
# 方法1：删除含有缺失值的样本
data1 = movie.dropna()
pd.notnull(data1).all()

# 方法2：替换
# 含有缺失值的字段
# Revenue (Millions)
# Metascore
movie["Revenue (Millions)"].fillna(movie["Revenue (Millions)"].mean(numeric_only=True), inplace=True)
movie["Metascore"].fillna(movie["Metascore"].mean(numeric_only=True), inplace=True)
```

### 不是缺失值 NaN
不是缺失值 NaN，而是有默认标记，例如"?"
#### 方法
将默认标记替换为NaN，再执行缺失值处理
#### API
```
replace(to_replace=, value=np.nan)
```
- ```to_replace```
  - 要替换的字符
- ```value```
  - 替换成的字符

例如
```
# 读取数据
path = "https://archive.ics.uci.edu/ml/machine-learning-databases/breast-cancer-wisconsin/breast-cancer-wisconsin.data"
name = ["Sample code number", "Clump Thickness", "Uniformity of Cell Size", "Uniformity of Cell Shape", "Marginal Adhesion", "Single Epithelial Cell Size", "Bare Nuclei", "Bland Chromatin", "Normal Nucleoli", "Mitoses", "Class"]

data = pd.read_csv(path, names=name)

# 1）替换
data_new = data.replace(to_replace="?", value=np.nan)

# 2）删除缺失值
data_new.dropna(inplace=True)
```

## 数据离散化
### 数据的离散化定义
连续属性的离散化就是将连续属性的值域上，将值域划分为若干个离散的区间，最后用不同的符号或整数 值代表落在每个子区间的属性值
### 数据的离散化的目的
连续属性离散化的目的是为了简化数据结构，数据离散化技术可以用来减少给定连续属性值的个数。离散化方法经常作为数据挖掘的工具
### 数据离散化的方法
#### 分组
##### 自动分组
```
sr = pd.qcut(data, bins)
```
##### 自定义分组
```
sr = pd.cut(data, [])
```
#### 将分组好的结果转换成 one-hot 编码（哑变量）
```
pd.get_dummies(sr, prefix=)
```
```
例如：
# 1）准备数据
data = pd.Series([165,174,160,180,159,163,192,184], index=['No1:165', 'No2:174','No3:160', 'No4:180', 'No5:159', 'No6:163', 'No7:192', 'No8:184'])
# 2）分组
# 自动分组
sr = pd.qcut(data, 3)
sr.value_counts()  # 看每一组有几个数据
# 3）转换成one-hot编码
pd.get_dummies(sr, prefix="height")

# 自定义分组
bins = [150, 165, 180, 195]
sr = pd.cut(data, bins)
# get_dummies
pd.get_dummies(sr, prefix="身高")
```

## 合并
### 按方向
#### ```pd.concat([data1, data2], axis=1)```
- ```axis```
  - 0 为列索引
  - 1 为行索引

### 按索引
```
pd.merge(left, right, how="inner", on=[])
```
on：索引

例如
```
left = pd.DataFrame({'key1': ['K0', 'K0', 'K1', 'K2'],
                        'key2': ['K0', 'K1', 'K0', 'K1'],
                        'A': ['A0', 'A1', 'A2', 'A3'],
                        'B': ['B0', 'B1', 'B2', 'B3']})

right = pd.DataFrame({'key1': ['K0', 'K1', 'K1', 'K2'],
                        'key2': ['K0', 'K0', 'K0', 'K0'],
                        'C': ['C0', 'C1', 'C2', 'C3'],
                        'D': ['D0', 'D1', 'D2', 'D3']})

pd.merge(left, right, how="inner", on=["key1", "key2"])

pd.merge(left, right, how="left", on=["key1", "key2"])

pd.merge(left, right, how="outer", on=["key1", "key2"])
```

## 交叉表与透视表
找到两个变量之间的关系

### 交叉表
交叉表用于计算一列数据对于另外一列数据的分组个数（寻找两个列之间的关系）
#### 方法
```
pd.crosstab(value1, value2)
```
例如
```
data = pd.crosstab(stock["week"], stock["pona"])
data.div(data.sum(axis=1), axis=0).plot(kind="bar", stacked=True)
```

### 透视表
#### 方法
```
DataFrame.pivot_table([], index=[])
```
例如
```
# 透视表操作
stock.pivot_table(["pona"], index=["week"])
```

## 分组与聚合
### 定义
分组与聚合通常是分析数据的一种方式，通常与一些统计函数一起使用，查看数据的分组情况
### 方法
```
DataFrame.groupby(key, as_index=False) 
```
#### key
分组的列数据，可以多个

例如
```
col =pd.DataFrame({'color': ['white','red','green','red','green'], 'object': ['pen','pencil','pencil','ashtray','pen'],'price1':[5.56,4.20,1.30,0.56,2.75],'price2':[4.75,4.12,1.60,0.75,3.15]})

# 进行分组，对颜色分组，price1进行聚合
# 用dataframe的方法进行分组
col.groupby(by="color")["price1"].max()

# 或者用Series的方法进行分组聚合
col["price1"].groupby(col["color"]).max()
```















































































































































































































































































































