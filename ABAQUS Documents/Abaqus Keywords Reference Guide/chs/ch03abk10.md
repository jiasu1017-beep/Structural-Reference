# *CECURRENT






### *CECURRENT在电传导分析中指定集中电流。

此选项用于在耦合热-电和耦合热-电-结构分析中向模型的任何节点施加集中电流。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**历史数据 

**级别：**步骤

**Abaqus/CAE: **载荷模块

##### **参考：**

- ["耦合热-电分析，" Abaqus 分析用户指南第 6.7.3 节](../usb/usb-link.md#usb-anl-ajouleheating)
- ["完全耦合热-电-结构分析，" Abaqus 分析用户指南第 6.7.4 节](../usb/usb-link.md#usb-anl-acoupthermalelecstruct)

### **可选参数：**

AMPLITUDE

将此参数设置为在步骤中定义电流大小的幅值曲线名称（["幅值曲线，" Abaqus 分析用户指南第 34.1.2 节](../usb/usb-link.md#usb-prc-pamplitude)）。如果省略此参数，则根据 [*STEP](ch18abk36.md) 选项上 AMPLITUDE 参数分配的值，参考大小将在步骤开始时立即应用或在线性分布于整个步骤（["定义分析，" Abaqus 分析用户指南第 6.1.2 节](../usb/usb-link.md#usb-anl-aover)）。

OP

设置 OP=MOD（默认）以保留现有的 [*CECURRENT](ch03abk11.md)，此选项修改现有的集中电流或定义额外的集中电流。

设置 OP=NEW 以移除模型上所有现有的 [*CECURRENT](ch03abk11.md)。

### **用于在节点处定义集中电流的数据行：**

**第一行：**

根据需要重复此数据行，以在各个节点或节点集上定义电流。




