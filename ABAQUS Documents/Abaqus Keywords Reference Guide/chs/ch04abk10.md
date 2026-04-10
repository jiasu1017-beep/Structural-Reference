# *DECURRENT





### *DECURRENT在电磁分析中指定分布电流密度。

此选项用于在耦合热电分析和耦合热电结构分析，输入分布电流密度，或在涡流分析和静磁分析中输入体积电流密度。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**历史数据 

**级别：**步骤

**Abaqus/CAE：**载荷模块

##### **参考：**

- ["耦合热电分析，" Abaqus分析用户指南第6.7.3节](../usb/usb-link.md#usb-anl-ajouleheating)
- ["全耦合热电结构分析，" Abaqus分析用户指南第6.7.4节](../usb/usb-link.md#usb-anl-acoupthermalelecstruct)
- ["涡流分析，" Abaqus分析用户指南第6.7.5节](../usb/usb-link.md#usb-anl-aeddycurrent)
- ["静磁分析，" Abaqus分析用户指南第6.7.6节](../usb/usb-link.md#usb-anl-amagnetostatic)

### **可选参数：**

AMPLITUDE

将此参数设置为振幅曲线的名称，该曲线定义步骤期间电流密度的大小（["振幅曲线，" Abaqus分析用户指南第34.1.2节](../usb/usb-link.md#usb-prc-pamplitude)）。如果省略此参数，则参考值将在步骤开始时立即应用或在线性地跨越步骤应用，具体取决于分配给 [*STEP](ch18abk36.md) 选项上 AMPLITUDE 参数的值（["定义分析，" Abaqus分析用户指南第6.1.2节](../usb/usb-link.md#usb-anl-aover)）。

OP

设置 OP=MOD（默认）以保留现有的 [*DECURRENT](ch04abk11.md)s，此选项定义要添加或修改的分布电流密度。

如果应该移除模型上所有现有的 [*DECURRENT](ch04abk11.md)s，设置 OP=NEW。

### **时谐涡流分析的可选、互斥参数：**

IMAGINARY

包含此参数以定义体积电流密度的虚部（异相）。

REAL

包含此参数（默认）以定义体积电流密度的实部（同相）。

### **在耦合热电或耦合热电结构分析中定义分布电流密度的数据行：**

**第一行：**

根据需要重复此数据行，以定义各个单元或单元集合的电流密度。

### **在涡流或静磁分析中定义体积电流密度的数据行：**

**第一行：**

根据需要重复此数据行，以定义各个单元或单元集合的体积电流密度。




