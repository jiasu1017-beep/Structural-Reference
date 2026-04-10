# *DSA CONTROLS





### *DSA CONTROLS设置DSA求解控制。

此选项可用于控制DSA计算的精度或效率。

**产品：**Abaqus/Design  

**类型：**模型数据或历史数据  

**级别：**模型、步骤

##### **参考：**

- ["设计灵敏度分析，" Abaqus分析用户指南第19.1.1节](../usb/usb-link.md#usb-anl-adsa)

### **可选参数：**

FORMULATION

使用此参数在多增量分析中选择设计灵敏度分析公式类型。如果用作历史数据，则此参数将被忽略。

设置 FORMULATION=INCREMENTAL（默认）以选择增量设计灵敏度分析。

设置 FORMULATION=TOTAL 以选择总设计灵敏度分析。

RESET

包含此参数以将值重置为模型数据选项上指定的值，或者如果不存在模型数据选项，则重置为原始默认值。此操作在将任何其他更改应用于值之前生效。

SIZING FREQUENCY

将此参数设置为执行默认扰动 sizing算法的频率（增量（静态步骤）或模式（频率步骤））。对于执行DSA计算的每个步骤的第一个增量或第一个特征模式，即使 SIZING FREQUENCY 设置为0，算法也将始终执行。默认值为 SIZING FREQUENCY=0。

TOLERANCE

将此参数设置为要与默认扰动 sizing算法一起使用的容差。默认值为 TOLERANCE=![](../graphics/key_eqn00636.gif)。

### **覆盖选定设计参数的默认扰动 sizing算法的数据行（对于这些设计参数，SIZING FREQUENCY 和 TOLERANCE 参数将被忽略）：**

**第一行：**

为每个要覆盖默认算法的设计参数重复此数据行。




