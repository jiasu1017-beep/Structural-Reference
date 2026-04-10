# *ELEMENT OPERATOR OUTPUT









### *ELEMENT OPERATOR OUTPUT将单元算子输出写入SIM文档。

此选项用于以逐单元或组装形式将热矩阵写入SIM文档。它只能用于非耦合传热分析。

**产品：**Abaqus/Standard

**类型：**历史数据

**级别：**步骤

##### **参考：**

- ["生成热矩阵，" Abaqus分析用户指南第10.3.2节](../usb/usb-link.md#usb-anl-amtxgenerationgeneral)

### **可选参数：**

ASSEMBLE

包含此参数以写入组装矩阵。默认情况下，单元矩阵被写入。

DAMPING

包含此参数以输出热容矩阵。

ELSET

使用此参数为模型的一部分写入矩阵。将此参数设置为包含所选模型部分中所有单元的单元集名称。默认情况下，为整个模型中的所有支持单元生成矩阵，包括内部单元。

FREQUENCY

将此参数设置为输出频率（以增量计）。除非 FREQUENCY=0，否则输出将始终在每个步骤的最后增量写入。默认值为 FREQUENCY=1。设置 FREQUENCY=0 以抑制输出。

LOAD

包含此参数以输出由 LOADTYPE 参数选择的通量。

LOADTYPE

使用此参数选择要输出的载荷类型。

设置 LOADTYPE=EXTERNAL（默认）以输出外部热通量。

设置 LOADTYPE=NET 以输出净热通量。

STIFFNESS

包含此参数以输出热传导矩阵。

**此选项没有关联的数据行。**



