# *CAP PLASTICITY






### *CAP PLASTICITY指定改进的 Drucker-Prager/帽盖塑性模型。

此选项用于为使用改进的 Drucker-Prager/帽盖塑性模型的弹塑性材料定义屈服面参数。必须与 [*CAP HARDENING](ch03abk03.md) 选项结合使用，并且在 Abaqus/Standard 分析中包含蠕变材料行为时，还须与 [*CAP CREEP](ch03abk02.md) 选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE: **属性模块

##### **参考：**

- ["改进的 Drucker-Prager/帽盖模型，" Abaqus 分析用户指南第 23.3.2 节](../usb/usb-link.md#usb-mat-ccapplastic)
- [*CAP HARDENING](ch03abk03.md)
- [*CAP CREEP](ch03abk02.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为除了温度之外还包括在 Drucker-Prager/帽盖参数定义中的场变量依赖项数。如果省略此参数，则假定 Drucker-Prager/帽盖参数为常数或仅依赖于温度。请参阅 ["材料数据定义"中的"指定场变量依赖性"，Abaqus 分析用户指南第 21.1.2 节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，了解更多详细信息。

### **用于定义 Drucker-Prager/帽盖塑性屈服面参数的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于一时需要）：**

根据需要重复此数据行集，以定义 Drucker-Prager/帽盖参数对温度和其他预定义场变量的依赖性。




