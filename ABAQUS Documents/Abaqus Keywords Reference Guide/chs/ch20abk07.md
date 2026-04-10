# *USER ELEMENT





### *USER ELEMENT引入用户定义的元素类型。

此选项用于引入线性或通用用户定义元素。它必须先于[*ELEMENT](ch05abk07.md)选项上对此用户元素的任何引用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**部件、部件实例、模型

**Abaqus/CAE：**执行器/传感器相互作用可以在Interaction模块中定义。

##### **参考：**

- ["用户定义元素," Section 32.15.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-euserelem)
- ["UEL," Section 1.1.28 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uuel)
- ["VUEL," Section 1.2.12 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uexpuel)
- [*ELEMENT](ch05abk07.md)
- [*MATRIX](ch13abk09.md)
- [*UEL PROPERTY](ch20abk01.md)

### 引入线性用户定义元素（仅限Abaqus/Standard）

### **必需参数：**

TYPE

将此参数设置为用于在[*ELEMENT](ch05abk07.md)选项上识别此元素的元素类型键。在Abaqus/Standard中，此类型键的格式必须为U*n*，其中*n*是小于10000的正整数。要使用此元素类型，请在[*ELEMENT](ch05abk07.md)选项上设置TYPE=U*n*。

### **可选参数：**

FILE

将此参数设置为其读取数据的结果文件（无扩展名）的名称。请参见["输入语法规则," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax)，了解此类文件名的语法。

此参数仅在用户定义的元素类型是线性的且其刚度和/或质量矩阵将从先前分析（在先前分析中通过[*ELEMENT MATRIX OUTPUT](ch05abk08.md)或[*SUBSTRUCTURE MATRIX OUTPUT](ch18abk44.md)选项写入）的Abaqus/Standard结果文件读取时才能使用。当使用此参数时，所有值都从结果文件获取。例如，如果从结果文件读取的刚度或质量不是对称的，则UNSYMM参数将自动被调用。

如果省略此参数，则数据将从标准输入文件读取。

INTEGRATION

此参数仅适用于Abaqus/Standard分析。

将此参数设置为要在高斯积分中使用的积分点数量。此参数必须与TENSOR参数一起使用。

TENSOR

此参数仅适用于Abaqus/Standard分析。

包含此参数以指定元素类型。此参数必须与INTEGRATION参数一起使用。

设置TENSOR=THREED以指定它是应力/位移或热传递分析中的三维元素。

设置TENSOR=TWOD以指定它是热传递分析中的二维元素。

设置TENSOR=PSTRAIN以指定它是应力/位移分析中的平面应变元素。

设置TENSOR=PSTRESS以指定它是应力/位移分析中的平面应力元素。

### **如果包含FILE参数，则为必需参数：**

OLD ELEMENT

将此参数设置为正在读取其矩阵的元素被分配的元素编号。此参数也可以设置为子结构标识符，以从Abaqus/Standard结果文件读取子结构矩阵。

STEP

将此参数设置为写入元素矩阵的步号。如果使用在生成期间输出矩阵的子结构，则不需要此参数。

INCREMENT

将此参数设置为写入元素矩阵的增量号。如果使用在生成期间输出矩阵的子结构，则不需要此参数。

### **如果省略FILE参数，则为必需参数：**

LINEAR

包含此参数以指示元素类型的行为是线性的，由刚度矩阵和/或质量矩阵定义。[*MATRIX](ch13abk09.md)选项是定义元素行为所必需的。

NODES

将此参数设置为与此类型元素关联的节点数。

### **如果省略FILE参数，则为可选参数：**

COORDINATES

Abaqus/Standard在用户子程序[`UEL`](../sub/sub-link.md#sub-xsl-uel)中分配空间以存储每个节点处的坐标值。默认坐标值数量等于用户元素的最大活动自由度，最大为3。使用COORDINATES参数增加坐标值的数量。

UNSYMM

如果元素矩阵不是对称的，则包含此参数。此参数将导致Abaqus/Standard使用其非对称方程求解功能。

此参数的存在或不存在决定了必须提供矩阵以供读取的形式。

### **如果省略FILE参数，则为数据行：**

**第一行：**

**如果后续节点的活动自由度不同，则为第二行：**

根据需要重复第二数据行。

### 引入通用用户定义元素

### **必需参数：**

TYPE

将此参数设置为用于在[*ELEMENT](ch05abk07.md)选项上识别此元素的元素类型键。在Abaqus/Standard中此类型键的格式必须为U*n*，在Abaqus/Explicit中必须为VU*n*，其中*n*是小于10000的正整数。要使用此元素类型，请在[*ELEMENT](ch05abk07.md)选项上设置TYPE=U*n*（或VU*n*）。

NODES

将此参数设置为与此类型元素关联的节点数。

### **可选参数：**

COORDINATES

将此参数设置为在Abaqus/Standard的用户子程序[`UEL`](../sub/sub-link.md#sub-xsl-uel)和Abaqus/Explicit的用户子程序[`VUEL`](../sub/sub-link.md#sub-xsl-vuel)中元素任何节点点所需的最大坐标数。Abaqus分配空间以存储与此类型元素关联的所有节点处的坐标值。默认值为COORDINATES=1。

Abaqus将更改COORDINATES的值为您指定的COORDINATES参数值或用户元素的最大活动自由度值（小于或等于3）中的最大值。例如，如果COORDINATES=1且用户元素的自由度为2、3和6，则COORDINATES的值将更改为3。如果COORDINATES=2且用户元素的自由度为11和12，则COORDINATES的值将保持为2。

I PROPERTIES

将此参数设置为在用户子程序[`UEL`](../sub/sub-link.md#sub-xsl-uel)（或[`VUEL`](../sub/sub-link.md#sub-xsl-vuel)）中定义此类元素所需的数据的整数属性值数量。默认值为I PROPERTIES=0。

PROPERTIES

将此参数设置为在用户子程序[`UEL`](../sub/sub-link.md#sub-xsl-uel)（或[`VUEL`](../sub/sub-link.md#sub-xsl-vuel)）中定义此类元素所需的数据的实数（浮点）属性值数量。默认值为PROPERTIES=0。

UNSYMM

此参数仅适用于Abaqus/Standard分析。

如果元素矩阵不是对称的，则包含此参数。此参数将导致Abaqus/Standard使用其非对称方程求解功能。

VARIABLES

将此参数设置为必须存储在元素内的解相关状态变量数。其值必须大于0。默认值为VARIABLES=1。

### **定义通用用户定义元素的数据行：**

**第一行：**

**如果后续节点的活动自由度不同，则为第二行：**

根据需要重复第二数据行。





