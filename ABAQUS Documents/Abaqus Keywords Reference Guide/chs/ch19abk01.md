# *TEMPERATURE





### *TEMPERATURE指定温度作为预定义场。

此选项用于在分析期间将温度指定为预定义场。

要在Abaqus/Standard的重新启动分析中使用此选项，原始分析中必须已指定[*TEMPERATURE](ch19abk01.md)或[*INITIAL CONDITIONS](ch09abk18.md)、TYPE=TEMPERATURE。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**历史数据

**级别：**步

**Abaqus/CAE：**Load模块

##### **参考：**

- ["预定义场," Section 34.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pfields)
- ["UTEMP," Section 1.1.51 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uutemp)

### **使用数据行格式的可选参数：**

AMPLITUDE

将此参数设置为给出整个步中温度随时间变化的幅度曲线名称（参见["幅度曲线," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude))。

如果在Abaqus/Standard分析中省略此参数，则根据[*STEP](ch18abk36.md)选项上的AMPLITUDE参数分配的值，参考幅值将在步开始时立即应用或在整个步中线性应用（参见["定义分析," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)）。如果在Abaqus/Explicit分析中省略此参数，则在步中执行线性插值。

INPUT

将此参数设置为包含此选项数据行的备用输入文件名称。有关此类文件名的语法，请参见["输入语法规则," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax)。如果省略此参数，则假定数据跟随在关键字行之后。

OP

设置OP=MOD（默认）以保留现有的[*TEMPERATURE](ch19abk01.md)值，并由此选项修改现有温度或定义额外温度。

设置OP=NEW以删除所有现有的[*TEMPERATURE](ch19abk01.md)值。可以定义新温度。

对于一般分析步，通过OP=NEW删除的温度将重置为[*INITIAL CONDITIONS](ch09abk18.md)选项上给定的值，如果未定义初始温度则重置为零。对于线性扰动步，通过OP=NEW删除的温度始终重置为零。如果温度正在返回到其初始条件值，则上述AMPLITUDE参数不适用。相反，在Abaqus/Standard分析中，由[*STEP](ch18abk36.md)选项给出的AMPLITUDE参数控制行为，在Abaqus/Explicit分析中，温度始终斜坡回到其初始条件。如果通过OP=NEW将温度重置为新值（不是初始条件），则适用上述AMPLITUDE参数。

### **从结果或输出数据库文件读取温度的必需参数：**

FILE

将此参数设置为其读取数据的結果或输出数据库文件的名称。文件扩展名是可选的；但是，如果`.fil`和`.odb`文件都存在，且省略了INTERPOLATE参数，则将使用结果文件。如果使用了INTERPOLATE参数，则必须存在输出数据库文件。请参见["输入语法规则," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax)，了解此类文件名的语法。此参数不能用于[*STATIC](ch18abk31.md)、RIKS分析步。

### **从结果或输出数据库文件读取温度的可选参数：**

ABSOLUTE EXTERIOR TOLERANCE

此参数仅与INTERPOLATE参数一起使用时才相关。将此参数设置为当前模型的节点可能位于FILE参数指定的输出数据库模型区域之外的绝对值（以模型使用的单位给出）。如果未使用此参数或其值为0.0，则将应用EXTERIOR TOLERANCE参数。

EXTERIOR TOLERANCE

此参数仅与INTERPOLATE参数一起使用时才相关。将此参数设置为平均元素尺寸的分数，当前模型的节点可能位于FILE参数指定的输出数据库中模型元素的区域之外。默认值为0.05。

如果指定了两个容差参数，Abaqus使用更严格的容差。

BSTEP

将此参数设置为（其结果或输出数据库文件用作此选项输入的分析的）步号，该步开始要读取的历史数据。如果未提供值，Abaqus将从文件上可用的第一步开始读取温度数据。

BINC

将此参数设置为（其结果或输出数据库文件用作此选项输入的分析的）增量号，该增量开始要读取的历史数据。如果未提供值，Abaqus将从文件上BSTEP的第一步可用的第一个增量开始读取温度数据（不包括使用[*FILE FORMAT](ch06abk08.md)、ZERO INCREMENT在Abaqus/Standard中写入的结果文件中的任何零增量）。

ESTEP

将此参数设置为（其结果或输出数据库文件用作此选项输入的分析的）步号，该步结束要读取的历史数据。如果未提供值，则ESTEP等于BSTEP。

EINC

