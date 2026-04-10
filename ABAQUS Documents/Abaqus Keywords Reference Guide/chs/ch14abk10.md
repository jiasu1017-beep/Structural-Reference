# *NODE OUTPUT









### *NODE OUTPUT为节点数据定义输出数据库请求。

此选项用于将节点变量写入输出数据库。它必须与[*OUTPUT](ch15abk03.md)选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**类型：**历史数据  

**级别：**步骤

**Abaqus/CAE：**步骤模块

##### **参考：**

- ["输出到输出数据库，" Abaqus Analysis User's Guide第4.1.3节](../usb/usb-link.md#usb-out-odboutput)
- [*OUTPUT](ch15abk03.md)

### **当[*NODE OUTPUT](ch14abk11.md)选项与[*OUTPUT](ch15abk03.md)、HISTORY选项结合用于Abaqus/Standard或Abaqus/Explicit时，需要以下互斥参数之一：**

NSET

将此参数设置为要为此输出请求的节点集名称。

TRACER SET

此参数仅适用于Abaqus/Explicit分析。

将此参数设置为此输出请求的追踪器集名称。

### **当[*NODE OUTPUT](ch14abk11.md)选项与[*OUTPUT](ch15abk03.md)、FIELD选项结合使用时的可选参数：**

EXTERIOR

此参数仅适用于Abaqus/Standard和Abaqus/Explicit分析。

包含此参数以将输出限制为仅属于外部三维单元的节点。

如果省略此参数和NSET参数，将为模型中的所有节点写入输出。

NSET

将此参数设置为此输出请求的节点集名称。

如果省略此参数和EXTERIOR参数，将为模型中的所有节点写入输出。

TRACER SET

此参数仅适用于Abaqus/Explicit分析。

将此参数设置为此输出请求的追踪器集名称。

此参数仅对位移输出请求有效。

### **当[*NODE OUTPUT](ch14abk11.md)选项与[*OUTPUT](ch15abk03.md)、HISTORY选项结合使用时的可选参数：**

GLOBAL

此参数仅适用于Abaqus/Standard和Abaqus/Explicit分析。

此参数仅在与用于定义局部坐标系的[*TRANSFORM](ch19abk11.md)选项一起使用的节点处相关。

设置GLOBAL=NO以在局部方向写入向量值节点变量。

设置GLOBAL=YES（默认）以在全局方向写入向量值节点变量。此默认值为[*NODE PRINT](ch14abk12.md)选项上默认值的相反值，因为大多数后处理器假定分量在全局系统中给出。

### **可选参数：**

VARIABLE

设置VARIABLE=ALL以指示所有适用于此程序和材料类型的节点变量都应写入输出数据库。

设置VARIABLE=PRESELECT以指示当前程序类型的默认节点输出变量应写入输出数据库。可以在数据行上请求其他输出变量。

如果省略此参数，则必须在数据行上指定请求输出的节点变量。

### **请求节点输出的数据行：**

**第一行：**

根据需要重复此数据行以定义要写入输出数据库的节点变量。