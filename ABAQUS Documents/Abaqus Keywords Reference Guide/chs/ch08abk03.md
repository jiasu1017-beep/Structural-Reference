# *HEAT TRANSFER






### *HEAT TRANSFER瞬态或稳态非耦合热传递分析。

此选项用于控制瞬态或稳态响应的非耦合热传递。

**产品：** Abaqus/Standard  Abaqus/CFD  Abaqus/CAE  

**类型：** 历史数据  

**级别：** 步骤  

**Abaqus/CAE：** Step 模块

##### **参考文献：**

- ["非耦合热传递分析，" Abaqus Analysis User's Guide 第 6.5.2 节](../usb/usb-link.md#usb-anl-aheattransfer)
- ["空腔辐射，" Abaqus Analysis User's Guide 第 41.1.1 节](../usb/usb-link.md#usb-cni-acavityradiation)

### **激活 Abaqus/CFD 实体热传递分析的必需参数：**

CENTERING

设置 CENTERING=ELEMENT 以选择以单元为中心的热传递分析。

TYPE

设置 TYPE=THERMAL FLOW 以指示使用 Abaqus/CFD 进行热传递分析。

### **可选参数：**

DELTMX

此参数仅适用于 Abaqus/Standard 分析。

将此参数设置为瞬态热传递分析中增量期间允许的最大温度变化。Abaqus/Standard 将限制时间步长，以确保在步骤的任何增量期间，任何节点（温度自由度通过边界条件、MPC 等约束的节点除外）都不会超过此值。如果省略 DELTMX 参数，将使用固定时间增量。

END

此参数仅适用于 Abaqus/Standard 分析。

设置 END=PERIOD（默认）以分析特定时间段。设置 END=SS 以在达到稳态时结束分析。

此参数仅与瞬态分析相关。

STEADY STATE

包含此参数以选择稳态分析。如果省略此参数，则假定为瞬态分析。如果在 Abaqus/CFD 实体热传递分析中使用此参数，则数据行上给出的值将被忽略。

### **空腔辐射分析的可选参数：**

MXDEM

此参数仅适用于 Abaqus/Standard 分析。

将此参数设置为增量期间随温度和场变量允许的最大发射率变化。如果超过此值，Abaqus/Standard 将减少增量，直到发射率的最大变化小于指定值。如果省略此参数，则使用默认值 0.1。

### **控制纯热传递分析的增量和稳态条件的数据行：**

**第一（也是唯一）行：**

### **定义 Abaqus/CFD 实体热传递分析的数据行（TYPE=THERMAL FLOW）：**

**第一（也是唯一）行：**




