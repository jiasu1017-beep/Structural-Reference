# *PARAMETER SHAPE VARIATION









### *PARAMETER SHAPE VARIATION定义参数化形状变化。

此选项用于定义参数化形状变化。

**产品：**Abaqus/Standard  Abaqus/Explicit  

**类型：**模型数据  

**级别：**部件、部件实例  

##### **参考：**

- ["参数化形状变化，" Abaqus Analysis User's Guide第2.1.2节](../usb/usb-link.md#usb-int-iparshapevar)
- ["设计灵敏度分析，" Abaqus Analysis User's Guide第19.1.1节](../usb/usb-link.md#usb-anl-adsa)

### **必需参数：**

PARAMETER

将此关键字参数设置为形状变化数据引用的参数名称。如果此参数也是设计参数，则形状变化用于定义节点坐标的设计灵敏度分析设计梯度。

### **可选参数（互斥——如果未指定参数，Abaqus假定形状变化数据将直接在数据行上输入）：**

FILE

将此参数设置为包含来自先前Abaqus/Standard分析结果的 结果文件名，该文件包含来自[*BUCKLE](ch02abk16.md)或[*FREQUENCY](ch06abk35.md)分析的模式形状或来自[*STATIC](ch18abk31.md)分析的节点位移。此选项不能用于基于部件实例装配定义的模型。

INPUT

将此参数设置为包含形状变化数据的备用输入文件名称。

### **如果使用FILE参数，则需要以下参数：**

STEP

将此参数设置为要从其中读取模式或位移数据的步骤号。

### **如果使用FILE参数，则以下是可选参数：**

INC

将此参数设置为要从其中读取位移数据的增量号。如果省略此参数，Abaqus将从结果文件中指定步骤的最后一个可用增量读取数据。

MODE

将此参数设置为此选项输入的结果文件中要从中读取模式数据的模式号。如果省略此参数，Abaqus将从结果文件中指定步骤的第一个可用模式读取数据。

NSET

将此参数设置为其上要应用形状变化值的节点集。如果省略此参数，形状变化将应用于模型中的所有节点。

### **如果省略FILE参数：**

SYSTEM

设置SYSTEM=R（默认）以将形状变化指定为笛卡尔坐标值。设置SYSTEM=C以将形状变化指定为圆柱坐标值。设置SYSTEM=S以将形状变化指定为球坐标值。

### **如果省略FILE和INPUT参数，则定义形状变化的数据行：**

**第一行：**

根据需要重复此数据行以定义形状变化。此数据行上给出的数据不能被参数化。

**图16.3-1** 坐标系。

![](../graphics/kimperfection-nls.png)