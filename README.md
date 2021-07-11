# UEFI

# ACPI

# PCIe
1. PCI设备具有独立的地址空间，即PCI总线地址空间，该空间与存储器地址空间通过Host Bridge隔离。处理器需要通过Host Bridge 才能访问PCI设备，PCI设备需要通过Host Bridge才能访问主存储器。
2. PCI 并行总线随着时钟频率提高，并行传输干扰严重，PCI 到 PCIe 最大改变就是并行变为串行，使用差分信号传输，降低干扰，从而大幅提升传输频率。从PCI 设备的 33MHZ 到 PCIe 的 GHZ。
3. PCI 是总线结构，而PCIe是点对点结构。

## PCI
### 配置空间（configuration space）
传统的PCI设备配置空间通过in/out指令来访问，配置空间地址和数据分别对应端口0xCF8，0XCFC。端口所在地址空间与内存地址空间单独编码。CFGADR和CFGDAT都是32位端口，各标志位含义如下。

## PCIe
### 总线结构

### Transaction routing

### Address Decoder

### 基本信息
除了兼容PCI的BDF划分（8:5:3），最多支持256个BUSes，PCIe对此作了扩展支持，及PCI segment Groups支持，系统允许最多存在2^16 Groups，每个 Groups 包含256个Buses。
### 配置空间（configuration space）
PCIe设备通过[Enhanced Configuration Mechanism](https://wiki.osdev.org/PCI_Express)来访问配置空间，PCIe host bridge 对应的配置空间起始地址记录在ACPI表中，ACPI表以RSDP为入口点，在Linux 内核启动过程中会通过在EBDA范围（Extended BIOS Data Area）[搜索RSDP节点](https://zhuanlan.zhihu.com/p/49500489)，然后找到对应的MCFG表项，该字段记录了配置空间所对应的MMIO基地址。
因此访问特定PCI Segment Groups中的某个设备的配置空间就可以通过访问内存地址来实现（MMIO_Starting_Physical_Address + ( (Bus - MMIO_Starting_Bus) << 20 | Device << 15 | Function << 12 ).）

MCFG字段由hostbridge 的PCIEXBAR寄存器所定义，包含了起始地址和size信息。

### 设备枚举（device enumeration）

### BAR 地址空间分配



## 参考链接
[深入PCI与PCIe之一：硬件篇](https://zhuanlan.zhihu.com/p/26172972)
[深入PCI与PCIe之二：软件篇](https://zhuanlan.zhihu.com/p/26244141)

