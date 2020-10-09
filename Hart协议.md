#### 										**Hart（Highway accessable remote transmitter）协议**



![1601430794768](C:\Users\Slade\AppData\Roaming\Typora\typora-user-images\1601430794768.png)

1.HART协议物理层

规定信号传输方式、介质、设备阻抗和信号电压。

传输介质通常为双绞线同轴电缆，线路阻抗在200~1200Ω，最大距离可达1500m左右。

![1601432183779](C:\Users\Slade\AppData\Roaming\Typora\typora-user-images\1601432183779.png)

![1602151051651](C:\Users\Slade\AppData\Roaming\Typora\typora-user-images\1602151051651.png)

在千兆速率下，向PHY提供GTXCLK信号，TXD、TXEN、TXER信号与此时钟信号同步。否则，在10/100M速率下，PHY提供 TXCLK时钟信号，其它信号与此信号同步。其工作频率为25MHz（100M网络）或2.5MHz（10M网络）



 发送器：

GTXCLK——吉比特TX..信号的时钟信号（125MHz）
    ◇ TXCLK——10/100M信号时钟
    ◇ TXD[7..0]——被发送数据
    ◇ TXEN——发送器使能信号
    ◇ TXER——发送器错误（用于破坏一个数据包）

接收器：

  ◇ RXCLK——接收时钟信号（从收到的数据中提取，因此与GTXCLK无关联）
    ◇ RXD[7..0]——接收数据
    ◇ RXDV——接收数据有效指示
    ◇ RXER——接收数据出错指示
    ◇ COL——冲突检测（仅用于半双工状态）

管理配置
    ◇ MDC——配置接口时钟
    ◇ MDIO——配置接口I/O

 以太网帧的格式为：前导符+开始位+目的mac地址+源mac地址+类型/长度+数据+padding(optional)+32bitCRC

关于RMII口和MII口的问题
    RMII口是用两根线来传输数据的，
    MII口是用4根线来传输数据的，
    GMII是用8根线来传输数据的。

![1602041086849](C:\Users\Slade\AppData\Roaming\Typora\typora-user-images\1602041086849.png)

![1602050123134](C:\Users\Slade\AppData\Roaming\Typora\typora-user-images\1602050123134.png)

注：OTXA 输出 调制完成的FKS发送信号，耦合到4-20mA电路上

IRXA 输入 从4-20mA电路上接收FSK输入信号

ORXD  输出 接收到已解调的Hart数据，传给uart(数字信号)

ITXD 输入 输入传输数据，从uart过来的待发送的HART数据流

![1602050481104](C:\Users\Slade\AppData\Roaming\Typora\typora-user-images\1602050481104.png)

![1602142159926](C:\Users\Slade\AppData\Roaming\Typora\typora-user-images\1602142159926.png)

![1602084161858](C:\Users\Slade\AppData\Roaming\Typora\typora-user-images\1602084231222.png)



![1602084094540](C:\Users\Slade\AppData\Roaming\Typora\typora-user-images\1602084094540.png)

![1602084324877](C:\Users\Slade\AppData\Roaming\Typora\typora-user-images\1602084324877.png)

![1602213088045](C:\Users\Slade\AppData\Roaming\Typora\typora-user-images\1602213088045.png)

![1602213655397](C:\Users\Slade\AppData\Roaming\Typora\typora-user-images\1602213655397.png)

待解决问题：

![1602214675897](C:\Users\Slade\AppData\Roaming\Typora\typora-user-images\1602214675897.png)

![](D:\Git\picture\待解决问题.png)