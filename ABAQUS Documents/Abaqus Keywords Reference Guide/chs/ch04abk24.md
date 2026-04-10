# *DIRECT CYCLIC





### *DIRECT CYCLIC直接获取结构的稳定循环响应。

此选项用于在Abaqus/Standard中提供非线性、非等温准静态分析的直接循环过程。它还可用于预测延性体材料的渐进损伤和失效，和/或在低循环疲劳分析中预测层合复合材料中界面处的分层/脱粘生长。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**历史数据 

**级别：**步骤

**Abaqus/CAE：**步骤模块

##### **参考：**

- ["直接循环分析，" Abaqus分析用户指南第6.2.6节](../usb/usb-link.md#usb-anl-adirectcyclic)
- ["使用直接循环方法的低循环疲劳分析，" Abaqus分析用户指南第6.2.7节](../usb/usb-link.md#usb-anl-adirectcyclicfatigue)
- [*TIME POINTS](ch19abk07.md)

### **可选参数：**

CETOL

将此参数设置为基于增量开始时的条件计算和增量结束时的条件计算的蠕变应变率导出的蠕变应变增量之间的最大差异，从而控制蠕变积分的时间积分精度。

此参数可与 [*TIME POINTS](ch19abk07.md) 选项结合使用。在这种情况下，Abaqus/Standard将确保响应也在 [*TIME POINTS](ch19abk07.md) 选项上指定的每个时间点进行评估。

如果此参数和 DELTMX 参数都被省略，则将使用固定时间步进，时间增量等于初始时间增量，或精确遵循 [*TIME POINTS](ch19abk07.md) 选项上指定的时间点。

CONTINUE

设置 CONTINUE=YES 以指定当前 [*DIRECT CYCLIC](ch04abk24.md) 步骤是前一个直接循环步骤的延续。然后将前一个 [*DIRECT CYCLIC](ch04abk24.md) 步骤中获得的Fourier级数中的位移解用作当前步骤的起始值。

设置 CONTINUE=NO（默认）以将所有位移Fourier系数重置为零，从而允许应用与前一个直接循环步骤中的条件非常不同的循环载荷条件。

DELTMX

将此参数设置为在直接循环分析期间允许的增量中的最大温度变化。Abaqus/Standard将限制时间增量，以确保在该步骤的任何增量的任何节点上都不会超过此值。

此参数可与 [*TIME POINTS](ch19abk07.md) 选项结合使用。在这种情况下，Abaqus/Standard将确保响应也在 [*TIME POINTS](ch19abk07.md) 选项上指定的每个时间点进行评估。

如果此参数和 CETOL 参数都被省略，则将使用固定时间步进，时间增量等于初始时间增量，或精确遵循 [*TIME POINTS](ch19abk07.md) 选项上指定的时间点。

FATIGUE

包含此参数以使用直接循环方法结合损伤外推技术执行低循环疲劳分析。多个循环可以包含在单个直接循环分析中。该分析基于连续损伤方法对体材料中的本构点建模渐进损伤和失效。它还可用于模拟层合复合材料中界面处的分层/脱粘生长。

TIME POINTS

将此参数设置为定义结构响应将被评估的时间点的 [*TIME POINTS](ch19abk07.md) 选项的名称。

### **在不包含 FATIGUE 参数的直接循环分析中控制增量和Fourier表示的数据行：**

**第一行（也是唯一一行）：**

### **使用直接循环方法的低循环疲劳分析的数据行：**

**第一行：**

**第二行：**




