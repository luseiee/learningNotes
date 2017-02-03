Title         : Computer Network (Fifth Version)

Author        : Lu, Phil

Sub Title   : Andrew S.Tanenbaum


[TITLE]

# 引言

## 笔记

- 应用层：HTTP, SMTP, RTP, DNS
- 传输层：TCP, UDP
- 互联网层：IP, ICMP
- 链路层：DSL, SONET, 802.11, Ethernet

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

- 路由器两个功能：路由和转发。转发：拿到数据包，处理，根据路由表发到相应路由器。路由:生成路由表。路由器一般有缓冲区，可以接受数据包后放在缓存区慢慢处理。

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

### 服务质量

- 不同的应用有不同的需求，典型的如视频电话：对延迟抖动要求极高，对丢失的要求很低

- Asynchronous Transfer Mode (ATM 网络) 支持恒定比特率，可变实时非实时，可变比特率等。

- 流量整形：不管接收速率，一直以同样的速率输出流量。两种算法，漏桶算法和令牌桶算法。

- 包调度算法：在同一个流的数据包之间以及在竞争流之间分配路由器资源的算法。就是数据包到了以后先处理谁的问题。

- QoS routing: 在路由层面满足用户的Qos(Quality of Service)需求。

### 网络互连

- 不同的网络之间数据包格式不同，我们应该怎么样去连接它们。用一个公共层来隐藏现有网络的差异。

- 举个例子，源端 - 通过802.11 - 路由器 - 通过MPLS（网络层）- 路由器 - 通过Ethernet - 目标端

- 过程会是这样的，都采用IP协议，通过802.11后，802.11头就被丢弃，然后查询路由表，建立MPLS虚电路，再封装数据包到达下一个地点，之后剥掉MPLS头，由于数据包太大，分成数份，再加上Ethernet头（当然也要加上IP头），再传输。

- 从这里可以看出路由和交换的区别，一个按网络地址转发，一个按MAC地址转发，互不相关。

- **隧道**:连接不同的网络协议，比如：主机1 - IPv6 - 路由器 - IPv4 - 路由器 - IPv6 - 主机2。可以这样做，在IPv4这里不动IPv6的数据包，把它整个封装在IPv4的头里面。这样就形成了一个隧道，数据无法从隧道中逃出。这也催生了VPN。这个叫ipv4overipv6

- **互联网路由**：在互联网中，由于是网络互联，因此每个网络中的路由算法不同，而且互相可能不透明。因此有一些术语要讨论，域内（introdomain）域间（interdomain），域间路由协议成为边界网关协议（BGP，border gateway protocal）。由于每个网络独立于其他网络运营，称为自治系统（AS，autonomous system）

- **数据包分段**，不同的链路会涉及不同数据包长度，因此可能会涉及到数据包分段问题。这里最关键的参数是MTU（Path maximum transmission unit），路径最大传输单元。有几种分段策略，如非透明分段，透明分段，路径MTU发现等等。

### Internet的网络层

Internet中的进程通信是这样的。传输层获得数据流，分段作为ip数据包发送。理论上数据包可以达到64KB，但是一般不超过1500字节，因为这是以太网一个帧的大小。IP路由器转发每个数据包直到目的地，接收方，网络层充足还原成最初的数据报，再将将数据交给传输层。

#### IPv4协议

- IPv4头：至少20字节，160位。包括，协议版本，IHL（头的长度），区分服务（一般不用），总长度（IPv4总长度），标识（让目标主机确定一个新到达的分段属于哪个数据报），空一位，DF位（要求路由器不能分段该数据报），MF位（告诉接收方这是不是分段后的最后一段），分段偏移量，生存期（以秒记，限制数据包的时间），协议（告诉网络层应该把它交给TCP还是UDP之类的），头校验位，**源地址**，**目标地址**，选项字段（一般不用）

#### IP地址

- 同一个网络上的主机一般具有连续的IP地址，甚至只有一个ip地址。

- IP地址分为网络位（前缀）和主机位，前缀长度一般用slash分割，或者使用子网掩码。前缀长度＝子网掩码1的个数。

- **为什么要使用层次化地址？**这样可以使得路由表远远小于按每个IP地址索引所需要的大小，通过分层方式使得路由器只要30万条前缀的路由就可以索引近10亿台主机。缺点是会浪费很多地址，给有些机构分配了大量空间但是用得很少。

- **一家公司获得ip的过程**： ICANN(Internet Corporation for Assigned Names and Number)将部分地址空间授权给各区域机构，这些机构再把IP地址发放给ISP和其他公司。

- **子网**：比如一个学校申请了`/16`的地址空间，随后电子系和艺术系需要使用ip，但是新申请两块不仅ip不连续而且还浪费。这个时候需要在内部再划分子网（子网在这本书前半部本的含义是所有路由和线路的集合）。因此可以这样，`/17`给电子系,`/18`给艺术系，剩下四分之一未分配。使用时，只要在学校的总路由器上设置一些表项。

- **CIDR无类域间路由**: ISP和骨干网络的路由表太长，利用路由聚合（route aggregation）为超网（supernet）。所以同一个ip地址，有的路由器把它当作`/22`看，有的则把它当`/20`看（聚合过了），这个设计称为CIDR（Classless Inter-Domain Routing）。就是意思说对一些总的路由器，没必要把ip路由得很细，比如从北京发往金山的，路由只要能路由到上海就行了。CIDR的匹配方式是用最长匹配前缀

- **分类和特殊寻址**: 
```
  A类：0xxxxxxx......(1Byte网络位) 1.0.0.0～127.255.255.255   128个网络，每个1600多万台主机
  B类：10xxxxxxxxxxxxxx....（2Byte网络位）128.0.0.0～191.255.255.255  16384个网络，65536台主机
  C类：110xxx...xxx....(3Byte网络位)  192.0.0.0～223.255.255.255.255  200万个网络，256台主机
  D类：1110xxxxxx...xxx(组播地址)    224.0.0.0～239.255.255.255
  E类：1111xxxx....xxxxx(保留地址)   240.0.0.0～255.255.255.255
  实际上如今这些类已经不再关心
```

- **NAT网络地址转换**: Network Address Translation，为了解决ip地址短缺问题。客户网络内部使用内部ip地址，公网为内部ip保留了三个ip段。
```
  10.0.0.0 ~ 10.255.255.255/8 (1600万个主机)
  172.16.0.0 ~ 172.31.255.255/12  (1048576个主机)
  192.168.0.0 ~ 192.168.255.255/16  (65536个主机)
```
数据包离开驻地时，首先要通过一个NAT盒子（集成到路由器或者adsl调制解调器），转换成真实ip地址。那么数据包返回的时候要如何确定发给哪个主机呢？现在的解决方法不是很好，它会修改上层协议（UDP或者TCP）的头以方便寻址。

#### IPv6

- IPv6的头是40字节，分别为版本，区分服务，流标签，有效载荷长度，下一个头，跳数限制，源地址，目标地址。

- 校验和字段被去掉了，因为计算校验和会极大降低性能。现在使用的大多是可靠网络，而且数据链路层和传输层通常有它们自己的校验和。

- IPv6也可以有扩展头

#### Internet 控制协议

网络层除了有用于数据传输的IP协议外还有好几个辅助控制协议。

- **ICMP(Internet Control Message Protocal)协议**: Internet控制消息协议。当路由器在处理一个数据包时发生了意外，可以通过ICMP向数据包的源端报告有关事件。

- **ARP(Address Resolution Protocal)地址解析协议**:这个协议是为了将IP地址映射到数据链路层的地址。方法是发送广播包到以太网请求目标地址IP的主机，然后每台主机都会检查，并且正确主机会去应答，同时双方都将结果缓存。如果目标不在同一个以太网，那么就会进行两次ARP广播，第一次广播会得到源端路由器的MAC地址，然后路由器转发到目标路由器后再进行一次ARP广播，获得目标主机的地址。注意ARP广播不能穿透局域网。这个协议本身属于数据链路层。

- **ARP代理**: 没看懂

- **DHCP - 动态主机配置协议**: 每个网络有一个DHCP服务器负责地址配置。计算机向DHCP请求IP地址。

#### 标签交换和MPLS(MultiProtocal Label Switching)

- MPLS在每个数据包前面加一个标签，路由器根据数据包标签而不是数据包目的地址实施转发。转发速度会非常快。

- MPLS属于2.5层协议，因为它必须在IP数据包的头前面再加上一个新的MPLS头。随后外面要再包上一层成帧协议的标签。所以MPLS可以用于整个网络传输中的一段。

#### OSPF - 内部网关路由协议

