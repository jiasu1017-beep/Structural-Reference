# *CO-SIMULATION






### *CO-SIMULATION识别用于与 Abaqus 联合仿真的分析程序。

此选项用于识别用于与 Abaqus 联合仿真的分析程序以及用于定义耦合和会合方案的联合仿真控制。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**类型：**历史数据 

**级别：**步骤

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["联合仿真：概述，" Abaqus 分析用户指南第 17.1.1 节](../usb/usb-link.md#usb-anl-acosimulationover)
- ["准备 Abaqus 分析以进行联合仿真，" Abaqus 分析用户指南第 17.2.1 节](../usb/usb-link.md#usb-anl-acosimulationprep)
- ["结构到结构联合仿真，" Abaqus 分析用户指南第 17.3.1 节](../usb/usb-link.md#usb-anl-acosimabqtoabq)
- ["流体到结构和共轭热传递联合仿真，" Abaqus 分析用户指南第 17.3.2 节](../usb/usb-link.md#usb-anl-acosimcfdtoabq)
- [*CO-SIMULATION CONTROLS](ch03abk79.md)
- [*CO-SIMULATION REGION](ch03abk80.md)

### **必需参数：**

NAME

将此参数设置为一个标签，用于引用联合仿真事件。联合仿真名称遵守标签的命名约定（请参阅 ["输入语法规则，" Abaqus 分析用户指南第 1.2.1 节](../usb/usb-link.md#usb-int-iinputsyntax)），但不能以数字开头。

PROGRAM

设置 PROGRAM=MULTIPHYSICS 以在 Abaqus 和 SIMULIA 联合仿真引擎之间交换数据，后者可以与支持 SIMULIA 联合仿真引擎的第三方分析程序交换数据。此参数也应于 Abaqus/CFD 到 Abaqus/Standard 或 Abaqus/CFD 到 Abaqus/Explicit 的联合仿真。

设置 PROGRAM=ABAQUS 以在 Abaqus/Standard 到 Abaqus/Explicit 联合仿真中与另一个 Abaqus 分析交换数据。

设置 PROGRAM=DIRECT 以在 Abaqus 和某些第三方分析程序之间交换数据。有关更多信息，请参阅相应的第三方程序文档。

设置 PROGRAM=MPCCI 以在 Abaqus 和基于网格的并行代码耦合接口（MpCCI）之间交换数据，后者可以与支持 MpCCI 的第三方分析程序交换数据。

### **可选参数：**

CONTROLS

当 PROGRAM=ABAQUS 或 PROGRAM=MPCCI 时需要此参数。

将此参数设置用于定义耦合和会合方案的联合仿真控制名称。

对于 PROGRAM=DIRECT 或 PROGRAM=MULTIPHYSICS，联合仿真控制在联合仿真配置文件中定义。

### **此选项没有关联的数据行。**




