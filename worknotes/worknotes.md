Title         : Ebay Intern
Author        : Lu, Phil

[TITLE]
# StubHub System

## System 

* POD1, POD2: 两个几乎一样的server组
* Role: 一个POD下有许多不同的Role，每个Role负责网站的不同的功能，每个role下都有若干个server。通常为偶数个，比如说16个。
* PoolA, PoolB: 每个Role下的服务器被分为两个Pool，PoolA是单数号服务器，PoolB是偶数号服务器
* Role based design: 每个role下的server做exact same job，因此当其中一个或几个出问题的时候不会影响网站的正常运作。
* Physical Machine & Virtual Machine: 在整个system中，有些server是virtual machine，有一些则是physical，在远程看来它们是一模一样的，
但是当问题出现需要重启的时候，physical machine就必须要人去，所以CDC（ebay在上海公司）无法去操作类似reboot的工作。

## Deploy Process

1. Deploy PoolA: 此时PoolB在工作
2. Enable PoolA: 此时测试组测试PoolA性能
3. If OK: Deply PoolB: 此时PoolA在工作中
   if not OK: Disable PoolA
4. Deploy PoolB: 此时所有服务器都在工作
5. Enable PoolB: 这步在command line完成，首先check server里的code都match，随后用命令enable

## Cluster

- 有些role是cluster的，cluster的特点是服务器(在shard中称为node)之间互相通信而且有一个server takes the lead，
当有一半的server挂掉的时候整个cluster才会挂掉。  
- ebay的Role中只有部分有关big data的Role才会使用cluster，运维成本大一些。
- 一个cluster有多个shard，每个shard处理不同的工作，一个cluster中仍然有16个server，并且一个shard中有8个server配合工作。
一个shard中的8个server中有一个down掉会有其他server take the lead.
- 一个server会为不同的shard进行工作，但是一个server出问题不一定会影响它所服务的所有的shard
- debug一个cluster的时候不能采用kill一个server的方式，而且shutdown一个server需要很长时间，
因为它需要把data传递给同一个shard中的许多其他server中。
> RAID 5, 与cluster概念类似，用于存储技术: 
RAID Level 5是一种储存性能、数据安全和存储成本兼顾的存储解决方案。它使用的是Disk Striping（硬盘分区）技术。RAID 5至少需要三块硬盘，
RAID 5不是对存储的数据进行备份，而是把数据和相对应的奇偶校验信息存储到组成RAID5的各个磁盘上，
并且奇偶校验信息和相对应的数据分别存储于不同的磁盘上。当RAID5的一个磁盘数据发生损坏后，可以利用剩下的数据和相应的奇偶校验信息去恢复被损坏的数据。

- 当shard中有node不正常的时候，这种状态被称为degraded，这时不会影响正常工作，但是需要去进行recovery
- ebay使用的cluster平台是Solr
> Solr is the popular, blazing-fast, open source enterprise search platform built on Apache Lucene™.
- ebay使用的管理程序是CDT，这是ebay自己开发的

# Queueing Model For StubHub

## Which Model to Use

### Single Station M/M/m Model

> Take SPA role as an example.

- We may consider the simple service like SPA as a M/M/m model. It corresponds to the **qsmmm** function in Octave queueing package. The reason is that we can regard SPA Role as a black box, it accepts requests of the same one class and gives the output.

** Required input **

1. Arrival Rate lambda: Get from Splunk or other platform.

2. Service Rate mu: Get data from Splunk or other platform.

3. m: m means the number of servers. It's more proper to regard m as the maximum number of requests the server can deal with at the same time.

### Single Class Open Queueing Network
> Take POD1 as an example.

- According to us, POD1 is very suitable for Single Class Open Queueing Network. It corresponds to the *qnos* function in Octave.  Each role is regarded as one service center. There's a condition for using this model, we must consider the request for one specific role is of the same class.

** Required input **

1. Arrival Rate to each role.

2. Routing matrix for these roles. If no routing happens, just assign 0 to it.

3. The service rate for each role. And the maximum capacity of each role.

### Multiple Class Open Queueing Network
> Take POD1 as an example.

- If for each role, there are different type of requests. We need one more dimension for class C. It corresponds to the **qnom** function in Octave.

** Required input **

Similar to single class situation, all add one dimension.

## Project Plan for Recent
> Basically the same as the document we received.

> We may start from SPA role.

1. Learn to use the prototype of Octave queueing package. *Finished.*

2. Develop a simulation tool for these queueing models. * Working on it. *

3. Data gathering from Splunk or ExtraHop. *Need Support.*


- make sure the arriving fits the Poisson distribution.
- get the arriving rate
- check if the service time fits the exponential distribution.
- get the serving rate
- test the capacity of SPA server. This may be done on POD31.


4. Use the data gathered to determine if the prototype and simulation tool are successful.

5. Extend the project to the whole POD.