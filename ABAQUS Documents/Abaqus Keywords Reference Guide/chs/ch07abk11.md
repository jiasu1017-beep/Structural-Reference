# *GASKET SECTION






### *GASKET SECTION为垫片单元指定单元特性。

此选项用于定义垫片单元的特性。

**产品：** Abaqus/Standard  Abaqus/CAE  

**类型：** 模型数据  

**级别：** 零件、零件实例  

**Abaqus/CAE：** Property 模块

##### **参考文献：**

- ["垫片单元：概述，" Abaqus Analysis User's Guide 第 32.6.1 节](../usb/usb-link.md#usb-elm-egasketoverview)
- ["使用材料模型定义垫片行为，" Abaqus Analysis User's Guide 第 32.6.5 节](../usb/usb-link.md#usb-elm-egasketmatbehavior)
- ["使用垫片行为模型直接定义垫片行为，" Abaqus Analysis User's Guide 第 32.6.6 节](../usb/usb-link.md#usb-elm-egasketbehavior)

### **必需参数：**

ELSET

将此参数设置为包含正在定义其垫片行为的单元的单元集名称。

### **必需的、互斥的参数：**

BEHAVIOR

将此参数设置为指定单元集所引用的垫片行为名称。

MATERIAL

将此参数设置为垫片所用材料的名称。

### **可选参数：**

ORIENTATION

将此参数设置为 [*ORIENTATION](ch15abk01.md) 选项（["方向，" Abaqus Analysis User's Guide 第 2.2.5 节](../usb/usb-link.md#usb-int-corientation)）的名称，用于为指定单元集中垫片单元的积分点计算定义局部坐标系。

STABILIZATION STIFFNESS

此参数通常不需要。它用于更改除链接单元外的所有单元使用的默认稳定刚度，以稳定在所有节点都未支撑的垫片单元，例如那些延伸到相邻组件之外的单元。默认值设置为厚度方向初始压缩刚度的 109 倍。要更改默认值，请将此参数设置为所需的稳定刚度。单位为应力（[FL2](../popups/usb-int-iconventions-unitsym.md)）。如果厚度行为以力与闭合的关系来定义，则需要将初始压缩刚度除以横截面积以将单位转换为应力，然后才能用它来设置所需的稳定刚度。

### **定义垫片单元属性的数据行：**

**第一（也是唯一）行：**




