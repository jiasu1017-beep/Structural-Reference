# *FIELD









### *FIELD指定预定义场变量值。

此选项用于指定分析中使用的预定义场变量的值。要在Abaqus/Standard的重启动分析中使用此选项，必须在原始分析中指定[*FIELD](ch06abk07.md)或[*INITIAL CONDITIONS](ch09abk18.md)，TYPE=FIELD。

**产品：**Abaqus/Standard  Abaqus/Explicit

**类型：**历史数据

**级别：**步骤

##### **参考：**

- ["预定义场，" Abaqus分析用户指南第34.6.1节](../usb/usb-link.md#usb-prc-pfields)
- ["UFIELD，" Abaqus用户子程序参考指南第1.1.32节](../sub/sub-link.md#sub-rtn-uufield)
- ["VUFIELD，" Abaqus用户子程序参考指南第1.2.14节](../sub/sub-link.md#sub-rtn-uexpfield)

### **可选参数：**

VARIABLE

将此参数设置为场变量编号。用户必须从1开始连续编号。默认值为VARIABLE=1，除非使用NUMBER参数。VARIABLE和NUMBER参数是互斥的。

### **使用数据行格式的可选参数：**

AMPLITUDE

将此参数设置为幅值曲线名称，该曲线给出整个步骤中场变量的时间变化（请参见["幅值曲线，" Abaqus分析用户指南第34.1.2节](../usb/usb-link.md#usb-prc-pamplitude)）。

如果在Abaqus/Standard分析中省略此参数，则参考幅值在步骤开始时立即应用或在线性范围内应用，取决于[*STEP](ch18abk36.md)选项上AMPLITUDE参数的值。如果在Abaqus/Explicit分析中省略此参数，则参考幅值在线性范围内应用。

INPUT

将此参数设置为包含此选项数据行的备用输入文件名称。请参见["输入语法规则，" Abaqus分析用户指南第1.2.1节](../usb/usb-link.md#usb-int-iinputsyntax)，获取此类文件名的语法。如果省略此参数，则假定数据跟随在关键字行之后。

OP

设置 OP=MOD（默认），现有[*FIELD](ch06abk07.md)变量值保持不变，此选项修改现有值或定义额外值。

如果应删除所有现有的[*FIELD](ch06abk07.md)变量值，则设置 OP=NEW。可以定义新的场变量值。

对于一般分析步骤，通过OP=NEW删除的场变量将重置为[*INITIAL CONDITIONS](ch09abk18.md)选项上给定的值；如果未定义初始场，则重置为零。对于线性扰动步骤，通过OP=NEW删除的场变量始终重置为零。如果场变量正在返回其初始条件值，则上述AMPLITUDE参数不适用。相反，[*STEP](ch18abk36.md)选项上给出的AMPLITUDE参数控制在Abaqus/Standard分析中的行为。默认是将场变量线性斜坡回其初始条件。在Abaqus/Explicit分析中，场变量始终线性斜坡回其初始条件。如果场变量通过OP=NEW重置为新值（不是其初始条件），则适用上述AMPLITUDE参数。

### **从结果或输出数据库文件读取预定义场变量值的必需参数：**

FILE

将此参数设置为读取数据的结果（`.fil`）或输出数据库（`.odb`）文件名称。文件扩展名是可选的；但是，如果`.fil`和`.odb`文件都存在，且省略了INTERPOLATE参数，则将使用结果文件。如果使用了INTERPOLATE参数，则必须存在输出数据库文件。请参见["输入语法规则，" Abaqus分析用户指南第1.2.1节](../usb/usb-link.md#usb-int-iinputsyntax)，获取此类文件名的语法。

此参数不能在[*STATIC](ch18abk31.md)，RIKS分析步骤中使用。

### **从结果或输出数据库文件读取预定义场变量值的可选参数：**

BSTEP

将此参数设置为步骤编号（其结果文件被用作此选项输入的分析），开始读取历史数据。如果未提供值，Abaqus将从读取文件上可用的第一步开始读取场变量数据。

BINC

将此参数设置为增量编号（其结果或输出数据库文件被用作此选项输入的分析），开始读取历史数据。如果未提供值，Abaqus将从结果或输出数据库文件上步骤BSTEP的第一个可用增量开始读取场变量数据（如果结果文件是在Abaqus/Standard中使用[*FILE FORMAT](ch06abk08.md)，ZERO INCREMENT写入的，则排除任何零增量）。

ESTEP

将此参数设置为步骤编号（其结果或输出数据库文件被用作此选项输入的分析），结束读取历史数据。如果未提供值，则ESTEP等于BSTEP。

EINC

将此参数设置为增量编号（其结果或输出数据库文件被用作此选项输入的分析），结束读取历史数据。如果未提供值，则EINC为结果文件上步骤ESTEP的最后一个可用增量。

### **从输出数据库文件读取预定义场变量值的必需参数：**

OUTPUT VARIABLE

将此变量设置为标量节点输出变量，该变量将从输出数据库读取并用于初始化指定的预定义场。有关可用于初始化预定义场的标量节点输出变量列表，请参见["预定义场，" Abaqus分析用户指南第34.6.1节](../usb/usb-link.md#usb-prc-pfields)。

### **从输出数据库文件读取预定义场变量值的可选参数：**

INTERPOLATE

包含此参数以指示需要被读入预定义场的标量节点输出变量（由OUTPUT VARIABLE参数指定）需要在不同网格之间进行插值。此功能用于从先前Abaqus分析期间生成的结果数据库文件读取节点值。

### **在用户子程序[`UFIELD`](../sub/sub-link.md#sub-xsl-ufield)或[`VUFIELD`](../sub/sub-link.md#sub-xsl-vufield)中定义数据的必需参数：**

USER

包含此参数以指示将使用用户子程序[`UFIELD`](../sub/sub-link.md#sub-xsl-ufield)或[`VUFIELD`](../sub/sub-link.md#sub-xsl-vufield)来定义场变量值。对于Abaqus/Standard分析，将为数据行上给出的每个节点调用[`UFIELD`](../sub/sub-link.md#sub-xsl-ufield)。对于Abaqus/Explicit分析，将为每个场变量调用[`VUFIELD`](../sub/sub-link.md#sub-xsl-vufield)，或者在使用NUMBER参数时为一组场变量调用。

如果数据行上也给出了值，这些值将被忽略。如果除了用户子程序外还指定了结果文件，则从结果文件读取的值将被传递到用户子程序中进行可能的修改。

### **在用户子程序[`UFIELD`](../sub/sub-link.md#sub-xsl-ufield)或[`VUFIELD`](../sub/sub-link.md#sub-xsl-vufield)中定义数据的可选参数：**

NUMBER

此参数允许在用户子程序[`UFIELD`](../sub/sub-link.md#sub-xsl-ufield)或[`VUFIELD`](../sub/sub-link.md#sub-xsl-vufield)中同时更新多个（可能是所有）场变量；例如，因为它们是相互依赖的。将此参数设置为一个点上要同时更新的场变量数。NUMBER和VARIABLE参数是互斥的。

BLOCKING

此参数仅适用于Abaqus/Explicit分析。它与用户子程序参数列表中使用的`NBLOCK`变量相关。

设置 BLOCKING=YES 以启用对给定节点集的阻塞。阻塞大小将在Abaqus/Explicit中设置为预定义值。

设置 BLOCKING=NO（默认）以禁用阻塞。

使用 BLOCKING=*n* 指定阻塞大小。

### **在梁和壳中定义预定义场变量梯度的数据行：**

**第一行：**

根据需要重复此数据行，以在不同节点或节点集上定义场变量。

### **在梁和壳中定义温度点处预定义场变量的数据行：**

**第一行：**

**后续行（仅当单元中有超过七个温度点时需要）：**

根据需要重复此组数据行，以在不同节点或节点集上定义场变量。

### **使用数据行格式为实体单元定义预定义场变量的数据行：**

**第一行：**

根据需要重复此数据行，以在不同节点或节点集上定义场变量。

### **从Abaqus/Standard结果或输出数据库文件读取场变量值：**

当从结果或输出数据库文件读取场变量数据时，不使用数据行。

### **使用用户子程序[`UFIELD`](../sub/sub-link.md#sub-xsl-ufield)或[`VUFIELD`](../sub/sub-link.md#sub-xsl-vufield)定义场变量的数据行：**

**第一行：**

根据需要重复此数据行。