- 前面提到过Internet由大量的独立网络或自治系统构成，在自己的网络内部，可以使用自己的内部路由算法，叫域内路由算法(introdomain routing),也叫内部网关协议(interior gateway protocal)，OSPF是一个普遍实际使用的路由协议。这个路由协议定义了一些路由算法和实现方法。细节没看。

#### BGP - 外部网关路由协议

- AS之间，可以使用另一个协议，称为边界网管协议(Border Gateway Protocal)。是因为域间协议需要考虑政治方面的因素。例如，我这个AS不希望称为过路的，就是我希望发送数据包，我也希望接受数据包，但是我不要转发别人的数据包。实际中的例子有：教育网络不承载商业流量，五角大楼的流量不要经过伊拉克等等等等。

- 一个很简单的例子，ABCD四个AS互联，ABC都是D的客户，那么A发往C可以通过D来中转，只要它们告诉D它们的一些目标主机的IP地址。这个叫做中转流量。有一天A和C发现我们可以直接互相传输，它们于是互相通报了自己的一些目标主机，然后A和B也这么干了，但是A不会把B的目标主机告诉C，因为这样就要做中转服务啦。这种叫做对等（peering）传输。


#### Internet组播

- IP用D类IP地址支持一对多的通信。本地组播地址的例子有：
```
  224.0.0.1  LAN上的全部系统
  ...
```

- 有一个协议叫Internet组管理协议(IGMP, Internet Group Management Protocal),用来确定哪些主机属于哪些组。

#### 移动IP

- 首先，做法和之前很像。移动主机在外地获得一个外地网点的新IP地址（转交地址），移动主机通过转交地址告诉家乡代理自己在哪里。然后家乡代理将发给自己的数据包全部通过隧道发给移动主机。

- 之后讲了一些细节，没有仔细看

## 课后习题

> (1) Give two example computer applications for which connection-oriented service is appropriate. Now give two examples for which connectionless service is best.

Sol.

面向连接服务：SSH，文件传输

无连接服务：视频通话，游戏在线对战，需要快速应答的服务一般需要无连接服务。

> (2) Are there any circumstances when connection-oriented service will (or at least should) deliver packets out of order? Explain.

Sol. 

接收端将无法正确接收数据，比如视频传输，顺序一错视频就乱了。

Wrong!

Circumstance是情况的意思，在terminal中ctrl-c应该被最先传送，而不是排在队尾。

> (3) Datagram subnets route each packet as a separate unit, independent of all others. Virtual-circuit subnets do not have to do this, since each data packet follows a predetermined route. Does this observation mean that virtual-circuit subnets do not need the capability to route isolated packets from an arbitrary source to an arbitrary destination? Explain your answer.

Sol.

并不是如此，虚电路网络对不同方向的数据包需要建立不同的虚电路，因此也要具备这样的能力。

补充：在建立虚电路的时候需要把setup package从任意端传输到任意接收方。

> (4) Give three examples of protocol parameters that might be negotiated when a connection is set up.

Sol.

IP协议，协商IP包的最大跳数，是否可以分段，还有出错时的处理方式。

> (5) Consider the following design problem concerning implementation of virtual-circuit service. If virtual circuits are used internal to the subnet, each data packet must have a 3-byte header and each router must tie up 8 bytes of storage for circuit identification. If datagrams are used internally, 15-byte headers are needed but no router table space is required. Transmission capacity costs 1 cent per 106 bytes, per hop. Very fast router memory can be purchased for 1 cent per byte and is depreciated over two years, assuming a 40-hour business week. The statistically average session runs for 1000 sec, in which time 200 packets are transmitted. The mean packet requires four hops. Which implementation is cheaper, and by how much?

Sol.

Virtual Circuits: `200 * 3 * 4 / 10 ^ 6 + 1000 * 8 * 5 / 2 / 52 / 40 / 3600`
Datagrams: `15 * 4 * 200 / 10 ^ 6`

> (6) Assuming that all routers and hosts are working properly and that all software in both is free of all errors, is there any chance, however small, that a packet will be delivered to the wrong destination?

Sol.

有可能，当有ip冲突或者传输过程中发生ip地址变更的情况。

Wrong!

答案是错误可能出在低层上，比如物理层

> (7) Give a simple heuristic for finding two paths through a network from a given source to a given destination that can survive the loss of any communication line (assuming two such paths exist). The routers are considered reliable enough, so it is not necessary to worry about the possibility of router crashes.

Sol.

先找出一条最短路径，再把这条路径删除，找出另一条最短路径。只要两条路径没有公共部分即可。

> (8) Consider the subnet of Fig.5-12(a). Distance vector routing is used, and the following vectors have just come in to router C: from B: (5, 0, 8, 12, 6, 2); from D: (16, 12, 6, 0, 9, 10); and from E: (7, 6, 3, 9, 0, 4). The measured delays to B, D, and E, are 6, 3, and 5, respectively. What is C's new routing table? Give both the outgoing line to use and the expected delay.

Sol.

这题是距离矢量算法。

```
  C 到 A 11 经过 B
  A 11 B
  B 6  B
  C 0  -
  D 3  D
  E 5  E
  F 8  B
```

> (9) If delays are recorded as 8-bit numbers in a 50-router network, and delay vectors are exchanged twice a second, how much bandwidth per (full-duplex) line is chewed up by the distributed routing algorithm? Assume that each router has three lines to other routers.

Sol.

每个路由器需要维护一张400bit的表，因此传输0.5s一次会浪费单个方向800bps的带宽

> (10) In Fig. 5-14 the Boolean OR of the two sets of ACF bits are 111 in every row. Is this just an accident here, or does it hold for all subnets under all circumstances?

Sol.

这题讲的是链路状态路由算法。

这个永远是对的，ACK标志标志表示来自哪里，它可能由两条路线过来，而发送标志表示要发送往哪里。

> (11) For hierarchical routing with 4800 routers, what region and cluster sizes should be chosen to minimize the size of the routing table for a three-layer hierarchy? A good starting place is the hypothesis that a solution with k clusters of k regions of k routers is close to optimal, which means that k is about the cube root of 4800 (around 16). Use trial and error to check out combinations where all three parameters are in the general vicinity of 16.

Sol.

这题讲的是层次路由。

层次可以分许多层，和网络中路由器的数量规模有关。

16 15 20

> (12) In the text it was stated that when a mobile host is not at home, packets sent to its home LAN are intercepted by its home agent on that LAN. For an IP network on an 802.3 LAN, how does the home agent accomplish this interception?

Sol.

家乡代理拥有主机的IP地址即可截获，有什么问题吗？

Conceivably it might go into promiscuous mode, reading all frames dropped onto the LAN, but this is very inefficient. Instead, what is normally done is that the home agent tricks the router into thinking it is the mobile host by re- sponding to ARP requests. When the router gets an IP packet destined for the mobile host, it broadcasts an ARP query asking for the 802.3 MAC-level ad- dress of the machine with that IP address. When the mobile host is not around, the home agent responds to the ARP, so the router associates the mobile user’s IP address with the home agent’s 802.3 MAC-level address.

上面是标准答案，实际上就是在ARP广播时相应家乡代理自己的MAC地址，实际上就是拥有了主机的IP地址嘛。

> (13) Looking at the subnet of Fig. 5-6, how many packets are generated by a broadcast from B, using a. (a)reverse path forwarding? b. (b)the sink tree?

Sol.

reverse path forwarding，路由器接收到广播包时，检查是否是自己给广播源发包的路径，是的话说明是从最优路径发过来的，这时给所有其他节点发包，最后算下来发了21次

sink tree是汇集树，是由B到所有节点最短路径的集合，这样发的话发14个包，每个树枝必会到一个节点，而且不会重复。

> (14)  Suppose that node B in Fig. 5-20 has just rebooted and has no routing information in
its tables. It suddenly needs a route to H. It sends out broadcasts with TTL set to 1, 2,
3, and so on. How many rounds does it take to find a route?

Sol.

这题考查自组织网络路由，就是路由器本身也在移动的情况。TTL分别设置为1，2，3是为了使搜索半径不断增大。由于B和H距离为3，因此TTL设置为3的时候可以发现，因此3轮可以发现路由。

> (15) As a possible congestion control mechanism in a subnet using virtual circuits internally,
a router could refrain from acknowledging a received packet until (1) it knows its last transmission along the virtual circuit was received successfully and (2) it has a free buffer. For simplicity, assume that the routers use a stop-and-wait protocol and that each virtual circuit has one buffer dedicated to it for each direction of traffic. If it takes T sec to transmit a packet (data or acknowledgement) and there are n routers on the path, what is the rate at which packets are delivered to the destination host? Assume that transmission errors are rare and that the host-router connection is infinitely fast.

Sol.

讲的是拥塞控制，这个方法不好，需要前一个包完全确认了才能传输下一个包。

