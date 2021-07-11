# UEFI

# ACPI

# PCIe

## PCI

## PCIe
### 配置空间（configuration space）
PCIe host bridge 对应的配置空间起始地址记录在ACPI表中，ACPI表以RSDP为入口点，在Linux 内核启动过程中会通过在EBDA范围（Extended BIOS Data Area）[搜索RSDP节点](https://zhuanlan.zhihu.com/p/49500489)，然后找到对应的MCFG字段，该字段记录了配置空间所对应的MMIO地址。

### 设备枚举

### BAR 地址空间分配



