# *CONTACT DAMPING






### *CONTACT DAMPING定义接触表面之间的粘性阻尼。

此选项用于定义两个相互作用表面之间的粘性阻尼。必须与 [*SURFACE INTERACTION](ch18abk50.md)、[*GAP](ch07abk01.md) 或 [*INTERFACE](ch09abk22.md) 选项结合使用。在 Abaqus/Standard 中，此选项主要用于阻尼表面接近或分离过程中的相对运动。在 Abaqus/Explicit 中，此选项在使用惩罚或软化接触时用于阻尼振荡。如果为表面相互作用指定了用户子程序 [`VUINTER`](../sub/sub-link.md#sub-xsl-vuinter) 或 [`VUINTERACTION`](../sub/sub-link.md#sub-xsl-vuinteraction)，则此选项不适用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**Abaqus/Standard 中的模型数据；Abaqus/Explicit 中的模型数据或历史数据  

**级别：**部件、部件实例、装配、Abaqus/Standard 中的模型；Abaqus/Explicit 中的模型或步骤

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["机械接触属性：概述，" Abaqus 分析用户指南第 37.1.1 节](../usb/usb-link.md#usb-cni-acontactmechanical)
- ["接触阻尼，" Abaqus 分析用户指南第 37.1.3 节](../usb/usb-link.md#usb-cni-acontactdamping)

### **必需参数：**

DEFINITION

使用此参数选择数据行上指定的阻尼系数的维度。在 Abaqus/Standard 分析中唯一可用的选项是 DEFINITION=DAMPING COEFFICIENT。

设置 DEFINITION=CRITICAL DAMPING FRACTION 以使用无量纲阻尼系数 *B*。阻尼力使用 ![](../graphics/key_eqn00363.gif) 计算，其中 *m* 是节点质量，![](../graphics/key_eqn00364.gif) 是节点接触刚度（单位为 ![](../graphics/key_eqn00365.gif)），![](../graphics/key_eqn00366.gif) 是表面之间相对弹性滑动的速率。对于具有软化行为的运动接触和惩罚接触，使用默认值 *B*=0.03。

设置 DEFINITION=DAMPING COEFFICIENT 以相对于相对速度以阻尼系数 *C*（压力单位）指定阻尼，这样阻尼力将使用 ![](../graphics/key_eqn00367.gif) 计算，其中 *A* 是节点面积，![](../graphics/key_eqn00366.gif) 是表面之间的相对弹性滑动速率。如果未定义接触面积（如可能发生在基于节点的表面或 GAP 或 ITT 型接触单元上），系数单位为每相对速度的力。对于三维梁或桁架的接触，系数单位为每单位长度每单位速度的力。

### **可选参数：**

TANGENT FRACTION

将此参数设置为切向阻尼系数除以法向阻尼系数。此参数仅影响切向阻尼；法向阻尼系数在下方数据行上定义。如果不需要切向阻尼，将此参数设置为零。默认值为 Abaqus/Standard 中 0.0，Abaqus/Explicit 中 1.0。

### **用于定义接触表面之间法向粘性阻尼的数据行：**

**第一行（也是唯一一行）：**




