# *CRADIATE






### *CRADIATE在一个或多个节点或顶点处指定辐射条件和相关的环境温度。

此选项用于在完全耦合热应力分析中的节点与非反射环境之间施加辐射边界条件。在 Abaqus/Standard 中，它还用于热传递、耦合热-电和耦合热-电-结构分析。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**历史数据 

**级别：**步骤

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["热载荷，" Abaqus 分析用户指南第 34.4.4 节](../usb/usb-link.md#usb-prc-pthermal)

### **可选参数：**

AMPLITUDE

将此参数设置为给出环境温度随时间变化的 [*AMPLITUDE](ch01abk09.md) 选项名称。

如果在 Abaqus/Standard 分析中省略此参数，则根据 [*STEP](ch18abk36.md) 选项上 AMPLITUDE 参数分配的值，参考大小将在步骤开始时立即应用或在线性分布于整个步骤（请参阅 ["定义分析，" Abaqus 分析用户指南第 6.1.2 节](../usb/usb-link.md#usb-anl-aover)）。如果在 Abaqus/Explicit 分析中省略此参数，参考大小将在步骤开始时立即应用。

OP

设置 OP=MOD（默认）以保留现有的 [*CRADIATE](ch03abk84.md) 定义，此选项修改现有的辐射条件或定义额外的辐射条件。

设置 OP=NEW 以移除模型上所有现有的 [*CRADIATE](ch03abk84.md) 定义。

REGION TYPE

此参数仅适用于 Abaqus/Explicit 分析。

此参数仅适用于施加在自适应网格域边界上的集中辐射条件。如果集中辐射条件施加在自适应网格域内部的节点上，这些节点将始终跟随材料移动。

设置 REGION TYPE=LAGRANGIAN（默认）以将集中辐射条件施加到跟随材料（非自适应）的节点。

设置 REGION TYPE=SLIDING 以将集中辐射条件施加到可以在材料上滑动的节点。通常对节点施加网格约束以将其空间固定。

设置 REGION TYPE=EULERIAN 以将集中辐射条件施加到可以独立于材料移动的节点。此选项仅用于材料可以流入或流出自适应网格域的边界区域。必须沿欧拉边界区域使用网格约束法向，以允许材料流过该区域。如果没有施加网格约束，欧拉边界区域的行为将与滑动边界区域相同。

### **用于定义辐射条件的数据行：**

**第一行：**

根据需要重复此数据行以定义辐射条件。




