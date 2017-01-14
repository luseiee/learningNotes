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