# *CFLOW






### *CFLOW指定集中流体流量。

此选项用于向任何节点（包括固结问题中富集元素中的虚拟节点）施加集中流体流量。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**历史数据 

**级别：**步骤

**Abaqus/CAE: **载荷模块

##### **参考：**

- ["耦合孔隙流体扩散和应力分析，" Abaqus 分析用户指南第 6.8.1 节](../usb/usb-link.md#usb-anl-acoupdiffstress)
- ["静地应力状态，" Abaqus 分析用户指南第 6.8.2 节](../usb/usb-link.md#usb-anl-ageostatstress)
- ["孔隙流体流量，" Abaqus 分析用户指南第 34.4.7 节](../usb/usb-link.md#usb-prc-pporousflow)
- ["使用扩展有限元法将不连续性建模为富集特征，" Abaqus 分析用户指南第 10.7.1 节](../usb/usb-link.md#usb-anl-aenrichment)

### **可选参数：**

AMPLITUDE

将此参数设置为在步骤中定义流量大小的幅值曲线名称。如果省略此参数，则根据 [*STEP](ch18abk36.md) 选项上 AMPLITUDE 参数分配的值，参考大小将在步骤开始时立即应用或在线性分布于整个步骤（请参阅 ["定义分析，" Abaqus 分析用户指南第 6.1.2 节](../usb/usb-link.md#usb-anl-aover)）。

OP

设置 OP=MOD（默认）以保留现有的 [*CFLOW](ch03abk15.md)，此选项修改现有的集中流量或定义额外的集中流量。

设置 OP=NEW 以移除模型上所有现有的 [*CFLOW](ch03abk15.md)。

PHANTOM

此参数仅适用于 Abaqus/Standard 中的富集元素。

设置 PHANTOM=NODE 以向富集元素中最初与指定真实节点重合的虚拟节点施加集中流量。

设置 PHANTOM=EDGE 以向富集元素中两个指定真实角节点之间的元素边缘处的虚拟节点施加集中流量。

### **未使用 PHANTOM 参数时定义集中流量的数据行：**

**第一行：**

根据需要重复此数据行以定义集中流量。

### **PHANTOM=NODE 时定义集中流量的数据行：**

**第一行：**

根据需要重复此数据行以定义集中流量。

### **PHANTOM=EDGE 时定义集中流量的数据行：**

**第一行：**

根据需要重复此数据行以定义集中流量。




