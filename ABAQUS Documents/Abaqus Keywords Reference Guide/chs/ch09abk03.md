# *IMPERFECTION






### *IMPERFECTION引入用于后屈曲分析的几何缺陷。

此选项用于为后屈曲分析在模型中引入几何缺陷。

**产品：** Abaqus/Standard  Abaqus/Explicit  

**类型：** 模型数据  

**级别：** 模型  

##### **参考文献：**

- ["在模型中引入几何缺陷，" Abaqus Analysis User's Guide 第 11.3.1 节](../usb/usb-link.md#usb-anl-aimperfection)
- ["不稳定坍塌和后屈曲分析，" Abaqus Analysis User's Guide 第 6.2.4 节](../usb/usb-link.md#usb-anl-apostbuckling)
- ["特征值屈曲预测，" Abaqus Analysis User's Guide 第 6.2.3 节](../usb/usb-link.md#usb-anl-aeigenbuckling)

### **可选参数（互斥——如果未指定任何参数，Abaqus 假定缺陷数据将直接在数据行上输入）：**

FILE

将此参数设置为来自先前 Abaqus/Standard 分析的结果文件名，其中包含来自 [*BUCKLE](ch02abk16.md) 或 [*FREQUENCY](ch06abk35.md) 分析的振型，或来自 [*STATIC](ch18abk31.md) 分析的节点位移。

INPUT

将此参数设置为包含缺陷数据的备用输入文件的名称，通常以节点号和全局坐标系中的缺陷值的形式给出。请参阅 ["输入语法规则，" Abaqus Analysis User's Guide 第 1.2.1 节](../usb/usb-link.md#usb-int-iinputsyntax)，了解此类文件名的语法。

### **如果使用了 FILE 参数，则为必需参数：**

STEP

将此参数设置为要从其中读取模态或位移数据的步骤号（在其结果文件用作此选项输入的分析中）。

### **如果使用了 FILE 参数，则为可选参数：**

INC

将此参数设置为增量号（在其结果文件用作此选项输入的分析中），从中读取位移数据。如果省略此参数，Abaqus 将从结果文件上指定步骤的最后一个可用增量读取数据。

NSET

将此参数设置为要将几何缺陷值应用于其上的节点集。如果省略此参数，缺陷将应用于模型中的所有节点。

### **如果省略了 FILE 参数，则为可选参数：**

SYSTEM

设置 SYSTEM=R（默认）以将缺陷指定为 Cartesian 坐标的扰动值。设置 SYSTEM=C 以将缺陷指定为圆柱坐标的扰动值。设置 SYSTEM=S 以将缺陷指定为球坐标的扰动值。请参阅 [图 9.3-1](ch09abk03.md#kimperfection-imp)。

SYSTEM 参数完全局部于此选项，不应与 [*SYSTEM](ch18abk59.md) 选项混淆。当读取数据行时，指定的缺陷值将转换为全局矩形 Cartesian 坐标系。此转换要求对象以全局坐标系的原点为中心；即，当使用圆柱坐标或球坐标将缺陷指定为扰动值时，[*SYSTEM](ch18abk59.md) 选项应关闭。

### **将缺陷定义为结果文件中振型线性叠加的数据行：**

**第一行：**

根据需要重复此数据行，以将缺陷定义为振型的线性组合。

### **基于结果文件静态分析解的缺陷数据行：**

**第一（也是唯一）行：**

### **如果省略了 FILE 和 INPUT 参数，则定义缺陷的数据行：**

**第一行：**

根据需要重复此数据行以定义缺陷。

**图 9.3-1** 坐标系。

![](../graphics/kimperfection-nls.png)




