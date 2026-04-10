# *CONTACT CLEARANCE






### *CONTACT CLEARANCE定义接触间隙属性。

此选项用于创建接触间隙属性定义。接触间隙属性将管理通过 [*CONTACT CLEARANCE ASSIGNMENT](ch03abk56.md) 选项分配这些属性的任何接触相互作用。

**产品：**Abaqus/Explicit  

**类型：**模型数据  

**级别：**模型  

##### **参考：**

- ["控制 Abaqus/Explicit 中通用接触的初始接触状态，" Abaqus 分析用户指南第 36.4.4 节](../usb/usb-link.md#usb-cni-aadjustgeneral)
- [*CONTACT](ch03abk54.md)
- [*CONTACT CLEARANCE ASSIGNMENT](ch03abk56.md)
- [*DISTRIBUTION](ch04abk29.md)

### **必需参数：**

NAME

将此参数设置为一个标签，用于引用此接触间隙属性。

### **可选参数：**

ADJUST

设置 ADJUST=YES（默认）以通过调整节点坐标来解决间隙，而不会在模型中产生应变。ADJUST=YES 仅能用于在分析第一步中定义的间隙。

设置 ADJUST=NO 以存储接触偏移，以便能够满足间隙而不调整节点坐标。

CLEARANCE

将此参数设置为整个从节点集的初始间隙值或节点分布的名称（请参阅 ["分布定义，" Abaqus 分析用户指南第 2.8.1 节](../usb/usb-link.md#usb-int-adefiningdistributions)）。对于实体元素表面上的从节点，间隙值必须为非负。默认值为 0.0。

SEARCH ABOVE

将此参数设置为将在其上搜索要包含在间隙规范中的从节点的距离。实体元素的默认值约为附加到从节点的元素尺寸的十分之一。结构元素（如壳单元）的默认值是与从节点关联的厚度。

如果使用了 SEARCH NSET 参数，则不能使用此参数。

SEARCH BELOW

将此参数设置为将在其下搜索要包含在间隙规范中的从节点的距离。实体元素的默认值约为附加到从节点的元素尺寸的十分之一。结构元素（如壳单元）的默认值是与从节点关联的厚度。

如果使用了 SEARCH NSET 参数，则不能使用此参数。

SEARCH NSET

将此参数设置为一个节点集的名称，该节点集包含要包含在间隙规范中的从节点。指定的间隙将在此节点集中的所有从节点上强制执行，无论它们是在各自主表面的上方还是下方。此参数还可用于识别 VCCT 分析中初始粘结的节点。

如果使用了 SEARCH ABOVE 或 SEARCH BELOW 参数，则不能使用此参数。

### **此选项没有关联的数据行。**




