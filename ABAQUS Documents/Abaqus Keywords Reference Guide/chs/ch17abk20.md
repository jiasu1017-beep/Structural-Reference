# *ROTARY INERTIA







### *ROTARY INERTIA定义刚体转动惯量。

此选项用于定义与ROTARYI单元相关的刚体转动惯量值。

它还用于定义与ROTARYI单元相关的质量比例阻尼（用于直接积分动态分析和显式动态分析）和复合阻尼（用于模态动态分析）。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**零件，零件实例，装配  

**Abaqus/CAE：**属性模块和相互作用模块。

##### **参考：**

- ["转动惯量，" Abaqus Analysis User's Guide第30.2.1节](../usb/usb-link.md#usb-elm-erotinertia)

### **必需参数：**

ELSET

将此参数设置为包含正在给出其值的ROTARYI单元的单元集名称。

### **可选参数：**

ALPHA

将此参数设置为![](../graphics/key_eqn00077.gif)因子，以为直接积分动力学或显式动力学中使用时创建与ROTARYI单元的惯性比例阻尼。此值在模态动力学中被忽略。默认为0.0。

COMPOSITE

此参数仅适用于Abaqus/Standard分析。

将此参数设置为临界阻尼分数，用于在模态动力学中计算模态复合阻尼因子时与ROTARYI单元一起使用。默认为0.0。

此值在直接积分动力学中被忽略。在基于SIM架构的基于模式的分析中也会被忽略，这些分析应改用[*COMPOSITE MODAL DAMPING](ch03abk27.md)选项。

ORIENTATION

将此参数设置为[*ORIENTATION](ch15abk01.md)选项（["方向，" Abaqus Analysis User's Guide第2.2.5节](../usb/usb-link.md#usb-int-corientation)）的名称，该选项用于定义正在给出其转动惯量值的局部轴方向。如果省略ORIENTATION参数，则假定惯性张量分量是相对于全局轴给出的；即全局和局部惯性轴重合。

在大位移分析中（Abaqus/Explicit分析或在Abaqus/Standard分析的[*STEP](ch18abk36.md)选项上包含NLGEOM参数时），惯性局部轴随ROTARYI单元所连接节点的旋转而旋转。

### **定义转动惯量的数据行：**

**第一行（也是唯一一行）：**

转动惯量应以[ML2](../popups/usb-int-iconventions-unitsym.md)为单位给出。Abaqus不使用任何特定的物理单位，因此用户的选择必须一致。
