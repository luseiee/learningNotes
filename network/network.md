Title         : Computer Network (Fifth Version)

Author        : Lu, Phil

Sub Title   : Andrew S.Tanenbaum


[TITLE]

# 引言

## 课后习题

> (1) Imagine that you have trained your St. Bernard, Bernie, to carry a box of three 8mm tapes instead of a flask of brandy. (When your disk fills up, you consider that an emergency.) These tapes each contain 7 gigabytes. The dog can travel to your side, wherever you may be, at 18 km/hour. For what range of distances does Bernie have a higher data rate than a transmission line whose data rate (excluding overhead) is 150 Mbps?

Sol. 

`7 * 1024 * 8 * 3 / (d / 5) = 150`  
`d = 5734.4m`

Wrong!

`1 kbps = 1000 bit/s`  
1024 should be 1000  
`d = 5600m`  


> (2) An alternative to a LAN is simply a big timesharing system with terminals for all users. Give two advantages of a client-server system using a LAN.

Sol.

(1) 可以更好地利用网络资源，timesharing system容易造成资源浪费  
(2) 构建简单，客户机和服务机上各运行一个进程即可


> (3) The performance of a client-server system is influenced by two network factors: the bandwidth of the network (how many bits/sec it can transport) and the latency (how many seconds it takes for the first bit to get from the client to the server). Give an example of a network that exhibits high bandwidth and high latency. Then give an example of one with low bandwidth and low latency.

Sol.

(1). 下载大型文件，建立连接需要很久，一旦建立下载很快  
(2). 语音通话，不能有高延迟

A transcontinental fiber link might have many gigabits/sec of bandwidth, but the latency will also be high due to the speed of light propagation over thousands of kilometers. In contrast, a 56-kbps modem calling a computer in the same building has low bandwidth and low latency.

> (4) Besides bandwidth and latency, what other parameter is needed to give a good characterization of the quality of service offered by a network used for digitized voice traffic?

Sol.

(1) 丢包率  
(2) 安全性  
(3) 断点传输  
(4) 对语音通话而言，统一的传输时间也很重要  

> (5) A factor in the delay of a store-and-forward packet-switching system is how long it takes to store and forward a packet through a switch. If switching time is 10 μsec, is this likely to be a major factor in the response of a client-server system where the client is in New York and the server is in California? Assume the propagation speed in copper and fiber to be 2/3 the speed of light in vacuum.

Sol.

`2000km / 200000km/s = 10ms`

It won't be a major factor.

> (6) A client-server system uses a satellite network, with the satellite at a height of 40,000 km. What is the best-case delay in response to a request?

Sol.

`40,000 * 2 / 300000 = 267ms`

> (7) In the future, when everyone has a home terminal connected to a computer network, instant public referendums on important pending legislation will become possible. Ultimately, existing legislatures
could be eliminated, to let the will of the people be expressed directly. The positive aspects of such a
direct democracy are fairly obvious; discuss some of the negative aspects.

Sol.

安全性存在问题

> (8) A collection of five routers is to be connected in a point-to-point subnet. Between each pair of routers,
the designers may put a high-speed line, a medium-speed line, a low-speed line, or no line. If it takes 100 ms of computer time to generate and inspect each topology, how long will it take to inspect all of them?

Sol.

`4 ^ (4 + 3 + 2 + 1) * 100ms = more than one day`

> (9) A disadvantage of a broadcast subnet is the capacity wasted when multiple hosts attempt to access the channel at the same time. As a simplistic example, suppose that time is divided into discrete slots, with each of the n hosts attempting to use the channel with probability p during each slot. What fraction of the slots are wasted due to collisions?

Sol.

`P = 1 - n * p * (1 - p) ^ (n - 1) - p ^ n`

> (10) What are two reasons for using layered protocols?

Sol.

(1) 使得层与层之间不会影响，一层内的协议更新不会使得整个网络连接发生变化  
(2) 把大的任务分细，明确各层提供的服务

> (11) The president of the Specialty Paint Corp. gets the idea to work with a local beer brewer to produce an
invisible beer can (as an anti-litter measure). The president tells her legal department to look into it, and they in turn ask engineering for help. As a result, the chief engineer calls his counterpart at the other company to discuss the technical aspects of the project. The engineers then report back to their respective legal departments, which then confer by telephone to arrange the legal aspects. Finally, the two corporate presidents discuss the financial side of the deal. Is this an example of a multilayer protocol in the sense of the OSI model?

