# *FAIL STRESS









### *FAIL STRESS定义基于应力的失效准则的参数。

此选项用于定义基于应力的失效准则的应力极限。它只能与[*ELASTIC](ch05abk03.md)选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**属性模块

##### **参考：**

- ["平面应力正交各向异性失效准则，" Abaqus分析用户指南第22.2.3节](../usb/usb-link.md#usb-mat-cfailuremeasures)
- [*ELASTIC](ch05abk03.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为除了温度之外，失效准则定义中包含的场变量依赖项数。如果省略此参数，则假定失效准则仅取决于温度。有关更多信息，请参见["材料数据定义，" Abaqus分析用户指南第21.1.2节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)中的"指定场变量依赖性"。

### **定义基于应力的失效准则的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值不为零时需要）：**

根据需要重复此组数据行，以将失效准则定义为温度和其他预定义场变量的函数。




