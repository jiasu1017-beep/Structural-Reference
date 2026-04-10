# *FILM PROPERTY









### *FILM PROPERTY将膜系数定义为温度和场变量的函数。

此选项用于为完全耦合的热应力分析将膜系数定义为温度和场变量的函数。在Abaqus/Standard中，它也用于传热、耦合热-电和耦合热-电-结构分析。它只能与[*FILM](ch06abk10.md)、[*CFILM](ch03abk14.md)和[*SFILM](ch18abk08.md)选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**相互作用模块

##### **参考：**

- ["热载荷，" Abaqus分析用户指南第34.4.4节](../usb/usb-link.md#usb-prc-pthermal)
- [*FILM](ch06abk10.md)
- [*CFILM](ch03abk14.md)

### **必需参数：**

NAME

将此参数设置为一个标签，用于引用此膜属性。此标签在[*FILM](ch06abk10.md)或[*CFILM](ch03abk14.md)选项的数据行中被引用。

### **可选参数：**

DEPENDENCIES

将此参数设置为膜系数定义中包含的场变量数。如果省略此参数，则假定膜系数仅取决于温度。有关更多信息，请参见["材料数据定义，" Abaqus分析用户指南第21.1.2节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)中的"指定场变量依赖性"。

### **将膜系数定义为温度和场变量的函数的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于六时需要）：**

根据需要重复此组数据行以创建膜属性表。




