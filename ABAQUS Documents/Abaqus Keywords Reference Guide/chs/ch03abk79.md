# *CO-SIMULATION CONTROLS






### *CO-SIMULATION CONTROLS指定联合仿真的耦合和会合方案。

此选项用于指定联合仿真的耦合和会合方案。它必须与 [*CO-SIMULATION](ch03abk78.md) 选项结合使用，以识别为其指定联合仿真控制的分析程序。当在 [*CO-SIMULATION](ch03abk78.md) 选项上使用 PROGRAM=ABAQUS 或 PROGRAM=MPCCI 时，此选项是联合仿真所必需的。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**类型：**历史数据 

**级别：**步骤

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["联合仿真：概述，" Abaqus 分析用户指南第 17.1.1 节](../usb/usb-link.md#usb-anl-acosimulationover)
- ["准备 Abaqus 分析以进行联合仿真，" Abaqus 分析用户指南第 17.2.1 节](../usb/usb-link.md#usb-anl-acosimulationprep)
- ["结构到结构联合仿真，" Abaqus 分析用户指南第 17.3.1 节](../usb/usb-link.md#usb-anl-acosimabqtoabq)
- ["流体到结构和共轭热传递联合仿真，" Abaqus 分析用户指南第 17.3.2 节](../usb/usb-link.md#usb-anl-acosimcfdtoabq)
- [*CO-SIMULATION](ch03abk78.md)
- [*CO-SIMULATION REGION](ch03abk80.md)

### 为 CO-SIMULATION、PROGRAM=ABAQUS 指定耦合和会合方案

### **必需参数：**

NAME

将此参数设置为一个标签，用于识别联合仿真控制。同一输入文件中的所有联合仿真控制名称必须唯一。

### **可选参数：**

FACTORIZATION FREQUENCY

此参数与 TIME INCREMENTATION=SUBCYCLE 参数结合使用时有效。

设置 FACTORIZATION FREQUENCY=EXPLICIT INCREMENT（默认）以指定每 Abaqus/Explicit 增量对接口矩阵进行分解。

设置 FACTORIZATION FREQUENCY=STANDARD INCREMENT 以指定每 Abaqus/Standard 增量对接口矩阵进行一次分解。

TIME INCREMENTATION

设置 TIME INCREMENTATION=SUBCYCLE（默认）以允许 Abaqus 多次步进一个或多个增量，以达到与外部程序交换数据的下一个目标时间。此设置仅在 Abaqus/Standard 或 Abaqus/Explicit 分析中有效。

设置 TIME INCREMENTATION=LOCKSTEP 以强制 Abaqus 仅步进一个增量以达到下一个目标时间。

### **此选项没有关联的数据行。**

### 为 CO-SIMULATION、PROGRAM=MPCCI 指定耦合和会合方案

### **必需参数：**

NAME

将此参数设置为一个标签，用于识别联合仿真控制。同一输入文件中的所有联合仿真控制名称必须唯一。

STEP SIZE

将此参数设置为一个值，以定义在整个耦合仿真中使用的恒定耦合步骤大小。

设置 STEP SIZE=IMPORT 以使 Abaqus 从外部程序为下一个耦合步骤导入耦合步骤大小。

设置 STEP SIZE=EXPORT 以使 Abaqus 向外部程序导出耦合步骤大小以进行下一个耦合步骤。

设置 STEP SIZE=MAX 以使 Abaqus 基于 Abaqus 和外部程序的建议耦合步骤大小选择最大耦合步骤大小。

设置 STEP SIZE=MIN 以使 Abaqus 基于 Abaqus 和外部程序的建议耦合步骤大小选择最小耦合步骤大小。

### **此选项没有关联的数据行。**




