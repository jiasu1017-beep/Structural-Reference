# *DFLOW





### *DFLOW指定渗流固结分析中的分布渗流量。

此选项用于在固结问题中输入渗流量（垂直于模型表面的孔隙流体速度）。

**产品：**Abaqus/Standard  Abaqus/CFD  Abaqus/CAE  

**类型：**历史数据 

**级别：**步骤

**Abaqus/CAE：**载荷模块

##### **参考：**

- ["孔隙流体流动，" Abaqus分析用户指南第34.4.7节](../usb/usb-link.md#usb-prc-pporousflow)
- ["DFLOW，" Abaqus用户子程序参考指南第1.1.2节](../sub/sub-link.md#sub-rtn-udflow)

### **可选参数：**

AMPLITUDE

将此参数设置为定义步骤期间渗流量大小的 [*AMPLITUDE](ch01abk09.md) 曲线名称。对于均匀渗流类型，如果省略此参数，则参考值将在步骤开始时立即应用或线性地跨越步骤应用，具体取决于分配给 [*STEP](ch18abk36.md) 选项上 AMPLITUDE 参数的值（请参见["定义分析，" Abaqus分析用户指南第6.1.2节](../usb/usb-link.md#usb-anl-aover)）。对于在用户子程序 [`DFLOW`](../sub/sub-link.md#sub-xsl-dflow) 中定义的流量，振幅引用将被忽略。

OP

设置 OP=MOD（默认）以保留现有的 [*DFLOW](ch04abk19.md)s，此选项修改现有流量或定义额外流量。

如果应该移除模型上所有现有的 [*DFLOW](ch04abk19.md)s，设置 OP=NEW。可以定义新流量。

### **定义均匀渗流的数据行：**

**第一行：**

根据需要重复此数据行，以定义各个单元或单元集合的均匀渗流。

### **定义非均匀渗流的数据行：**

**第一行：**

非均匀渗流大小通过用户子程序 [`DFLOW`](../sub/sub-link.md#sub-xsl-dflow) 定义。

根据需要重复此数据行，以定义各个单元或单元集合的非均匀渗流。




