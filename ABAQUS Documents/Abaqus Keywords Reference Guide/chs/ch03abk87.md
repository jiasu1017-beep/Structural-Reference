# *CRUSHABLE FOAM






### *CRUSHABLE FOAM指定可压碎泡沫塑性模型。

此选项用于为使用可压碎泡沫塑性模型的弹塑性材料指定材料行为的塑性部分。必须与 [*CRUSHABLE FOAM HARDENING](ch03abk88.md) 选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型

**Abaqus/CAE: **属性模块

##### **参考：**

- ["可压碎泡沫塑性模型，" Abaqus 分析用户指南第 23.3.5 节](../usb/usb-link.md#usb-mat-ccrushfoam)
- [*CRUSHABLE FOAM HARDENING](ch03abk88.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为除了温度之外还包括在可压碎泡沫参数定义中的场变量依赖项数。如果省略此参数，则假定可压碎泡沫参数为常数或仅依赖于温度。请参阅 ["材料数据定义"中的"指定场变量依赖性"，Abaqus 分析用户指南第 21.1.2 节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，了解更多详细信息。

HARDENING

设置 HARDENING=VOLUMETRIC（默认）以指定体积硬化模型。

设置 HARDENING=ISOTROPIC 以指定各向同性硬化模型。

### **用于使用体积硬化（HARDENING=VOLUMETRIC）定义可压碎泡沫塑性模型的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于五时需要）：**

根据需要重复此数据行集，以定义可压碎泡沫参数对温度和其他预定义场变量的依赖性。

### **用于使用各向同性硬化（HARDENING=ISOTROPIC）定义可压碎泡沫塑性模型的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于五时需要）：**

根据需要重复此数据行集，以定义可压碎泡沫参数对温度和其他预定义场变量的依赖性。




