# *PRESSURE STRESS







### *PRESSURE STRESS为质量扩散分析指定等效压力应力作为预定义场。

此选项只能用于[*MASS DIFFUSION](ch13abk06.md)分析中，以将压力指定为预定义场。用户在节点处定义等效压力应力，Abaqus/Standard将压力插值到材料点。

**产品：**Abaqus/Standard  

**类型：**历史数据  

**级别：**步骤  

##### **参考：**

- ["质量扩散分析，" Abaqus Analysis User's Guide第6.9.1节](../usb/usb-link.md#usb-anl-amassdiffusion)
- ["预定义场，" Abaqus Analysis User's Guide第34.6.1节](../usb/usb-link.md#usb-prc-pfields)

### **使用数据行格式的可选参数：**

AMPLITUDE

将此参数设置为给出整个步骤中压力时间变化的幅值曲线名称。如果省略AMPLITUDE参数，则参考幅值将在步骤开始时立即应用或线性应用于整个步骤，具体取决于[*STEP](ch18abk36.md)选项上分配给AMPLITUDE参数的值（参见["定义分析，" Abaqus Analysis User's Guide第6.1.2节](../usb/usb-link.md#usb-anl-aover)）。

INPUT

将此参数设置为包含此选项数据行的备用输入文件名称。请参阅["输入语法规则，" Abaqus Analysis User's Guide第1.2.1节](../usb/usb-link.md#usb-int-iinputsyntax)，了解此类文件名的语法。如果省略此参数，则假定数据跟在关键字行之后。

OP

设置OP=MOD（默认）以保留现有的[*PRESSURE STRESS](ch16abk28.md)值，此选项可修改现有值或定义额外值。

如果应移除所有现有的[*PRESSURE STRESS](ch16abk28.md)值，则设置OP=NEW。可以定义新的压力应力值。

对于一般分析步骤，通过OP=NEW移除的压力将重置为[*INITIAL CONDITIONS](ch09abk18.md)选项上给出的值，如果没有定义初始压力则重置为零。对于线性扰动步骤，通过OP=NEW移除的压力始终重置为零。如果压力正在返回其初始条件值，则上述AMPLITUDE参数不适用。而是[*STEP](ch18abk36.md)选项上给出的AMPLITUDE参数控制行为。如果通过OP=NEW将压力重置为新值（不是初始条件），则上述AMPLITUDE参数适用。

### **从结果文件读取等效压力应力的必需参数：**

FILE

将此参数设置为从中读取数据的结果文件名称（包括可选的`.fil`扩展名）。请参阅["输入语法规则，" Abaqus Analysis User's Guide第1.2.1节](../usb/usb-link.md#usb-int-iinputsyntax)，了解此类文件名的语法。

### **从结果文件读取等效压力应力的可选参数：**

BSTEP

将此参数设置为（其结果文件被用作此选项输入的分析）的步骤号，该步骤开始要读取的历史数据。如果没有提供值，Abaqus/Standard将从结果文件上可用的第一个步骤开始读取压力数据。

BINC

将此参数设置为（其结果文件被用作此选项输入的分析）的增量号，该增量开始要读取的历史数据。如果没有提供值，Abaqus/Standard将从结果文件上步骤BSTEP的第一个可用增量（不包括任何零增量）开始读取压力数据。

ESTEP

将此参数设置为（其结果文件被用作此选项输入的分析）的步骤号，该步骤结束要读取的历史数据。如果没有提供值，则ESTEP被视为等于BSTEP。

EINC

将此参数设置为（其结果文件被用作此选项输入的分析）的增量号，该增量结束要读取的历史数据。如果没有提供值，则EINC被视为结果文件上步骤ESTEP的最后一个可用增量。

### **在用户子程序[`UPRESS`](../sub/sub-link.md#sub-xsl-upress)中定义数据的必需参数：**

USER

包含此参数以指示将使用用户子程序[`UPRESS`](../sub/sub-link.md#sub-xsl-upress)来定义等效压力应力值。[`UPRESS`](../sub/sub-link.md#sub-xsl-upress)将为数据行上给出的每个节点调用。如果数据行上也给出了值，这些值将被忽略。如果除了用户子程序[`UPRESS`](../sub/sub-link.md#sub-xsl-upress)外还指定了结果文件，则从结果文件读取的值将被传递到[`UPRESS`](../sub/sub-link.md#sub-xsl-upress)中进行可能的修改。

### **使用数据行格式定义压力的数据行：**

**第一行：**

根据需要重复此行以定义不同节点或节点集处的压力。

### **从Abaqus/Standard结果文件读取压力（FILE）：**

当从结果文件读取压力数据时，不使用数据行。

### **使用用户子程序[`UPRESS`](../sub/sub-link.md#sub-xsl-upress)定义等效压力应力的数据行：**

**第一行：**

根据需要重复此行。[`UPRESS`](../sub/sub-link.md#sub-xsl-upress)将为列出的每个节点调用。
