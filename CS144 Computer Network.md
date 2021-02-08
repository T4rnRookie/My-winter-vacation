#  CS144 Computer Network

## Lecture 01 Introduction to Computer Networking

### ![image-20210111171941807](CS144 Computer Network.assets/image-20210111171941807.png)

双向字节流模式

![image-20210111172259809](CS144 Computer Network.assets/image-20210111172259809.png)

双方建立连接 可以互相进行写数据和读数据

双方都可以选择关闭连接 用户浏览器端 o r 服务端

World wide web

![image-20210111172410204](CS144 Computer Network.assets/image-20210111172410204.png)

当使用http://前面的协议

访问网站发送 get请求

200 ok代表成功访问 当然 还会有不同的请求也有不同的响应

http全部使用 ASCII码 格式类似 

![image-20210111172550259](CS144 Computer Network.assets/image-20210111172550259.png)

### BitTorrent

和http一样的字节流

![image-20210111175041861](CS144 Computer Network.assets/image-20210111175041861.png)

### SKype

![image-20210111180122900](CS144 Computer Network.assets/image-20210111180122900.png)

当出现NAT的时候 （地址转换）

打开NAT之后 能连接互联网，而互联网不能访问我们



![image-20210111180233178](CS144 Computer Network.assets/image-20210111180233178.png)



在这种情况下 我们再使用一个集合服务器

![](CS144 Computer Network.assets/image-20210111180406121.png)

称这种方法为反向链接

当两台客户端都在NAT之后

![image-20210111180457532](CS144 Computer Network.assets/image-20210111180457532.png)



用中继服务器来连接

![image-20210111175504901](CS144 Computer Network.assets/image-20210111175504901.png)

www 用客户端和服务器模型

BitTorrent peer-to-peer(点对点)

SKype  集合服务器或者中继服务器

### The 4 layer Internet Model

![image-20210111182207219](CS144 Computer Network.assets/image-20210111182207219.png)

在网络中 分层是最主要和最核心的概念

#### 链路层

![image-20210111182337091](CS144 Computer Network.assets/image-20210111182337091.png)

#### 网络层

![image-20210111182833918](CS144 Computer Network.assets/image-20210111182833918.png)



网络层将数据传给链路层，链路层为网络层提供服务

![](CS144 Computer Network.assets/image-20210111183038062.png)

网络层不关心链路层怎么工作的

![image-20210111183223648](CS144 Computer Network.assets/image-20210111183223648.png)

数据包发送到internet 必须使用 internet协议

数据包不能保证传送时候万无一失，所以要执行另一个协议

这就是传输层的协议 TCP

#### 传输层

TCP/IP

![image-20210111183408256](CS144 Computer Network.assets/image-20210111183408256.png)

TCP为应用程序提供服务，确保网络层的正确数据传输

应用程序不需要可靠的网络传输时候

可以使用UDP 协议

只是将数据交给Network

#### 应用层

通常需要双向可靠的字节流

每一层仅与同一层发生链路连接

![image-20210111183837336](CS144 Computer Network.assets/image-20210111183837336.png)



#### Summary



![image-20210111183920185](CS144 Computer Network.assets/image-20210111183920185.png)

每一层只和对应的层交流，通过对下一层的api来利用下一层的服务





![image-20210111184115587](CS144 Computer Network.assets/image-20210111184115587.png)



IP运行在链路层可以通过wifi dsl 3g Ethernet等

![image-20210111184203119](CS144 Computer Network.assets/image-20210111184203119.png)



#### The7-layer osi Model

![image-20210111184236475](CS144 Computer Network.assets/image-20210111184236475.png)

不做过多的赘述 因为已经淘汰了

### The IP service model

IP 数据由标头和数据组成



IP 服务模型

![image-20210111185214823](CS144 Computer Network.assets/image-20210111185214823.png)

类似邮箱服务

发送者和接受者不知道走的路径

IP不能保证数据包到达 必要时会丢弃数据，当堵塞的时候，会丢弃下一个

Ip不会重新发送数据包也不会告诉我们