The protocol is terrible. Let time be slotted in units of T sec. In slot 1 the source router sends the first packet. At the start of slot 2, the second router has received the packet but cannot acknowledge it yet. At the start of slot 3, the third router has received the packet, but it cannot acknowledge it either, so all the routers behind it are still hanging. The first acknowledgement can only be sent when the destination host takes the packet from the destination router. Now the acknowledgement begins propagating back. It takes two full transits of the network, 2(n − 1)T sec, before the source router can send the second packet. Thus, the throughput is one packet every 2(n − 1)T sec.

> (17) Describe two major differences between the ECN and the RED method.

Sol.

这两种是拥塞控制算法。

ECN (Explicit Congestion Notification, 显式拥塞通知)，路由器在它转发的数据包上打上标记，发出信号，接收方注意到拥塞时，发送应答包的同时告知发送方，让发送方降低传送速率。

RED (Random Early Detection, 随机早期检测), 路由器维护一个运行队列长度的平均值，当超过阈值的时候就开始随机丢弃数据包，快速发送方发现丢包就开始降低发送速率。

主要区别是一个显式通知，一个隐式通知，一个是缓存区开始不够了才通知，另一个是提前预知。

> (18) An ATM network uses a token bucket scheme for traffic shaping. A new token is put into the bucket every 5 μsec. Each token is good for one cell, which contains 48 bytes of data. What is the maximum sustainable data rate?

Sol.

With a token every 5 μsec, 200,000 cells/sec can be sent. Each packet holds 48 data bytes or 384 bits. The net data rate is then 76.8 Mbps.

> (19) A computer on a 6-Mbps network is regulated by a token bucket. The token bucket is filled at a rate of 1 Mbps. It is initially filled to capacity with 8 megabits. How long can the computer transmit at the full 6 Mbps?

Sol.

8 / (6 - 1) = 1.6s

> (21) The CPU in a router can process 2 million packets/sec. The load offered to it is 1.5 million packets/sec. If a route from source to destination contains 10 routers, how much time is spent being queued and serviced by the CPUs?

Sol.

这题用到排队论，服务速率为2，到达速率为1.5，那么服务时间为 1／2million / (1 - 1.5 / 2) = 2us。 10个routers就是20us.

> (22) Consider the user of differentiated services with expedited forwarding. Is there a guarantee that expedited packets experience a shorter delay than regular packets? Why or why not?

Sol.

不保证，过多包被标记为加速的，那么可能反而变慢了。

> (23) Suppose that host A is connected to a router R 1, R 1 is connected to another router, R 2, and R 2 is connected to host B. Suppose that a TCP message that contains 900 bytes of data and 20 bytes of TCP header is passed to the IP code at host A for delivery to B. Show the Total length, Identification, DF, MF, and Fragment offset fields of the IP header in each packet transmitted over the three links. Assume that link A-R1 can support a maximum frame size of 1024 bytes including a 14-byte frame header, link R1-R2 can support a maximum frame size of 512 bytes, including an 8-byte frame header, and link R2-B can support a maximum frame size of 512 bytes including a 12- byte frame header.

Sol.

```
Link A-R1 :
Length: 900 + 20 (TCP) + 20 (IP) = 940 Bytes, ID:X , DF:0 , MF:0 , Fragment offset:0
Link R1-R2:
(1) Length = 500; ID = x; DF = 0; MF = 1; Offset = 0 (2) Length = 460; ID = x; DF = 0; MF = 0; Offset = 60
Link R2-B:
(1) Length = 500; ID = x; DF = 0; MF = 1; Offset = 0 (2) Length = 460; ID = x; DF = 0; MF = 0; Offset = 60
不用去考虑数据链路层的成帧部分，IP协议不关心。
```

> (24) A router is blasting out IP packets whose total length (data plus header) is 1024 bytes. Assuming that packets live for 10 sec, what is the maximum line speed the router can operate at without danger of cycling through the IP datagram ID number space?

Sol.

IP包的ID字段拥有16位，因此65536个不同编号

65536 ＊ 1024 * 8 / 10 = 54 Gbps

> (25)  An IP datagram using the Strict source routing option has to be fragmented. Do you think the option is copied into each fragment, or is it sufficient to just put it in the first fragment? Explain your answer.

Sol.

Strict Source Routing 严格源路由，是IPv4头的可选项，表明该包必须经过指定路由。

必须要在每个fragment都要包括。

> (26) Suppose that instead of using 16 bits for the network part of a class B address originally, 20 bits had been used. How many class B networks would there have been?

Sol.

B类地址，前缀10定死，因此18bits可以用，所以有2^18个B类网络。

> (28) A network on the Internet has a subnet mask of 255.255.240.0. What is the maximum number of hosts it can handle?

Sol.

4096

> (29) 为什么以太网地址不能特定于一个网络，而IP地址却可以？

Sol.

Each Ethernet adapter sold in stores comes hardwired with an Ethernet (MAC) address in it. When burning the address into the card, the manufac- turer has no idea where in the world the card will be used, making the address useless for routing. In contrast, IP addresses are either assigned either stati- cally or dynamically by an ISP or company, which knows exactly how to get to the host getting the IP address.

> (30) A large number of consecutive IP address are available starting at 198.16.0.0. Suppose that four organizations, A, B, C, and D, request 4000, 2000, 4000, and 8000 addresses, respectively, and in that order. For each of these, give the first IP address assigned, the last IP address assigned, and the mask in the w.x.y.z/s notation.

Sol. 
```
A: 198.16.0.0 – 198.16.15.255 written as 198.16.0.0/20 
B: 198.16.16.0 – 198.23.15.255 written as 198.16.16.0/21 
C: 198.16.32.0 – 198.47.15.255 written as 198.16.32.0/20 
D: 198.16.64.0 – 198.95.15.255 written as 198.16.64.0/19
```

> (31) A router has just received the following new IP addresses: 57.6.96.0/21, 57.6.104.0/21, 57.6.112.0/21, and 57.6.120.0/21. If all of them use the same outgoing line, can they be aggregated? If so, to what? If not, why not?

Sol.

可以聚合成57.6.96.0/19, 这个时候会有57.6.120.0/21没有被聚合，但是有最大匹配原则所以不要紧。

> (32)  The set of IP addresses from 29.18.0.0 to 19.18.128.255 has been aggregated to 29.18.0.0/17. However, there is a gap of 1024 unassigned addresses from 29.18.60.0 to 29.18.63.255 that are now suddenly assigned to a host using a different outgoing
line. Is it now necessary to split up the aggregate address into its constituent blocks, add the new block to the table, and then see if any reaggregation is possible? If not, what can be done instead?

Sol.

不需要，因为有最长匹配，所以单独聚合即可。

> (34) Many companies have a policy of having two (or more) routers connecting the company to the Internet to provide some redundancy in case one of them goes down. Is this policy still possible with NAT? Explain your answer.

Sol.

After NAT is installed, it is crucial that all the packets pertaining to a single connection pass in and out of the company via the same router, since that is where the mapping is kept. If each router has its own IP address and all traffic belonging to a given connection can be sent to the same router, the mapping can be done correctly and multihoming with NAT can be made to work.

所以是可以的，只要网络中的每个主机发给特定router即可。

> (36) Describe a way to reassemble IP fragments at the destination.

Sol.

In the general case, the problem is nontrivial. Fragments may arrive out of order and some may be missing. On a retransmission, the datagram may be fragmented in different-sized chunks. Furthermore, the total size is not known until the last fragment arrives. Probably the only way to handle reassembly is to buffer all the pieces until the last fragment arrives and the size is known. Then build a buffer of the right size, and put the fragments into the buffer, maintaining a bit map with 1 bit per 8 bytes to keep track of which bytes are present in the buffer. When all the bits in the bit map are 1, the datagram is complete.

所以就是等尾巴来，就可以确定总长度，然后等所有分段都来就可以重组了。

> (37) Most IP datagram reassembly algorithms have a timer to avoid having a lost fragment tie up reassembly buffers forever. Suppose that a datagram is fragmented into four fragments. The first three fragments arrive, but the last one is delayed. Eventually, the timer goes off and the three fragments in the receiver's memory are discarded. A little later, the last fragment stumbles in. What should be done with it?

Sol.

前三段已经被discard了，那么第四段再来会被当成新的，过一段时间一样被扔。

> (38)  In both IP and ATM, the checksum covers only the header and not the data. Why do you suppose this design was chosen?

Sol.

其他部分的checksum可以交给上层协议，而且开销太大，此外头的错误非常严重。

> (39)  A person who lives in Boston travels to Minneapolis, taking her portable computer with her. To her surprise, the LAN at her destination in Minneapolis is a wireless IP LAN, so she does not have to plug in. Is it still necessary to go through the entire business with home agents and foreign agents to make e-mail and other traffic arrive correctly?

