# *CONTACT INTERFERENCE






### *CONTACT INTERFERENCE规定接触对和接触单元的随时间变化的允许干涉。

此选项用于为接触对和接触单元规定随时间变化的允许干涉。它适用于解决接触体存在大量初始过盈的问题。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**历史数据 

**级别：**步骤

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["在 Abaqus/Standard 中建模接触干涉配合，" Abaqus 分析用户指南第 36.3.4 节](../usb/usb-link.md#usb-cni-acontactinterference)
- ["调整 Abaqus/Standard 接触对的初始表面位置并指定初始间隙，" Abaqus 分析用户指南第 36.3.5 节](../usb/usb-link.md#usb-cni-aadjustsurfaces)

### **可选参数：**

AMPLITUDE

将此参数设置为在步骤中定义规定干涉大小的幅值曲线名称。如果省略此参数，则规定干涉将在步骤开始时立即应用并在线性分布于整个步骤中减少到零。

OP

设置 OP=MOD（默认）以保留现有的 [*CONTACT INTERFERENCE](ch03abk66.md) 定义，此选项定义要添加或修改的接触干涉。设置 OP=NEW 以移除先前步骤中定义的所有 [*CONTACT INTERFERENCE](ch03abk66.md) 定义。

SHRINK

包含此参数以调用自动收缩配合能力。此能力仅能在分析的第一步中使用。当包含此参数时，除了应用此选项的接触对外，不需要其他数据。此外，任何指定的 AMPLITUDE 引用都将被忽略。

TYPE

使用此参数指定规定干涉将应用于接触对还是接触单元。设置 TYPE=CONTACT PAIR（默认）为接触对指定接触干涉。设置 TYPE=ELEMENT 为接触单元指定接触干涉。

### **为接触对定义允许接触干涉的数据行（TYPE=CONTACT PAIR）：**

**第一行：**

根据需要重复此数据行以指定额外的接触对。每一行定义一个接触对之间的不同接触干涉。

### **为接触单元定义允许接触干涉的数据行（TYPE=ELEMENT）：**

**第一行：**

根据需要重复此数据行以指定包含接触单元的额外单元集。




