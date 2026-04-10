# *BEAM ADDED INERTIA





### *BEAM ADDED INERTIA定义附加梁惯性。

此选项与[*BEAM SECTION](ch02abk06.md)或[*BEAM GENERAL SECTION](ch02abk05.md)选项配合使用，为剪切柔性Timoshenko梁单元定义每单位长度的附加质量和转动惯性。此选项还用于定义质量比例阻尼（用于直接积分动力学分析）以及与附加惯性相关的Abaqus/Standard复合阻尼（用于模态动力学分析）。

**产品：**Abaqus/Standard  Abaqus/Explicit

**类型：**模型数据

**级别：**部件、部件实例、装配

##### **参考：**

- ["选择梁单元，" Abaqus Analysis User's Guide第29.3.3节](../usb/usb-link.md#usb-elm-ebeamelem)
- ["梁截面行为，" Abaqus Analysis User's Guide第29.3.5节](../usb/usb-link.md#usb-elm-ebeamsectionbehavior)

### **可选参数：**

ALPHA

将此参数设置为等于![](../graphics/key_eqn00077.gif)因子，以在为直接积分动力学中使用此选项时创建的附加惯性相关惯性比例阻尼。此值在模态动力学中被忽略。默认值为ALPHA=0.0。（[T1](../popups/usb-int-iconventions-unitsym.md)的单位。）

COMPOSITE

此参数仅适用于Abaqus/Standard分析。

将此参数设置为与梁单元一起使用以计算模态复合阻尼因子时要使用的临界阻尼分数。默认值为COMPOSITE=0.0。

此值在直接积分动力学中被忽略。在基于SIM架构的模态分析中也忽略它，在这种情况下应改用[*COMPOSITE MODAL DAMPING](ch03abk27.md)选项。

### **定义附加梁惯性的数据行：**

**第一行：**

转动惯性应以[ML](../popups/usb-int-iconventions-unitsym.md)为单位给出。Abaqus不使用任何特定的物理单位，因此用户的选择必须一致。

根据需要重复此组数据行，以定义附加梁惯性。