Sol.

当然需要，无线网是数据链路层和物理层的事情，和IP层无关，还是要利用家乡代理。

> (41) The Protocol field used in the IPv4 header is not present in the fixed IPv6 header. Why not?

Sol.

因为在IPv6头中有一个字段叫下一个头，会说明该字段要交给哪一种上层协议处理。

> (42) When the IPv6 protocol is introduced, does the ARP protocol have to be changed? If so, are the changes conceptual or technical?

Sol.

不需要做任何改变，只是IP地址需要更长的空间而已。

# 传输层

## 传输服务

- 传输实体(transport entity)：在传输层内完成传输工作的硬件软件。它可以在操作系统内核，或在网络应用中，或以用户进程运行。

- 传输层和网络层服务相似，为什么需要传输层？因为用户对网络层没有真正的控制权。传输层的目标是在不可靠的网络上提供可靠的传输服务。

- 服务原语：socket（套接字）是一种服务原语。提供了诸如LISTEN，ACCEPT，CONNECT，SEND等原语。

- 传输层网络层数据链路层传输的数据分别称为段(segment)包(packet)帧(frame)

## 传输协议的组成

- 传输协议与数据链路协议非常相似。有以下几个要素。

- **Socket(套接字)**：这是一种接口（API），让程序员可以操纵传输层。

### 寻址

- 消息要发送给谁？术语叫TSAP(传输服务访问点，transport service access point)，实例是Port端口。相应的，网络层NSAP实例是IP地址。

- 第二个问题，消息发送端如何知道数据应该发往哪个Port？首先，一些常用服务被规定在固定端口上，比如smtp在25，ssh在22。第二，有一个特殊进程叫端口映射器，可以用服务名字来查找端口。

### 连接建立

- 建立连接没那么容易。比如用户与银行建立了连接，发送消息要转账，但是在网络中被延迟了。之后重发了信息，然而重发完后，原先的信息又到了，服务器无法知道这是重复请求，又转了一次账。

- 现在很好的一个解决办法是三次握手。

### 连接释放

- 连接释放也很困难。由于传输数据是双方的，因此连接释放需要双方各发送一次停止请求，最后会有四次挥手。

### 差错控制和流量控制

- 差错控制不用多说。流量控制是指接收方的buffer和处理速度有上限，发送方不能过快发送数据。

- 与数据链路层的区别。传输层是端到端的校验机制，而链路层只保护一条链路。比如说路由器内部出错，链路层是校验不出来的。只能靠传输层，所以链路层的校验并不是必不可少，但是它可以在小错误发生的时候处理得比较快。

### 拥塞控制

- 它与流量控制的区别。比如说水管往杯子倒水。流量控制是因为杯子太小，而拥塞控制则是因为水管太细。

- 拥塞控制涉及到带宽分配的效率和公平以及分配方式。

## UDP协议 (User Datagram Protocal) 用户数据报协议

- 采用UDP而不是原始IP的最主要价值是增加了源端口和目标端口。

- UDP头一共8字节64位：16位源端口，16位目标端口，16位UDP长度，16位UDP校验和。

- UDP没有流量控制，拥塞控制，重传机制。

- DNS是基于UDP的应用，因为它重传多少次都不会影响服务端。而且只需要传输一次，没必要建立连接。

### 远程过程调用RPC(应用层)

- 可以用于客户机-服务机之间的交互

### 实时传输协议RTP(Realtime Transport Protocol)

- 它是一个在应用层上实现的传输协议。

- RTP主要用于多媒体应用程序。基本功能是将几个实时数据流复用到一个UDP数据包流中。

- 数据包丢失的时候，接收方不会选择重传，而是交给应用程序来处理。如果是视频程序，可能会跳过该视频帧，如果是音频，可能会用插值法。

- RTCP协议，是RTP的控制协议，用来控制RTP的一些反馈信息，它不传送媒体数据，比如说控制有关延迟，缓冲，抖动，拥塞等等的信息

## TCP协议 (Transmission Control Protocol) Internet传输协议

### TCP概述

- TCP传输实体接受本地进程的用户数据流，将它们分割成不超过64KB(通常不超过1460字节，因为以太网帧的最大为1522字节)的分段。

- IP层不保证数据包一定倍正确的递交到接收方，也不指示数据报的发送速度有多快。正是TCP负责既要足够快地发送数据包，以便使用网络容量，但又不能引起网络拥塞；而且，TCP超时后，要重传。把数据报重新装配成正确的顺序也是TCP的人物。简而言之，TCP必须提供可靠性好的性能，这是IP层没有提供的。

### TCP服务模型

- TCP服务由发送端和接收端穿件套接字（socket）端点来获得。

- 一些知名端口：20，21:FTP，22:SSH，25:SMTP，80:HTTP，110:POP-3，143:IMAP，443:HTTPS，543:RTSP（媒体播放控制）。一般系统会有一个守护进程同时关注这些端口，然后把适当连接交给新的进程。

### TCP头

```
  一般为20Bytes
  源端口16位 目标端口16位
  序号SEQuence 32位
  确认号ACKnowledgement 32位
  TCP头长度4位 空4位 flag8位 窗口大小16位
  校验和16位 紧急指针16位
  选项
  数据(可选的，因为可以用来作为控制消息或者确认消息)
```
- SEQ表示的是字节开始的序号，注意每个字节都有一个序号
- ACK指定的是下一个期待的字节，因此三次握手的时候是用ACK＋1或者ACK＋N取决于数据的长度
- 头长度是*32位
- flag
- ACK:表示是否有ACK
- PSH:要求立刻发送不要缓冲
- RST:报错
- SYN:建立连接用
- FIN:释放连接
- 窗口大小表示对方可以发送多少字节过来,注意窗口大小虽然16位，但是尺度可以双方协商！！！
- 选项里面可以放时间戳等等

### TCP连接建立，三次握手

- 主机1: SYN(SEQ=x)
- 主机2: SYN(SEQ=y, ACK=x+1)
- 主机1: (SEQ=x+1, ACK=y+1)
- 主机2: (ACK=x+2, SEQ=y+1) 这步已经在通信了，上面是三次握手

### TCP连接释放，四次挥手

- 主机1: FIN(SEQ=x+2, ACQ=y+1)
- 主机2: (ACK=x+3)
- 主机2: FIN(SEQ=y+1)
- 主机1: (ACK=y+2)

### TCP连接管理模型

- TCP连接管理可以用有限状态机表示共有11种状态

### TCP滑动窗口

- 最重要的一点是，正确接收段的确认和接收端的缓冲区分配是分离的。因为确认接收了还要等应用程序去把它处理掉，所以两个不能同步的。

### TCP计时器管理

- 超时时间间隔应该多长，这对于802.11是非常困难的(因为确认到达时间的期望很分散)，因此也有很多算法

### TCP拥塞控制

- TCP维持一个拥塞窗口(congestion window),是发送端可以往网络发送的字节数

- 这里算法很多，不深究

## 性能问题

- TCP如何快速处理？

- 快速处理段技术，头压缩技术，长肥网络网络的协议

- 很多时候是CPU处理速度限制了网络速度

- 有一个指标叫带宽延迟乘积很影响实际网络速率。接收端的窗口必须至少比这个值大，才能不让延迟影响带宽。

## 延迟容忍网络DTN

- 在偶尔连接的网络中，可以把数据存储在某些节点，有链路时在工作。感觉没多大记的必要。和TCP,IP协议不一样。

## 课后习题

> (1) In our example transport primitives of Fig.6-2, LISTEN is a blocking call. Is this strictly necessary? If not, explain how a nonblocking primitive could be used. What advantage would this have over the scheme described in the text?

Sol.

The LISTEN call could indicate a willingness to establish new connections but not block. When an attempt to connect was made, the caller could be given a signal. It would then execute, say, OK or REJECT to accept or reject the con- nection. In our original scheme, this flexibility is lacking.

> (2) 像bittorrent这种点对点应用如何区分哪个是connect哪个listen呢？

Sol.

可以竞争，也可以随机，也可以由上层协议控制。

> (3) 假设网络层是百分百正确的那么三次握手协议会有什么样的变化？

Sol.

第三次握手就没有必要了，主机2收到主机1的请求时，直接就确立连接，返回给1确认信息后，1也确立连接。

> (7) Suppose that the clock-driven scheme for generating initial sequence numbers isused with a 15-bit wide clock counter. The clock ticks once every 100 msec, and the maximum packet lifetime is 60 sec. How often need resynchronization take place
a. (a)in the worst case?
b. (b)when the data consumes 240 sequence numbers/min?

Sol.

