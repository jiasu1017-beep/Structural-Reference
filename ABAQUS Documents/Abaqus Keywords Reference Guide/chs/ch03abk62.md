# *CONTACT FORMULATION






### *CONTACT FORMULATION为通用接触算法指定非默认接触公式。

此选项用于修改通用接触算法域内特定接触相互作用的接触公式。必须与 [*CONTACT](ch03abk54.md) 选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**Abaqus/Standard 中的模型数据；Abaqus/Explicit 中的模型数据或历史数据  

**级别：**Abaqus/Standard 中的模型；Abaqus/Explicit 中的模型或步骤

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["Abaqus/Standard 中通用接触的数值控制，" Abaqus 分析用户指南第 36.2.6 节](../usb/usb-link.md#usb-cni-agenlcontnumcontrolsstd)
- ["Abaqus/Explicit 中通用接触的接触公式，" Abaqus 分析用户指南第 38.2.1 节](../usb/usb-link.md#usb-cni-acontactformassign)
- [*CONTACT](ch03abk54.md)

### **必需参数：**

TYPE

设置 TYPE=EDGE TO EDGE 以控制 Abaqus/Standard 中使用的边缘到边缘（梁到梁）接触公式。此设置不适用于 Abaqus/Explicit。

设置 TYPE=MASTER SLAVE ROLES 以控制 Abaqus/Standard 中特定相互作用的主-从角色。此设置不适用于 Abaqus/Explicit。

设置 TYPE=PURE MASTER-SLAVE 以指定接触相互作用应使用纯主-从加权，用于 Abaqus/Explicit 中的特定节点到面接触表面对。此设置不适用于 Abaqus/Standard。

设置 TYPE=POLARITY 以选择在 Abaqus/Explicit 中双面元素的哪些边将考虑与另一个表面进行节点到面或欧拉-拉格朗日接触。此设置不适用于 Abaqus/Standard。

设置 TYPE=SLIDING TRANSITION 以控制 Abaqus/Standard 中特定相互作用在滑动时表面到表面公式的平滑度。此设置不适用于 Abaqus/Explicit。

### **可选参数：**

FORMULATION

此参数仅在 TYPE=EDGE TO EDGE 时适用。它用于激活在全球范围内用于边缘到边缘（梁到梁）接触的接触公式。

设置 FORMULATION=CROSS 以激活一种边缘到边缘接触公式，适用于非平行梁，将接触法线方向基于相应梁轴向方向的叉乘。

设置 FORMULATION=RADIAL 以激活一种边缘到边缘接触公式，适用于几乎平行的梁，将接触法线方向基于梁径向方向。

设置 FORMULATION=BOTH 以激活两种边缘到边缘接触公式。

设置 FORMULATION=NO（默认）以停用边缘到边缘接触公式。

### **用于在 Abaqus/Standard 中控制接触相互作用主-从角色的数据行：**

**第一行：**

根据需要重复此数据行。

### **用于在 Abaqus/Explicit 中为接触相互作用分配纯主-从角色的数据行：**

**第一行：**

根据需要重复此数据行。

### **用于在 Abaqus/Explicit 中为接触相互作用分配极性的数据行：**

**第一行：**

根据需要重复此数据行。

### **用于在 Abaqus/Standard 中控制接触相互作用在滑动时表面到表面公式平滑度的数据行：**

**第一行：**

根据需要重复此数据行。

### **在 Abaqus/Standard 中控制边缘到边缘（梁到梁）接触公式没有数据行。**




