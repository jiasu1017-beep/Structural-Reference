# *CAVITY DEFINITION






### *CAVITY DEFINITION定义热辐射的空腔。

此选项用于定义热辐射热传递的空腔。只能与 [*SURFACE](ch18abk47.md)、TYPE=ELEMENT 选项结合使用。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["空腔辐射，" Abaqus 分析用户指南第 41.1.1 节](../usb/usb-link.md#usb-cni-acavityradiation)
- [*SURFACE](ch18abk47.md)
- [*SURFACE PROPERTY](ch18abk52.md)

### **必需参数：**

NAME

将此参数设置为将用于引用空腔的标签。

### **可选参数：**

AMBIENT TEMP

将此参数设置为在开放空腔情况下辐射发生的外部介质的参考温度。如果省略此参数，则假定空腔是封闭的。

PARALLEL DECOMPOSITION

设置 PARALLEL DECOMPOSITION=ON 以在空腔辐射分析期间启用空腔的并行分解。

设置 PARALLEL DECOMPOSITION=OFF（默认）以在空腔辐射分析期间禁用空腔的并行分解。

SET PROPERTY

包含此参数以设置或重新定义构成空腔的表面的表面属性。如果省略此参数，则假定空腔由已作为表面定义一部分定义了表面属性的表面组成。

### **使用已定义表面属性的表面定义热辐射空腔的数据行（默认）：**

**第一行：**

根据需要重复此数据行以定义空腔。每行最多允许 16 个条目。

### **包含 SET PROPERTY 参数时定义空腔的数据行：**

**第一行：**

根据需要重复此数据行以定义空腔。每行最多允许 16 个条目。