首先，现在的规定是这样的，通信的时候初始段的序号等于始终序号，因此在x秒的时候同步的信号序号为x，注意，建立连接之后，序号就和时间无关了！！！！

第二，在时间x时，不允许发送x+T(T是lifetime)序号的段，这是为什么呢？因为你这个段会生存T秒，而在随后的T秒内如果要建立一个连接，可能会和你现在发的这个段序号一样的懂吗？

(a) 题目是这样的，假设在70秒的时候，你建立了一个连接，这个时候你发出去的信号序号为70。注意，之后你要发送的序号是71，然后你一直忍着不发（这就是最坏的情况），然后时间绕了一圈回来了，时间变成了11秒，此时你再想发71，对不起，规则不允许，因为在11秒的时候，不允许发71。这就是最坏情况了，所以必须重新同步一次。答案是3276.8-60=3216.8

(b) 这个时候变成追及问题，最后计算出来结果是5361.3

总结，你发送速率与时钟速率越接近，需要同步的间隔就越长。但是如果一上来超过时钟速率就直接GG。

因为这种方法不好所以后来创造了三次握手，两边的初始序列号都是随机值，就不需要那么麻烦的时钟什么的啦。只要双方确认了，后面都好办。

> (9) Imagine that a two-way handshake rather than a three-way handshake were used to
set up connections. In other words, the third message was not required. Are deadlocks
now possible? Give an example or show that none exist.

Sol.

有可能出问题，主机2的确认被延迟了，那么可能会建立起一个重复的连接。

> (11) Consider the problem of recovering from host crashes (i.e.,Fig.6-18). If the interval
between writing and sending an acknowledgement, or vice versa, can be made relatively small, what are the two best sender-receiver strategies for minimizing the chance of a protocol failure?

Sol.

If the AW or WA time is small, the events AC(W) and WC(A) are unlikely events. The sender should retransmit in state S1; the receiver’s order does not matter.

> (13) Discuss the advantages and disadvantages of credits versus sliding window protocols.

Sol.

滑动窗口协议用于流量控制。

The sliding window is simpler, having only one set of parameters (the win- dow edges) to manage. Furthermore, the problem of a window being increased and then decreased, with the segments arriving in the wrong order, does not occur. However, the credit scheme is more flexible, allowing a dynamic management of the buffering, separate from the acknowledgements.

> (14) 拥塞控制的公平性方面的策略，加法递增乘法递减(AIMD).

> (15) Why does UDP exist? Would it not have been enough to just let user processes send
raw IP packets?

Sol.

无法确认端口。

> (17)  A client sends a 128-byte request to a server located 100 km away over a 1-gigabit optical fiber. What is the efficiency of the line during the remote procedure call?

Sol.

发送包需要`128*8/1G＝1.024us`, 在路上的时间100km/200000 = 50us, 然后一来一回100us，因此利用率约为1%。
所以说这个时候的制约不是带宽而是距离。

> (19) Both UDP and TCP use port numbers to identify the destination entity when delivering a message. Give two reasons for why these protocols invented a new abstract ID (port numbers), instead of using process IDs, which already existed when these protocols were designed.

Sol. 

进程id动态变化，不易管理，端口号可以被进程绑定，而且一些知名服务需要用固定端口号。

Here are three reasons. First, process IDs are OS-specific. Using process IDs would have made these protocols OS-dependent. Second, a single process may establish multiple channels of communications. A single process ID (per process) as the destination identifier cannot be used to distinguish between these channels. Third, having processes listen on well-known ports is easy, but well-known process IDs are impossible.

> (20) 何时选用基于UDP的RPC，合适使用基于TCP的RPC。

Sol.

RPC是远程过程调用，可以建立客户端－服务器应用。如果请求不是幂等的(幂等是如同计数器加一这种命令，执行次数不同会产生不同结果)，那就可以考虑使用UDP。同时，如果传递的数据包并不大，可以考虑使用UDP。

> (22) 最小TCP MTU的总长度是多少？包括TCP和IP的开销，但是不包括数据链路层的开销。

Sol.

MTU是最大传输单元，最小的TCP MTU可以设置，如果一台主机不设置的话默认是536+20=556字节的TCP段。Internet要求每台主机至少能够处理556字节的段。

> (23) RTP is used to transmit CD-quality audio, which makes a pair of 16-bit samples 44,100 times/sec, one sample for each of the stereo channels. How many packets per second must RTP transmit?

Sol.

Each sample occupies 4 bytes. This gives a total of 256 samples per packet. There are 44,100 samples/sec, so with 256 samples/packet, it takes 44100/256 or 172 packets to transmit one second’s worth of music.

按照标准答案的理解，RTP的一个packet只能传输1024字节，不清楚这个规定是在哪里。

> (25) Would it be possible to place the RTP code in the operating system kernel, along with the UDP code? Explain your answer.

Sol.

应该要分开，RTP是基于UDP的协议，其他应用程序也要调用UDP，因此最好可以把两段代码分开。

错了！

Sure. The caller would have to provide all the needed information, but there is no reason RTP could not be in the kernel, just as UDP is.

> (26) 主机1的端口p和主机2的端口q之间可能存在多个TCP连接吗？

Sol.

不可能，一对端口之间只能有一个TCP连接。一个进程可以有多个TCP连接。

> (27) ACK标志位有什么用？

Sol.

ACK标志位用来表示ACK字段是否有意义。其实在连接已经建立起来之后ACK标志位已经没有意义了，因为ACK是必须的。而在连接建立的过程中，这是非常重要的。

> (28) 为什么TCP段的有效载荷是65495字节？

Sol.

因为TCP长度为16位标示，所以最多65535字节，然后去掉TCP头20字节，去掉IP头20字节。剩下65495字节。

> (30) Consider the effect of using slow start on a line with a 10-msec round-trip time and no congestion. The receive window is 24 KB and the maximum segment size is 2 KB. How
long does it take before the first full window can be sent?

Sol.

慢速启动是TCP协议中拥塞控制的一个算法，略看。The first bursts contain 2K, 4K, 8K, and 16K bytes, respectively. The next one is 24 KB and occurs after 40 msec.

> (31) Suppose that the TCP congestion window is set to 18 KB and a timeout occurs. How big
will the window be if the next four transmission bursts are all successful? Assume that
the maximum segment size is 1 KB.

Sol.

也是拥塞控制的算法，TCP维护一个拥塞窗口，略看。The next transmission will be 1 maximum segment size. Then 2, 4, and 8. So after four successes, it will be 8 KB.

> (33) A TCP machine is sending full windows of 65,535 bytes over a 1-Gbps channel that has
a 10-msec one-way delay. What is the maximum throughput achievable? What is the line efficiency?

Sol.

One window can be sent every 20 msec. This gives 50 windows/sec, for a maximum data rate of about 3.3 million bytes/sec. The line efficiency is then 26.4 Mbps/1000 Mbps or 2.6 percent.

因此有延迟的网络传输效率和窗口大小，延迟有很大关系。

> (34) What is the fastest line speed at which a host can blast out 1500-byte TCP payloads with a 120-sec maximum packet lifetime without having the sequence numbers wrap around? Take TCP, IP, and Ethernet overhead into consideration. Assume that Ethernet frames may be sent continuously.

Sol.

TCP中每个Byte会占用一个序号，而TCP的sequence number是32位的，所以可以每120s发送2^32Bytes信息，然而1500B信息需要1500+20+20+26(以太网)的段帧来发送因此需要的带宽为`2 ^ 32 * 8 * 1566 / 1500 / 120 = 299Mbps`。

The goal is to send 2^32 bytes in 120 sec or 35,791,394 payload bytes/sec. This is 23,860 1500-byte frames/sec. The TCP overhead is 20 bytes. The IP overhead is 20 bytes. The Ethernet overhead is 26 bytes. This means that for 1500 bytes of payload, 1566 bytes must be sent. If we are to send 23,860 frames of 1566 bytes every second, we need a line of 299 Mbps. With any- thing faster than this we run the risk of two different TCP segments having the same sequence number at the same time.

> (35) 为什么那么多人在为了ipv4的局限性做努力，而对TCP的局限性却没有人这样做。

Sol.

根本原因是IP协议运行在所有路由器上。

IP is a network level protocol while TCP is an end-to-end transport level protocol. Any change in the protocol specification of IP must be incorporated on all routers in the Internet. On the other hand, TCP can works fine as long as the two end points are running compatible versions. Thus, it is possible to have many different versions of TCP running at the same time on different hosts, but not this is not the case with IP.

> (36)  In a network that has a maximum TPDU size of 128 bytes, a maximum TPDU lifetime of 30 sec, and an 8-bit sequence number, what is the maximum data rate per connection?

Sol.

