# *FILM









### *FILM定义膜系数和相关的环境温度。

此选项用于为完全耦合的热应力分析提供膜系数和环境温度。在Abaqus/Standard中，它还用于为传热、耦合热-电和耦合热-电-结构分析提供膜系数和环境温度。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**历史数据

**级别：**步骤

**Abaqus/CAE：**相互作用模块

##### **参考：**

- ["热载荷，" Abaqus分析用户指南第34.4.4节](../usb/usb-link.md#usb-prc-pthermal)
- ["FILM，" Abaqus用户子程序参考指南第1.1.6节](../sub/sub-link.md#sub-rtn-ufilm)

### **可选参数：**

AMPLITUDE

将此参数设置为[*AMPLITUDE](ch01abk09.md)选项的名称，该选项给出环境温度 ![](../graphics/key_eqn00086.gif) 随时间的变化。

如果在Abaqus/Standard分析中省略此参数，则参考环境温度在步骤开始时立即应用或在线性范围内应用，取决于[*STEP](ch18abk36.md)选项（["定义分析，" Abaqus分析用户指南第6.1.2节](../usb/usb-link.md#usb-anl-aover)）上AMPLITUDE参数的值。如果在Abaqus/Explicit分析中省略此参数，则参考环境温度在步骤开始时立即应用。

对于非均匀膜系数（仅在Abaqus/Standard中可用），环境温度幅值在用户子程序[`FILM`](../sub/sub-link.md#sub-xsl-film)中定义，AMPLITUDE引用仅用于修改传入用户子程序的环境温度。

FILM AMPLITUDE

将此参数设置为[*AMPLITUDE](ch01abk09.md)选项的名称，该选项给出膜系数 *h* 随时间的变化。

如果在Abaqus/Standard分析中省略此参数，则参考膜系数在步骤开始时立即应用并在步骤中保持恒定，不依赖于[*STEP](ch18abk36.md)选项上分配给AMPLITUDE参数的值。如果在Abaqus/Explicit分析中省略此参数，则参考膜系数在步骤开始时立即应用。

如果膜系数通过[*FILM PROPERTY](ch06abk11.md)选项被定义为温度和场变量的函数，则FILM AMPLITUDE参数被忽略。

对于非均匀膜系数（仅在Abaqus/Standard中可用），膜系数幅值在用户子程序[`FILM`](../sub/sub-link.md#sub-xsl-film)中定义，FILM AMPLITUDE引用仅用于修改传入用户子程序的膜系数。

OP

设置 OP=MOD（默认），现有[*FILM](ch06abk10.md)保持不变，此选项修改现有膜或定义额外膜。

如果应删除应用于模型的所有现有[*FILM](ch06abk10.md)，则设置 OP=NEW。

REGION TYPE

此参数仅适用于Abaqus/Explicit分析。

此参数仅与应用于自适应网格域边界的膜条件相关。如果膜条件应用于自适应网格域内部的表面，则表面上的节点将沿所有方向随材料移动（它们将是非自适应的）。Abaqus/Explicit将在承受定义膜载荷的表面上自动创建边界区域。

设置 REGION TYPE=LAGRANGIAN（默认）以将膜条件应用于拉格朗日边界区域。拉格朗日边界区域的边缘将跟随材料，同时允许沿边缘和区域内部进行自适应网格划分。

设置 REGION TYPE=SLIDING 以将膜条件应用于滑动边界区域。滑动边界区域的边缘将在材料上滑动。自适应网格划分将沿边缘和区域内部发生。网格约束通常应用于滑动边界区域的边缘以将其空间固定。

设置 REGION TYPE=EULERIAN 以将膜条件应用于欧拉边界区域。此选项用于创建材料可以流过的边界区域。必须使用垂直于欧拉边界区域的网格约束以允许材料流过该区域。如果没有应用网格约束，欧拉边界区域的行为将与滑动边界区域相同。

### **定义环境温度和膜系数的数据行：**

**第一行：**

根据需要重复此数据行以定义膜条件。




