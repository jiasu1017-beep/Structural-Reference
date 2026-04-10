# *SUBSTRUCTURE LOAD CASE





### *SUBSTRUCTURE LOAD CASE开始子结构载荷情况的定义。

此选项用于开始对当前正在生成的子结构定义子结构载荷情况。它只能用于[*SUBSTRUCTURE GENERATE](ch18abk42.md)分析。

**产品：**Abaqus/Standard  Abaqus/CAE

**类型：**历史数据

**级别：**此选项在以部件实例装配定义的模型中不受支持。

##### **参考：**

- ["Defining substructures," Section 10.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asuperelementdef)
- [*SLOAD](ch18abk20.md)

### **必需参数：**

NAME

将此参数设置为一个标签，用于在分析期间向子结构施加载荷时在[*SLOAD](ch18abk20.md)选项规范中引用载荷情况。

### **定义载荷：**

输入任何机械载荷选项（["Concentrated loads," Section 34.4.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-ploadgeneral)和["Distributed loads," Section 34.4.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-ploaddistributed)）或热载荷选项（["Thermal loads," Section 34.4.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pthermal)）以定义形成载荷情况的载荷。为每个载荷指定一个幅值。此幅值将按[*SLOAD](ch18abk20.md)选项中指定的幅值和幅值参考进行缩放。载荷情况定义将持续直到遇到不是载荷选项之一的选项。如果边界条件包含在[*SUBSTRUCTURE LOAD CASE](ch18abk43.md)中，则它们始终处于活动状态，即使未使用[*SLOAD](ch18abk20.md)选项。




