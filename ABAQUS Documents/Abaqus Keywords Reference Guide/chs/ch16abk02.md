# *PARAMETER DEPENDENCE









### *PARAMETER DEPENDENCE为表格依赖参数定义依赖表。

此选项用于定义指定表格依赖参数和独立参数之间关系的依赖表。

**产品：**Abaqus/Standard  Abaqus/Explicit  

**类型：**模型数据  

**级别：**部件、部件实例、装配、模型、步骤

##### **参考：**

- ["参数化输入，" Abaqus Analysis User's Guide第1.4.1节](../usb/usb-link.md#usb-int-iparinput)
- ["参数化形状变化，" Abaqus Analysis User's Guide第2.1.2节](../usb/usb-link.md#usb-int-iparshapevar)

### **必需参数：**

NUMBER VALUES

将此关键字参数设置为参数依赖表每行的数值数量。此数字必须等于此表所使用的依赖参数数量和独立参数数量之和。

TABLE

将此关键字参数设置为此选项中定义的表名称。

### **定义参数依赖表的数据行：**

**第一行：**

根据需要重复此数据行以定义参数依赖表的附加行。此数据行上给出的数据不能被参数化。