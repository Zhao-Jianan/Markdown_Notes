# 基础网络知识
## Network
网络，具有通讯能力的多台设备连接而成
## Internet
互联网，特指世界上最大的计算机网络，由几十亿台设备连接而成，70年代末到80年代初，从小型网络发展而成
## LAN和WAN
LAN------Local Area Network------局域网
WAN------Wide Area Network-------广域网
LAN和WAN是相对的
## Web
Web------World Wid Web-----------全球广域网，也叫万维网，是基于超文本和HTTP的、全球性的、动态交互的、跨平台的分布式土星信息系统，是建立在Internet上的一种网络服务
Web即是世界上所有网站的集合
## IP
IP-------Internet Protocol
IP Address类似门牌号
数据如何传输，类似交通系统
### IPv4
一个地址是一个32位整数
地址由4各部分组成，每个部分取值0-255
### IPv6
128位整数，很大的数
## Port
Port-----端口
IP地址用来寻找到机器，端口用来寻找到机器上的程序
例如：
Http----80
MySQL---3306
FTP-----21
UE4-----7777
端口可能被防火墙挡住

程序运行后向操作系统申请，成功后独占使用
程序退出后，端口自动释放
### IP:Port
IP可以是内网IP，也可以是外网IP
IP:Port代表着网络中的一个程序
如果知道这个程序需要的数据格式，就可以与之通信
## 网络协议
### TCP
TCP------Transmission Control Protocol
是可靠的，像管道一样的连接
丢包会重发
如果网络差，TCP会丢包重发，从而导致网络更差
TCP三次握手
### UDP
UDP------User Datagram Protocol
只管发，不管对面有没有在接收
优点：发包效率高
### HTTP
HTTP-----Hypetext Transfer Protocol
用于网站，是基于TCP的一种协议
## 域名与DNS
域名-----Domain
为IP地址起一个好记的名字 
DNS------Domain Name System
记录域名与IP的对应关系
## 数据请求模式
有两种常见的请求模式
### Client-Server
服务器-客户端模式
客户端负责表现，服务端负责数据

#### 如何防外挂
1. 关键计算放在服务器
2. 服务器做足验证
3. 有些只能在客户端的计算，代码混淆、资源加密

#### 语言选择
客户端受限于引擎
Cocos-----C++,Lua,JS
Unity-----C#,Lua
UE4-------C++,蓝图

服务端可选方案更多
C++,Python,Java,PHP
### Peer-to-Peer
即P2p模式，比如BitTorrent



# 使用虚幻4开发网络游戏的两种方式
## 虚幻4只做客户端，服务器独立开发，适用于任何网络游戏
## 使用虚幻4同时开发客户端和服务器，适用于一部分网络游戏


# 对服务器要求较高的游戏玩法
## 多人同屏
## 高速操作，迅速同步
## 全球同服

# 虚幻4游戏进程的4种网络模式
1. Standalone
单机
2. Client
客户端
3. ListenServer
有服务器和一个客户端，在一个进程里
4. DedicatedServer
专用服务器

# Replication/复制
是一种同步机制
Actor及Actor中的属性，可以设置是否复制，Actor默认不勾选，Pawn默认勾选
复制是单向的，只能从服务器到客户端
## Actor的产生和复制
- 客户端Spawn的Actor，不会被复制
- 服务器Spawn的Actor，可以被复制
- 初始就放置在关卡中的Actor，可以被复制



# Authority/网络控制权
在网游中，由当前进程创建的Actor，对其拥有网络控制权
Has Authority，当前进程是否对这个Actor具有网络控制权。如果有，则当前进程可以销毁这个Actor

网络复制要注意避免复制引发的重复对象

一般生成对象都要在服务端运行，要进行Has Authority判定

在客户端射击，复制到客户端，并同步到其他所有客户端的方法：
- 第1步：创建一个服务端射击事件Server-ShootEvent，Replicates设为Run on Server，键盘射击输入触发时调用
- 第2步：创建一个射击多播事件All-ShootEvent,Replicates设为Multicast,服务端射击事件Server-Shoot触发时调用
- 第3步：创建一个射击事件ShootEvent，Replicates设为Not Replicated，写生成子弹等射击执行逻辑，射击多播事件All-ShootEvent触发时调用，调用时要加判断Has Authority，仅在拥有控制权的服务端运行，否则会生成重复对象


# RPC/远程程序调用
RPC-----Remote Procedure Call
一个进程调用另外一个进程上的函数

## 从服务器调用的RPC
| Actor 所有权       | Not Replicated（未复制） | NetMulticast（多播）         | Run on Server（服务器上运行） | Run on Owning Client（所属客户端上运行） |
|:------------------|:------------------------|:----------------------------|:------------------------------|:----------------------------------------|
| Client-owned actor | 在服务器上运行            | 在服务器和所有客户端上运行   | 在服务器上运行                 | 在 actor 的所属客户端上运行             |
| Server-owned actor | 在服务器上运行            | 在服务器和所有客户端上运行   | 在服务器上运行                 | 在服务器上运行                         |
| Unowned actor      | 在服务器上运行            | 在服务器和所有客户端上运行   | 在服务器上运行                 | 在服务器上运行                         |


## 从客户端调用的 RPC
| Actor 所有权              | Not Replicated（未复制） | NetMulticast（多播）         | Run on Server（服务器上运行） | Run on Owning Client（所属客户端上运行） |
|:-------------------------|:------------------------|:----------------------------|:------------------------------|:----------------------------------------|
| Owned by invoking client   | 在执行调用的客户端上运行  | 在执行调用的客户端上运行      | 在服务器上运行                 | 在执行调用的客户端上运行               |
| Owned by a different client| 在执行调用的客户端上运行  | 在执行调用的客户端上运行      | **丢弃**                       | 在执行调用的客户端上运行               |
| Server-owned actor         | 在执行调用的客户端上运行  | 在执行调用的客户端上运行      | **丢弃**                       | 在执行调用的客户端上运行               |
| Unowned actor              | 在执行调用的客户端上运行  | 在执行调用的客户端上运行      | **丢弃**                       | 在执行调用的客户端上运行               |



| 类型              | 生命周期 | 存在于             | 是否复制 | 进程内个数                            |
|:------------------|:----------|:-------------------|:----------|:---------------------------------------|
| GameInstance        | 进程       | 服务器和客户端         | 否         | 1                                     |
| GameMode            | 关卡       | 服务器               | N/A       | 1                                     |
| GameState           | 关卡       | 服务器和客户端         | 是         | 1                                     |
| PlayerController    | 关卡       | 服务器和客户端         | 是         | 服务器同玩家个数，客户端仅 1 个         |
| PlayerState         | 关卡       | 服务器和客户端         | 是         | 同玩家个数                              |
| Pawn/Character      | 逻辑控制    | 服务器和客户端         | 是         | 同玩家个数                              |


### 单机游戏改网络游戏不完全清单
1. 把Actor的复制打开
2. 重要数据的复制打开，且只在服务器修改
3. 需要同步的Actor，不在客户端Spawn
4.客户端的操作，先报告到服务器，服务器再广播到所有客户端
5. 某些逻辑只在服务器运行
6. 考虑相关性、延迟等更多因素
7. ……
 
### 项目开发时要重点思考
1. 哪些放服务端，哪些放客户端
2. 它们之间怎么通信？会不会覆盖？
3. 服务器应该做那些验证？



