![image-20210111185942226](CS144 Computer Network.assets/image-20210111185942226.png)

节省成本 快速的发送数据包

端对端原理

允许在顶部构建各种可信和不可信的服务，IP让应用层选择

适用于任何链路层

![image-20210111190806317](CS144 Computer Network.assets/image-20210111190806317.png)

尝试限制循环产生的后果

数据包太大会进行分段

用标头检验防止送错

允许新版本的ip 

IPV6的使用

IP允许将新字段添加到报头中

一个IPv4的标头

![image-20210111190656673](CS144 Computer Network.assets/image-20210111190656673.png)

### A  Day in the life of a packet

CLient and Server

![image-20210111191029261](CS144 Computer Network.assets/image-20210111191029261.png)

3-way handshake

First way 客户端检测到同步消息时 “Syn"

Second  SYN/ACK

Third Ack

具体内容如下

![image-20210111191335151](CS144 Computer Network.assets/image-20210111191335151.png)

![image-20210111191627533](CS144 Computer Network.assets/image-20210111191627533.png)



forwarding table 转发表

看一些真实的数据包

利用wireshark 我这里面访问了自己的blog

![image-20210111193819096](CS144 Computer Network.assets/image-20210111193819096.png)

那我们如何看网络层内部呢

我们可以使用traceroute工具

![image-20210111194624803](CS144 Computer Network.assets/image-20210111194624803.png)

可以看到经历多少个网关

通过客户端的web请求 20左右个网关跳转到

### Packet Switching

![image-20210111194856539](CS144 Computer Network.assets/image-20210111194856539.png)

![image-20210111194940066](CS144 Computer Network.assets/image-20210111194940066.png)

数据包交换的过程

self routing（不再使用）

forwarding table



不需要知道 packet 属于哪个流



![](CS144 Computer Network.assets/image-20210111195400180.png)

![image-20210111195616959](CS144 Computer Network.assets/image-20210111195616959.png)

数据流量是突发性的

![image-20210111195652165](CS144 Computer Network.assets/image-20210111195652165.png)

#### 小结

![image-20210111195824010](CS144 Computer Network.assets/image-20210111195824010.png)

多个flow可以充分利用link

## Principle :Layering

分层思想

顺序通信 每一层之间相互通信，为上一层提供定义明确的服务

![image-20210112213011567](CS144 Computer Network.assets/image-20210112213011567.png)

 

分离感使每个层都可以专注完成自己的工作

 邮政服务 分层思想

![image-20210112213522809](CS144 Computer Network.assets/image-20210112213522809.png)

本人不在乎信如何寄出的

每一层只和相连的上下层有关系

当然 分层思想也在计算机系统里面得到体现

比如一个程序的编译

![image-20210112213757757](CS144 Computer Network.assets/image-20210112213757757.png)

编译--链接--执行

layer只和上下层的layer交流，下层layer为上层提供了well-defined service，各layer可以随着时间改进而不影响其他层

举例：邮局系统；航空公司；编程

有时为了特殊目的，需要打破layering，比如在c语言中加入assembly code(汇编代码)，使得上层和底层的processor（处理器)不再相互独立。

#### 计算机分层的原因

模块化

定义明确的服务

重用

关注点分离

连续的提高

分层系统独特的(internet)

### Principle:Encapsulation

封装的思想

![image-20210112215002774](CS144 Computer Network.assets/image-20210112215002774.png)

比如通过web浏览器访问一个网站，发出一个http get请求是tcp段的Payload

封装http get的tcp段是ip数据包的payload  封装了 tcp段和http get的IP数据包是wifi的payload

两种提取数据包的方法

![image-20210112215304117](CS144 Computer Network.assets/image-20210112215304117.png)

![image-20210112215352079](CS144 Computer Network.assets/image-20210112215352079.png)

wireshark抓包

![image-20210112215508893](CS144 Computer Network.assets/image-20210112215508893.png)

封装可以使你递归分层

![image-20210112215601453](CS144 Computer Network.assets/image-20210112215601453.png)

