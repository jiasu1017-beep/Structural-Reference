# *CONNECTOR PLASTICITY






### *CONNECTOR PLASTICITY定义连接器单元中的塑性行为。

此选项用于定义连接器单元中的塑性行为。必须与 [*CONNECTOR HARDENING](ch03abk44.md) 选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["连接器行为，" Abaqus 分析用户指南第 31.2.1 节](../usb/usb-link.md#usb-elm-econnectorbehavior)
- ["连接器塑性行为，" Abaqus 分析用户指南第 31.2.6 节](../usb/usb-link.md#usb-elm-econnplastbehav)
- [*CONNECTOR BEHAVIOR](ch03abk35.md)
- [*CONNECTOR HARDENING](ch03abk44.md)
- [*CONNECTOR POTENTIAL](ch03abk49.md)

### **可选参数：**

COMPONENT

将此参数设置为指定塑性行为所对应的连接器相对运动分量。

如果省略此参数，则必须将 [*CONNECTOR POTENTIAL](ch03abk49.md) 选项与 [*CONNECTOR PLASTICITY](ch03abk48.md) 选项结合使用，以指定耦合塑性行为。

### **此选项没有关联的数据行。**




