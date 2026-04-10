# *CONNECTOR LOCK






### *CONNECTOR LOCK定义连接器单元的锁定准则。

此选项用于为具有可用相对运动分量的连接器单元定义锁定准则。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["连接器行为，" Abaqus 分析用户指南第 31.2.1 节](../usb/usb-link.md#usb-elm-econnectorbehavior)
- ["连接类型库，" Abaqus 分析用户指南第 31.1.5 节](../usb/usb-link.md#usb-elm-econnectortypelibrary)
- [*CONNECTOR BEHAVIOR](ch03abk35.md)

### **必需参数：**

COMPONENT

将此参数设置为你想要基于其上锁定准则的分量号。请参阅 ["连接类型库，" Abaqus 分析用户指南第 31.1.5 节](../usb/usb-link.md#usb-elm-econnectortypelibrary)，了解相对运动分量的定义。

### **可选参数：**

DEPENDENCIES

此参数仅适用于 Abaqus/Explicit 分析。

将此参数设置为除了温度之外还包括在连接器锁定数据定义中的场变量依赖项数。如果省略此参数，则假定连接器锁定与场变量无关。请参阅 ["材料数据定义"中的"指定场变量依赖性"，Abaqus 分析用户指南第 21.1.2 节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，了解更多详细信息。

EXTRAPOLATION

设置 EXTRAPOLATION=CONSTANT（默认，除非使用 [*CONNECTOR BEHAVIOR](ch03abk35.md)、EXTRAPOLATION=LINEAR）以对独立变量指定范围外的因变量使用常量外推。

设置 EXTRAPOLATION=LINEAR 以对独立变量指定范围外的因变量使用线性外推。

LOCK

将此参数设置为 ALL（默认）以在满足锁定准则时锁定所有相对运动分量。

将此参数设置为一个可用的分量号，以在满足锁定准则时仅锁定该相对运动分量。

REGULARIZE

此参数仅适用于 Abaqus/Explicit 分析。

设置 REGULARIZE=ON（默认，除非使用 [*CONNECTOR BEHAVIOR](ch03abk35.md)、REGULARIZE=OFF）以对用户定义的表格连接器锁定数据进行正则化。

设置 REGULARIZE=OFF 以直接使用用户定义的表格连接器锁定数据而不进行正则化。

RTOL

此参数仅适用于 Abaqus/Explicit 分析。

将此参数设置为用于正则化连接器锁定数据的容差。

如果省略此参数，则默认值为 RTOL=0.03，除非在 [*CONNECTOR BEHAVIOR](ch03abk35.md) 选项上指定了容差。

### **用于定义锁定准则的数据行：**

**Abaqus/Standard 的第一行（也是唯一一行）：**

**Abaqus/Explicit 的数据行：**

**后续行（仅在 DEPENDENCIES 参数值大于一时需要）：**

根据需要重复此数据行集，以将锁定准则定义为温度和其他预定义场变量的函数。




