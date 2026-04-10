# *DIFFUSIVITY





### *DIFFUSIVITY指定质量扩散率。

此选项用于定义扩散通过基体材料的相关材料的质量扩散率。它必须与 [*SOLUBILITY](ch18abk23.md) 选项结合使用。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["扩散率，" Abaqus分析用户指南第26.4.1节](../usb/usb-link.md#usb-mat-cdiffusivity)
- [*SOLUBILITY](ch18abk23.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为扩散率定义中包含的场变量数量。如果省略此参数，则假定扩散率不依赖于任何场变量，但可能仍取决于浓度和温度。请参见Abaqus分析用户指南第21.1.2节中的["指定场变量依赖性"](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，了解更多详细信息。

LAW

设置 LAW=GENERAL（默认）以选择一般质量扩散行为。设置 LAW=FICK 以选择Fick扩散定律。LAW=FICK 和 [*KAPPA](ch11abk01.md)、TYPE=TEMP 选项互斥。

TYPE

设置 TYPE=ISO（默认）以定义各向同性扩散率。设置 TYPE=ORTHO 以定义正交各向异性扩散率。设置 TYPE=ANISO 以定义完全各向异性扩散率。

### **定义各向同性扩散率的数据行（TYPE=ISO）：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于五时需要）：**

根据需要重复此组数据行，以将扩散率定义为浓度、温度和其他预定义场变量的函数。

### **定义正交各向异性扩散率的数据行（TYPE=ORTHO）：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于三时需要）：**

根据需要重复此组数据行，以将扩散率定义为浓度、温度和其他预定义场变量的函数。

### **定义各向异性扩散率的数据行（TYPE=ANISO）：**

**第一行：**

**后续行（仅在使用 DEPENDENCIES 参数时需要）：**

根据需要重复此组数据行，以将扩散率定义为浓度、温度和其他预定义场变量的函数。