Sol.

除了第一层（最底层，这里是engineer），高层之间不能有直接通信。

> (12)  What is the principal difference between connectionless communication and connection-oriented communication?

Sol.

面向连接的服务是先建立连接再通信。无连接服务是在传输时候带上目标地址，然后交由网络去通信。

> (13) Two networks each provide reliable connection-oriented service. One of them offers a reliable byte stream and the other offers a reliable message stream. Are these identical? If so, why is the distinction made? If not, give an example of how they differ.

Sol.

message的话每条信息有确定边界，而byte stream则没有确定边界。

> (14) What does ''negotiation'' mean when discussing network protocols? Give an example.

Sol.

协商就是建立一个双方接受的通信规则。

> (15) Which of the OSI layers handles each of the following:
a. (a) Dividing the transmitted bit stream into frames.
b. (b) Determining which route through the subnet to use.

Sol.

Transmission Layer and Network Layer

Wrong!

Data link layer and Network layer

这里很重要，数据是在data link层被划分为帧（frame）的

> (16) If the unit exchanged at the data link level is called a frame and the unit exchanged at the network level
is called a packet, do frames encapsulate packets or do packets encapsulate frames? Explain your
answer.

Sol.

高层的应该被封到低层里去。

> (17) A system has an n-layer protocol hierarchy. Applications generate messages of length M bytes. At each
of the layers, an h-byte header is added. What fraction of the network bandwidth is filled with headers?

Sol.

`hn / (M + hn)`

> (18) List two ways in which the OSI reference model and the TCP/IP reference model are the same. Now list
two ways in which they differ.

Sol.

OSI:  
Application       
Representation    
Session           
Transmission        
Network           
Data link         
Physical          

TCP/IP:  
Application: HTTP, SMTP, RTP, DNS  
Transmission: TCP, UDP  
internet: IP (Internet Protocal), ICMP  
Link: DSL, SONET, 802.11, Ethernet  

> (19) What is the main difference between TCP and UDP?

Sol.

TCP is connection oriented, reliable, fast.  
UDP is connectionless oriented, unreliable, slow.  

> (20) When a file is transferred between two computers, two acknowledgement strategies are possible. In the first one, the file is chopped up into packets, which are individually acknowledged by the receiver, but the file transfer as a whole is not acknowledged. In the second one, the packets are not acknowledged
individually, but the entire file is acknowledged when it arrives. Discuss these two approaches.

Sol.

If the network is reliable, use the second one.

> (21) How long was a bit on the original 802.3 standard in meters? Use a transmission speed of 10 Mbps and
assume the propagation speed in coax is 2/3 the speed of light in vacuum.

Sol.

802.3是以太网，这里计算出来是20米

> (22) An image is 1024 x 768 pixels with 3 bytes/pixel. Assume the image is uncompressed. How long does it
take to transmit it over a 56-kbps modem channel? Over a 1-Mbps cable modem? Over a 10-Mbps Ethernet? Over 100-Mbps Ethernet?

Sol.

337s, 19s, 1.9s, 0.19s

> (23) Ethernet and wireless networks have some similarities and some differences. One property of Ethernet is that only one frame at a time can be transmitted on an Ethernet. Does 802.11 share this property with Ethernet? Discuss your answer.

Sol.

Wireless networks also transmit one frame at a time, but determining when one can send is more difficult. Ethernet is a broadcast bus so the sender can just listen to see if there is any traffic before sending. Due to range issues with wireless, a sender cannot be sure that there are not other transmissions just because it cannot "hear" other transmissions. Wireless senders use either a central base station or use methods discussed in Chapter 4 to avoid collisions.

> (24) Wireless networks are easy to install, which makes them inexpensive since installation costs usually far overshadow equipment costs. Nevertheless, they also have some disadvantages. Name two of them.

Sol.

无法控制范围，容易被人利用。任何人可以接收到传送中的包。  
此外，传输更慢。

> (25) List two advantages and two disadvantages of having international standards for network protocols.

Sol.

好处：统一的标准使得兼容性更好，成本降低。
坏处：不好的标准可能很难被淘汰，比如OSI比TCP／IP先进但没有被采用。

