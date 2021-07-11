# UEFI

# ACPI

# PCIe

## PCI
### 配置空间（configuration space）
传统的PCI设备配置空间通过in/out指令来访问，配置空间地址和数据分别对应端口0xCF8，0XCFC。端口所在地址空间与内存地址空间单独编码。

## PCIe
### 基本信息
除了兼容PCI的BDF划分（8:5:3），最多支持256个BUSes，PCIe对此作了扩展支持，及PCI segment Groups支持，系统允许最多存在2^16 Groups，每个 Groups 包含256个Buses。
### 配置空间（configuration space）
PCIe设备通过Enhanced Configuration Mechanism来访问配置空间，PCIe host bridge 对应的配置空间起始地址记录在ACPI表中，ACPI表以RSDP为入口点，在Linux 内核启动过程中会通过在EBDA范围（Extended BIOS Data Area）[搜索RSDP节点](https://zhuanlan.zhihu.com/p/49500489)，然后找到对应的MCFG表项，该字段记录了配置空间所对应的MMIO基地址。
因此访问特定PCI Segment Groups中的某个设备的配置空间就可以通过访问内存地址来实现（MMIO_Starting_Physical_Address + ( (Bus - MMIO_Starting_Bus) << 20 | Device << 15 | Function << 12 ).）

### 设备枚举（device enumeration）

### BAR 地址空间分配