vpn的原理

![image-20210112220420056](CS144 Computer Network.assets/image-20210112220420056.png)

## Byte order and packet formats

![image-20210112220818354](CS144 Computer Network.assets/image-20210112220818354.png)

大端和小端表示法

大端更符合人类的用法，重要的数字在前

一些有趣的测试题

![image-20210112222132044](CS144 Computer Network.assets/image-20210112222132044.png)

其实蛮简单的就是高位字节如果放在内存的低地址端就是大端模式

相反则是小端模式

![image-20210118200920878](CS144 Computer Network.assets/image-20210118200920878.png)

而ARM则在大端

协议规范机构会选择一个并坚持下去

![image-20210118201207805](CS144 Computer Network.assets/image-20210118201207805.png)

但是

![image-20210118201230827](CS144 Computer Network.assets/image-20210118201230827.png)

## IPV4

![image-20210118203035614](CS144 Computer Network.assets/image-20210118203035614.png)

网络掩码告诉设备哪些ip地址本地。在同一链接中

同一无线网理论来说不用通过ip路由 直接访问

通过不同掩码进行位运算来判断是不是在本地

![image-20210118203552533](CS144 Computer Network.assets/image-20210118203552533.png)

在mac的ifconfig里面查看en1

![](CS144 Computer Network.assets/image-20210118203733458.png)

 我的ipv4是192.168.0.20 我的网络掩码是0xfffff00 是255.255.255.0的16进制

所以在192.168.0下的ip可以直接发送

### Quiz

![image-20210118204432713](CS144 Computer Network.assets/image-20210118204432713.png)

### 分配IP address

A B C 历史上

![image-20210118204658240](CS144 Computer Network.assets/image-20210118204658240.png)



![image-20210118205415575](CS144 Computer Network.assets/image-20210118205415575.png)

但是不灵活，所以今天

![image-20210118204743194](CS144 Computer Network.assets/image-20210118204743194.png)

怎么分配IPV4

IANA 建立多个RIR进行分配

![image-20210118205214250](CS144 Computer Network.assets/image-20210118205214250.png)

扩展阅读:https://www.cnblogs.com/hark0623/p/6547432.html

一些题目

![image-20210118210011348](CS144 Computer Network.assets/image-20210118210011348.png)

## LPM

最长前缀匹配



转发表

![image-20210119104656404](CS144 Computer Network.assets/image-20210119104656404.png)

x为通配符

**![image-20210119104741189](CS144 Computer Network.assets/image-20210119104741189.png)**

表示为CIDR

![image-20210119104848470](CS144 Computer Network.assets/image-20210119104848470.png)

### Quiz

![image-20210119105721512](CS144 Computer Network.assets/image-20210119105721512.png)

## ARP

IP得到Mac地址然后得到网关地址

Addressing Problem: 一个host对应多个IP地址，不容易对应

- 解决方案：gateway两侧ip地址不同，link address确定card，network address确定host
- 这有点历史遗留问题，ip和link address的机制没有完全地分离开，decoupled logically but coupled in practice
- 对于A，ip的目标是B，link的目标是gateway

![image-20210119122503749](CS144 Computer Network.assets/image-20210119122503749.png)

![image-20210119122724779](CS144 Computer Network.assets/image-20210119122724779.png)

利用ARP协议把网络层映射到链路层

**ARP，地址解析协议**：由IP得到MAC地址 => 进一步可得到gateway address

- 是一种request-reply protocol

- nodes cache mappings, cache entries expire

- 节点request a link layer broadcast address，然后收到回复，回复的packet有redundant data，看到它的节点都能生成mapping

- reply：原则上unicast，只回传给发送者=>实际实现时更常见broadcast

- No "sharing" of state: bad state will die eventually

- MacOS中保留20min

- gratuitous request: 要求不存在的mapping，推销自己

  ##### 

![image-20210119122810481](CS144 Computer Network.assets/image-20210119122810481.png)



ARP数据包

![image-20210119122904666](CS144 Computer Network.assets/image-20210119122904666.png)