# 物理层

## 笔记

### 知识点

- 通信介质：双绞线，同轴电缆，电力线（电力线上可以传数据），光纤

- 调制与多路复用：基带传输，同带传输，时分复用，频分复用，码分复用（数学上分离不同的码）

- 有关下行和上行：下行是下载，上行是上传，一般下行带宽会比较大

### 公共电话交换网络

- 电话网络：本地回路接到端局 - 中继线接到长途局 - 长途局之间用超高带宽中继线连接

- 奈奎斯特定律告诉我们带宽有多大，采样频率最高只能是它的两倍，换句话说，3000hz带宽，最多传输6000个符号，至于一个符号代表
多少信息量就和编码方式有关了，传递信息的上限是和信噪比有关的。

- 用电话网络的时候最大的限制在本地回路上

- 计算机的带宽和通信的带宽意义是不同的，一个是bps，还有一个是hz

### 移动电话系统

- 蜂窝状的所以是蜂窝移动网络 cell phone就是这么来的

- 基站传输，所以和有线电话不是一个系统

### 有线电视

- 电话公司和有线电视公司都提供internet接入服务，看你选择哪一个了。怪不得宽带上网一般是电话公司提供的服务。

- 用户接入Internet是先接到ISP上去的。

# 数据链路层

## 笔记

- 一个很主要的工作是把数据包封装成帧，成帧有很多算法，比如怎么确定头尾之类的

- 差错控制，接收确认帧

- 汉明码这类知识也在这一层中

- 后面又讲了一些协议，其实就是一些伪代码，讲两台主机的数据链路层的进程应该要做哪些事情

- 滑动窗口协议是为了在两个方向都实现传输。
这里主要讲的是捎带确认的思想（将接收方返回的确认信息中搭载要传送的数据帧）  
这里又会有很多算法，比如，怎么样效率最高拉，网络层不发数据来，那我确认信息就一直攥在手里不发了吗？然后设计了种种算法使得效率最高。

# 介质访问控制子层

## 笔记

### 要解决的问题

- 这一层还是数据链路层的一部分，主要解决的问题是什么呢？信道分配问题！就是有多台主机要使用一个信道的时候，会有冲突，这个时候应该怎么办呢？这里有一个疑惑，物理层的时候讲的频分复用之类的不就是信道多用吗？和这里有什么区别。

- 我觉得这里应该这样看，物理层是使得信道利用率高，是从物理层上看的。比如它使得一条双绞线可以三台机器同时传输数据。那么这里应该看成三条信道了。在数据链路上，就又把其中一条来看成单一信道来继续进行探讨了。

### 多路访问协议

- 这些讲的都是MAC协议，MAC：Medium Access Control

- 算法是一步步优化的。首先，一条信道，n个主机，都可以任意传送，冲突就重发。（ALOHA）接着，把时间分成一段段（分槽ALOHA）。再加上监听，就是知道信道上有没有信号在传（CSMA）。那么这里面一旦有空了谁先传？先到先得？还是有什么协议（其中一种有令牌传递，拿到令牌的才能传）

- 无线局域网（802.11）遇到的问题就是，很难监听信道有没有冲突，因此有自己的一套协议。

### 以太网 802.3

#### 经典以太网

经典以太网以同轴电缆连接，没有交换机，MAC子层协议规定了帧的格式：

前导码－目标地址（6 Byte）－源地址（6 Byte）－类型－数据－填充－校验和

目标地址第一位为1，则表示那是一个组地址，称为组播，反之为单播

MAC地址：前三个字节代表网络设备制造商，后三个是该制造商的设备。

经典以太网采用1-坚持CSMA算法

#### 交换式以太网

> 交换机和集线器的区别：

>（1）从OSI体系结构来看，集线器属于OSI的第一层物理层设备，交换机属于OSI的第二层数据链路层设备。
    集线器只是对数据的传输起到同步、放大和整形的作用，对数据传输中的短帧、碎片等无法有效处理，不能保证数据传输的完整性和正确性；而交换机不但可以对数据的传输做到同步、放大和整形，而且可以过滤短帧、碎片等。

