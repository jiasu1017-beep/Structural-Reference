# *SURFACE OUTPUT





### *SURFACE OUTPUT指定要写入输出数据库的表面变量。

此选项用于将表面变量写入输出数据库。它必须与[*OUTPUT](ch15abk03.md)选项一起使用。

**产品：**Abaqus/CFD

**类型：**历史数据

**级别：**步

##### **参考：**

- ["输出到输出数据库," Section 4.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-odboutput)
- [*OUTPUT](ch15abk03.md)

### **必需参数：**

SURFACE

将此参数设置为正在为其发出此输出请求的表面名称。

### **请求表面输出的数据行：**

**第一行：**

根据需要重复此数据行，以定义要写入输出数据库的变量列表。