TPDU:Transport Protocol Data Unit 协议数据单元。

`2 ^ 8 * 128 * 8 / 30 = 8.7kbps`

> (37) Suppose that you are measuring the time to receive a TPDU. When an interrupt occurs,
you read out the system clock in milliseconds. When the TPDU is fully processed, you read out the clock again. You measure 0 msec 270,000 times and 1 msec 730,000 times. How long does it take to receive a TPDU?

Sol.

27次是0ms，73次是1ms，那么平均是730us。

> (38) A CPU executes instructions at the rate of 1000 MIPS. Data can be copied 64 bits at a time, with each word copied costing 10 instructions. If an coming packet has to be copied four times, can this system handle a 1-Gbps line? For simplicity, assume that all instructions, even those instructions that read or write memory, run at the full 1000- MIPS rate.

Sol.

`1000M * 64 /10 / 4 = 1.6 Gbps > 1Gbps 可以`.

> (41) For a 1-Gbps network operating over 4000 km, the delay is the limiting factor, not the bandwidth. Consider a MAN with the average source and destination 20 km apart. At what data rate does the round-trip delay due to the speed of light equal the transmission delay for a 1-KB packet?

Sol.

`20 * 2 / 200000 = 200us延迟
发送1KB要200us的话，带宽至少要1024 * 8 * 1 / 200u = 40 Mbps`

> (43) What is the bandwidth-delay product for a 50-Mbps channel on a geostationary satellite? If the packets are all 1500 bytes (including overhead), how big should the window be in packets?

Sol.

The round-trip delay is about 540 msec, so with a 50-Mbps channel the bandwidth-product delay is 27 megabits or 3,375,000 bytes. With packets of 1500 bytes, it takes 2250 packets to fill the pipe, so the window should be at least 2250 packets.

# 应用层

## DNS (Domain Name System) 域名系统

### DNS名字空间

- DNS采用层级管理系统。包括com, edu, gov, net, cn, jp等等都是顶级域名。这些域又划分成子域，子域又可以进一步划分。在叶子上的子域包含若干主机。域名是自底向上的，以dot分开。

- 域名不区分大小写

- 创建一个新域，只要活得上级域的许可即可。

### 域名资源记录

- 记录组成了DNS数据库，DNS的基本功能就是将域名映射到资源记录。

- 资源记录的格式如下
```
  Domain_name  Time_to_live  Class  Type  Value
  
  Domain name: 域名，不必多解释
  Time to live: 指出该记录的稳定程度，记录可能是从上级域名服务器上缓存下来的，并不一定保证最新。
  Type: 一般都是IN，指Internet
  Value: 是指记录的值
  
  一些重要的Type:
  SOA: 授权开始
  A: 最常用，对应主机的IPV4地址
  AAAA: IPV4地址
  MX: 邮件交换
  NS: 名字服务器
  CNAME: 规范名，也就是别名
```

- 一些例子:
```
  我的clog:
  clog.science.		600	IN	CNAME	clog.science.herokudns.com.
  clog.science.herokudns.com. 300	IN	A	54.225.223.184
  clog.science.herokudns.com. 300	IN	A	54.221.218.81
  ...共好多条
  哇，好多备用服务器，但是直接访问这个IP没有办法到我的网站
```

- 第二个例子:
```
  cs.vu.nl  86400 IN  SOA   star boss (9527,7200,7200,241 920, 86400)
  cs.vu.nl  86400 IN  MX    1 zephyr
  cs.vu.nl  86400 IN  MX    2 top
  cs.vu.nl  86400 IN  NS    star
  
  star      86400 IN  A     130.27.56.205
  zephyr    86400 IN  A     130.37.20.10
  top       86400 IN  A     130.37.20.11
  www       86400 IN  CNAME star.cs.vu.nl
  ftp       86400 IN  CNAME zephyr.cs.vu.nl
```

### 域名服务器

- 每个区域都有一个或多个域名服务器。当要访问的地址无法在本地域名服务器找到时，会被转发给根域名服务器，然后再层层转发。有迭代查询，和递归查询两种。

- 通过长距离查询到的结果会被缓存下来，下次查询就会快很多。

- DNS采用UDP协议

```
  dig www.baidu.com
  dig clog.science
  dig命令可以看到dns的返回值
```

## 电子邮件

### 服务概述

- 用户代理 － 邮件传送代理 － SMTP － 邮件传送代理 － 接收端用户代理

- **用户代理**是一个程序，其实就是我们平时用的邮箱

- **邮件传送代理**是我们的邮箱服务提供商，比如126

### 邮件格式

- 在最开始的时候，邮件只能由文本消息组成。现在的解决方案是**MIME**，即Multipurpose Internet Mail Extensions，多用途Internet邮件扩展。它被包含在邮件头中，告诉接受者应该怎么样读取内容。

- MIME也被用于Web中
- MIME包括
```
  text        plain,html,xml,css
  image       gif,jpeg,tiff
  audio       basic,mpeg,mp4
  video       mpeg,mp4,quicktime
  application pdf,javascript,zip
  message     http,rfc822
  等等
```

### 邮件传送

- 为了确定要联系的正确邮件服务器，必须先咨询DNS
- 发送方的邮件传输代理与目标邮件服务器IP地址的端口25建立一个TCP连接
- 基于SMTP(Simple Mail Transfer Protocol)
- 从最初的邮件传输代理与邮件传输代理一跳完成邮件的传输

### 最后传递

- 邮件到了用户传送代理了，比如126邮箱了，然后再怎么传递给用户代理呢？
- 现在的用户希望从多个终端可以访问到自己的邮件，这个时候需要两种协议
- IMAP(Internet Message Access Protocol)或更早的POP3(Post Office Protocol)

## 万维网

### 概述

#### HTTP协议(HyperText Transfer Protocol)

- 抓取网页所用的“请求-响应”协议是一个简单的基于文本协议，它运行在TCP之上。

#### 静态页面与动态页面。

- 静态页面每次显示的是相同的一个文档，如果每次显示的是程序按需产生的内容，或者页面本身包含了一个程序，则称该网页为动态网页。

#### URL

- 访问页面时需要知道页面的资源位置，Web的解决方案是使用URL,统一资源定位符(Uniform Resource Locator)。URL包含三个部分，协议，页面所在机器的DNS名字，以及唯一指向特定页面的路径。

- 浏览器不止可以获得HTTP协议的资源，还有许多其他协议的URL
```
  http
  https
  ftp
  file 用于获取本地文件 file:///usr/lxc/xueshu/main.txt
  mailto  用于发送邮件
  rtsp  流式媒体
```

- URL,URN,URI: URI包括URL,URN，所以用URI是永远不会错的。URL必带协议，URN可以不带协议。

#### 其它

- MIME类型: 当一台服务器返回一个页面时，它同时也返回了一些关于此页面的信息，其中包括页面的MIME类型

- 有两种扩展浏览器的方式：插件(plugin)和辅助应用程序(helper application)。

- 浏览器也能打开本地的文件，不一定非得从web服务器上取回文件。

- 服务器端需要可以同时处理很多请求。一个解决方案时服务器由一个前端模块和k个处理模块组成。k＋1个线程全部处于同一个进程，这样可以同时处理k个请求。

#### Cookie

- Cookie:当用户请求一个web页面时，服务器除了提供请求的页面信息外，还以Cookie的形式提供一些附加信息。

- 一个Cookie可能包含最多5个字断，每个域最多存储20个Cookie。
```
  域          路径 内容            过期          安全
  aportal.com /   CustomerID=lxc 14-10-1017:00 否
```
如果不存在过期时间，则为关闭浏览器。安全选项表示只在SSL/TLS时使用。

- Cookie的一种用法：网上购物时，点一件商品就更新一次Cookie，但是我觉得用得更多的应该是数据库。

- Cookie的一种用法：广告公司在其他网站上放广告，然后广告图片是一个唯一名字的图片，每次访问该图片时就把该图片id作为Cookie返回给用户，用户访问另一个页面(也包含这个公司的广告),浏览器就知道用户之前访问过什么。

- 广告公司想要偷偷跟踪用户，可以将上面的广告做成1*1像素的

- 第三方cookie: 从一个不同于主页网站的其它网站获得cookie，例如上面的广告公司。浏览器可以阻止第三方cookie。

### 静态Web页面

- HTML, HyperText Markup Language
- CSS, Cascading Style Sheets

### 动态Web页面和Web应用

#### 服务器端动态Web页面生成

- 第一种方式是CGI(Common Gateway Interface)，公共网关接口。CGI提供了一个接口，允许Web服务器与后端程序及脚本通信，并生成HTML页面作为响应。如果没错的话，Python的WSGI是类似于CGI的一个东西。

