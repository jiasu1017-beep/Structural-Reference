# *IMPEDANCE PROPERTY






### *IMPEDANCE PROPERTY为声学介质边界定义阻抗参数。

此选项用于在声学分析中定义压力与表面位移和速度法向分量之间的比例因子。[*IMPEDANCE PROPERTY](ch09abk02.md) 选项必须与 [*IMPEDANCE](ch09abk01.md) 或 [*SIMPEDANCE](ch18abk17.md) 选项一起使用。

**产品：** Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：** 模型数据  

**级别：** 模型  

**Abaqus/CAE：** Interaction 模块

##### **参考文献：**

- ["声学和冲击载荷，" Abaqus Analysis User's Guide 第 34.4.6 节](../usb/usb-link.md#usb-prc-pacoustic)
- [*IMPEDANCE](ch09abk01.md)
- [*SIMPEDANCE](ch18abk17.md)

### **必需参数：**

NAME

将此参数设置为一个标签，用于在 [*IMPEDANCE](ch09abk01.md) 或 [*SIMPEDANCE](ch18abk17.md) 选项中引用该阻抗属性时进行引用。

### **可选参数：**

DATA

设置 DATA=ADMITTANCE（默认）以使用导纳值表指定阻抗。

设置 DATA=IMPEDANCE 以使用阻抗的实部和虚部表指定阻抗。

INPUT

将此参数设置为包含此选项数据行的备用输入文件的名称。请参阅 ["输入语法规则，" Abaqus Analysis User's Guide 第 1.2.1 节](../usb/usb-link.md#usb-int-iinputsyntax)，了解此类文件名的语法。如果省略此参数，则假定数据跟在关键字行之后。

### **使用 DATA=ADMITTANCE（默认）定义阻抗的数据行：**

**第一行：**

在 Abaqus/Standard 中根据需要重复此数据行，以描述系数随频率的变化。仅在直接积分步骤中使用输入的第一行。

### **使用 DATA=IMPEDANCE 定义阻抗的数据行：**

**第一行：**

在 Abaqus/Standard 中根据需要重复此数据行，以描述系数随频率的变化。仅在直接积分步骤中使用输入的第一行。




