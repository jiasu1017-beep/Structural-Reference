# *EMISSIVITY









### *EMISSIVITY指定表面发射率。

此选项用于定义腔体辐射问题中表面的发射率。它必须紧跟在[*SURFACE PROPERTY](ch18abk52.md)选项之后，并且必须与[*PHYSICAL CONSTANTS](ch16abk09.md)选项结合使用，后者用于定义斯特藩-玻尔兹曼常数。

**产品：**Abaqus/Standard  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**相互作用模块

##### **参考：**

- ["腔体辐射，" Abaqus分析用户指南第41.1.1节](../usb/usb-link.md#usb-cni-acavityradiation)
- [*SURFACE PROPERTY](ch18abk52.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为发射率定义中包含的场变量数。如果省略此参数，则假定发射率不依赖于任何场变量（但可能仍取决于温度）。有关更多信息，请参见["材料数据定义，" Abaqus分析用户指南第21.1.2节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)中的"指定场变量依赖性"。

### **定义表面发射率的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于六时需要）：**

根据需要重复此组数据行，以将发射率定义为温度和用户定义场变量的函数。




