# *UEL PROPERTY





### *UEL PROPERTY定义要与用户元素类型一起使用的属性值。

此选项用于定义用户元素的属性。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**部件、部件实例、模型

**Abaqus/CAE：**执行器/传感器相互作用属性可以在Interaction模块中定义。

##### **参考：**

- ["用户定义元素," Section 32.15.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-euserelem)
- [*USER ELEMENT](ch20abk07.md)

### **必需参数：**

ELSET

将此参数设置为包含正在为其定义属性值的用户元素的元素集名称。

### **可选参数：**

MATERIAL

此参数仅适用于Abaqus/Standard分析。

将此参数设置为要与这些元素一起使用的材料名称。

ORIENTATION

此参数仅适用于Abaqus/Standard分析。

将此参数设置为方向定义（["方向," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)）的名称，用于定义此集合中元素材料计算的局部坐标系。

### **可选参数（仅与线性用户元素的直接积分动态分析相关）：**

ALPHA

将此参数设置为Rayleigh质量阻尼因子，![](../graphics/key_eqn00080.gif)。

BETA

将此参数设置为Rayleigh刚度阻尼因子，![](../graphics/key_eqn00135.gif)。

### **定义线性用户元素的属性：**

不需要数据行。

### **如果PROPERTIES和/或I PROPERTIES参数在[*USER ELEMENT](ch20abk07.md)选项上的值为1或更大，则定义非线性用户元素属性的数据行：**

**第一行：**

根据需要重复此数据行。每行使用八个值用于实数和整数值。





