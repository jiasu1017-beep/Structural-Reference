# *DECHARGE





### *DECHARGE为压电分析输入分布电荷。

此选项用于在压电单元上输入分布电荷。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**历史数据 

**级别：**步骤

**Abaqus/CAE：**载荷模块

##### **参考：**

- ["压电分析，" Abaqus分析用户指南第6.7.2节](../usb/usb-link.md#usb-anl-apiezoelectric)

### **可选参数：**

AMPLITUDE

将此参数设置为振幅曲线的名称，该曲线定义步骤期间分布电荷的大小。如果省略此参数，则参考值将在步骤开始时立即应用或线性地跨越步骤应用，具体取决于分配给 [*STEP](ch18abk36.md) 选项上 AMPLITUDE 参数的值（["定义分析，" Abaqus分析用户指南第6.1.2节](../usb/usb-link.md#usb-anl-aover)）。

OP

设置 OP=MOD（默认）以保留现有的 [*DECHARGE](ch04abk10.md)s，此选项定义要添加或修改的电荷。如果应该移除模型上所有现有的 [*DECHARGE](ch04abk10.md)s，设置 OP=NEW。

### **矩阵生成和直接解稳态动力学分析的可选、互斥参数：**

IMAGINARY

包含此参数以定义载荷的虚部（异相）。

REAL

包含此参数（默认）以定义载荷的实部（同相）。

### **定义分布电荷的数据行：**

**第一行：**

根据需要重复此数据行，以定义各个单元或单元集合的分布电荷。




