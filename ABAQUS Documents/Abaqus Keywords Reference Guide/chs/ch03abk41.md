# *CONNECTOR ELASTICITY






### *CONNECTOR ELASTICITY定义连接器弹性行为。

此选项用于定义连接器单元的弹性行为。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["连接器行为，" Abaqus 分析用户指南第 31.2.1 节](../usb/usb-link.md#usb-elm-econnectorbehavior)
- ["连接器弹性行为，" Abaqus 分析用户指南第 31.2.2 节](../usb/usb-link.md#usb-elm-econnelastbehav)
- [*CONNECTOR BEHAVIOR](ch03abk35.md)

### **可选参数：**

COMPONENT

将此参数设置为指定弹性行为所对应的连接器相对运动分量。对于此相对运动分量，连接器将作为弹簧使用。如果要定义线性耦合行为，则省略此参数。

DEPENDENCIES

将此参数设置为除了温度之外还包括在连接器弹性数据定义中的场变量依赖项数。如果省略此参数，则假定连接器弹性与场变量无关。请参阅 ["材料数据定义"中的"指定场变量依赖性"，Abaqus 分析用户指南第 21.1.2 节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，了解更多详细信息。

EXTRAPOLATION

设置 EXTRAPOLATION=CONSTANT（默认，除非使用 [*CONNECTOR BEHAVIOR](ch03abk35.md)、EXTRAPOLATION=LINEAR）以对独立变量指定范围外的因变量使用常量外推。

设置 EXTRAPOLATION=LINEAR 以对独立变量指定范围外的因变量使用线性外推。

FREQUENCY DEPENDENCE

此参数仅与 Abaqus/Standard 分析中的耦合线性弹簧刚度定义相关。使用此参数定义具有频率依赖性的弹簧刚度项。

设置 FREQUENCY DEPENDENCE=OFF（默认）如果弹簧刚度项的频率依赖性未定义。

设置 FREQUENCY DEPENDENCE=ON 如果弹簧刚度项的频率依赖性已定义。

INDEPENDENT COMPONENTS

仅当包含 COMPONENT 和 NONLINEAR 参数时才能使用此参数。

设置 INDEPENDENT COMPONENTS=POSITION（默认）以指定对弹性定义中包含的相对位置分量的依赖。

设置 INDEPENDENT COMPONENTS=CONSTITUTIVE MOTION 以指定对弹性定义中包含的构象相对运动分量的依赖。

如果弹性仅依赖于用 COMPONENT 参数指定的构象相对运动分量（非耦合行为），则不应使用 INDEPENDENT COMPONENTS 参数。

NONLINEAR

仅当包含 COMPONENT 参数时才能使用此参数。

包含此参数以定义非线性弹性行为。省略此参数以定义线性弹性行为。

REGULARIZE

此参数仅适用于 Abaqus/Explicit 分析。

设置 REGULARIZE=ON（默认，除非使用 [*CONNECTOR BEHAVIOR](ch03abk35.md)、REGULARIZE=OFF）以对用户定义的表格连接器弹性数据进行正则化。

设置 REGULARIZE=OFF 以直接使用用户定义的表格连接器弹性数据而不进行正则化。

RTOL

此参数仅适用于 Abaqus/Explicit 分析。

将此参数设置为用于正则化连接器弹性数据的容差。

如果省略此参数，则默认值为 RTOL=0.03，除非在 [*CONNECTOR BEHAVIOR](ch03abk35.md) 选项上指定了容差。

RIGID

包含此参数以指示定义了刚性弹性行为。

UNSYMM

此参数仅与 Abaqus/Standard 分析中的耦合线性弹簧刚度定义相关。

如果耦合线性弹簧刚度矩阵不对称，则包含此参数。

### **用于定义线性非耦合弹性行为的数据行（包含了 COMPONENT 参数但省略了 NONLINEAR 参数）：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于五时需要）：**

根据需要重复此数据行集，以将弹性刚度定义为频率、温度和其他预定义场变量的函数。

### **用于定义线性耦合弹性行为的数据行（省略了 COMPONENT、NONLINEAR 和 UNSYMM 参数；必须指定所有 21 个弹性常数，无论是否包含温度或场变量依赖）：**

**第一行：**

**第二行：**

**第三行：**

**后续行（仅在 DEPENDENCIES 参数值大于二时需要）：**

根据需要重复此数据行集，以将连接器弹性行为定义为温度和其他预定义场变量的函数。

### **用于定义具有频率依赖性的线性耦合弹性行为的数据行（省略了 COMPONENT、NONLINEAR 和 UNSYMM 参数，并且 FREQUENCY DEPENDENCE=ON；必须指定所有 21 个刚度常数，无论是否包含频率、温度或场变量依赖）：**

**第一行：**

**第二行：**

**第三行：**

**后续行（仅在 DEPENDENCIES 参数值大于二时需要）：**

根据需要重复此数据行集，以将连接器弹性行为定义为频率、温度和其他预定义场变量的函数。

### **用于使用非对称存储定义线性耦合刚度矩阵的数据行（省略了 COMPONENT 和 NONLINEAR 参数并包含了 UNSYMM 参数；必须指定所有 36 个刚度常数，无论是否包含温度或场变量依赖）：**

**第一行：**

**第二行：**

**第三行：**

**第四行：**

**第五行：**

**后续行（仅在 DEPENDENCIES 参数值大于三时需要）：**

根据需要重复此数据行集，以将非对称连接器刚度行为定义为温度和其他预定义场变量的函数。

### **用于使用非对称存储和频率依赖性定义线性耦合刚度矩阵的数据行（省略了 COMPONENT 和 NONLINEAR 参数，包含了 UNSYMM 参数，并且 FREQUENCY DEPENDENCE=ON；必须指定所有 36 个刚度常数，无论是否包含频率、温度或场变量依赖）：**

**第一行：**

**第二行：**

**第三行：**

**第四行：**

**第五行：**

**后续行（仅在 DEPENDENCIES 参数值大于二时需要）：**

根据需要重复此数据行集，以将非对称连接器刚度行为定义为频率、温度和其他预定义场变量的函数。

### **用于定义依赖于指定相对运动分量方向上的位移/旋转的非线性弹性行为的数据行（包含了 COMPONENT 和 NONLINEAR 参数但省略了 INDEPENDENT COMPONENTS 参数）：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于五时需要）：**

根据需要重复此数据行集，以将连接器弹性行为定义为温度和其他预定义场变量的函数。

### **用于定义依赖于多个分量方向上的相对位置或运动 的非线性弹性行为的数据行（包含了 COMPONENT、NONLINEAR 和 INDEPENDENT COMPONENTS 参数）：**

**第一行：**

**后续行：**

不要重复第一数据行。根据需要重复后续数据行，以将弹性刚度定义为连接器相对位置或构象相对运动、温度和其他预定义场变量的函数。

### **用于在省略了 COMPONENT 参数时定义类刚性弹性行为的数据行：**

**第一行：**

如果为所有可用的相对运动分量定义了类刚性弹性行为，则省略此数据行。




