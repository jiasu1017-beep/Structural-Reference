# *DESIGN GRADIENT





### *DESIGN GRADIENT直接指定设计灵敏度分析的设计梯度。

此选项用于直接指定关于设计参数的设计梯度，不包括与形状相关的设计参数。（默认情况下，Abaqus/Design将根据输入文件的参数化自动数值确定关于非形状设计参数的设计梯度。关于形状设计参数的设计梯度必须通过 [*PARAMETER SHAPE VARIATION](ch16abk03.md) 选项指定。）

**产品：**Abaqus/Design  

**类型：**模型数据  

**级别：**部件、部件实例、装配、模型、步骤

##### **参考：**

- ["设计灵敏度分析，" Abaqus分析用户指南第19.1.1节](../usb/usb-link.md#usb-anl-adsa)
- [*PARAMETER](ch16abk01.md)
- [*DESIGN PARAMETER](ch04abk16.md)

### **必需参数：**

DEPENDENT

将此参数设置为其关于设计参数的梯度要被指定的参数名称列表。列表必须放在括号内，参数名称用逗号分隔；例如，`(depPar1, depPar2, depPar3)`。

INDEPENDENT

将此参数设置为要指定梯度的设计参数的名称。

### **定义设计梯度的数据行：**

**第一行：**

根据需要重复此数据行，以连续定义从属参数关于设计参数的梯度。每行最多允许16个条目。




