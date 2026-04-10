# *MATRIX









### *MATRIX读取线性用户单元的刚度矩阵或质量矩阵。

此选项只能与[*USER ELEMENT](ch20abk07.md)、LINEAR选项结合使用。它用于读取用户单元的刚度矩阵或质量矩阵。如果只需要刚度或质量，可以使用一次；如果需要同时提供两个矩阵，可以使用两次。

**产品：**Abaqus/Standard  

**类型：**模型数据  

**级别：**部件、部件实例、模型  

##### **参考：**

- ["用户定义单元，" Abaqus Analysis User's Guide第32.15.1节](../usb/usb-link.md#usb-elm-euserelem)
- [*USER ELEMENT](ch20abk07.md)

### **必需参数：**

TYPE

设置TYPE=MASS以定义质量矩阵。设置TYPE=STIFFNESS以定义刚度矩阵。

### **可选参数：**

INPUT

将此参数设置为要从中读取数据行的备用输入文件名称。如果省略此参数，则假定数据在关键字行之后。

### **定义矩阵的数据行：**

**第一行：**

根据需要重复此数据行。