>（2）从工作方式来看，集线器是一种广播模式，也就是说集线器的某个端口工作的时候其他所有端口都有收听到信息，容易产生广播风暴。交换机工作的时候只有发出请求的端口和目的端口之间相互响应而不影响其他端口，那么交换机就能够隔离冲突域和有效地抑制广播风暴的产生。 

>（3）从带宽来看，集线器共享带宽，交换机独享带宽。
集线器不管有多少个端口，所有端口都共享一条带宽，在同一时刻只能有两个端口传送数据，其他端口只能等待；同时集线器只能工作在半双工模式下。而对于交换机而言，每个端口都有一条独占的带宽，当两个端口工作时并不影响其他端口的工作，同时交换机不但可以工作在半双工模式下也可以工作在全双工模式下。

- 随后 百兆以太网，千兆以太网，万兆以太网都出炉了，区别在于发送速率变快了许多

### 无线局域网 802.11

物理层和MAC子层的协议都和以太网有区别

此外，MAC地址是对于网卡而言的，无线网卡有一个MAC地址，有线网卡也有一个MAC地址

有一个不同于802.3以太网的服务是，802.11需要考虑AP的切换，就是俗称的换一个wifi，它需要考虑如何在切换AP的时候数据包不会丢失。

### 宽带无线WiMAX 802.16

"最后一英里"的无线，范围很大，和3G网络，802.11都有区别

### 蓝牙，RFID无线射频识别等等

也有物理层，MAC子层等等

### 网桥

网桥的功能是将多个局域网连接在一起，它和交换机关系很紧密，有时可以共通概念。

### 交换设备总结

- 物理层：中继器，集线器

- 数据链路层：交换机，网桥

- 网络层：路由器：路由器剥掉数据链路层的帧头和帧尾（因此路由器不知道数据是哪个mac地址发过来的）然后用ip地址去转发它

- 传输层：传输网关

- 应用层：应用网关

### VLAN虚拟局域网

就是物理上处于同一个LAN的主机，可以使用交换机来让他们看起来是属于不同的LAN的，这个技术就是VLAN

比如一个公司，财务部门和IT部门需要分成VLAN，因为财务部门的一些内部服务不能让其他部门access

这个工作由交换机或者网桥完成，是属于数据链路层的，所以和IP无关，是将MAC分组？

# 网络层

## 笔记

### 网络层

- 网络层协议运行的环境：两台主机需要进行数据交换，路径上有许多的路由器，其中有些路由器在ISP设备上，有些在LAN上，但是在路由算法看来这些都是一样的

- 网络层的两种服务方式：1.无连接服务，带上目标地址，让路由器们自己找出最佳路径。2.有连接服务，一开始就在主机中间建立好路由路径，然后通信。

- 上面的两种协议：IP协议和MPLS协议。一种叫数据报网络（datagram network），一种叫虚电路网络（virtual-circuit network）。它们各有优劣。

### 路由算法

- 路由器两个功能：路由和转发。转发：拿到数据包，处理，根据路由表发到相应路由器。路由:生成路由表。

- 路由表：记录了哪个ip段应该发给哪个路由器（无连接），记录了带有某个标识的数据应该发到哪个路由器（有连接）

- 静态路由:即非自适应算法（nonadaptive algorithm)，路由选择在离线情况下计算好了。

- 动态路由，自适应算法，拓扑发生变化时，路由表也会发生变化。

- 随后介绍了许多路由算法，本质就是最短路径问题

- 层次路由：路由太多了，把路由分成区域再维护路由表

- 广播和组播：广播就是发给所有路由，组播是发给若干个接收者，这种时候一个个发很不好，所以也有特殊的算法。

- 选播路由：把包发给最近的一个组成员

- 移动主机路由：如果一个主机是移动的怎么办？这个主机要有个家乡代理，发送请求的（固定主机）发给移动主机的家乡代理，家乡代理处理数据包转发给移动主机，移动主机再直接回复发送者。这个转发的机制叫做隧道（tunneling）

- 自组织网络路由，就是连路由器都是移动的，路由器之间由无线通信

### 拥塞控制算法

- 当负载大于路由器和线路的能力的时候，就要有拥塞控制算法，可以流量感知，把流量拆分到多个路径。也可以准入控制，控制流量。路由器还可以往回传反馈给主机，这叫流量调节。最后可以负载脱落，就是丢弃数据包。

