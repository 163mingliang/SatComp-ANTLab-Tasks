# 任务C｜FPGA网络数据处理模块设计与验证

基础任务提供以下两个方案，**任选其一**完成。使用Verilog编写RTL代码，并通过Testbench进行功能仿真。

## 1. 基础任务（任选其一）

### 方案一：IPv6报文解析与匹配处理模块

参考IPv6基本报文格式，设计IPv6报文解析与匹配处理模块。

基础任务要求：

（1）采用40字节IPv6基本首部作为输入，暂不考虑以太网封装、IPv6扩展首部及实际网口接收。

（2）从报文首部中提取IPv6源地址、目的地址、Next Header及Hop Limit等字段。

（3）根据预设匹配规则（如目的IPv6地址精确匹配）判断报文是否符合条件，输出相应处理结果（如Forward或Drop）。

（4）编写Testbench，验证规则匹配成功、规则未命中及不同IPv6字段输入等情况。

模块接口与具体匹配规则可以自行设计，重点完成报文字段解析、匹配判断及结果输出。

### 方案二：基于AXI4-Stream接口的轮询仲裁模块

使用Verilog设计一个具有2路输入、1路输出的AXI4-Stream轮询仲裁模块，实现多个输入数据流之间的公平访问。

基础任务要求：

（1）采用AXI4-Stream接口，数据位宽可选32 bit或64 bit，至少支持TDATA、TVALID和TREADY信号。

（2）实现基于RR算法的轮询仲裁。当两路输入同时存在有效数据时，按照轮询顺序选择输出；当只有一路有效时，能够正常输出该路数据。

（3）正确处理TVALID/TREADY握手及输出端暂时无法接收数据的情况，保证数据不丢失、不重复。

（4）编写Testbench，验证单路输入、双路同时输入、输出反压及连续数据传输等场景。

可以以单次数据传输为仲裁单位，不要求处理完整的多拍报文。

## 2. 进阶任务（选做）

可进一步实现支持**Ethernet II以太网帧**（包含Ethernet Header、IPv6 Header及Payload）的解析与处理、IPv6前缀匹配。

可进一步拓展为多条IPv6数据流的RR仲裁（每条流有多个包含帧间隔的IPv6 Packets）。

可进一步扩展为4路输入，增加TKEEP、TLAST信号支持，实现完整报文级轮询仲裁，保证同一报文的多个数据拍连续输出、不发生报文交错。

有能力的同学可进一步开展Vivado综合、资源利用率及时序分析。

## 3. 参考资料

可参考IPv6协议规范（RFC 8200）、AXI4-Stream接口规范、Verilog教程及Vivado仿真资料。建议结合HDLBits等平台学习组合逻辑、时序逻辑和状态机设计。

- IPv6（RFC 8200）：https://www.rfc-editor.org/rfc/rfc8200
- AXI4-Stream（AMBA AXI4-Stream Protocol Specification）：https://developer.arm.com/documentation/ihi0051/latest/
- HDLBits：https://hdlbits.01xz.net/wiki/Main_Page

## 4. 提交要求

提交Verilog RTL源代码、Testbench、功能仿真结果及简要设计说明。说明模块输入输出接口、核心逻辑、测试场景及运行结果。

## 输入与测试参考

参见 [`examples/fpga/`](../examples/fpga/)：提供IPv6基本首部示例、字节偏移说明及AXI4-Stream握手测试建议。可自行定义模块端口与数据表示方式，但须注明端序和握手行为。
