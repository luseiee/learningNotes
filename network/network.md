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
- 窗口大小表示对方可以发送多少字节过来
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

TCP中每个Byte会占用一个序号，而TCP的sequence number是32位的，所以可以每120s发送2^32Bytes信息，然而1500B信息需要1500+20+20+26的段帧来发送因此需要的带宽为`2^32*8*1566/1500/120=299Mbps`。

The goal is to send 2^32 bytes in 120 sec or 35,791,394 payload bytes/sec. This is 23,860 1500-byte frames/sec. The TCP overhead is 20 bytes. The IP overhead is 20 bytes. The Ethernet overhead is 26 bytes. This means that for 1500 bytes of payload, 1566 bytes must be sent. If we are to send 23,860 frames of 1566 bytes every second, we need a line of 299 Mbps. With any- thing faster than this we run the risk of two different TCP segments having the same sequence number at the same time.