# *PREPRINT







### *PREPRINT选择分析输入文件处理器的打印输出。

此选项用于选择将从分析输入文件处理器获得的打印输出。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**作业模块

##### **参考：**

- ["输出，" Abaqus Analysis User's Guide第4.1.1节](../usb/usb-link.md#usb-out-ooutput)

### **可选参数：**

CONTACT

此参数仅适用于Abaqus/Standard分析。

设置CONTACT=YES以打印由接触对定义数据生成的接触约束的详细信息。设置CONTACT=NO（默认）以抑制此打印输出。

ECHO

设置ECHO=YES以打印输入数据的回显。设置ECHO=NO（默认）以抑制此打印输出。

HISTORY

设置HISTORY=YES以打印历史数据。设置HISTORY=NO（默认）以抑制此打印输出。

MODEL

设置MODEL=YES以打印模型定义数据。设置MODEL=NO（默认）以抑制此打印输出。

在Abaqus/Explicit中，设置MODEL=YES会自动设置MASS PROPERTY=YES。

PARSUBSTITUTION

设置PARSUBSTITUTION=YES以打印原始输入文件的修改版本，该版本不含输入模型参数化。设置PARSUBSTITUTION=NO（默认）以抑制此打印输出。

PARVALUES

设置PARVALUES=YES以打印原始输入文件的修改版本，显示用于模型参数化的参数及其值。设置PARVALUES=NO（默认）以抑制此打印输出。

MASS PROPERTY

此参数仅适用于Abaqus/Explicit分析。

设置MASS PROPERTY=YES以打印质量属性表，其中包括每个用户定义元素集的原始质量、初始质量缩放、非结构质量、质心和转动惯量。设置MASS PROPERTY=NO（默认）以抑制此打印输出。

如果MODEL=YES，即使MASS PROPERTY=NO，也会打印质量属性表。

**此选项没有关联的数据行。**
