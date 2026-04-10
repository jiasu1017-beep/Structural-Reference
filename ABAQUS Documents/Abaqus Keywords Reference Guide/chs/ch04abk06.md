# *DASHPOT





### *DASHPOT定义阻尼器行为。

此选项用于为阻尼器单元定义阻尼器行为。

在Abaqus/Standard分析中，它还用于为ITS和JOINTC单元定义阻尼器行为。如果 [*DASHPOT](ch04abk08.md) 选项用于定义ITS或JOINTC单元的部分行为，则必须将其与 [*ITS](ch09abk23.md) 或 [*JOINT](ch10abk01.md) 选项结合使用，且不应使用 ELSET 和 ORIENTATION 参数。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**部件、部件实例、装配  

**Abaqus/CAE：**属性模块和相互作用模块；仅支持与场变量无关的线性行为。对于非线性行为或包含场变量，请在相互作用模块中对连接器进行建模。

##### **参考：**

- ["阻尼器，" Abaqus分析用户指南第32.2.1节](../usb/usb-link.md#usb-elm-edashpot)
- ["柔性关节单元，" Abaqus分析用户指南第32.3.1节](../usb/usb-link.md#usb-elm-ejoint)
- ["管道支撑单元，" Abaqus分析用户指南第32.8.1节](../usb/usb-link.md#usb-elm-eitselem)

### **定义阻尼器单元行为时的必需参数：**

ELSET

将此参数设置为包含正在定义此行为的阻尼器单元的单元集合名称。

### **可选参数：**

DEPENDENCIES

除了温度之外，将此参数设置为阻尼器系数定义中包含的场变量依赖项数量。如果省略此参数，则假定阻尼器系数与场变量无关。有关详细信息，请参见Abaqus分析用户指南第21.1.2节中的["指定场变量依赖性"](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)。

NONLINEAR

包含此参数以定义非线性阻尼器行为。省略此参数以定义线性阻尼器行为。

ORIENTATION

此参数仅适用于Abaqus/Standard分析。

如果此选项用于定义DASHPOT1或DASHPOT2单元的行为，则此参数可用于引用方向定义，以便阻尼器在局部系统中工作。将此参数设置为 [*ORIENTATION](ch15abk01.md) 定义的名称（["方向，" Abaqus分析用户指南第2.2.5节](../usb/usb-link.md#usb-int-corientation)）。

RTOL

此参数仅适用于Abaqus/Explicit分析。

将此参数设置为用于正则化材料数据的容差。默认值为 RTOL=0.03。有关数据正则化的讨论，请参见Abaqus分析用户指南第21.1.2节中的["材料数据定义"](../usb/usb-link.md#usb-mat-cmaterialdata)。

### **为DASHPOTA或ITS单元定义线性阻尼器行为的数据行：**

**第一行：**

**第二行：**

**后续行（仅在 DEPENDENCIES 参数值大于五时需要）：**

根据需要重复此组数据行，以将阻尼器系数定义为频率、温度和其他预定义场变量的函数。

### **为DASHPOTA或ITS单元定义非线性阻尼器行为的数据行：**

**第一行：**

**第二行：**

**后续行（仅在 DEPENDENCIES 参数值大于五时需要）：**

根据需要重复此组数据行，以将阻尼器系数定义为温度和其他预定义场变量的函数。

### **为DASHPOT1、DASHPOT2或JOINTC单元定义线性阻尼器行为的数据行：**

**第一行：**

如果在定义阻尼器单元时在 [*DASHPOT](ch04abk08.md) 选项上包含 ORIENTATION 参数，或在定义关节单元时在 [*JOINT](ch10abk01.md) 选项上包含 ORIENTATION 参数，则此处指定的自由度在由所引用的 [*ORIENTATION](ch15abk01.md) 选项定义的局部系统中。

**第二行：**

**后续行（仅在 DEPENDENCIES 参数值大于五时需要）：**

根据需要重复此组数据行，以将阻尼器系数定义为频率、温度和其他预定义场变量的函数。

### **为DASHPOT1、DASHPOT2或JOINTC单元定义非线性阻尼器行为的数据行：**

**第一行：**

如果在定义阻尼器单元时在 [*DASHPOT](ch04abk08.md) 选项上包含 ORIENTATION 参数，或在定义关节单元时在 [*JOINT](ch10abk01.md) 选项上包含 ORIENTATION 参数，则此处指定的自由度在由所引用的 [*ORIENTATION](ch15abk01.md) 选项定义的局部系统中。

**第二行：**

**后续行（仅在 DEPENDENCIES 参数值大于五时需要）：**

根据需要重复此组数据行，以将阻尼器系数定义为温度和其他预定义场变量的函数。




