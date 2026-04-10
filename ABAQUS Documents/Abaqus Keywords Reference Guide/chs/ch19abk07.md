# *TIME POINTS





### *TIME POINTS指定要将数据写入输出数据库文件的时间点，或在直接循环分析中指定评估结构响应的时间点。

此选项用于指定要将数据写入输出数据库文件的时间点，或者如果与[*DIRECT CYCLIC](ch04abk24.md)选项结合使用，则用于指定加载历史中将要评估结构响应的时间点。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Step模块

##### **参考：**

- [*DIRECT CYCLIC](ch04abk24.md)
- [*OUTPUT](ch15abk03.md)

### **必需参数：**

NAME

将此参数设置为一个标签，用于引用时间点。

### **可选参数：**

GENERATE

如果包含此参数，每行数据应给出起始时间点，![](../graphics/key_eqn00153.gif)；结束时间点，![](../graphics/key_eqn01104.gif)；以及这两个指定时间点之间的时间增量，![](../graphics/key_eqn01105.gif)。

INPUT

将此参数设置为包含此选项数据行的备用输入文件名称。有关此类文件名的语法，请参见["输入语法规则," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax)。如果省略此参数，则假定数据跟随在关键字行之后。

### **如果省略GENERATE参数的数据行：**

**第一行：**

根据需要重复此数据行。每行最多允许八个条目。如果您将[*TIME POINTS](ch19abk07.md)选项与[*DIRECT CYCLIC](ch04abk24.md)选项结合使用，则列出时间点必须包括单个加载循环中的起始时间和结束时间。时间点必须以步时间指定。

### **如果包含GENERATE参数的数据行：**

**第一行：**

根据需要重复此数据行。如果您将[*TIME POINTS](ch19abk07.md)选项与[*DIRECT CYCLIC](ch04abk24.md)选项结合使用，则列出时间点必须包括单个加载循环中的起始时间和结束时间。时间点必须以步时间指定。





