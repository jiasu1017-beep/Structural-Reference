# *ADAPTIVE MESH CONSTRAINT





### *ADAPTIVE MESH CONSTRAINT指定自适应网格域中网格运动的约束。

**警告：**Abaqus/Explicit不允许网格位移出现跳跃。如果未指定振幅，Abaqus/Explicit将忽略用户提供的位移值，并强制执行零网格运动约束。

此选项用于为自适应网格域中的节点指定独立的网格运动，或定义必须跟随材料的节点。它只能与[*ADAPTIVE MESH](ch01abk04.md)选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**历史数据

**级别：**Step

**Abaqus/CAE：**位移和速度自适应网格约束在Step模块中受支持。

##### **参考：**

- ["在Abaqus/Explicit中定义ALE自适应网格域，" Abaqus Analysis User's Guide第12.2.2节](../usb/usb-link.md#usb-anl-aaledomains)
- ["在Abaqus/Standard中定义ALE自适应网格域，" Abaqus Analysis User's Guide第12.2.6节](../usb/usb-link.md#usb-anl-aalestd)
- ["UMESHMOTION，" Abaqus User Subroutines Reference Guide第1.1.43节](../sub/sub-link.md#sub-rtn-uumeshmotion)
- [*ADAPTIVE MESH](ch01abk04.md)

### **可选参数：**

AMPLITUDE

此参数仅与某些具有非零大小的变量相关。将此参数设置为定义规定网格运动大小的振幅曲线名称（["振幅曲线，" Abaqus Analysis User's Guide第34.1.2节](../usb/usb-link.md#usb-prc-pamplitude)）。

CONSTRAINT TYPE

设置CONSTRAINT TYPE=SPATIAL（默认值）来规定独立于底层材料的网格运动。

设置CONSTRAINT TYPE=LAGRANGIAN来定义必须跟随材料的节点。

OP

设置OP=MOD（默认值）来修改现有网格约束或向以前未约束的自由度添加网格约束。

如果当前生效的所有网格约束都应被移除，设置OP=NEW。要仅移除选定的网格约束，请使用OP=NEW并重新指定所有要保留的网格约束。

在单个step内，[*ADAPTIVE MESH CONSTRAINT](ch01abk05.md)选项的所有用途的OP参数必须相同。

TYPE

设置TYPE=DISPLACEMENT（默认值）来规定网格位移。

设置TYPE=VELOCITY来规定网格速度。

USER

此参数仅适用于Abaqus/Standard分析。

如果网格运动要在用户子程序[`UMESHMOTION`](../sub/sub-link.md#sub-xsl-umeshmotion)中定义，请包含此参数。当CONSTRAINT TYPE=LAGRANGIAN时，不能使用此参数。

### **规定独立于材料的网格运动的数据行（CONSTRAINT TYPE=SPATIAL）：**

**第一行：**

根据需要重复此数据行，以在不同节点和自由度处指定网格约束。

### **定义必须跟随材料的数据行（CONSTRAINT TYPE=LAGRANGIAN）：**

**第一行：**

根据需要重复此数据行。每行最多允许16个条目。