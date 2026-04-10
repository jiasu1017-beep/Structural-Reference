# *CRUSHABLE FOAM HARDENING






### *CRUSHABLE FOAM HARDENING为可压碎泡沫塑性模型指定硬化。

此选项用于为使用可压碎泡沫塑性模型的弹塑性材料定义硬化数据。必须与 [*CRUSHABLE FOAM](ch03abk87.md) 选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型

**Abaqus/CAE: **属性模块

##### **参考：**

- ["可压碎泡沫塑性模型，" Abaqus 分析用户指南第 23.3.5 节](../usb/usb-link.md#usb-mat-ccrushfoam)
- [*CRUSHABLE FOAM](ch03abk87.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为除了温度之外还包括在屈服面大小定义中的场变量依赖项数。如果省略此参数，则假定屈服面大小仅依赖于体积塑性应变，也可能依赖于温度。请参阅 ["材料数据定义"中的"指定场变量依赖性"，Abaqus 分析用户指南第 21.1.2 节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，了解更多详细信息。

### **用于定义可压碎泡沫硬化的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于五时需要）：**

根据需要重复此数据行集，以定义单轴压缩中的屈服应力对相应轴向塑性应变的依赖性，以及在需要时对温度和其他预定义场变量的依赖性。




