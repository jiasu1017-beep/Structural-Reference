# *COUPLING






### *COUPLING定义基于表面的耦合约束。

此选项用于在参考节点和位于表面上的节点组之间施加运动学或分布耦合约束。必须与 [*KINEMATIC](ch11abk02.md) 或 [*DISTRIBUTING](ch04abk27.md) 选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**部件、部件实例、装配  

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["耦合约束，" Abaqus 分析用户指南第 35.3.2 节](../usb/usb-link.md#usb-cni-pcoupling)
- ["基于单元的表面定义，" Abaqus 分析用户指南第 2.3.2 节](../usb/usb-link.md#usb-int-adeformablesurf)
- ["基于节点的表面定义，" Abaqus 分析用户指南第 2.3.3 节](../usb/usb-link.md#usb-int-anodebasedsurf)

### **必需参数：**

CONSTRAINT NAME

将此参数设置为一个标签，用于引用此约束。

REF NODE

将此参数设置为参考节点的节点号或包含参考节点的节点集名称。

SURFACE

将此参数设置为耦合节点所在表面的表面名称。

### **可选参数：**

INFLUENCE RADIUS

将此参数设置为中心在参考节点处的影响半径。如果省略此参数，则使用整个表面来定义耦合约束。

ORIENTATION

将此参数设置为在其中定义约束自由度局部系统的初始方向的 [*ORIENTATION](ch15abk01.md) 定义名称（["方向，" Abaqus 分析用户指南第 2.2.5 节](../usb/usb-link.md#usb-int-corientation)）。

### **此选项没有关联的数据行。**




