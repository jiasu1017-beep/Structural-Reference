# *FILTER









### *FILTER定义用于输出过滤和/或操作的滤波器和/或算子。

此选项定义一个数字滤波器和/或算子，与[*OUTPUT](ch15abk03.md)选项结合使用。它可用于在分析进行时对输出进行预过滤和/或操作。

**产品：**Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**过滤器工具集

##### **参考：**

- ["输出到输出数据库，" Abaqus分析用户指南第4.1.3节](../usb/usb-link.md#usb-out-odboutput)
- [*OUTPUT](ch15abk03.md)

### **必需参数：**

NAME

将此参数设置为一个标签，用于引用此滤波器和/或算子。

### **可选参数：**

HALT

如果希望在达到使用LIMIT参数指定的值时停止分析，则包含此参数。

此参数必须与LIMIT参数结合使用。

INVARIANT

此参数只能与OPERATOR参数结合使用，以指示您希望对单元或节点输出场变量的不变量进行过滤和/或操作。

设置 INVARIANT=FIRST 以将过滤应用于第一不变量。

设置 INVARIANT=SECOND 以将过滤应用于第二不变量。

设置 INVARIANT=MAXP 以将过滤应用于最大主应力。

设置 INVARIANT=INTERMP 以将过滤应用于中间主应力。

设置 INVARIANT=MINP 以将过滤应用于最小主应力。

有关更多信息，请参见["输出到输出数据库，" Abaqus分析用户指南第4.1.3节](../usb/usb-link.md#usb-out-odboutput)。

LIMIT

如果希望为输出变量设置限制（上限值），则包含此参数。

此参数必须与OPERATOR参数结合使用。

OPERATOR

此参数可以与TYPE参数一起使用或不使用。当与过滤器类型一起使用时，它将对过滤后的数据进行操作；当不使用过滤器类型使用时，它将对原始（未过滤）数据进行操作。

如果希望获取使用此滤波器的变量的最大值，请设置 OPERATOR=MAX。您可以使用LIMIT参数为最大值设置上限值。

如果希望获取使用此滤波器的变量的最小值，请设置 OPERATOR=MIN。您可以使用LIMIT参数为最小值设置上限值。

如果希望获取使用此滤波器的变量的绝对最大值，请设置 OPERATOR=ABSMAX。您可以使用LIMIT参数为该值设置上限值。

START CONDITION

此参数必须与TYPE参数一起使用。

设置 START CONDITION=DC（默认）以使用等于第一个原始数据值的常数值对滤波器进行预充电。

设置 START CONDITION=USER DEFINED 以使用等于用户定义值的常数值对滤波器进行预充电。

TYPE

设置 TYPE=BUTTERWORTH（当省略OPERATOR时的默认值）以定义Butterworth滤波器。

设置 TYPE=CHEBYS1 以定义I型Chebyshev滤波器。

设置 TYPE=CHEBYS2 以定义II型Chebyshev滤波器。

### **定义Butterworth滤波器的数据行：**

**第一行：**

**第二行（仅在START CONDITION=USER DEFINED时需要）：**

### **定义I型Chebyshev滤波器的数据行：**

**第一行：**

**第二行（仅在START CONDITION=USER DEFINED时需要）：**

### **定义II型Chebyshev滤波器的数据行：**

**第一行：**

**第二行（仅在START CONDITION=USER DEFINED时需要）：**




