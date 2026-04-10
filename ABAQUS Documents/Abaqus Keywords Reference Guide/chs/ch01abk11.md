# *AQUA





### *AQUA定义用于加载浸没梁型结构的流体变量。

此选项用于定义流体属性和稳态流速度。

**产品：**Abaqus/Aqua  

**类型：**模型数据

**级别：**模型

##### **参考：**

- ["Abaqus/Aqua分析，" Abaqus Analysis User's Guide第6.11.1节](../usb/usb-link.md#usb-anl-aaqua)

### **可选参数：**

INPUT

将此参数设置为包含此选项数据行的备用输入文件名称。参见["输入语法规则，" Abaqus Analysis User's Guide第1.2.1节](../usb/usb-link.md#usb-int-iinputsyntax)，了解此类文件名的语法。如果省略此参数，则假定数据跟在关键字行之后。

### **定义流体属性和稳态流的数据行：**

**第一行：**

**第二行：**

根据需要重复第二数据行，以将稳态流速度定义为高度和空间坐标的函数。参见["输入语法规则，" Abaqus Analysis User's Guide第1.2.1节](../usb/usb-link.md#usb-int-iinputsyntax)，了解如何将属性定义为多个自变量的函数。