e.g.

hardware:1(Ethernet)

protocol: 0x0800(IP)

hardware length:6 (48 bit Ethernet)

protocol length:4(32 bit IP)

opcode: 1(request) /2(reply)

Destination: broadcast (ff:ff:ff:ff:ff:ff)

## Unit1 Summary

![image-20210119124616503](CS144 Computer Network.assets/image-20210119124616503.png)

了解分层的思想

Internet将数据分解为包，所以理解封装让两个层交互的方法

1.应用层如何使用Internet

2.四层思想

3.互联网协议：IP IPV4

4.网络思想

![image-20210119124839457](CS144 Computer Network.assets/image-20210119124839457.png)

## Lab0 networking warmup

warmup的实验是要配一个g++环境这样子，然后安装个telnet 写个交互流

我就跟着简单做一遍 

how to fetch a web page

![image-20210119131735502](CS144 Computer Network.assets/image-20210119131735502.png)

![image-20210119132712031](CS144 Computer Network.assets/image-20210119132712031.png)

让writing  a. webget

只用我们写一个函数，然后函数的示例代码给我们了

https://cs144.github.io/doc/lab0/class_t_c_p_socket.html

## TCP service model

**![image-20210120124451931](CS144 Computer Network.assets/image-20210120124451931.png)**

两个应用使用tcp建立通道

![image-20210120124518038](CS144 Computer Network.assets/image-20210120124518038.png)

TCP三次握手

**![image-20210120125132875](CS144 Computer Network.assets/image-20210120125132875.png)**

![image-20210120125234089](CS144 Computer Network.assets/image-20210120125234089.png)

TCP通过fin关闭链接



![image-20210120125736445](CS144 Computer Network.assets/image-20210120125736445.png)

![****](CS144 Computer Network.assets/image-20210120125423532.png)

### TCP的段头



![ ](CS144 Computer Network.assets/image-20210120130257382.png)



![image-20210120132618341](CS144 Computer Network.assets/image-20210120132618341.png)

TCP链接unique ID

五个部分，104bit

唯一性

- 要求source port initiator每次increment:64k new connections
- TCP picks ISN to avoid overlap with previous connection with same ID, 多一个域，增加随机性
- ISN的意义在于：1）security，避免自己的window被overlap 2）便于filter out不同类型的包

![image-20210120130403207](CS144 Computer Network.assets/image-20210120130403207.png)

主机A和主机B链接 包括初始序列号

**![image-20210120130647925](CS144 Computer Network.assets/image-20210120130647925.png)**



会进行偏移

![image-20210120130753023](CS144 Computer Network.assets/image-20210120130753023.png)

### TCP端口的分用

![image-20210120130937015](CS144 Computer Network.assets/image-20210120130937015.png)

## UDP

UDP数据格式

![image-20210120131716920](CS144 Computer Network.assets/image-20210120131716920.png)



UDP的数据包比较简单

![image-20210120132635957](CS144 Computer Network.assets/image-20210120132635957.png)

![image-20210120131748856](CS144 Computer Network.assets/image-20210120131748856.png)

他破坏了分层的思想

并且不保证数据能够传输到达



![image-20210120132031710](CS144 Computer Network.assets/image-20210120132031710.png)

### UDP的服务模型

* Checksum对于IPv4可选，可以为全0 * checksum用了IP header，违背layering principle，因为能detect错传 * UDP header有length字段，而TCP没有，因为TCP对空间要求高，用隐含的方式计算length * port demultiplexing, connectionless, unreliable

![image-20210120132104551](CS144 Computer Network.assets/image-20210120132104551.png)

UDP可以不按数据传输，并且不安全，不保证数据能够传输，网络文件系统的早期版本就这样 

DNS使用UDP 使UDP变得快速

## ICMP service model

![image-20210120134222993](CS144 Computer Network.assets/image-20210120134222993.png)

![image-20210120134421500](CS144 Computer Network.assets/image-20210120134421500.png)

个人理解相当于一个汇报员



