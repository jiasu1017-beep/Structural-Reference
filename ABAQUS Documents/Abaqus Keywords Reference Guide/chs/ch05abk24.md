# *ENERGY PRINT









### *ENERGY PRINT打印总能量摘要。

此选项用于将整个模型或模型一部分的总能量内容摘要打印到数据（`.dat`）文件。

**产品：**Abaqus/Standard

**类型：**历史数据

**级别：**步骤

##### **参考：**

- ["输出到数据和结果文件，" Abaqus分析用户指南第4.1.2节](../usb/usb-link.md#usb-out-oprintfile)

### **可选参数：**

ELSET

将此参数设置为正在为其发出输出请求的单元集名称。如果省略此参数，将输出整个模型的能量。

FREQUENCY

将此参数设置为输出频率（以增量计）。除非 FREQUENCY=0，否则输出将始终在每个步骤的最后增量打印。默认值为 FREQUENCY=1。设置 FREQUENCY=0 以抑制输出。

**此选项没有关联的数据行。**



