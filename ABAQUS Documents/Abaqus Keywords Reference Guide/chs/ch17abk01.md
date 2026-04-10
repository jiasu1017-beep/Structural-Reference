# *RADIATE







### *RADIATE在热传递分析中指定辐射条件。

此选项用于在完全耦合热应力分析中的非凹面与非反射环境之间施加辐射边界条件。在Abaqus/Standard中，它还用于热传递、耦合热电和耦合热电结构分析。

它必须与[*PHYSICAL CONSTANTS](ch16abk09.md)选项结合使用，该选项用于定义Stefan-Boltzmann常数。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**历史数据  

**级别：**步骤  

**Abaqus/CAE：**相互作用模块

##### **参考：**

- ["热载荷，" Abaqus Analysis User's Guide第34.4.4节](../usb/usb-link.md#usb-prc-pthermal)

### **可选参数：**

AMPLITUDE

将此参数设置为给出环境温度随时间变化的[*AMPLITUDE](ch01abk09.md)选项名称。

如果在Abaqus/Standard分析中省略此参数，则参考幅值将在步骤开始时立即应用或线性应用于整个步骤，具体取决于[*STEP](ch18abk36.md)选项上分配给AMPLITUDE参数的值（参见["定义分析，" Abaqus Analysis User's Guide第6.1.2节](../usb/usb-link.md#usb-anl-aover)）。如果在Abaqus/Explicit分析中省略此参数，则数据行上给出的参考幅值将应用于整个步骤。

OP

设置OP=MOD（默认）以保留现有的[*RADIATE](ch17abk01.md)定义，此选项可修改现有辐射条件或定义额外的辐射条件。

如果应移除应用于模型的所有现有的[*RADIATE](ch17abk01.md)定义，则设置OP=NEW。

REGION TYPE

此参数仅适用于Abaqus/Explicit分析。

此参数仅与应用于自适应网格域边界的辐射条件相关。如果辐射条件应用于自适应网格域内部的表面，则表面上的节点将沿所有方向随材料移动（它们将是非自适应的）。Abaqus/Explicit将自动在被定义辐射条件作用的表面上创建边界区域。

设置REGION TYPE=LAGRANGIAN（默认）以将辐射条件应用于Lagrangian边界区域。Lagrangian边界区域的边缘将跟随材料，同时允许沿边缘和区域内部进行自适应网格划分。

设置REGION TYPE=SLIDING以将辐射条件应用于滑动边界区域。滑动边界区域的边缘将在材料上滑动。自适应网格划分将沿边缘和区域内部发生。网格约束通常应用于滑动边界区域的边缘以将其空间固定。

设置REGION TYPE=EULERIAN以将辐射条件应用于Eulerian边界区域。此选项用于创建材料可以流过的边界区域。必须沿垂直于Eulerian边界区域的方向使用网格约束，以允许材料流过该区域。如果没有应用网格约束，Eulerian边界区域的行为将与滑动边界区域相同。

### **定义辐射条件的数据行：**

**第一行：**

根据需要重复此数据行以定义辐射条件。
