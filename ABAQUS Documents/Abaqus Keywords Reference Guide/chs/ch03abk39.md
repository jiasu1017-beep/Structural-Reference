# *CONNECTOR DAMPING





### *CONNECTOR DAMPING定义连接器阻尼行为。

此选项用于为连接器单元定义阻尼行为。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Interaction模块

##### **参考：**

- ["连接器行为"，Abaqus Analysis User's Guide第31.2.1节](../usb/usb-link.md#usb-elm-econnectorbehavior)
- ["连接器阻尼行为"，Abaqus Analysis User's Guide第31.2.3节](../usb/usb-link.md#usb-elm-econndampingbehav)
- [*CONNECTOR BEHAVIOR](ch03abk35.md)

### **可选参数：**

COMPONENT

将此参数设置为为连接器指定阻尼行为的相对运动分量。对于此相对运动分量，对于TYPE=VISCOUS，连接器将充当阻尼器。省略此参数以定义耦合行为。

TYPE

将此参数设置为VISCOUS（默认值）以指定速度比例阻尼。

将此参数设置为STRUCTURAL以指定位移比例阻尼。此设置适用于稳态动力学直接分析和子空间投影分析，以及在Abaqus/Standard中支持非对角阻尼的稳态和瞬态基于模态的分析。如果TYPE=STRUCTURAL，则仅允许线性阻尼行为。

### **TYPE=VISCOUS的可选参数：**

DEPENDENCIES

将此参数设置为除了温度之外还包括在连接器阻尼数据定义中的场变量依赖项数。如果省略此参数，则假定连接器阻尼独立于场变量。请参见["指定场变量依赖性"，Abaqus Analysis User's Guide第21.1.2节"材料数据定义"](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，以获取更多信息。

EXTRAPOLATION

设置EXTRAPOLATION=CONSTANT（默认值，除非使用[*CONNECTOR BEHAVIOR](ch03abk35.md)，EXTRAPOLATION=LINEAR）以在独立变量的指定范围外使用常量外推。

设置EXTRAPOLATION=LINEAR以在独立变量的指定范围外使用线性外推。

FREQUENCY DEPENDENCE

此参数仅与Abaqus/Standard分析中的耦合线性粘性阻尼定义相关。使用此参数定义具有频率依赖性的粘性阻尼项。

设置FREQUENCY DEPENDENCE=OFF（默认值），如果未定义阻尼项的频率依赖性。

设置FREQUENCY DEPENDENCE=ON，如果定义了阻尼项的频率依赖性。

INDEPENDENT COMPONENTS

此参数只能在包含COMPONENT和NONLINEAR参数时使用。

设置INDEPENDENT COMPONENTS=POSITION（默认值）以指定阻尼定义中包含的相对位置分量的依赖关系。

设置INDEPENDENT COMPONENTS=CONSTITUTIVE MOTION以指定阻尼定义中包含的本构相对运动分量的依赖关系。

如果阻尼仅依赖于COMPONENT参数指定的分量中的相对速度，则不应使用INDEPENDENT COMPONENTS参数。

NONLINEAR

此参数只能在包含COMPONENT参数时使用。

包含此参数以定义非线性阻尼行为。省略此参数以定义线性阻尼行为。

REGULARIZE

此参数仅适用于Abaqus/Explicit分析。

设置REGULARIZE=ON（默认值，除非使用[*CONNECTOR BEHAVIOR](ch03abk35.md)，REGULARIZE=OFF）以正则化用户定义的表格连接器阻尼数据。

设置REGULARIZE=OFF以直接使用用户定义的表格连接器阻尼数据而不进行正则化。

RTOL

此参数仅适用于Abaqus/Explicit分析。

将此参数设置为用于正则化连接器阻尼数据的容差。

如果省略此参数，默认值为RTOL=0.03，除非在[*CONNECTOR BEHAVIOR](ch03abk35.md)选项上指定了容差。

UNSYMM

此参数仅与Abaqus/Standard分析中的线性耦合粘性阻尼定义相关。

如果线性耦合粘性阻尼矩阵不对称，则包含此参数。

### **定义线性解耦粘性阻尼行为的数据行（TYPE=VISCOUS，COMPONENT，NONLINEAR参数省略）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于五时需要）：**

根据需要重复此数据行集，以将阻尼系数定义为频率、温度和其他预定义场变量的函数。

### **定义线性耦合粘性阻尼行为的数据行（TYPE=VISCOUS，COMPONENT、NONLINEAR和UNSYMM参数省略；必须指定所有21个阻尼常数，无论是否包含温度或场变量依赖）：**

**第一行：**

**第二行：**

**第三行：**

**后续行（仅在DEPENDENCIES参数的值大于二时需要）：**

根据需要重复此数据行集，以将连接器阻尼行为定义为温度和其他预定义场变量的函数。

### **定义具有频率依赖性的线性耦合粘性阻尼行为的数据行（TYPE=VISCOUS，COMPONENT、NONLINEAR和UNSYMM参数省略，且FREQUENCY DEPENDENCE=ON；必须指定所有21个阻尼常数，无论是否包含频率、温度或场变量依赖）：**

**第一行：**

**第二行：**

**第三行：**

**后续行（仅在DEPENDENCIES参数的值大于二时需要）：**

根据需要重复此数据行集，以将连接器阻尼行为定义为频率、温度和其他预定义场变量的函数。

### **使用不对称存储定义线性耦合粘性阻尼行为的数据行（省略COMPONENT和NONLINEAR参数且包含UNSYMM；必须指定所有36个阻尼常数，无论是否包含温度或场变量依赖）：**

**第一行：**

**第二行：**

**第三行：**

**第四行：**

**第五行：**

**后续行（仅在DEPENDENCIES参数的值大于三时需要）：**

根据需要重复此数据行集，以将不对称连接器阻尼行为定义为温度和其他预定义场变量的函数。

### **使用不对称存储和频率依赖性定义线性耦合粘性阻尼行为的数据行（省略COMPONENT和NONLINEAR参数，包含UNSYMM参数，且FREQUENCY DEPENDENCE=ON；必须指定所有36个阻尼常数，无论是否包含频率、温度或场变量依赖）：**

**第一行：**

**第二行：**

**第三行：**

**第四行：**

**第五行：**

**后续行（仅在DEPENDENCIES参数的值大于二时需要）：**

根据需要重复此数据行集，以将不对称连接器阻尼行为定义为频率、温度和其他预定义场变量的函数。

### **定义依赖于指定相对运动分量方向速度的非线性粘性阻尼行为的数据行（TYPE=VISCOUS，COMPONENT，NONLINEAR，INDEPENDENT COMPONENTS参数省略）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于五时需要）：**

根据需要重复此数据行集，以将连接器阻尼行为定义为温度和其他预定义场变量的函数。

### **定义依赖于多个分量方向上的相对位移、位置或运动的线性粘性阻尼行为的数据行（TYPE=VISCOUS，COMPONENT，NONLINEAR，INDEPENDENT COMPONENTS）：**

**第一行：**

**后续行：**

**延续行（如需要）：**

不要重复第一数据行。根据需要重复后续数据行，以将阻尼行为定义为连接器相对（角）速度、位置或运动；温度；以及其他预定义场变量的函数。

### **定义线性解耦结构阻尼行为的数据行（TYPE=STRUCTURAL，COMPONENT）：**

**第一行：**

根据需要重复此数据行，以将阻尼系数定义为频率的函数。

### **定义线性耦合结构阻尼行为的数据行（TYPE=STRUCTURAL，省略COMPONENT参数）：**

**第一行：**

**第二行：**

**第三行：**




