# *ENERGY FILE









### *ENERGY FILE将能量输出写入结果文件。

此选项用于在Abaqus/Standard分析中将模型总能量的摘要写入结果（`.fil`）文件，或在Abaqus/Explicit分析中写入所选结果（`.sel`）文件。在Abaqus/Explicit分析中，它必须与[*FILE OUTPUT](ch06abk09.md)选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**历史数据

**级别：**步骤

**Abaqus/CAE：**不支持；Abaqus/CAE仅从输出数据库文件读取输出。

##### **参考：**

- ["输出到数据和结果文件，" Abaqus分析用户指南第4.1.2节](../usb/usb-link.md#usb-out-oprintfile)
- [*FILE OUTPUT](ch06abk09.md)

### **可选参数：**

ELSET

此参数仅适用于Abaqus/Standard分析。

将此参数设置为正在为其发出输出请求的单元集名称。如果省略此参数，将输出整个模型的能量。

FREQUENCY

此参数仅适用于Abaqus/Standard分析。

将此参数设置为输出频率（以增量计）。除非 FREQUENCY=0，否则输出将始终在每个步骤的最后增量写入结果文件。默认值为 FREQUENCY=1。设置 FREQUENCY=0 以抑制输出。

**此选项没有关联的数据行。**



