# *MATRIX INPUT









### *MATRIX INPUT读取模型一部分的矩阵。

此选项可用于输入稀疏格式的矩阵。

**产品：**Abaqus/Standard  

**类型：**模型数据  

**级别：**模型  

##### **参考：**

- ["定义矩阵，" Abaqus Analysis User's Guide第2.11.1节](../usb/usb-link.md#usb-int-idefiningmatrices)
- [*MATRIX ASSEMBLE](ch13abk10.md)

### **必需参数：**

NAME

将此参数设置为将用于引用此矩阵的标签。

### **可选参数：**

INPUT

将此参数设置为要从中以文本格式读取数据行的备用输入文件名称。

将此参数设置为.sim文件名称以从SIM数据库读取矩阵。在这种情况下，MATRIX参数也是必需的。

如果省略此参数，则假定数据在关键字行之后。

MATRIX

此参数定义要从SIM数据库读取的矩阵。它必须与定义.sim文件的INPUT参数一起使用。

设置MATRIX=STIFFNESS以读取刚度矩阵。

设置MATRIX=MASS以读取质量矩阵。

设置MATRIX=VISCOUS DAMPING以读取粘性阻尼矩阵。

设置MATRIX=STRUCTURAL DAMPING以读取结构阻尼矩阵。

SCALE FACTOR

将此参数设置为一个非零实数，所有矩阵条目都将乘以此数。默认值为。

TYPE

此参数定义矩阵的形状。

设置TYPE=SYMMETRIC（默认）以读取方对称矩阵的上三角或下三角部分。如果指定了满矩阵，则对角线上方和下方的对应项必须相等。

设置TYPE=UNSYMMETRIC以读取方非对称矩阵。

### **以稀疏格式定义矩阵的数据行（仅非零项）：**

**第一行：**

给出数据以按下三角、上三角或方阵格式定义对称矩阵。对于要对称的方阵，对角线上方和下方的对应条目必须具有完全相同的值。

根据需要重复此数据行。