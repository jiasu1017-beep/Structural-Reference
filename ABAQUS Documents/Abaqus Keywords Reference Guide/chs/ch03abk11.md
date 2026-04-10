# *CECHARGE






### *CECHARGE在压电分析中指定集中电荷。

此选项用于向压电模型中的任何节点施加电荷。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**历史数据 

**级别：**步骤

**Abaqus/CAE: **载荷模块

##### **参考：**

- ["压电分析，" Abaqus 分析用户指南第 6.7.2 节](../usb/usb-link.md#usb-anl-apiezoelectric)

### **可选参数：**

AMPLITUDE

将此参数设置为在步骤中定义电荷大小的幅值曲线名称。如果省略此参数，则根据 [*STEP](ch18abk36.md) 选项上 AMPLITUDE 参数分配的值，参考大小将在步骤开始时立即应用或在线性分布于整个步骤（["定义分析，" Abaqus 分析用户指南第 6.1.2 节](../usb/usb-link.md#usb-anl-aover)）。

OP

设置 OP=MOD（默认）以保留现有的 [*CECHARGE](ch03abk10.md)，此选项修改现有的电荷或定义额外的电荷。

设置 OP=NEW 以移除模型上所有现有的 [*CECHARGE](ch03abk10.md)。

### **矩阵生成和直接解稳态动力学分析的可选、互斥参数：**

IMAGINARY

包含此参数以定义集中电荷的虚部（异相）部分。

REAL

包含此参数（默认）以定义集中电荷的实部（同相）部分。

### **用于定义集中电荷的数据行：**

**第一行：**

根据需要重复此数据行，以在各个节点或节点集上定义集中电荷。