![image-20210120134544379](CS144 Computer Network.assets/image-20210120134544379.png)

ICMP的type code多样 只需要在线查找即可

![image-20210120134627822](CS144 Computer Network.assets/image-20210120134627822.png)

### ping命令

调用ICMP. 回显ICMP



![image-20210120135151151](CS144 Computer Network.assets/image-20210120135151151.png)

### traceroute

![image-20210120135855866](CS144 Computer Network.assets/image-20210120135855866.png)

所以不断发送udp 改变TTL的大小就可以知道经过哪些路由器和返回的时间

![image-20210120140124251](CS144 Computer Network.assets/image-20210120140124251.png)

UDP消息发送端口到B，故意选择一个B不知道的端口，这样B会回显一个ICMP消息 unreachable

### Summary

ICMP知道网络层到最终主机和路由器的信息

ICMP介于网络层和传输层之间，一般划分在IP层中

通IP包封装ICMP数据

## End to End principle

![image-20210121082630800](CS144 Computer Network.assets/image-20210121082630800.png)

只有运输错误检测 没有存储，所以保证到达可以使用端对端，所以TCP也并不是完全可靠

**Why Doesn't the Network Help?**

- e.g.：压缩数据、Reformat/translate/improve requests、serve cached data、add security、migrate connections across the network
- end-to-end principle: function的正确完整实现只依赖于通信系统的end points

end-to-end check

- e.g. File Transfer: link layer的error detection只检测transmission错误，不检测error storage
- e.g. TCP小概率会出错（stack）、BitTorrent
- wireless link相比wire link功能复杂，可靠性低，所以在link layer重传，可提升TCP性能
- RFC1958: "strong" end to end: 不推荐在middle实现任何功能，比如在link layer重传，假定了reliabilty的提升值得latency的牺牲

## Error Detection: 3 schemes

## 



- detect errors的三个算法：checksums, CRC(cyclic redundancy checks), MAC(message authentication codes)

- 增补方式

  - append: ethernet CRC, TLS MAC
  - prepend: IP checksum

- Checksum (IP, TCP)

  - not very robust, 只能检1位错
  - fast and cheap even in software
  - IP, UDP, TCP use one's complement算法：16-bit word packet求和，进位加到底部，再取反码（特例：0xffff -> 0xffff，因为在TCP，checksum field为0意味着没有checksum）

