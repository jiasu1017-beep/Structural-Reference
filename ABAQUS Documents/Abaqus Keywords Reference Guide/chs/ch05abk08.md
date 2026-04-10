# *ELEMENT MATRIX OUTPUT









### *ELEMENT MATRIX OUTPUT将单元刚度矩阵和质量矩阵写入文件。

此选项用于将单元刚度矩阵以及可用的质量矩阵写入结果文件、用户定义的文件或数据文件。

**产品：**Abaqus/Standard

**类型：**历史数据

**级别：**步骤

##### **参考：**

- ["输出，" Abaqus分析用户指南第4.1.1节](../usb/usb-link.md#usb-out-ooutput)

### **必需参数：**

ELSET

将此参数设置为正在为其发出输出请求的单元集名称。

### **可选参数：**

DLOAD

设置 DLOAD=YES 以写入来自分布在单元上的载荷的载荷向量。默认值为 DLOAD=NO。

FILE NAME

此参数只能与参数 OUTPUT FILE=USER DEFINED 一起使用。它用于指定将写入数据的文件名称（不带扩展名）。扩展名`.mtx`将被添加到用户提供的文件名；请参见["输入语法规则，" Abaqus分析用户指南第1.2.1节](../usb/usb-link.md#usb-int-iinputsyntax)，获取此类文件名的语法。如果在指定 OUTPUT FILE=USER DEFINED 时未包含此参数，则输出将被写入数据文件。

FREQUENCY

将此参数设置为输出频率（以增量计）。除非 FREQUENCY=0，否则输出将始终在每个步骤的最后增量写入。默认值为 FREQUENCY=1。设置 FREQUENCY=0 以抑制输出。

MASS

设置 MASS=YES 以写入质量矩阵。默认值为 MASS=NO。

OUTPUT FILE

设置 OUTPUT FILE=RESULTS FILE（默认）以将数据写入常规结果文件，格式参见["结果文件输出格式，" Abaqus分析用户指南第5.1.2节](../usb/usb-link.md#usb-out-fformat)。

设置 OUTPUT FILE=USER DEFINED 以将结果写入用户指定的文件，格式为[*USER ELEMENT](ch20abk07.md)，LINEAR选项（["用户定义单元，" Abaqus分析用户指南第32.15.1节](../usb/usb-link.md#usb-elm-euserelem)）。文件名使用 FILE NAME 参数指定。

STIFFNESS

设置 STIFFNESS=YES 以写入刚度矩阵（或传热单元的算子矩阵）。默认值为 STIFFNESS=NO。

**此选项没有关联的数据行。**



