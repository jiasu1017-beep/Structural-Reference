# *INCREMENTATION OUTPUT






### *INCREMENTATION OUTPUT定义时间增量数据的输出数据库请求。

此选项用于将增量变量写入输出数据库。它必须与 [*OUTPUT](ch15abk03.md), HISTORY 选项一起使用。

**产品：** Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：** 历史数据  

**级别：** 步骤  

**Abaqus/CAE：** Step 模块

##### **参考文献：**

- ["输出到输出数据库，" Abaqus Analysis User's Guide 第 4.1.3 节](../usb/usb-link.md#usb-out-odboutput)
- [*OUTPUT](ch15abk03.md)

### **可选参数：**

VARIABLE

设置 VARIABLE=ALL 以指示所有适用于此步骤类型的增量变量都应写入输出数据库。

设置 VARIABLE=PRESELECT 以指示当前步骤类型的默认增量输出变量应写入输出数据库。可以在数据行上请求其他输出变量。

如果省略此参数，则必须在数据行上指定请求输出的增量变量。

### **请求增量输出的数据行：**

**第一行：**

根据需要重复此数据行，以定义要写入输出数据库的时间增量变量。