- CGI它只是一个接口定义：它不负责服务器的实现，也不负责网页应用的实现，它只是一个两边接口方式的约定。所以，它并不是另一个 WEB 应用框架。通常意义上的 WEB 应用框架，也只相当于 WSGI 网页应用端的一种实现。

- 第二种方式是在HTML页面中嵌入少量的脚本，然后让服务器来执行这些脚本以便生成最终发送给客户的页面。PHP就是其中一种。通常用扩展名php来标示包含PHP的Web页面，而不是用html。注意这里的关键是脚本运行在服务器端。

- 除此之外还有JSP(JavaServer Pages),Java服务器页面，页面中的动态部分用Java编写。

- 还有ASP.NET(Active Server Page)是Microsoft版本的PHP和JSP。它使用Microsoft专用的.NET网络应用框架来生成动态内容。使用这种技术的页面具有文件扩展名.aspx。

#### 客户端动态Web页面生成

- JavaScript是一种非常高级的语言，它的变异速度很快，每个浏览器对它的支持都不一样。

- PHP和JavaScript看上去很相似，它们都是嵌入在HTML中的代码，但它们的处理方式完全不同。

- PHP是当服务器收到用户请求时，服务器加载PHP文件，并执行内嵌的PHP脚本，由此返回页面给用户。

- 除了JavaScript外，适用于Windows平台的方法是VBScript。还有Applet，使用浏览器的JVM运行。Microsoft还允许Web页面包含ActiveX控件，它被编译成x86机器指令，可以直接在裸机上运行。

#### AJAX - Asynchronous JavaScript and XML

- AJAX它不是一种语言，是一组需要一起协同工作的技术。
```
  (1) 用来表现页面信息的HTML和CSS
  (2) 浏览时改变部分页面的DOM(Document Object Model)
  (3) 使得程序和服务器交换应用数据的XML(eXtensible Markup Language)
  (4) 程序发送和检索XML数据的异步方式
  (5) 将所有功能组合在一起的JavaScript
```

- 文档对象模型DOM表示结构化成一棵反映HTML元素的树。它的意义在于给程序提供了一种改变部分页面内容的方法，没有必要重写整个页面。

- 可扩展标记语言XML是一个说明结构化内容的语言。
```
  <author>
    <first_name> George </first_name>
    <last_name> Phil </last_name>
  </author>
```
用户可以自定义标签，它非常适合于浏览器端运行的程序和服务器传输信息，但它没有说明如何显示作为网页的文档。XSLT可以将XML转换成HTML。

- 不用HTML而采用XML来表示数据的另一个优点是数据更容易被程序分析。

- HTML有点马虎，有时候标签不正确关闭也可以显示，而XML则要求十分严格。

- HTML也可以按照XML术语来定义。称为XHTML。HTML5.0是HTML像XHTML的过渡。

- SOAP(Simple Object Access Protocol),简单对象访问协议。是实现基于XML和HTTP协议的一种简单的程序间通信方式。

- 动态Web技术总结
```
  客户端:
  Java虚拟机，VB脚本解释器，HTML/CSS/XML解释器，JavaScript解释器，插件，辅助应用程序
  服务器端:
  PHP,JSP,ASP,CGI脚本
```

### HTTP (HyperText Transfer Protocol)

- HTTP是一个简单的请求－响应协议，它通常运行在TCP之上。HTTP提供的进程间通信并不仅限于Web。

- HTTP 1.1相比于HTTP 1.0最大的区别在于它支持持续连接。1.0是一个请求一个响应之后TCP连接就断掉了。在一个连接的开始阶段，TCP使用慢启动过程来增加吞吐量，直到它了解网络路径的行为。这个预热期的后果是多个短TCP连接比一个长TCP连接传输信息所需时间要长很多。

- HTTP方法
```
  GET     读取一个页面  通用形式 GET filename HTTP/1.1
  HEAD    读取页面的头
  POST    附加一个Web页面
  PUT     存储一个Web页面
  DELETE  删除一个Web页面
  TRACE   指示服务器发回收到的请求，用于调试
  CONNECT 通过代理连接
  OPTIONS 向服务器查询一个页面并且获得可用于该页面的方法和头
```

- HTTP响应，每个响应消息由一个状态行以及可能的附加信息(如Web页面)，状态行有
```
  1xx   消息        100=服务器同意请求   不常用
  2xx   成功       200=请求成功  204=没有内容
  3xx   重定向     301＝移动页面 304=缓存的页面仍然有效
  4xx   客户错误    403=页面禁止  404=页面没找到
  5xx   服务器错误  500=服务器内部错误  503=稍后再试
```

- 消息头：请求行(如GET)后面可能还有额外的行，包含更多信息。同样，响应消息也有响应头。
```
  User-Agent      请求      有关浏览器及平台信息
  Accept          请求      用户可以接受的MIME类型
  Accept-Charset  请求      用户可以接受的字符集
  Accept-Encoding 请求      用户可接受的页面编码(如gzip)
  Accept-Language 请求      用户可处理的自然语言
  If-Modified-Since请求     检查本地缓存是否有效
  If-None-Match   请求      用于缓存
  Host            请求      服务器的DNS名字，这是强制的
  Authorization   请求      检查用户权限
  Referer         请求      发出请求的先前URL，对于跟踪Web浏览很有用
  Cookie          请求      与后面的Set-Cookie配套使用，返回浏览器传来的Cookie
  Set-Cookie      响应      客户需要存储的Cookie
  Server          响应      关于服务器的信息
  Content-Encoding响应      内容编码(如gzip)
  Content-Language响应      页面使用的自然语言
  Content-Length  响应      页面以字节计的长度
  Content-Type    响应      页面的MIME类型
  Content-Range   响应      页面的一部分
  Last-Modified   响应      页面最后修改的时间
  Expires         响应      页面不再有效的时间
  Location        响应      通知客户应该尝试另外一个URL
  Accept-Ranges   响应      指出服务器能接受的请求的字节范围
  Date            两者      发送消息的日期与时间
  Cache-Control   两者      指示如何处理缓存
  ETag            两者      页面内容的标签，主要用于缓存
  Upgrade         两者      发送方希望切换的协议
```

- 缓存，缓存是为了打开重复页面时不必再进行重复传输。检查缓存是否是最新的有多种策略。

- Telnet命令可以用来建立TCP连接
```
  telnet www.baidu.com  80
  GET / HTTP/1.1
  Host: www.baidu.com
  
  得到HTML响应
```

### 移动Web

- 在移动设备上使用Web会有屏幕小，通信昂贵等问题

- 通过User-Agent头来给移动用户返回内容较少的页面

- 此外，还有转码的方法，转码工作是介于服务器和移动电话之间完成的

## 流式音视频

### 数字音频

- 在每秒44100个采样并且每个样值16位的情况下，无压缩的CD质量单声道需要705.6kbps。

- MP3和AAC是两种流行的音频压缩算法。

### 数字视频

- JPEG, Joint Photographic Experts Group, 联合图像专家组

- MPEG, Motion Picture Experts Group, 运动图像专家组

- I帧，P帧，B帧

### 流式存储媒体

