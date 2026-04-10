# *RADIATION OUTPUT







### *RADIATION OUTPUT为腔体辐射变量定义输出数据库请求。

此选项用于将腔体辐射变量写入输出数据库。它必须与[*OUTPUT](ch15abk03.md)选项结合使用。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**历史数据  

**级别：**步骤  

**Abaqus/CAE：**步骤模块

##### **参考：**

- ["输出到输出数据库，" Abaqus Analysis User's Guide第4.1.3节](../usb/usb-link.md#usb-out-odboutput)
- [*OUTPUT](ch15abk03.md)

### **可选的互斥参数（如果未指定，将为模型中的所有腔体提供输出）：**

CAVITY

将此参数设置为此输出请求所针对的腔体名称。

ELSET

将此参数设置为此输出请求所针对的元素集名称。

SURFACE

将此参数设置为此输出请求所针对的表面名称。

### **可选参数：**

VARIABLE

设置VARIABLE=ALL以指示所有适用于此过程和材料类型的腔体辐射变量都应写入输出数据库。

如果省略此参数，则必须在数据行上指定请求输出的腔体辐射变量。

### **请求腔体辐射输出的数据行：**

**第一行：**

根据需要重复此数据行，以定义要写入输出数据库的腔体辐射变量。
