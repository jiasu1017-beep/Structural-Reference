# *MATRIX OUTPUT









### *MATRIX OUTPUT以各种形式输出生成的矩阵。

此选项用于将生成的全局矩阵以组装形式或逐单元形式写入文件。它只能用于矩阵生成分析。

**产品：**Abaqus/Standard  

**类型：**历史数据  

**级别：**步骤

##### **参考：**

- ["生成矩阵，" Abaqus Analysis User's Guide第10.3.1节](../usb/usb-link.md#usb-anl-amtxgenerationperturbation)
- [*MATRIX GENERATE](ch13abk12.md)

### **至少需要以下参数之一：**

STIFFNESS

包含此参数以输出刚度矩阵。

MASS

包含此参数以输出质量矩阵。

VISCOUS DAMPING

包含此参数以输出粘性阻尼矩阵。

STRUCTURAL DAMPING

包含此参数以输出结构阻尼矩阵。

LOAD

包含此参数以输出荷载矩阵。

### **可选参数：**

FORMAT

设置FORMAT=MATRIX INPUT（默认）以指定输出使用与Abaqus/Standard中矩阵定义技术使用的格式一致的矩阵输入文本格式。

设置FORMAT=LABELS以指定输出使用标准标签格式。

设置FORMAT=COORDINATE以指定输出使用通用数学坐标格式。

**此选项没有关联的数据行。**