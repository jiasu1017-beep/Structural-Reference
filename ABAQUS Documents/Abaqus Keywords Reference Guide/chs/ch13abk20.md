# *MODAL OUTPUT









### *MODAL OUTPUT在基于模式的动力学或复特征值提取程序期间将广义坐标（模态幅度）数据写入输出数据库。

此选项用于在基于模式的动力学或复特征值提取程序期间将广义坐标（模态幅度和相位）值写入Abaqus/Standard输出数据库。它必须与[*OUTPUT](ch15abk03.md)、HISTORY选项结合使用。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**历史数据  

**级别：**步骤

**Abaqus/CAE：**步骤模块

##### **参考：**

- ["输出到输出数据库，" Abaqus Analysis User's Guide第4.1.3节](../usb/usb-link.md#usb-out-odboutput)
- [*OUTPUT](ch15abk03.md)

### **可选参数：**

VARIABLE

设置VARIABLE=ALL以指示所有适用于此程序和材料类型的模态变量都应写入输出数据库。

如果省略此参数，则必须在数据行上指定请求输出的模态变量。

### **请求模态输出的数据行：**

**第一行：**

根据需要重复此数据行以定义要写入输出数据库的模态变量。