性能指标

1、100Mbps传输速度

2、刷新周期（最小）100uS FPGA可达200uS

3、传输距离100m

4、M12&RJ45连接头

5、IEEE802.3标准以太网介质传输，无论主站从站都可以运行在标准以太网之上

POWERLINK网络模型

主要有物理层、数据链路层和应用层组成

![](D:\Git\picture\POWERLINK协议网络模型.png)



 POWERLINK帧结构

![](D:\Git\picture\powerlink帧结构.bmp)

0-13字节是标准以太网帧头，14-n是powerlink数据帧信息，n+1-n+4是CRC校验序列，数据帧最长可以1518字节，最短是64字节。

POWERLINK两种工作模式

​    1、请求应答模式

![](D:\Git\picture\powerlink请求应答模式.bmp)

该种模式下的性能：完成一个站的通信所需要的时间，取决于物理层的传输速度和需要传送的数据包大小。 

​    2、定时主动上报模式（PRC 模式）

![](D:\Git\picture\POWERLINK PRC模式.bmp)

PRC 模式的通信过程： 
1. 主站发生广播数据帧 PresMN，主站把多个从站需要的数据在该数据帧里打包，然
    后以广播的方式发送出去，各个从站根据配置信息，从该数据帧中取走相应的数据。
    该数据帧为标准的以太网数据帧，最大有效数据容量为 1490Bytes。 
2. 从站接受到 PresMN 以后，根据主站配置的上报时间，来决定什么时候该上报
    PresCN，当定时器到了上报时间，从站就以广播的方式上报 PresCN。该数据帧包
    了主站以及其他从站需要的数据信息。 
3. 主站和从站是支持 PRC 模式，还是支持请求/应答模式，是由它自身的参数决定的。
    可以通过参数设置，在一个周期内，让某些从节点采用 PRC 模式，而另外一些从
    节点采用请求/应答模式。这种搭配使得网络容量可以灵活搭配。 


Multiplexing（复合结构）

![](D:\Git\picture\复合多用.bmp)

异步通信

从 SoC 数据帧开始到 SoA 数据帧的时间段为同步阶段，SoA 和 AsyncData 为异步阶段。SoA 数据帧包了请求哪个从站上报数据，而 AsyncData 数据帧为该从站上报的数据。在每
个循环周期，只能有一个从节点上报异步数据，如果有多个从节点需要异步通信，那么需要在多个周期内完。

POWERLINK 五种协议帧

  五种协议帧

![](D:\Git\picture\powerink 5种帧协议.png)

SoC数据帧格式

![](D:\Git\picture\SoC数据帧格式.bmp)

PReq数据帧格式

![](D:\Git\picture\PReq数据帧格式.bmp)

PRes数据帧格式

![](D:\Git\picture\PRes数据帧格式.bmp)

SoA数据帧格式

![](D:\Git\picture\SoA数据帧格式.bmp)

Asynd数据帧格式

![](D:\Git\picture\Asynd数据帧格式.bmp)