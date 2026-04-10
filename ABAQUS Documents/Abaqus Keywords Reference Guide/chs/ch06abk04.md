# *FAILURE RATIOS









### *FAILURE RATIOS定义*CONCRETE模型的失效面形状。

此选项用于定义混凝土模型的失效面形状。如果使用，它必须出现在[*CONCRETE](ch03abk28.md)选项之后。[*FAILURE RATIOS](ch06abk04.md)选项也可以与[*TENSION STIFFENING](ch19abk04.md)和[*SHEAR RETENTION](ch18abk12.md)选项结合使用。

**产品：**Abaqus/Standard  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**属性模块

##### **参考：**

- ["混凝土弥散裂纹，" Abaqus分析用户指南第23.6.1节](../usb/usb-link.md#usb-mat-cconcrete)
- [*CONCRETE](ch03abk28.md)
- [*TENSION STIFFENING](ch19abk04.md)
- [*SHEAR RETENTION](ch18abk12.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为除了温度之外，失效比定义中包含的场变量依赖项数。如果省略此参数，则假定失效比仅取决于温度。有关更多信息，请参见["材料数据定义，" Abaqus分析用户指南第21.1.2节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)中的"指定场变量依赖性"。

### **为混凝土模型定义失效面的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于三时需要）：**

根据需要重复此组数据行，以定义失效比对温度和其他预定义场变量的依赖关系。




