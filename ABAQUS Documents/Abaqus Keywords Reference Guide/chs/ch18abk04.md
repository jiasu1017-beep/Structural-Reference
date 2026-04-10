# *SECTION POINTS





### *SECTION POINTS定位梁截面中需要应力和应变输出的点。

此选项在Abaqus/Standard和Abaqus/Explicit中作为模型数据与[*BEAM GENERAL SECTION](ch02abk05.md)选项配合使用，在Abaqus/Standard中作为历史数据与[*BEAM SECTION GENERATE](ch02abk07.md)选项配合使用。

当与[*BEAM GENERAL SECTION](ch02abk05.md)选项和预定义库截面配合使用时，它定位梁截面中需要轴向应力和轴向应变输出的截面点。

当与[*BEAM GENERAL SECTION](ch02abk05.md)，SECTION=MESHED选项配合使用时，它定位梁截面模型中需要应力和应变输出的单元和积分点，并提供确定应力应变输出所需的面纱函数导数的材料数据。

当与[*BEAM SECTION GENERATE](ch02abk07.md)选项配合使用时，它将用户定义的截面点标签与在后续梁分析中需要应力和应变输出的梁截面模型中的单元和积分点相关联。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型或历史数据

**级别：**部件、部件实例、步

**Abaqus/CAE：**Property模块

##### **参考：**

- ["Using a general beam section to define the section behavior," Section 29.3.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eusingbeamgensect)
- ["Meshed beam cross-sections," Section 10.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-ameshedsection)
- [*BEAM GENERAL SECTION](ch02abk05.md)

**此选项没有关联的参数。**

### **当与[*BEAM GENERAL SECTION](ch02abk05.md)选项和预定义库截面配合使用时，用于定位输出截面点的数据行：**

**第一行：**

继续给出 ![](../graphics/key_eqn01050.gif) 坐标对，所需点数不限。在任何数据行上最多可指定四对点。如果将点(0,0)指定为行上的最后一个条目，则除非它是唯一请求的点，否则将被忽略。

### **当与[*BEAM GENERAL SECTION](ch02abk05.md)，SECTION=MESHED选项配合使用时，用于定位网格截面单元和积分点编号的数据行：**

**第一行：**

**第二行：**

根据需要重复此组数据行以获取所需的积分点数。

### **当与[*BEAM SECTION GENERATE](ch02abk07.md)选项配合使用时，用于定位截面模型中单元和积分点编号的数据行：**

**第一行：**

根据需要重复此数据行以指定单元和积分点。




