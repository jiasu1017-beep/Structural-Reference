# *CAPACITY






### *CAPACITY定义理想气体物种的恒压摩尔热容。

此选项用于定义理想气体物种的恒压摩尔热容。只能与 [*FLUID BEHAVIOR](ch06abk16.md) 选项结合使用。

**产品：**Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["流体空腔定义，" Abaqus 分析用户指南第 11.5.2 节](../usb/usb-link.md#usb-anl-afluidcavities)
- ["充气器定义，" Abaqus 分析用户指南第 11.5.4 节](../usb/usb-link.md#usb-anl-afluidinflator)
- [*FLUID BEHAVIOR](ch06abk16.md)
- [*FLUID CAVITY](ch06abk19.md)

### **必需参数：**

TYPE

设置 TYPE=POLYNOMIAL 以多项式表达式的形式定义恒压摩尔热容。

设置 TYPE=TABULAR 以表格形式定义恒压摩尔热容。

### **可选参数：**

DEPENDENCIES

此参数仅与 TYPE=TABULAR 相关。将此参数设置为包括在恒压摩尔热容规范中的场变量数。如果省略此参数，则假定恒压摩尔热容不依赖于任何场变量，但仍可能依赖于温度。

### **TYPE=POLYNOMIAL 的数据行：**

**第一行（也是唯一行）：**

### **TYPE=TABULAR 的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于六时需要）：**

根据需要重复此数据行集，以将恒压热容定义为温度和其他预定义场变量的函数。