将此参数设置为（其结果或输出数据库文件用作此选项输入的分析的）增量号，该增量结束要读取的历史数据。如果未提供值，则EINC取自文件上ESTEP步的最后一个可用增量。

BTRAMP

将此参数设置为起始时间（相对于总步长时间测量），之后从结果文件读取的温度将斜坡回到其初始条件值。默认值为![](../graphics/key_eqn00237.gif)，在这种情况下不会发生温度斜坡。此功能用于从先前非循环的热传递分析创建循环温度历史。

DRIVING ELSETS

此参数仅与INTERPOLATE参数一起使用时才相关。包含此参数以指示温度场从先前分析的用户指定元素集插值到当前作业中的用户指定节点集。此参数用于消除先前分析中元素区域接近或接触时的映射歧义。要完成部件实例到部件实例的映射，请将您的元素集和节点集定义为对应于先前分析和当前分析中的相应实例。

INTERPOLATE

包含此参数以指示需要在不同网格之间插值温度场。此功能用于从热传递分析期间生成的结果或输出数据库文件读取温度，或从与子建模功能一起使用的全局模型分析生成的结果或输出数据库文件读取温度。此参数与MIDSIDE参数互斥。如果热传递分析使用一阶元素而当前网格相同但使用二阶元素，请改用MIDSIDE参数。

MIDSIDE

包含此参数以指示将从角节点温度插值二阶元素中的中节点温度。此功能用于从使用一阶元素的热传递分析生成的结果或输出数据库文件读取温度。此参数与INTERPOLATE参数互斥。

### **在用户子程序[`UTEMP`](../sub/sub-link.md#sub-xsl-utemp)中定义数据的必需参数：**

USER

此参数仅适用于Abaqus/Standard分析。

包含此参数以指示将使用用户子程序[`UTEMP`](../sub/sub-link.md#sub-xsl-utemp)定义温度值。[`UTEMP`](../sub/sub-link.md#sub-xsl-utemp)将为数据行上给出的每个节点调用。

如果数据行上也给出了值，这些值将被忽略。如果除了用户子程序[`UTEMP`](../sub/sub-link.md#sub-xsl-utemp)外还指定了结果或输出数据库文件，则从该文件读取的值将被传递到[`UTEMP`](../sub/sub-link.md#sub-xsl-utemp)中以进行可能的修改。

### **定义梁和壳中温度梯度的数据行：**

**第一行：**

根据需要重复此数据行，以定义不同节点或节点集处的温度。

### **定义梁和壳中温度点处温度的数据行：**

**第一行：**

**后续行（仅在元素中有超过七个温度点时需要）：**

如果任何节点需要超过七个温度值，请继续下一行。如果模型中任何其他节点具有超过七个温度点，则可能需要为某些节点留下空白数据行，因为Abaqus期望为任何节点读取的温度总数基于模型中所有节点的最大温度值数量。这些尾部初始值为零，将不会在分析中使用。

根据需要重复此组数据行，以定义不同节点或节点集处的温度。

### **使用数据行格式定义实体或框架元素温度的数据行：**

**第一行：**

根据需要重复此数据行，以在不同节点或节点集处指定温度。

### **如果从Abaqus结果或输出数据库文件读取温度（除了存在DRIVING ELSETS参数时）且未使用用户子程序（包含FILE参数，省略USER参数），则不需要数据行。**

### **使用数据行格式使用用户子程序[`UTEMP`](../sub/sub-link.md#sub-xsl-utemp)定义温度的数据行（省略FILE参数，包含USER参数）：**

**第一行：**

根据需要重复此数据行。[`UTEMP`](../sub/sub-link.md#sub-xsl-utemp)将为列出的每个节点调用。

### **当从Abaqus结果或输出数据库文件读取温度时，使用用户子程序[`UTEMP`](../sub/sub-link.md#sub-xsl-utemp)定义温度的数据行（包含FILE和USER参数）：**

**第一行：**

根据需要重复此数据行。数据行上识别的节点将被分配来自结果或输出数据库文件的值；可选地，这些值可以在用户子程序[`UTEMP`](../sub/sub-link.md#sub-xsl-utemp)中修改。

### **当包含FILE、INTERPOLATE和DRIVING ELSETS参数时定义温度的数据行：**

**第一行：**

根据需要重复此数据行。数据行上识别的节点集将被分配来自结果（`.fil`）或输出数据库（`.odb`）文件中元素集的值。如果在后续数据行上定义了重复节点，则该节点将从后续温度映射中移除并打印到数据（`.dat`）文件中。





