# *CONTACT CONTROLS ASSIGNMENT






### *CONTACT CONTROLS ASSIGNMENT为通用接触算法分配接触控制。

此选项用于在 Abaqus/Explicit 中修改通用接触算法域内特定接触相互作用的接触控制。必须与 [*CONTACT](ch03abk54.md) 选项结合使用。

**产品：**Abaqus/Explicit  

**类型：**模型数据或历史数据  

**级别：**模型、步骤

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["Abaqus/Explicit 中通用接触的接触控制，" Abaqus 分析用户指南第 36.4.5 节](../usb/usb-link.md#usb-cni-acontactcontrolsassign)
- [*CONTACT](ch03abk54.md)

### **必需的互斥参数：**

AUTOMATIC OVERCLOSURE RESOLUTION

包含此参数以在初始过盈解析期间存储偏移而不是调整节点，从而在通用接触域中的表面对之间进行处理。

CONTACT THICKNESS REDUCTION

设置 CONTACT THICKNESS REDUCTION=SELF 以将自动接触厚度减少限制为仅潜在自接触的区域和壳表面的周长。

设置 CONTACT THICKNESS REDUCTION=NOPERIMSELF 以将自动接触厚度减少限制为仅潜在自接触的区域。

NODAL EROSION

设置 NODAL EROSION=NO（默认）以在所有接触面和边缘被侵蚀后，将基于单元的表面的节点保留为点质量。

设置 NODAL EROSION=YES 以在所有接触面和边缘被侵蚀后，从通用接触域中删除基于单元的表面的节点。

ROTATIONAL TERMS

设置 ROTATIONAL TERMS=NONE（默认）以忽略壳和梁厚度偏移对摩擦接触的影响。

对于摩擦接触，设置 ROTATIONAL TERMS=STRUCTURAL 以在滑动增量计算中考虑壳和梁厚度偏移的增量旋转，并对由于壳和梁厚度而偏离接触界面的节点施加力矩。

TYPE

设置 TYPE=ENHANCED EDGE TRACKING（默认）以激活边缘到边缘接触的默认跟踪算法。

设置 TYPE=EDGE TRACKING 以激活边缘到边缘接触的替代跟踪算法。

设置 TYPE=FOLD TRACKING 以激活节点到面接触的非默认跟踪算法。

设置 TYPE=FOLD INVERSION CHECK 以激活折叠反转检查。

设置 TYPE=SCALE PENALTY 以分配一个缩放因子给默认惩罚刚度。

### **可选参数：**

SEEDING

此参数控制在耦合欧拉-拉格朗日分析期间如何在拉格朗日表面上创建接触种子。

设置 SEEDING=GLOBAL（如果未激活自适应网格细化，则为默认）以基于整个欧拉网格中最小的欧拉单元尺寸在拉格朗日表面上创建种子；播种在分析开始时执行一次。

设置 SEEDING=LOCAL 以基于拉格朗日面附近最小的欧拉单元尺寸在拉格朗日表面上创建种子；一旦检测到附近的欧拉单元，就立即对每个面执行一次播种。

设置 SEEDING=DYNAMIC（如果激活自适应网格细化，则为默认）以基于拉格朗日面附近最小的欧拉单元尺寸在拉格朗日表面上创建种子；种子密度在分析过程中更新。

### **AUTOMATIC OVERCLOSURE RESOLUTION 的数据行：**

**第一行：**

根据需要重复此数据行。如果接触控制分配重叠，则最后一个分配适用于重叠区域。

### **当指定了 NODAL EROSION 参数时，此选项不使用数据行。**

### **TYPE=FOLD TRACKING 的数据行：**

**第一行：**

根据需要重复此数据行。

### **TYPE=FOLD INVERSION CHECK 的数据行：**

**第一行：**

根据需要重复此数据行。

### **TYPE=SCALE PENALTY 的数据行：**

**第一行：**

根据需要重复此数据行。如果接触控制分配重叠，则最后一个分配适用于重叠区域。




