# *EPJOINT









### *EPJOINT定义弹塑性关节单元的属性。

此选项用于定义弹塑性关节单元的属性。[*JOINT ELASTICITY](ch10abk02.md)选项以及如果要定义塑性，则[*JOINT PLASTICITY](ch10abk03.md)选项必须紧跟此选项。

**产品：**Abaqus/Standard

**类型：**模型数据

**级别：**部件，部件实例

##### **参考：**

- ["弹塑性关节，" Abaqus分析用户指南第32.10.1节](../usb/usb-link.md#usb-elm-eepjoint)
- [*JOINT ELASTICITY](ch10abk02.md)
- [*JOINT PLASTICITY](ch10abk03.md)

### **必需参数：**

ELSET

将此参数设置为包含正在定义属性的弹塑性关节单元的单元集名称。

ORIENTATION

将此参数设置为在关节中给出局部系统方向的[*ORIENTATION](ch15abk01.md)定义（["方向，" Abaqus分析用户指南第2.2.5节](../usb/usb-link.md#usb-int-corientation)）的名称。

### **可选参数：**

SECTION

如果关节模拟桩靴，则将此参数设置为SPUD CAN。如果关节不模拟桩靴，则不需要此参数。

### **使用SECTION=SPUD CAN定义桩靴几何形状的数据行：**

**第一行（也是唯一一行）：**

根据需要包含[*JOINT ELASTICITY](ch10abk02.md)和[*JOINT PLASTICITY](ch10abk03.md)选项以定义关节行为。




