# *MOHR COULOMB HARDENING









### *MOHR COULOMB HARDENING指定莫尔-库仑塑性模型的硬化。

此选项用于为由莫尔-库仑塑性模型定义的材料定义分段线性硬化/软化行为。它必须与[*MOHR COULOMB](ch13abk23.md)选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["莫尔-库仑塑性，" Abaqus Analysis User's Guide第23.3.3节](../usb/usb-link.md#usb-mat-cmohrcoulomb)
- [*MOHR COULOMB](ch13abk23.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为除温度外内聚屈服应力定义中包含的场变量依赖数量。如果省略此参数，则假定内聚屈服应力仅取决于塑性应变，也可能取决于温度。

### **定义莫尔-库仑硬化的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于5时需要）：**

根据需要重复此组数据行，以定义内聚屈服应力对塑性应变以及对温度和其他预定义场变量的依赖性（如果需要）。