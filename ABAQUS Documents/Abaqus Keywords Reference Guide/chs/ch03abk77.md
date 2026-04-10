# *CORRELATION






### *CORRELATION定义随机响应载荷的互相关属性。

此选项用于定义作为随机载荷定义的一部分的互相关，用于 [*RANDOM RESPONSE](ch17abk07.md) 分析过程。[*PSD-DEFINITION](ch16abk32.md) 选项也需要给出要与互相关定义结合使用的频率函数。

**产品：**Abaqus/Standard  

**类型：**历史数据 

**级别：**步骤

##### **参考：**

- ["随机响应分析，" Abaqus 分析用户指南第 6.3.11 节](../usb/usb-link.md#usb-anl-arandomresponse)
- [*PSD-DEFINITION](ch16abk32.md)
- ["UCORR，" Abaqus 用户子程序参考指南第 1.1.22 节](../sub/sub-link.md#sub-rtn-uucorr)

### **TYPE=CORRELATED 和 TYPE=UNCORRELATED 的必需参数：**

PSD

将此参数设置为在 [*PSD-DEFINITION](ch16abk32.md) 选项上定义的频率函数名称，以与此互相关选项关联。

### **可选参数：**

COMPLEX

设置 COMPLEX=YES 以在互相关定义中包含实部和虚部。另一种选择是仅使用 COMPLEX=NO（默认）包含实部。

INPUT

将此参数设置为一个备用输入文件的名称，该文件包含此选项的数据行。请参阅 ["输入语法规则，" Abaqus 分析用户指南第 1.2.1 节](../usb/usb-link.md#usb-int-iinputsyntax)，了解此类文件名的语法。如果省略此参数，则假定数据跟随在关键字行之后。

TYPE

设置 TYPE=CORRELATED（默认）如果应包含互相关矩阵中的所有项。

设置 TYPE=UNCORRELATED 如果仅应使用对角项。

设置 TYPE=MOVING NOISE 用于移动噪声载荷。在这种情况下，步骤中只能使用一个 [*CORRELATION](ch03abk77.md) 选项。COMPLEX 参数不能与 TYPE=MOVING NOISE 结合使用。

USER

包含此参数以指示将调用用户子程序 [`UCORR`](../sub/sub-link.md#sub-xsl-ucorr) 获取互相关矩阵的缩放因子。如果包含此参数，则 TYPE 参数只能设置为 CORRELATED 或 UNCORRELATED。

### **TYPE=CORRELATED 或 TYPE=UNCORRELATED 的数据行：**

**第一行：**

根据需要重复此数据行以定义载荷工况及其关联的缩放因子。

### **包含 USER 参数时的数据行：**

**第一行：**

根据需要重复此数据行以定义要关联的载荷工况。

### **TYPE=MOVING NOISE 的数据行：**

**第一行：**

根据需要重复此数据行以定义随机载荷。