- Web页面实时播放视频是这样的一个过程。浏览器通过HTTP请求元文件(可能是这样一段文本: rtsp://joes-movie-server/movie-0025.mp4)，然后媒体播放器(插件或者辅助应用)通过RTSP进行实时播放。

- RTSP (Real Time Streaming Protocol)，实时流协议，基于UDP或TCP

### 流式直播媒体

- 实际上的Internet不是通过UDP传输给用户的，而是与每个用户建立一个单独的TCP连接。原因是，IP组播在Internet上没有真正部署，想想也是，怎么可能向全世界主机组播呢？ISP和网络仅在自己内部支持它。所以还是要先建立TCP连接。

### 实时会议

- H.323是Internet实时音频视频呼叫的标准，它将电话网络和Ineternet连接了。类似Skype等等。

- SIP-会话发起协议，是为了设计一种更加简单和模块化的方法来实现IP语音。

## 内容分发

### 内容与Internet流量

- 一些受欢迎的网站，使用一台计算机是不能处理全部流量的，这个时候就需要内容分发系统。例如Youtube。

### 服务器农场与Web代理

- 为了加快Web响应速度。服务器端可以建设服务器农场，用一个计算机集群代替单个服务器。客户端可以采用更好的缓存技术尤其是代理缓存。

#### 服务器农场

- 服务器农场需要解决的问题是如何让多个服务器看起来像一个单一网站。

- 第一种解决方案是利用DNS将请求分配到各个服务器，比如各个IP地址轮流。

- 第二种方案是使用前端作为DNS映射的IP地址，然后由前端将请求广播给各个服务器。

#### Web代理

- Web代理是一个被多个用户共享的高速缓存。它的原本用意是缓存一些经常被用户访问的页面，然后没有缓存的页面交由代理服务器去获取。

- 代理服务器算二级缓存，自己的浏览器的缓存是一级缓存，当然代理服务器还可以有代理。

- 代理服务器的还有一个好处是可以设置黑名单网站

### CDN, Content Dilivery Network, 内容分发网络

- 内容分发网络，是用于流行的网站分摊流量用的，而且希望用户通过距离自己比较近的服务器去获取数据。

- 方案有三个，前两个不太好。第一种是用代理服务器，但是问题是用户不可能按照网站设想的那样去设置代理服务器。

- 最好的方案是DNS重定向，将负责该网站的DNS服务器设置为返回请求IP距离最近的镜像服务器的IP。

- 这种CDN技术是由Akamai公司提供的。CDN一般是付费服务，这样子公司就不需要自己购买大量的服务器了。CDN一般放在各大ISP上，其实这对于ISP是有很多好处的。ISP减少了上行流量，省钱了，而且由于CDN的存在，访问速度变快了，因此ISP也乐于让CDN公司来构建他们的服务。

### P2P, Peer-to-Peer, 对等网络

- 一个P2P对等网络的基本思想是，将Internet中的多台计算机连接在一起资源集中来进行内容分发。

- N个用户，每个用户1Mbps，那么该网络的总上传下载带宽都是NMbps。

#### BitTorrent

- 这是一个开放标准

- 种子是一个很小的文件，被对等用户用来验证从其他对等用户下载来的内容的完整性。文件被分成比如512KB大小的块，对每个块进行哈希运算，把哈希值存在种子文件里。

- 每个对等网络还是有服务器的，服务器维护活跃的用户表，然后用户可以从中获取信息。 这个服务器叫做跟踪器。



# 网络安全

## 概述

- 网络安全被分为四类问题：保密，鉴别，不可否认和完整性控制。

- 加密可以发生在网络的每一层中。物理层中，防止搭线窃听。

- 数据链路层也可以加密，但是由于在路由器上必须要解密因此容易遭到路由器内部的攻击。

- 网络层可以安装防火墙等措施来过滤好的和坏的数据包

- 传输层，可以对端到端整个链接进行加密。

- 最后是在应用层进行加密。

## 密码学概论

- 密文C是加密算法E在秘钥K的情况下的结果。所以加密算法都是带参数的函数。

- Kerckhoff原理：所有的算法必须是公开的而密钥是保密的。

- 置换密码：例如凯撒密码，比如abcc变成efgg。

- 替代密码：其实就是变换顺序abc变成bca。

- 一次性密钥：不可破解的，但是实际使用上有局限性。量子密码是理论上完美的密码。

- 两个基本的密码学准则:第一，所有的消息必须包含足够大的冗余度，因而主动入侵者发送的随机垃圾消息不可能有机会被解释为有效的信息。第二，消息必须具有一定的新鲜度来对抗重放攻击。

## 对称秘钥算法

- 加密硬件中有P盒可以完成替代，S盒可以完成置换。

### DES (Data Encryption Standard) 数据加密标准

- 是一种块加密算法，就是对固定长度的数据块，比如64位进行加密。

- 是一种加密算法，使用了P盒S盒以及其他一些算法等等，秘钥长度56位。

- 这种算法是可以破解的，但是很实用。

- 一种改进是三重DES，即K1加密K2解密K1加密，这样就可以将秘钥长度扩展为112位，无法被破解。

### AES (Advanced Encryption Standard) 高级加密标准

- DES已经不再安全，于是美国政府开展竞赛决出了一种更加高级的加密算法。

- 它支持128,192,256位秘钥长度，软硬件实现都可以，算法完全公有。

- AES和DES加密速度都非常快，完全可以做到实时加密。

### 密码模式

- 电码模式：每个块的密文仅仅与它本身有关，这是DES和AES最基础的用法。它容易被利用。比如交换两个加密后的块等等。

- 密码块链模式：每个块都和前面的块链接起来，缺点是错了一位后面就全部崩溃。

- 密码反馈模式：错一位只有部分会崩溃。

- 流密码模式，计数器模式：等等都有各自优缺点。

- 以上密码模式都可以基于AES，DES再使用。




# 网络安全

## 概述

- 网络安全被分为四类问题：保密，鉴别，不可否认和完整性控制。

- 加密可以发生在网络的每一层中。物理层中，防止搭线窃听。

- 数据链路层也可以加密，但是由于在路由器上必须要解密因此容易遭到路由器内部的攻击。

- 网络层可以安装防火墙等措施来过滤好的和坏的数据包

- 传输层，可以对端到端整个链接进行加密。

- 最后是在应用层进行加密。

## 密码学概论

- 密文C是加密算法E在秘钥K的情况下的结果。所以加密算法都是带参数的函数。

- Kerckhoff原理：所有的算法必须是公开的而密钥是保密的。

- 置换密码：例如凯撒密码，比如abcc变成efgg。

- 替代密码：其实就是变换顺序abc变成bca。

- 一次性密钥：不可破解的，但是实际使用上有局限性。量子密码是理论上完美的密码。

- 两个基本的密码学准则:第一，所有的消息必须包含足够大的冗余度，因而主动入侵者发送的随机垃圾消息不可能有机会被解释为有效的信息。第二，消息必须具有一定的新鲜度来对抗重放攻击。

## 对称秘钥算法

- 加密硬件中有P盒可以完成替代，S盒可以完成置换。

### DES (Data Encryption Standard) 数据加密标准

- 是一种块加密算法，就是对固定长度的数据块，比如64位进行加密。

- 是一种加密算法，使用了P盒S盒以及其他一些算法等等，秘钥长度56位。

- 这种算法是可以破解的，但是很实用。

- 一种改进是三重DES，即K1加密K2解密K1加密，这样就可以将秘钥长度扩展为112位，无法被破解。

### AES (Advanced Encryption Standard) 高级加密标准

- DES已经不再安全，于是美国政府开展竞赛决出了一种更加高级的加密算法。

- 它支持128,192,256位秘钥长度，软硬件实现都可以，算法完全公有。

- AES和DES加密速度都非常快，完全可以做到实时加密。

### 密码模式

- 电码模式：每个块的密文仅仅与它本身有关，这是DES和AES最基础的用法。它容易被利用。比如交换两个加密后的块等等。

- 密码块链模式：每个块都和前面的块链接起来，缺点是错了一位后面就全部崩溃。

- 密码反馈模式：错一位只有部分会崩溃。

- 流密码模式，计数器模式：等等都有各自优缺点。

- 以上密码模式都可以基于AES，DES再使用。

## 公开秘钥算法

- 对称秘钥算法弱点，秘钥总要分发给大量用户，一旦秘钥被窃取，整个加密方式变得毫无用处。

- 公开秘钥算法：有公钥和私钥，公钥加密私钥解密。

- 需要满足，公钥无法推测出私钥，需要抵御选择明文攻击。

### RSA

- 这种方法的安全性建立在分解大数的难度基础之上。

- 这种加密方式很不容易被暴力破解，但是加密解密速度相比于对称密钥要慢很多。

- 实际上大多数基于RSA的系统主要利用公开密钥算法来分发一次性会话密钥。再将这些会话密钥用于某一个对称密钥算法，比如AES和三重DES。

## 数字签名

- 数字签名需要满足：第一，接收方可以验证发送方的身份，第二，发送方不能否定该消息的内容，第三，接收方不能伪造这样的消息。

### 对称密钥签名

- 第一种做法是需要一个双方信任的第三方机构保存Alice和Bob的密钥，然后Alice发来信息，第三方解密然后用Bob的密钥加密发给Bob，消息中需要加入时间戳。

### 公开密钥签名

- 实际上很难找到这样的第三方。

- 采用公开密钥签名。Alice持有Bob的公钥，Bob持有Alice的公钥。

- Alice给消息用自己的私钥加密再用Bob的公钥加密然后发给Bob，Bob用自己的私钥解密，再用Alice的公钥解密。这样就可以保证信息是Alice发过来的了，而且Bob不能加以伪造。

### 消息摘要

- 用公钥密钥的方式可以实现认证，但是加密有时候是完全不必要的。所以签名的另外一个方法是使用消息摘要。

#### SHA-1 和 SHA-2 和 MD5

- 这两种都是消息摘要的方式，消息摘要可以用来和明文一起传递。

- 具体方法是，明文加上加密后的消息摘要(加密可以使用RSA)

### 生日攻击

- 破解m位的消息摘要，不需要2的m次数量级次数的操作。事实上只需要2的0.5m次数量级。

- 其原理是，使得一个班上有两个同学生日相同的概率超过0.5只需要23个同学，而不是想象中的100位同学。



