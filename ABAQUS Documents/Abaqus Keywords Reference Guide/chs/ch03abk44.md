# *CONNECTOR HARDENING






### *CONNECTOR HARDENING定义连接器单元中的塑性初始屈服值和硬化行为。

此选项用于指定连接器可用相对运动分量中的初始屈服面大小，以及可选的屈服后硬化行为。必须与 [*CONNECTOR PLASTICITY](ch03abk48.md) 选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["连接器行为，" Abaqus 分析用户指南第 31.2.1 节](../usb/usb-link.md#usb-elm-econnectorbehavior)
- ["连接器塑性行为，" Abaqus 分析用户指南第 31.2.6 节](../usb/usb-link.md#usb-elm-econnplastbehav)
- ["循环加载下金属的模型，" Abaqus 分析用户指南第 23.2.2 节](../usb/usb-link.md#usb-mat-chardening)
- [*CONNECTOR BEHAVIOR](ch03abk35.md)
- [*CONNECTOR ELASTICITY](ch03abk41.md)
- [*CONNECTOR HARDENING](ch03abk44.md)
- [*CONNECTOR PLASTICITY](ch03abk48.md)
- [*CONNECTOR POTENTIAL](ch03abk49.md)

### **可选参数：**

DEFINITION

设置 DEFINITION=EXPONENTIAL LAW 以直接指定各向同性硬化参数 ![](../graphics/key_eqn00350.gif) 和 *b*。此参数仅对 TYPE=ISOTROPIC 有效。

设置 DEFINITION=HALF CYCLE（TYPE=KINEMATIC 的默认）以提供第一个半周期的力/矩与塑性运动数据。此参数仅对 TYPE=KINEMATIC 有效。

设置 DEFINITION=PARAMETERS 以直接指定运动硬化参数 *C* 和 ![](../graphics/key_eqn00029.gif)。此参数仅对 TYPE=KINEMATIC 有效。

设置 DEFINITION=STABILIZED 以提供稳定周期的力/矩与塑性运动数据。此参数仅对 TYPE=KINEMATIC 有效。

设置 DEFINITION=TABULAR（TYPE=ISOTROPIC 的默认）以提供力/矩与塑性运动值。可以使用单轴测试数据或来自循环实验的处理数据（如 ["连接器行为，" Abaqus 分析用户指南第 31.2.1 节](../usb/usb-link.md#usb-elm-econnectorbehavior) 中所述）。此参数仅对 TYPE=ISOTROPIC 有效。

DEPENDENCIES

将此参数设置为除了温度之外还包括在连接器硬化数据定义中的场变量依赖项数。如果省略此参数，则假定连接器硬化与场变量无关。请参阅 ["材料数据定义"中的"指定场变量依赖性"，Abaqus 分析用户指南第 21.1.2 节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，了解更多详细信息。

EXTRAPOLATION

设置 EXTRAPOLATION=CONSTANT（默认，除非使用 [*CONNECTOR BEHAVIOR](ch03abk35.md)、EXTRAPOLATION=LINEAR）以对独立变量指定范围外的因变量使用常量外推。

设置 EXTRAPOLATION=LINEAR 以对独立变量指定范围外的因变量使用线性外推。

RATE FILTER FACTOR

此参数仅适用于 Abaqus/Explicit 分析。

将此参数设置为用于过滤等效相对塑性运动率的因子，以评估率相关连接器硬化数据。默认值为 0.9。

RATE INTERPOLATION

此参数仅适用于 Abaqus/Explicit 分析，仅用于插值率相关连接器硬化数据。

设置 RATE INTERPOLATION=LINEAR（默认）以在使用对数间隔插值率相关硬化数据时，对等效相对塑性运动率使用线性间隔。

设置 RATE INTERPOLATION=LOGARITHMIC 以在使用对数间隔插值率相关硬化数据时，对等效相对塑性运动率使用对数间隔。

REGULARIZE

此参数仅适用于 Abaqus/Explicit 分析。

设置 REGULARIZE=ON（默认，除非使用 [*CONNECTOR BEHAVIOR](ch03abk35.md)、REGULARIZE=OFF）以对用户定义的表格连接器硬化数据进行正则化。

设置 REGULARIZE=OFF 以直接使用用户定义的表格连接器硬化数据而不进行正则化。

RTOL

此参数仅适用于 Abaqus/Explicit 分析。

将此参数设置为用于正则化连接器硬化数据的容差。

如果省略此参数，则默认值为 RTOL=0.03，除非在 [*CONNECTOR BEHAVIOR](ch03abk35.md) 选项上指定了容差。

TYPE

设置 TYPE=ISOTROPIC（默认）以指定初始屈服面大小，以及可选的各向同性硬化数据。

设置 TYPE=KINEMATIC 以指定运动硬化数据。

### **TYPE=ISOTROPIC、DEFINITION=TABULAR 的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于四时需要）：**

根据需要重复此数据行集，以将弹性范围大小定义为连接器等效相对塑性运动，等效相对塑性运动率，温度和场变量的函数。

### **TYPE=ISOTROPIC、DEFINITION=EXPONENTIAL LAW 的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于四时需要）：**

根据需要重复此数据行集，以将弹性范围大小和各向同性硬化参数定义为温度和场变量的函数。

### **TYPE=KINEMATIC、DEFINITION=HALF CYCLE 的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于五时需要）：**

根据需要重复此数据行集，以将屈服力/矩定义为连接器相对塑性运动，温度和场变量的函数。

### **TYPE=KINEMATIC、DEFINITION=STABILIZED 的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于四时需要）：**

根据需要重复此数据行集，以将屈服力/矩定义为连接器相对塑性运动，构象运动范围，温度和场变量的函数。

### **TYPE=KINEMATIC、DEFINITION=PARAMETERS 的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于四时需要）：**

根据需要重复此数据行集，以将零相对塑性运动时的屈服力/矩和运动硬化参数定义为温度和场变量的函数。




