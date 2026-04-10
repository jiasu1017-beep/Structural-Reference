# *CFILM






### *CFILM在一个或多个节点或顶点处定义薄膜系数和相关环境温度。

此选项用于在完全耦合热应力分析中向模型中的任何节点提供薄膜系数和环境温度。在 Abaqus/Standard 中，它还用于在热传递、耦合热-电和耦合热-电-结构分析中向模型中的任何节点提供薄膜系数和环境温度。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**历史数据 

**级别：**步骤

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["热载荷，" Abaqus 分析用户指南第 34.4.4 节](../usb/usb-link.md#usb-prc-pthermal)
- ["FILM，" Abaqus 用户子程序参考指南第 1.1.6 节](../sub/sub-link.md#sub-rtn-ufilm)

### **可选参数：**

AMPLITUDE

将此参数设置为给出环境温度 ![](../graphics/key_eqn00086.gif) 随时间变化的 [*AMPLITUDE](ch01abk09.md) 选项名称。

如果在 Abaqus/Standard 分析中省略此参数，则根据 [*STEP](ch18abk36.md) 选项上 AMPLITUDE 参数分配的值，环境温度将在步骤开始时立即应用或在线性分布于整个步骤（["定义分析，" Abaqus 分析用户指南第 6.1.2 节](../usb/usb-link.md#usb-anl-aover)）。如果在 Abaqus/Explicit 分析中省略此参数，则数据行上给出的参考环境温度将在步骤开始时立即应用。

对于非均匀薄膜系数（仅在 Abaqus/Standard 中可用），环境温度幅值在用户子程序 [`FILM`](../sub/sub-link.md#sub-xsl-film) 中定义，AMPLITUDE 参考仅用于修改传入用户子程序的环境温度。

FILM AMPLITUDE

将此参数设置为给出薄膜系数 *h* 随时间变化的 [*AMPLITUDE](ch01abk09.md) 选项名称。

如果省略此参数，参考薄膜系数将在步骤开始时立即应用并在步骤中保持不变。

如果薄膜系数通过 [*FILM PROPERTY](ch06abk11.md) 选项定义为温度和场变量的函数，则 FILM AMPLITUDE 参数将被忽略。

对于非均匀薄膜系数（仅在 Abaqus/Standard 中可用），薄膜系数幅值在用户子程序 [`FILM`](../sub/sub-link.md#sub-xsl-film) 中定义，FILM AMPLITUDE 参考仅用于修改传入用户子程序的薄膜系数。

OP

设置 OP=MOD（默认）以保留现有的 [*CFILM](ch03abk14.md)，此选项修改现有的薄膜或定义额外的薄膜。

设置 OP=NEW 以移除模型上所有现有的 [*CFILM](ch03abk14.md)。

REGION TYPE

此参数仅适用于 Abaqus/Explicit 分析。

此参数仅适用于施加在自适应网格域边界上的集中薄膜。如果集中薄膜施加在自适应网格域内部的节点上，这些节点将始终跟随材料移动。

设置 REGION TYPE=LAGRANGIAN（默认）以将集中薄膜施加到跟随材料（非自适应）的节点。

设置 REGION TYPE=SLIDING 以将集中薄膜施加到可以在材料上滑动的节点。通常对节点施加网格约束以将其空间固定。

设置 REGION TYPE=EULERIAN 以将集中薄膜施加到可以独立于材料移动的节点。此选项仅用于材料可以流入或流出自适应网格域的边界区域。必须沿欧拉边界区域使用网格约束法向，以允许材料流过该区域。如果没有施加网格约束，欧拉边界区域的行为将与滑动边界区域相同。

USER

此参数仅适用于 Abaqus/Standard 分析。

包含此参数以指示通过此选项指定的任何非零薄膜系数将在用户子程序 [`FILM`](../sub/sub-link.md#sub-xsl-film) 中定义。如果使用此参数，则此选项的数据行定义的任何薄膜系数和环境温度值（可能由 AMPLITUDE 和 FILM AMPLITUDE 参数修改）将被忽略，并可在子程序 [`FILM`](../sub/sub-link.md#sub-xsl-film) 中重新定义。

### **用于定义环境温度和薄膜系数的数据行：**

**第一行：**

根据需要重复此数据行以定义薄膜条件。




