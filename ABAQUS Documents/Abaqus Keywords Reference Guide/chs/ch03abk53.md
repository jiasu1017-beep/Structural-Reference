# *CONSTRAINT CONTROLS






### *CONSTRAINT CONTROLS重置过约束检查控制。

**警告：**使用此选项指定用于强制执行与连接器单元关联的约束的技术。否则，除非用户确定模型没有过约束，否则不应使用此选项。过约束意味着应用多个一致的或不一致的运动约束。许多模型具有被过约束的节点自由度，此类过约束可能导致不准确的求解或收敛失败。默认情况下，模型将被检查过约束。一致的过约束将在可能时移除，而如果检测到不一致的过约束，则会发出错误消息。

**产品：**Abaqus/Standard  

**类型：**模型数据或历史数据  

**级别：**模型、步骤

##### **参考：**

- ["过约束检查，" Abaqus 分析用户指南第 35.6.1 节](../usb/usb-link.md#usb-cni-aoverconstraintchecks)
- ["连接器：概述，" Abaqus 分析用户指南第 31.1.1 节](../usb/usb-link.md#usb-elm-econnectoroverview)
- ["网格绑定约束，" Abaqus 分析用户指南第 35.3.1 节](../usb/usb-link.md#usb-cni-ptiedconstraint)
- ["与 Abaqus/Standard 中接触建模相关的常见困难，" Abaqus 分析用户指南第 39.1.2 节](../usb/usb-link.md#usb-cni-acontacttrouble)

### **可选和互斥参数（仅限模型数据）：**

DELETE SLAVE

包含此参数以删除与绑定从节点关联的接触单元。

NO CHANGES

包含此参数以执行过约束检查，但阻止 Abaqus 更改模型以移除冗余约束。将生成关于过约束的详细消息。如果省略此参数，Abaqus 将尝试自动更改模型。

NO CHECKS

包含此参数以禁止此模型的过约束检查。如果省略此参数，将执行过约束检查。

PRINT

设置 PRINT=YES 以将约束链打印到消息文件。如果设置 PRINT=NO（默认），则不会打印约束链。

### **可选参数（仅限历史数据）：**

CHECK FREQUENCY

将此参数设置为所需的过约束检查频率（以增量为单位）。除非过约束检查被禁止，否则过约束检查总是在步骤的第一个增量开始时执行。默认值为 CHECK FREQUENCY=1，这样每个增量都会执行过约束检查。设置 CHECK FREQUENCY=0 以禁止此步骤中的过约束检查。

TERMINATE ANALYSIS

设置 TERMINATE ANALYSIS=NO（默认）以允许在遇到过约束时继续分析。将发出关于过约束的详细消息。

如果在线性扰动步骤（不需要迭代）中使用了 FIRST OCCURRENCE 或 CONVERGED，则在遇到过约束时将在第一个增量中停止分析。

设置 TERMINATE ANALYSIS=FIRST OCCURRENCE 以在非线性通用步骤中第一次遇到过约束时终止分析。

设置 TERMINATE ANALYSIS=CONVERGED 以在非线性通用步骤的增量中达到收敛且存在过约束时终止分析。

如果在线性扰动步骤中使用 FIRST OCCURRENCE 或 CONVERGED（其中不需要迭代），则在遇到过约束时将在第一个增量中停止分析。

### **此选项没有关联的数据行。**




