# *MATERIAL









### *MATERIAL开始材料定义。

此选项用于指示材料定义的开始。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["材料数据定义，" Abaqus Analysis User's Guide第21.1.2节](../usb/usb-link.md#usb-mat-cmaterialdata)

### **必需参数：**

NAME

将此参数设置为将用于在单元属性选项中引用该材料的标签。同一输入文件中的材料名称必须唯一。此外，材料名称应与[*CONNECTOR BEHAVIOR](ch03abk35.md)和[*FLUID BEHAVIOR](ch06abk16.md)等属性定义关联的名称保持唯一。材料名称遵循标签的命名约定，但不能以数字开头。

### **可选参数：**

RTOL

此参数仅适用于Abaqus/Explicit分析。

将此参数设置为用于正则化材料数据的容差。默认值为RTOL=0.03。

SRATE FACTOR

此参数仅适用于Abaqus/Explicit分析。

将此参数设置为用于过滤等效塑性应变率以评估应变率相关材料数据的因子。默认值为0.9。

STRAIN RATE REGULARIZATION

此参数仅适用于Abaqus/Explicit分析，仅用于正则化应变率相关的材料数据。

设置STRAIN RATE REGULARIZATION=LOGARITHMIC（默认）以使用对数正则化处理应变率相关材料数据。

设置STRAIN RATE REGULARIZATION=LINEAR以使用线性正则化处理应变率相关材料数据。

**此选项没有关联的数据行。**