# *DEPVAR





### *DEPVAR指定解相关状态变量。

此选项用于在每个积分点为解相关状态变量分配空间。如果使用了 [*DEPVAR](ch04abk14.md) 选项，它必须出现在需要解相关状态变量的 [*MATERIAL](ch13abk08.md) 定义内。

此外，可以为由此选项分配的部分或全部解相关状态变量给出输出键和描述。如果使用 [*ELEMENT OUTPUT](ch05abk10.md) 选项请求解相关状态变量的场或历史输出，则为其在此选项下指定了键的解相关状态变量的输出标识符将由字符串"SDV_"后跟指定的键组成。类似地，此选项下指定的描述将用于写入输出数据库的相应场描述。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["用户子程序：概述，" Abaqus分析用户指南第18.1.1节](../usb/usb-link.md#usb-anl-asubroutineover)
- ["用户定义的机械材料行为，" Abaqus分析用户指南第26.7.1节](../usb/usb-link.md#usb-mat-cusermat)
- ["有限元到SPH粒子的转换，" Abaqus分析用户指南第15.2.2节](../usb/usb-link.md#usb-anl-asphconversion)

### **可选、互斥参数：**

CONVERT

此参数仅适用于允许连续有限单元转换为SPH粒子的Abaqus/Explicit分析。

将此参数设置为此选项控制单元转换标志的状态变量编号（请参见["有限元到SPH粒子的转换，" Abaqus分析用户指南第15.2.2节](../usb/usb-link.md#usb-anl-asphconversion)）。

DELETE

将此参数设置为此选项控制单元删除标志的状态变量编号（请参见["用户定义的机械材料行为，" Abaqus分析用户指南第26.7.1节](../usb/usb-link.md#usb-mat-cusermat)）。

### **指定解相关状态变量数量的数据行：**

**第一行：**

### **为选定的解相关状态变量指定输出描述的可选数据行：**

**第二行：**

为每个要定义输出键和描述的解相关状态变量重复此数据行。如果未为解相关状态变量给出输出键和描述，将使用默认输出标识符 SDV*n* 和描述"解相关状态变量"。




