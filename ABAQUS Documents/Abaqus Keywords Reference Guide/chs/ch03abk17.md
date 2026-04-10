# *CHANGE FRICTION






### *CHANGE FRICTION更改摩擦属性。

将此选项与 [*FRICTION](ch06abk36.md) 选项结合使用，以在步骤之间更改摩擦属性值。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**历史数据 

**级别：**步骤

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["机械接触属性：概述，" Abaqus 分析用户指南第 37.1.1 节](../usb/usb-link.md#usb-cni-acontactmechanical)
- ["摩擦行为，" Abaqus 分析用户指南第 37.1.5 节](../usb/usb-link.md#usb-cni-afriction)
- ["连接器行为，" Abaqus 分析用户指南第 31.2.1 节](../usb/usb-link.md#usb-elm-econnectorbehavior)
- [*FRICTION](ch06abk36.md)

### **必需的互斥参数：**

ELSET

如果接触条件是用接触单元建模的，或者摩擦是在连接器单元中定义的，则使用此参数。将此参数设置为包含正在重新定义摩擦属性的接触或连接器单元的单元集名称。

INTERACTION

如果接触条件是用基于表面的接触对或通用接触建模的，则使用此参数。将此参数设置为正在重新定义摩擦属性的 [*SURFACE INTERACTION](ch18abk50.md) 属性定义名称。

### **可选参数：**

AMPLITUDE

将此参数设置为在步骤中给出摩擦系数和允许弹性滑动的任何更改的时间变化的幅值曲线名称（在 [*AMPLITUDE](ch01abk09.md) 选项中定义）（["幅值曲线，" Abaqus 分析用户指南第 34.1.2 节](../usb/usb-link.md#usb-prc-pamplitude)）。

如果省略此参数，则根据 [*STEP](ch18abk36.md) 选项上 AMPLITUDE 参数分配的值进行这些摩擦属性的转换（请参阅 ["定义分析，" Abaqus 分析用户指南第 6.1.2 节](../usb/usb-link.md#usb-anl-aover)）。摩擦系数和允许弹性滑动以外的摩擦属性更改总是立即进行。当摩擦应力非零时，摩擦属性的突然更改可能导致收敛困难。

RESET

包含此参数以将摩擦属性重置为其原始值。使用此参数时，不需要 [*FRICTION](ch06abk36.md) 选项来重新定义摩擦属性。

**此选项没有关联的数据行。**




