# *CONNECTOR LOAD






### *CONNECTOR LOAD为连接器单元中可用的相对运动分量指定载荷。

此选项用于向连接器单元中可用的相对运动分量施加集中力和力矩。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**历史数据 

**级别：**步骤

**Abaqus/CAE: **载荷模块

##### **参考：**

- ["连接器驱动，" Abaqus 分析用户指南第 31.1.3 节](../usb/usb-link.md#usb-elm-econnectoractuation)

### **可选参数：**

AMPLITUDE

将此参数设置为在步骤中定义载荷大小的幅值曲线名称。

如果在 Abaqus/Standard 分析中省略此参数，则根据 [*STEP](ch18abk36.md) 选项上 AMPLITUDE 参数分配的值，参考大小将在步骤开始时立即应用或在线性分布于整个步骤（请参阅 ["定义分析，" Abaqus 分析用户指南第 6.1.2 节](../usb/usb-link.md#usb-anl-aover)）。如果在 Abaqus/Explicit 分析中省略此参数，参考大小将在步骤开始时立即应用。

LOAD CASE

此参数仅适用于 Abaqus/Standard 分析。

将此参数设置为载荷工况号。此参数在 [*RANDOM RESPONSE](ch17abk07.md) 分析中使用（["随机响应分析，" Abaqus 分析用户指南第 6.3.11 节](../usb/usb-link.md#usb-anl-arandomresponse)），此时它是 [*CORRELATION](ch03abk77.md) 选项上载荷工况的交叉引用。该参数的值在所有其他过程中被忽略。

OP

设置 OP=MOD（默认）以保留现有的 [*CONNECTOR LOAD](ch03abk45.md)，此选项修改现有的连接器载荷或定义额外的连接器载荷。

设置 OP=NEW 以移除模型上所有现有的 [*CONNECTOR LOAD](ch03abk45.md)。可以定义新的连接器载荷。

### **矩阵生成和稳态动力学分析（直接、模态或子空间）的可选互斥参数：**

IMAGINARY

包含此参数以定义载荷的虚部（异相）部分。

REAL

包含此参数（默认）以定义载荷的实部（同相）部分。

### **用于为特定相对运动分量定义连接器载荷的数据行：**

**第一行：**

根据需要重复此数据行以定义连接器载荷。