- CRC: computes remainder of a polynomial (Ethernet)，见

  通信与网络笔记

  - 虽然more expensive，但支持硬件计算
  - 可对抗2 bits error、奇数error、小于c bits的突发错(burst)
  - 可incrementally计算
  - e.g. USB(CRC-16): [![\bf{M} = 0x8005 = x^{16}+x^{15}+x^2+1](https://camo.githubusercontent.com/5f31430afa7b86231396fc615c0f08ce692e87b4ac256f4778356f91a9ec22d6/68747470733a2f2f7777772e7a686968752e636f6d2f6571756174696f6e3f7465783d25354362662537424d253744253230253344253230307838303035253230253344253230782535452537423136253744253242782535452537423135253744253242782535453225324231)](https://camo.githubusercontent.com/5f31430afa7b86231396fc615c0f08ce692e87b4ac256f4778356f91a9ec22d6/68747470733a2f2f7777772e7a686968752e636f6d2f6571756174696f6e3f7465783d25354362662537424d253744253230253344253230307838303035253230253344253230782535452537423136253744253242782535452537423135253744253242782535453225324231) ，对于generator需要给左边pad 1

- MAC: message authentication code: cryptographic transformation of data(TLS)

  - robust to malicious modifications, but not errors
  - 检错能力有局限，受随机性影响，不如CRC，no error detection guarantee
  - [![c=MAC(M,s)](https://camo.githubusercontent.com/d470baf31520d3996ac99d59b47496354db00e91cb4b25fc0be797c722153d2d/68747470733a2f2f7777772e7a686968752e636f6d2f6571756174696f6e3f7465783d632533444d41432532384d25324373253239)](https://camo.githubusercontent.com/d470baf31520d3996ac99d59b47496354db00e91cb4b25fc0be797c722153d2d/68747470733a2f2f7777772e7a686968752e636f6d2f6571756174696f6e3f7465783d632533444d41432532384d25324373253239) ，M + c意味着对方有secret或者replay
  - 对于replay，`ctr++`, 具体见[我的密码学笔记](https://github.com/huangrt01/CS-Notes/blob/master/Notes/Output/Cryptography I%2C Stanford University%2C Coursera.md)的TLS部分

![image-20210121085428079](CS144 Computer Network.assets/image-20210121085428079.png)



所以最好的方法是三种方法组合使用

## Fnite state Machines

FSM example

![image-20210121090038456](CS144 Computer Network.assets/image-20210121090038456.png)

空闲 请求 请求挂起

![image-20210121090316469](CS144 Computer Network.assets/image-20210121090316469.png)

### Quiz

![image-20210121090501688](CS144 Computer Network.assets/image-20210121090501688.png)

FIN wait 1

## Flow control Stop and wait

![image-20210121091245009](CS144 Computer Network.assets/image-20210121091245009.png)

当发送和接受的速度不同时

所以是发出等待然后再发

![image-20210121110028399](CS144 Computer Network.assets/image-20210121110028399.png)

![image-20210121110106524](CS144 Computer Network.assets/image-20210121110106524.png)

![image-20210121110140314](CS144 Computer Network.assets/image-20210121110140314.png)

![image-20210122093013758](CS144 Computer Network.assets/image-20210122093013758.png)

### Sliding window

****![image-20210122093319664](CS144 Computer Network.assets/image-20210122093319664.png)

- Maintain 3 variables
  - Receive window size(RWS)
  - Last acceptable segment(LAS)
  - Last segment received(LSR)
- Maintain invariant: [![(LAS - LSR) \leq RWS](https://camo.githubusercontent.com/af506ff114907c731f2256f742d875b6c34e483ba22924fa85d9a67de2ebbbcc/68747470733a2f2f7777772e7a686968752e636f6d2f6571756174696f6e3f7465783d2532384c41532532302d2532304c53522532392532302535436c6571253230525753)](https://camo.githubusercontent.com/af506ff114907c731f2256f742d875b6c34e483ba22924fa85d9a67de2ebbbcc/68747470733a2f2f7777772e7a686968752e636f6d2f6571756174696f6e3f7465783d2532384c41532532302d2532304c53522532392532302535436c6571253230525753)
- 如果收到的packet比LAS小，则发送ack
  - 发送cumulative acks: 收到1, 2, 3, 5，发送3
  - TCP acks are next expected data，因此要加一，上个例子改为4，初值为0

**RWS, SWS, and Sequence Space**

- [![RWS \geq 1, SWS \geq 1, RWS \leq SWS](https://camo.githubusercontent.com/e1b5a0a0e37225649f31f50c4c96bd6dcff9194eb6c8c06af2a8b93573a0bb88/68747470733a2f2f7777772e7a686968752e636f6d2f6571756174696f6e3f7465783d52575325323025354367657125323031253243253230535753253230253543676571253230312532432532305257532532302535436c6571253230535753)](https://camo.githubusercontent.com/e1b5a0a0e37225649f31f50c4c96bd6dcff9194eb6c8c06af2a8b93573a0bb88/68747470733a2f2f7777772e7a686968752e636f6d2f6571756174696f6e3f7465783d52575325323025354367657125323031253243253230535753253230253543676571253230312532432532305257532532302535436c6571253230535753)
- if [![RWS = 1](https://camo.githubusercontent.com/2c09d0c2108d95bd2e2f0719b7d30291dd51706e659994b89ab031eb8cacaeee/68747470733a2f2f7777772e7a686968752e636f6d2f6571756174696f6e3f7465783d52575325323025334425323031)](https://camo.githubusercontent.com/2c09d0c2108d95bd2e2f0719b7d30291dd51706e659994b89ab031eb8cacaeee/68747470733a2f2f7777772e7a686968752e636f6d2f6571756174696f6e3f7465783d52575325323025334425323031) , "go back N" protocol ,need SWS+1 sequence numbers (需要多重传)
- if [![RWS = SWS](https://camo.githubusercontent.com/cd03dba3e9cb1a88233af850130b7d7c56bd439f150a173b7dbfb03293c3184c/68747470733a2f2f7777772e7a686968752e636f6d2f6571756174696f6e3f7465783d525753253230253344253230535753)](https://camo.githubusercontent.com/cd03dba3e9cb1a88233af850130b7d7c56bd439f150a173b7dbfb03293c3184c/68747470733a2f2f7777772e7a686968752e636f6d2f6571756174696f6e3f7465783d525753253230253344253230535753) , need 2SWS sequence numbers
- 通常需要 [![RWS+SWS](https://camo.githubusercontent.com/9413e1ca410204f0e836ab6b600c7546891c34de77444bb318704e431083f99a/68747470733a2f2f7777772e7a686968752e636f6d2f6571756174696f6e3f7465783d525753253242535753)](https://camo.githubusercontent.com/9413e1ca410204f0e836ab6b600c7546891c34de77444bb318704e431083f99a/68747470733a2f2f7777772e7a686968752e636f6d2f6571756174696f6e3f7465783d525753253242535753) sequence numbers：考虑临界情况，RWS最左侧的ACK没有成功发送，重传后收到了RWS最右侧的ACK

**TCP Flow Control**

- Receiver advertises RWS using window field
- Sender can only send data up to LAR+SWS

- Maintain 3 variables
  - Receive window size(RWS)
  - Last acceptable segment(LAS)
  - Last segment received(LSR)
- Maintain invariant: [![(LAS - LSR) \leq RWS](https://camo.githubusercontent.com/af506ff114907c731f2256f742d875b6c34e483ba22924fa85d9a67de2ebbbcc/68747470733a2f2f7777772e7a686968752e636f6d2f6571756174696f6e3f7465783d2532384c41532532302d2532304c53522532392532302535436c6571253230525753)](https://camo.githubusercontent.com/af506ff114907c731f2256f742d875b6c34e483ba22924fa85d9a67de2ebbbcc/68747470733a2f2f7777772e7a686968752e636f6d2f6571756174696f6e3f7465783d2532384c41532532302d2532304c53522532392532302535436c6571253230525753)
- 如果收到的packet比LAS小，则发送ack
  - 发送cumulative acks: 收到1, 2, 3, 5，发送3
  - TCP acks are next expected data，因此要加一，上个例子改为4，初值为0

## 选择性重复协议

****

![image-20210122095515972](CS144 Computer Network.assets/image-20210122095515972.png)

![image-20210122095932398](CS144 Computer Network.assets/image-20210122095932398.png)

protocol可能的运转方式 (ARQ: automatic repeat request)

- Go-back-N: pessimistic，重传ack, ack+1, ack+2 ...
  - e.g. RWS=1的情形
- Selective repeat: optimistic，重传ack, last_sent, last_sent+1, ...
  - e.g. RWS=SWS=N的情形
  - 对burst of losses效果不好

## TCP Header

![](CS144 Computer Network.assets/image-20210122100103141.png)

- pseudo header：类似2-2，checksum的计算囊括了IP header

- ack: 如果是bi-directional，也携带data信息；如果是uni-directional，好像不携带

- URG: urgent, PSH: push

- ACK: 除了第一个packet SYN，其它seg的ACK都置换为1

- RST: reset the connection

- urgent pointer：和URG联系，指出哪里urgent

  ## TCP Setup and Teardown

  

4次挥手

![image-20210122101648416](CS144 Computer Network.assets/image-20210122101648416.png)

![image-20210122102030039](CS144 Computer Network.assets/image-20210122102030039.png)

![image-20210122102340327](CS144 Computer Network.assets/image-20210122102340327.png)

## Transport Layer

**![image-20210122102946611](CS144 Computer Network.assets/image-20210122102946611.png)**



