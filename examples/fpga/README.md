# FPGA输入与测试参考

## 方案一：IPv6基本首部

IPv6基本首部固定40字节（RFC 8200），这里只输入**IPv6基本首部**，不包含Ethernet Header和Payload。

| 字节偏移（从0计） | 长度 | 字段 |
| --- | ---: | --- |
| 0—3 | 4字节 | Version、Traffic Class、Flow Label |
| 4—5 | 2字节 | Payload Length |
| 6 | 1字节 | Next Header |
| 7 | 1字节 | Hop Limit |
| 8—23 | 16字节 | Source Address |
| 24—39 | 16字节 | Destination Address |

[示例首部十六进制](ipv6_header_example.txt)中源地址为`2001:db8::1`，目的地址为`2001:db8::2`，Next Header为17，Hop Limit为64。可修改目的地址验证匹配与不匹配两种情况。自行定义RTL端口、有效信号与端序，设计说明中注明即可。

## 方案二：AXI4-Stream轮询仲裁

输入通道0、1以及输出通道均至少包括`TDATA`、`TVALID`、`TREADY`。有效传输成立条件为**TVALID && TREADY**；未握手前发送端应维持TVALID及对应TDATA稳定。输出端TREADY=0时应保持待发送数据，不得重复授权或丢弃数据。轮询仲裁的指针可在每次成功传输后推进。

建议验证以下场景：

1. 仅输入0持续有效，输出全部数据；仅输入1持续有效，输出全部数据。
2. 两路同时持续有效，观察轮询公平性。
3. 下游间歇性拉低TREADY，检查数据不丢失、不重复且顺序合理。
4. 两路随机出现TVALID，检查无请求时输出不产生虚假数据。

基础任务按**单次握手/数据拍**仲裁即可，完整Packet级仲裁（TKEEP、TLAST、多拍帧）属于进阶内容。
