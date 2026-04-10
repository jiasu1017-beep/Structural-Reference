# *SPRING





### *SPRING定义弹簧行为。

此选项用于为弹簧单元定义弹簧行为。它还用于分配结构阻尼因子以形成弹簧刚度矩阵的虚部。虚刚度表示对频率域动态方程和支持非对角阻尼的时域模式动态分析的单元级阻尼贡献（参见["Modal dynamic analysis," Section 2.5.5 of the Abaqus Theory Guide](../stm/stm-link.md#stm-anl-modaldynamic)）。

在Abaqus/Standard分析中，它还用于为ITS和JOINTC单元定义弹簧行为。如果[*SPRING](ch18abk29.md)选项用于定义ITS或JOINTC单元行为的一部分，则必须与[*ITS](ch09abk23.md)或[*JOINT](ch10abk01.md)选项配合使用，且不应使用ELSET和ORIENTATION参数。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**部件、部件实例、装配

**Abaqus/CAE：**Property模块和Interaction模块；仅支持独立于场变量的线性行为。对于非线性行为或包含场变量，请在Interaction模块中对连接器建模。

##### **参考：**

- ["Springs," Section 32.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-espring)
- ["Flexible joint element," Section 32.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ejoint)
- ["Tube support elements," Section 32.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eitselem)

### **如果正在定义弹簧单元行为时的必需参数：**

ELSET

将此参数设置为包含要定义此行为的弹簧单元的单元集名称。

### **可选参数：**

COMPLEX STIFFNESS

此参数与直接求解和基于子空间的稳态分析以及在支持非对角阻尼的Abaqus/Standard中具有[*FREQUENCY](ch06abk35.md)，DAMPING PROJECTION=ON的基于模式的分析相关。

包含此参数以定义刚度的实部和虚部。虚部表示结构阻尼。

如果省略此参数，则默认为仅实刚度。

DEPENDENCIES

将此参数设置为除了温度之外还包括在实弹簧刚度数据定义中的场变量依赖项数。如果省略此参数，则假定弹簧刚度与场变量无关。有关更多信息，请参见["Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata)中的"使用DEPENDENCIES参数定义场变量依赖性"。

NONLINEAR

包含此参数以定义非线性弹簧行为。省略此参数以定义线性弹簧行为。

ORIENTATION

此参数仅适用于Abaqus/Standard分析。

如果此选项用于定义SPRING1或SPRING2单元的行为，则此参数可用于引用方向定义，以便弹簧在局部系统中作用。将此参数设置为[*ORIENTATION](ch15abk01.md)定义的名称（["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)）。

RTOL

此参数仅适用于Abaqus/Explicit分析。

将此参数设置为用于正则化材料数据的容差。默认值为RTOL=0.03。有关数据正则化的讨论，请参见["Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata)。

### **为SPRINGA或ITS单元定义线性弹簧行为的数据行：**

**第一行：**

**第二行：**

**后续行（仅在DEPENDENCIES参数值大于五时需要）：**

根据需要重复此组数据行，以将弹簧刚度定义为频率、温度和其他预定义场变量的函数。

### **为SPRINGA或ITS单元定义非线性弹簧行为的数据行：**

**第一行：**

**第二行：**

**后续行（仅在DEPENDENCIES参数值大于五时需要）：**

根据需要重复此组数据行，以将弹簧刚度定义为温度和其他预定义场变量的函数。

### **为SPRING1、SPRING2或JOINTC单元定义线性弹簧行为的数据行：**

**第一行：**

如果在定义弹簧单元的[*SPRING](ch18abk29.md)选项上或定义接头单元的[*JOINT](ch10abk01.md)选项上包含了ORIENTATION参数，则此处指定的自由度在由引用的[*ORIENTATION](ch15abk01.md)选项定义的局部系统中。

**第二行：**

**后续行（仅在DEPENDENCIES参数值大于五时需要）：**

根据需要重复此组数据行，以将弹簧刚度定义为频率、温度和其他预定义场变量的函数。

### **为SPRING1、SPRING2或JOINTC单元定义非线性弹簧行为的数据行：**

**第一行：**

如果在定义弹簧单元的[*SPRING](ch18abk29.md)选项上或定义接头单元的[*JOINT](ch10abk01.md)选项上包含了ORIENTATION参数，则此处指定的自由度在由引用的[*ORIENTATION](ch15abk01.md)选项定义的局部系统中。

**第二行：**

**后续行（仅在DEPENDENCIES参数值大于五时需要）：**

根据需要重复此组数据行，以将弹簧刚度定义为温度和其他预定义场变量的函数。

### **为具有COMPLEX STIFFNESS的SPRINGA单元定义线性弹簧行为的数据行：**

**第一行：**

**第二行：**

根据需要重复此组数据行，以将弹簧刚度和结构阻尼因子定义为频率的函数。

### **为具有COMPLEX STIFFNESS的SPRING1和SPRING2单元定义线性弹簧行为的数据行：**

**第一行：**

如果在定义弹簧单元的[*SPRING](ch18abk29.md)选项上包含了ORIENTATION参数，则此处指定的自由度在由引用的[*ORIENTATION](ch15abk01.md)选项定义的局部系统中。

**第二行：**

根据需要重复此组数据行，以将弹簧刚度和结构阻尼因子定义为频率的函数。




