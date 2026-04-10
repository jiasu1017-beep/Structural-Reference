# *ENERGY OUTPUT









### *ENERGY OUTPUT定义整个模型或单元集能量数据的输出数据库请求。

此选项用于将整个模型或单元集能量请求写入输出数据库。它必须与[*OUTPUT](ch15abk03.md)，HISTORY选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE

**类型：**历史数据

**级别：**步骤

**Abaqus/CAE：**步骤模块

##### **参考：**

- ["输出到输出数据库，" Abaqus分析用户指南第4.1.3节](../usb/usb-link.md#usb-out-odboutput)
- [*OUTPUT](ch15abk03.md)

### **可选参数：**

ELSET

将此参数设置为正在为其发出输出请求的单元集名称。

VARIABLE

设置 VARIABLE=ALL 以指示所有适用于此过程和材料类型的能量变量都应写入输出数据库。

设置 VARIABLE=PRESELECT 以指示当前过程类型的默认能量输出变量应写入输出数据库。可以在数据行上请求其他输出变量。

如果省略此参数且数据行上未指定能量变量，则所有能量变量都将写入输出数据库。

PER ELEMENT SET

此参数仅适用于Abaqus/Explicit分析。

包含此参数以指示请求的能量变量将为每个用户定义的单元集写入输出数据库（所有内部单元集，包括在Abaqus/CAE中定义的内部单元集和在分析期间创建的内部单元集，均被排除）。

PER SECTION

此参数仅适用于Abaqus/Explicit分析。

包含此参数以指示请求的能量变量将为每个与截面定义关联的用户定义单元集写入输出数据库（所有内部单元集，包括在Abaqus/CAE中定义的内部单元集和在分析期间创建的内部单元集，均被排除）。

### **请求能量输出的数据行：**

**第一行：**

根据需要重复此数据行，以定义要写入输出数据库的能量变量。




