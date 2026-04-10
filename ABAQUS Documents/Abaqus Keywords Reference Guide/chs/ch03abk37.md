# *CONNECTOR DAMAGE EVOLUTION





### *CONNECTOR DAMAGE EVOLUTION为连接器单元指定连接器损伤演化。

此选项用于为具有相对运动可用分量的连接器单元定义连接器损伤演化。它必须与[*CONNECTOR DAMAGE INITIATION](ch03abk38.md)选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Interaction模块

##### **参考：**

- ["连接类型库"，Abaqus Analysis User's Guide第31.1.5节](../usb/usb-link.md#usb-elm-econnectortypelibrary)
- ["连接器行为"，Abaqus Analysis User's Guide第31.2.1节](../usb/usb-link.md#usb-elm-econnectorbehavior)
- ["连接器损伤行为"，Abaqus Analysis User's Guide第31.2.7节](../usb/usb-link.md#usb-elm-econndamagebehav)
- [*CONNECTOR BEHAVIOR](ch03abk35.md)
- [*CONNECTOR DAMAGE INITIATION](ch03abk38.md)
- [*CONNECTOR POTENTIAL](ch03abk49.md)

### **必需参数：**

TYPE

设置TYPE=MOTION以使用连接器本构相对运动（位移/旋转）或塑性相对运动（位移/旋转）来指定损伤演化。

设置TYPE=ENERGY以使用损伤后演化耗散能来指定损伤演化。

### **可选参数：**

AFFECTED COMPONENTS

包含此参数以在数据行上标识将发生损伤的相对运动分量。

如果省略此参数且在关联的[*CONNECTOR DAMAGE INITIATION](ch03abk38.md)选项上包含了COMPONENT参数，则只有指定分量将发生损伤。

如果此参数和关联的[*CONNECTOR DAMAGE INITIATION](ch03abk38.md)选项上的COMPONENT参数都被省略，则只有关联的[*CONNECTOR POTENTIAL](ch03abk49.md)定义涉及的相对运动分量将发生损伤。

DEGRADATION

设置DEGRADATION=MAXIMUM（默认值）以指示与此选项关联的损伤值将首先与其他损伤机制（如果已定义）的损伤值进行比较，并且仅考虑最大值作为总体损伤。

设置DEGRADATION=MULTIPLICATIVE以指示与此选项关联的损伤值将乘法贡献于总体损伤。

DEPENDENCIES

将此参数设置为除了温度之外还包括在连接器损伤演化定义中的场变量依赖项数。如果省略此参数，则假定连接器损伤演化独立于场变量。请参见["指定场变量依赖性"，Abaqus Analysis User's Guide第21.1.2节"材料数据定义"](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，以获取更多信息。

EXTRAPOLATION

设置EXTRAPOLATION=CONSTANT（默认值，除非使用[*CONNECTOR BEHAVIOR](ch03abk35.md)，EXTRAPOLATION=LINEAR）以在独立变量的指定范围外使用常量外推。

设置EXTRAPOLATION=LINEAR以在独立变量的指定范围外使用线性外推。

REGULARIZE

此参数仅适用于Abaqus/Explicit分析。

设置REGULARIZE=ON（默认值，除非使用[*CONNECTOR BEHAVIOR](ch03abk35.md)，REGULARIZE=OFF）以正则化用户定义的表格连接器损伤数据。

设置REGULARIZE=OFF以直接使用用户定义的表格连接器损伤数据而不进行正则化。

RTOL

此参数仅适用于Abaqus/Explicit分析。

将此参数设置为用于正则化连接器损伤数据的容差。

如果省略此参数，默认值为RTOL=0.03，除非在[*CONNECTOR BEHAVIOR](ch03abk35.md)选项上指定了容差。

SOFTENING

此参数只能与TYPE=MOTION结合使用。

设置SOFTENING=LINEAR（默认值）以指定线性损伤演化规律。

设置SOFTENING=EXPONENTIAL以指定指数损伤演化规律。

设置SOFTENING=TABULAR以表格形式指定损伤演化规律。

### **定义TYPE=MOTION，SOFTENING=LINEAR的损伤演化的数据行：**

**第一行（仅在包含AFFECTED COMPONENTS参数时需要）：**

**如果包含AFFECTED COMPONENTS参数则为第二行；否则为第一行：**

**后续行（仅在DEPENDENCIES参数的值大于五时需要）：**

不要重复指定受影响分量的数据行。根据需要重复后续数据行集，通过指定作为模式混合比、温度和其他预定义场变量函数的连接器相对塑性或本构运动来定义连接器损伤演化。

### **定义TYPE=MOTION，SOFTENING=EXPONENTIAL的损伤演化的数据行：**

**第一行（仅在包含AFFECTED COMPONENTS参数时需要）：**

**如果包含AFFECTED COMPONENTS参数则为第二行；否则为第一行：**

**后续行（仅在DEPENDENCIES参数的值大于四时需要）：**

不要重复指定受影响分量的数据行。根据需要重复后续数据行集，通过指定作为模式混合比、温度和其他预定义场变量函数的最终失效时连接器相对塑性或本构运动以及指数规律参数来定义连接器损伤演化。

### **定义TYPE=MOTION，SOFTENING=TABULAR的损伤演化的数据行：**

**第一行（仅在包含AFFECTED COMPONENTS参数时需要）：**

**如果包含AFFECTED COMPONENTS参数则为第二行；否则为第一行：**

**后续行（仅在DEPENDENCIES参数的值大于四时需要）：**

不要重复指定受影响分量的数据行。根据需要重复后续数据行集，以将连接器损伤演化定义为连接器相对塑性或本构运动、模式混合比、温度和其他预定义场变量的函数。

### **定义TYPE=ENERGY的损伤演化的数据行：**

**第一行（仅在包含AFFECTED COMPONENTS参数时需要）：**

**如果包含AFFECTED COMPONENTS参数则为第二行；否则为第一行：**

**后续行（仅在DEPENDENCIES参数的值大于五时需要）：**

不要重复指定受影响分量的数据行。根据需要重复后续数据行集，通过指定作为模式混合比、温度和其他预定义场变量函数的损伤后耗散能来定义连接器损伤演化。




