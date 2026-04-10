# *CO-SIMULATION REGION






### *CO-SIMULATION REGION识别 Abaqus 模型中的接口区域，并指定在联合仿真期间要交换的场。

此选项用于识别将跨其交换数据的区域，并指定要传递通过这些区域的场。它必须与 [*CO-SIMULATION](ch03abk78.md) 选项结合使用，以识别用于与 Abaqus 联合仿真的分析程序。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**类型：**历史数据 

**级别：**步骤

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["联合仿真：概述，" Abaqus 分析用户指南第 17.1.1 节](../usb/usb-link.md#usb-anl-acosimulationover)
- ["准备 Abaqus 分析以进行联合仿真，" Abaqus 分析用户指南第 17.2.1 节](../usb/usb-link.md#usb-anl-acosimulationprep)
- [*CO-SIMULATION](ch03abk78.md)

### 为 CO-SIMULATION、PROGRAM=MULTIPHYSICS 或 PROGRAM=MPCCI 定义联合仿真区域

### **必需的互斥参数：**

EXPORT

当 TYPE=NODE、SURFACE 或 VOLUME 时，包含此参数以指定要导出到耦合分析的场和伴随区域。

当 TYPE=DISCRETE 时，包含此参数以指定要导出的传感器变量。

IMPORT

当 TYPE=NODE、SURFACE 或 VOLUME 时，包含此参数以指定要从耦合分析导入的场和伴随区域。

当 TYPE=DISCRETE 时，包含此参数以指定要导入的执行器变量。

### **可选参数：**

TYPE

设置 TYPE=NODE 以定义仅包含节点的联合仿真区域。

设置 TYPE=SURFACE（默认）以定义联合仿真表面区域。

设置 TYPE=VOLUME 以定义联合仿真体积区域。

设置 TYPE=DISCRETE 以通过传感器和执行器定义耦合。

### **TYPE=NODE 的数据行：**

**第一行：**

根据需要重复此数据行以为给定区域定义超过七个场标识符。重复此选项以定义导入和/或导出场。当 PROGRAM=MULTIPHYSICS 时，只能为联合仿真声明一个节点集。

### **TYPE=SURFACE 的数据行：**

**第一行：**

根据需要重复此数据行以为给定区域定义超过七个场标识符。重复此选项以定义导入和/或导出场。当 PROGRAM=MULTIPHYSICS 时，只能为联合仿真声明一个表面。

### **TYPE=VOLUME 的数据行：**

**第一行：**

根据需要重复此数据行以为给定区域定义超过七个场标识符。重复此选项以定义导入和/或导出场。当 PROGRAM=MULTIPHYSICS 时，只能为联合仿真声明一个单元集。

### **TYPE=DISCRETE 的数据行：**

**第一行：**

根据需要重复此数据行以为给定区域定义超过七个传感器或执行器定义。数据行可以仅引用传感器名称或仅引用执行器名称，根据 IMPORT 或 EXPORT 参数设置。

### 为 CO-SIMULATION、PROGRAM=ABAQUS 定义联合仿真区域

### **可选参数：**

TYPE

设置 TYPE=SURFACE（默认）以定义基于表面的联合仿真区域。

设置 TYPE=NODE 以使用节点集定义联合仿真区域。

### **TYPE=SURFACE 的数据行：**

**第一行（也是唯一一行）：**

### **TYPE=NODE 的数据行：**

**第一行（也是唯一一行）：**




