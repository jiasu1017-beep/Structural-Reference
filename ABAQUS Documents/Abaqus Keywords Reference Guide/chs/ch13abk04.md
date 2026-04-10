# *MASS DIFFUSION









### *MASS DIFFUSION瞬态或稳态非耦合质量扩散分析。

此选项用于控制非耦合瞬态或稳态质量扩散分析。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**历史数据  

**级别：**步骤

**Abaqus/CAE：**步骤模块

##### **参考：**

- ["质量扩散分析，" Abaqus Analysis User's Guide第6.9.1节](../usb/usb-link.md#usb-anl-amassdiffusion)

### **可选参数：**

DCMAX

将此参数设置为允许在增量中的最大归一化浓度变化。Abaqus/Standard将限制时间步长以确保在任何分析增量中任何节点（边界条件节点除外）都不会超过此值。如果省略DCMAX参数，则使用固定时间增量。

END

设置END=PERIOD（默认）以分析数据行上指定的整个时间周期。设置END=SS以在达到稳态时结束分析。

STEADY STATE

包含此参数以选择稳态分析。如果省略此参数，则假定为瞬态分析。

### **定义质量扩散分析时间步进的数据行：**

**第一行（也是唯一一行）：**



