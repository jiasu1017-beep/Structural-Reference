# *CONNECTOR FRICTION






### *CONNECTOR FRICTION定义连接器单元中的摩擦力和力矩。

此选项用于定义连接器单元中的摩擦力和力矩。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["连接类型库，" Abaqus 分析用户指南第 31.1.5 节](../usb/usb-link.md#usb-elm-econnectortypelibrary)
- ["连接器行为，" Abaqus 分析用户指南第 31.2.1 节](../usb/usb-link.md#usb-elm-econnectorbehavior)
- ["连接器摩擦行为，" Abaqus 分析用户指南第 31.2.5 节](../usb/usb-link.md#usb-elm-econnfrictionbehav)
- [*CONNECTOR BEHAVIOR](ch03abk35.md)
- [*CONNECTOR DERIVED COMPONENT](ch03abk40.md)
- [*CONNECTOR POTENTIAL](ch03abk49.md)
- [*FRICTION](ch06abk36.md)

### **可选参数：**

PREDEFINED

包含此参数以指定预定义的摩擦行为（如果连接类型可用）。Abaqus 自动定义接触力和切向牵引的大小，如 ["连接类型库，" Abaqus 分析用户指南第 31.1.5 节](../usb/usb-link.md#usb-elm-econnectortypelibrary) 中所示。

STICK STIFFNESS

将此参数设置为与摩擦行为相关的粘滞刚度。如果省略此参数，则选择一个默认值（通常适当）。

### **用于指定用户定义摩擦的可选参数（与 PREDEFINED 参数互斥）：**

COMPONENT

将此参数设置为指定用户定义摩擦行为所对应的连接器相对运动分量。

省略此参数并使用 [*CONNECTOR POTENTIAL](ch03abk49.md) 选项与 [*CONNECTOR FRICTION](ch03abk43.md) 选项结合使用，以指定耦合的用户定义摩擦行为。

CONTACT FORCE

将此参数设置为关联的 [*CONNECTOR DERIVED COMPONENT](ch03abk40.md) 选项的名称或定义摩擦产生接触力的连接器相对运动分量号。

DEPENDENCIES

将此参数设置为除了温度之外还包括在连接器摩擦数据定义中的场变量依赖项数。如果省略此参数，则假定摩擦力和力矩或接触正压力贡献与场变量无关。请参阅 ["材料数据定义"中的"指定场变量依赖性"，Abaqus 分析用户指南第 21.1.2 节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，了解更多详细信息。

EXTRAPOLATION

设置 EXTRAPOLATION=CONSTANT（默认，除非使用 [*CONNECTOR BEHAVIOR](ch03abk35.md)、EXTRAPOLATION=LINEAR）以对独立变量指定范围外的因变量使用常量外推。

设置 EXTRAPOLATION=LINEAR 以对独立变量指定范围外的因变量使用线性外推。

INDEPENDENT COMPONENTS

设置 INDEPENDENT COMPONENTS=POSITION（默认）以指定对摩擦行为定义中包含的相对位置分量的依赖。

设置 INDEPENDENT COMPONENTS=CONSTITUTIVE MOTION 以指定对摩擦行为定义中包含的构象相对运动分量的依赖。

REGULARIZE

此参数仅适用于 Abaqus/Explicit 分析。

设置 REGULARIZE=ON（默认，除非使用 [*CONNECTOR BEHAVIOR](ch03abk35.md)、REGULARIZE=OFF）以对用户定义的表格连接器摩擦数据进行正则化。

设置 REGULARIZE=OFF 以直接使用用户定义的表格连接器摩擦数据而不进行正则化。

RTOL

此参数仅适用于 Abaqus/Explicit 分析。

将此参数设置为用于正则化连接器摩擦数据的容差。

如果省略此参数，则默认值为 RTOL=0.03，除非在 [*CONNECTOR BEHAVIOR](ch03abk35.md) 选项上指定了容差。

### **用于为预定义摩擦行为定义参数（几何常数和内部接触力）的数据行（包含了 PREDEFINED 参数）：**

**第一行（也是唯一一行）：**

对于 SLIPRING 连接类型，不需要数据行。

### **用于为不依赖于一个或多个分量方向上的相对位置或运动的用户定义摩擦定义内部接触力的数据行（同时省略了 PREDEFINED 和 INDEPENDENT COMPONENTS 参数）：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于五时需要）：**

根据需要重复此数据行集，以将内部接触力定义为累积滑移，温度和场变量的函数。如果不需要指定内部接触力，则省略这些数据行。

### **用于为依赖于一个或多个分量方向上的相对位置或运动的用户定义摩擦定义内部接触力的数据行（省略了 PREDEFINED 参数并包含了 INDEPENDENT COMPONENTS 参数）：**

**第一行：**

**后续行：**

**续行（如需要）：**

不要重复第一数据行。根据需要重复后续数据行，以将内部接触力定义为连接器相对位置或构象相对运动，累积滑移，温度和其他预定义场变量的函数。




