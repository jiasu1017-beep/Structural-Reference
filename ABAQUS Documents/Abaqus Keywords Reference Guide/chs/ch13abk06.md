# *MASS









### *MASS指定点质量。

此选项用于定义与MASS单元关联的集中质量值。

它还用于定义与MASS单元关联的质量比例阻尼（用于直接积分动力分析和显式动力分析）和复合阻尼（用于模态动力分析）。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**部件、部件实例、装配  

**Abaqus/CAE：**属性模块和相互作用模块。

##### **参考：**

- ["点质量，" Abaqus Analysis User's Guide第30.1.1节](../usb/usb-link.md#usb-elm-emasses)

### **必需参数：**

ELSET

将此参数设置为包含要赋予值的MASS单元的单元集名称。

### **可选参数：**

ALPHA

将此参数设置为![](../graphics/key_eqn00077.gif)因子，以在为直接积分动力学或显式动力学使用MASS单元时创建质量比例阻尼。此值在模态动力学中被忽略。默认值为0.0。

COMPOSITE

此参数仅适用于Abaqus/Standard分析。

将此参数设置为在与MASS单元一起计算模态复合阻尼因子时要使用的临界阻尼比。此参数仅适用于基于SIM架构的模式分析。默认值为0.0。

对于基于SIM架构的模态分析，应改用[*COMPOSITE MODAL DAMPING](ch03abk27.md)选项。此值在直接积分动力学中被忽略。

ORIENTATION

此参数仅在TYPE=ANISOTROPIC时适用。

将此参数设置为[*ORIENTATION](ch15abk01.md)选项的名称，用于定义各向异性质量张量的主方向。如果省略ORIENTATION参数，则假定主方向与全局轴重合。

在大位移分析中，各向异性质量的局部轴随MASS单元所连接节点的旋转（如果处于活动状态）而旋转。

TYPE

设置TYPE=ISOTROPIC（默认）用于各向同性质量张量。

设置TYPE=ANISOTROPIC用于可能具有三个不同主值的各向异性质量张量。

### **定义各向同性质量大小的数据行（非重量）：**

**第一行（也是唯一一行）：**

Abaqus不使用任何特定的物理单位，因此用户的选择必须一致。

### **定义各向异性质量张量三个主值的数据行（非重量）：**

**第一行（也是唯一一行）：**

Abaqus不使用任何特定的物理单位，因此用户的选择必须一致。