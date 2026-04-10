# *KINEMATIC COUPLING






### *KINEMATIC COUPLING将一组节点的所有或特定自由度约束到参考节点的刚体运动。

此选项用于在节点或节点集的自由度与由参考节点定义的刚体运动之间施加约束。提供这种类型的运动约束的首选方法是使用 [*KINEMATIC](ch11abk02.md) 选项的 [*COUPLING](ch03abk83.md) 选项。

**产品：** Abaqus/Standard  Abaqus/CAE  

**类型：** 模型数据  

**级别：** 零件、零件实例、装配  

**Abaqus/CAE：** 不支持；此选项已被与运动约束结合使用的耦合约束所取代。

##### **参考文献：**

- ["运动约束：概述，" Abaqus Analysis User's Guide 第 35.1.1 节](../usb/usb-link.md#usb-cni-pkinematic)

### **必需参数：**

REF NODE

将此参数设置为参考节点的节点编号或包含参考节点的节点集名称。如果选择节点集名称，则该节点集必须恰好包含一个节点。

### **可选参数：**

ORIENTATION

将此参数设置为给 [*ORIENTATION](ch15abk01.md) 定义（["方向，" Abaqus Analysis User's Guide 第 2.2.5 节](../usb/usb-link.md#usb-int-corientation)）的名称，该定义指定定义约束自由度的局部系统的初始方向。

### **指定要约束的节点和自由度的数据行：**

**第一行：**

根据需要重复此数据行，以指定不同节点和自由度的约束。当指定了 ORIENTATION 参数时，自由度位于初始配置中的参考局部系统中；否则，它们位于全局系统中。在这两种情况下，这些方向将在大位移分析中随参考节点旋转（当在 [*STEP](ch18abk36.md) 选项上包含 NLGEOM 参数时）。




