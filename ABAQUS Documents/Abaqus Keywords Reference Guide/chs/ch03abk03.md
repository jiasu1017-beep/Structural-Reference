# *CAP HARDENING






### *CAP HARDENING指定 Drucker-Prager/帽盖塑性硬化。

此选项用于为使用 Drucker-Prager/帽盖屈服面的弹塑性材料指定材料模型的硬化部分。必须与 [*CAP PLASTICITY](ch03abk04.md) 选项结合使用，并且在 Abaqus/Standard 分析中包含蠕变材料行为时，还须与 [*CAP CREEP](ch03abk02.md) 选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE: **属性模块

##### **参考：**

- ["改进的 Drucker-Prager/帽盖模型，" Abaqus 分析用户指南第 23.3.2 节](../usb/usb-link.md#usb-mat-ccapplastic)
- [*CAP PLASTICITY](ch03abk04.md)
- [*CAP CREEP](ch03abk02.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为除了温度之外还包括在静水屈服应力定义中的场变量依赖项数。如果省略此参数，则假定静水屈服应力仅依赖于体积塑性应变，也可能依赖于温度。请参阅 ["材料数据定义"中的"指定场变量依赖性"，Abaqus 分析用户指南第 21.1.2 节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，了解更多详细信息。

SCALESTRESS

将此参数设置为您想要对屈服应力进行缩放的因子。

### **用于定义 Drucker-Prager/帽盖塑性硬化的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于五时需要）：**

根据需要重复此数据行集，以定义静水屈服应力对体积非弹性应变（在 Abaqus/Standard 中）或体积塑性应变（在 Abaqus/Explicit 中）的依赖性，以及在需要时对温度和其他预定义场变量的依赖性。




