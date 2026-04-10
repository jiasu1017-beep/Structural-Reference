# *SFILM





### *SFILM定义用于传热分析表面上散热系数和相关环境温度。

此选项用于为完全耦合热应力分析提供表面上散热系数和环境温度。在Abaqus/Standard中，它还用于传热、耦合热电和耦合热电结构分析。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE

**类型：**历史数据

**级别：**步

**Abaqus/CAE：**Interaction模块

##### **参考：**

- ["Thermal loads," Section 34.4.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pthermal)
- ["FILM," Section 1.1.6 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-ufilm)

### **可选参数：**

AMPLITUDE

将此参数设置为给出环境温度 ![](../graphics/key_eqn00086.gif) 随时间变化的[*AMPLITUDE](ch01abk09.md)选项的名称。

如果在Abaqus/Standard分析中省略此参数，则根据[*STEP](ch18abk36.md)选项上AMPLITUDE参数分配的值（["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)），参考环境温度将在步开始时立即应用或在线性跨越步应用。如果在Abaqus/Explicit分析中省略此参数，则参考环境温度将在步开始时立即应用。

对于类型FNU的非均匀膜（仅在Abaqus/Standard中可用），环境温度幅值在用户子程序[`FILM`](../sub/sub-link.md#sub-xsl-film)中定义，AMPLITUDE引用仅用于修改传递到用户子程序的环境温度。

FILM AMPLITUDE

此参数仅适用于Abaqus/Standard和Abaqus/Explicit分析。

将此参数设置为给出膜系数 *h* 随时间变化的[*AMPLITUDE](ch01abk09.md)选项的名称。

如果在Abaqus/Standard分析中省略此参数，则参考膜系数在步开始时立即应用并在步中保持恒定，独立于[*STEP](ch18abk36.md)选项上AMPLITUDE参数分配的值。如果在Abaqus/Explicit分析中省略此参数，则数据行上给出的参考环境温度将在整个步中应用。

如果使用[*FILM PROPERTY](ch06abk11.md)选项将膜系数定义为温度和场变量的函数，则忽略FILM AMPLITUDE参数。

对于类型FNU的非均匀膜（仅在Abaqus/Standard中可用），膜系数幅值在用户子程序[`FILM`](../sub/sub-link.md#sub-xsl-film)中定义，FILM AMPLITUDE引用仅用于修改传递到用户子程序的膜系数。

OP

设置OP=MOD（默认）以修改现有膜或定义附加膜。

如果应删除应用于模型的所有现有[*SFILM](ch18abk08.md)s，则设置OP=NEW。

### **定义环境温度和膜系数的数据行：**

**第一行：**

根据需要重复此数据行以定义不同表面的膜条件。




