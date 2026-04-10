# *SOLUBILITY





### *SOLUBILITY指定溶解度。

此选项用于定义材料通过基体材料扩散的溶解度。它必须与[*DIFFUSIVITY](ch04abk23.md)选项配合使用。

**产品：**Abaqus/Standard  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Property模块

##### **参考：**

- ["Solubility," Section 26.4.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-csolubility)
- [*DIFFUSIVITY](ch04abk23.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为溶解度定义中包含的场变量依赖项数。如果省略此参数，则假定溶解度是常数或仅取决于温度。有关更多信息，请参见["Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)中的"指定场变量依赖性"。

### **定义溶解度的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于六时需要）：**

根据需要重复此组数据行，以将溶解度定义为温度和其他预定义场变量的函数。




