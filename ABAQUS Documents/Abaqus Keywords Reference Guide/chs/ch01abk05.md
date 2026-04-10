# *ADAPTIVE MESH





### *ADAPTIVE MESH定义自适应网格域。

此选项用于定义自适应网格域，并指定该域自适应网格划分的频率和强度。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**历史数据

**级别：**Step

**Abaqus/CAE：**在Step模块中受支持；每个step只能定义一个自适应网格域。

##### **参考：**

- ["在Abaqus/Explicit中定义ALE自适应网格域，" Abaqus Analysis User's Guide第12.2.2节](../usb/usb-link.md#usb-anl-aaledomains)
- ["在Abaqus/Explicit中进行ALE自适应网格划分和重映射，" Abaqus Analysis User's Guide第12.2.3节](../usb/usb-link.md#usb-anl-aaleremesh)
- ["在Abaqus/Standard中定义ALE自适应网格域，" Abaqus Analysis User's Guide第12.2.6节](../usb/usb-link.md#usb-anl-aalestd)
- ["在Abaqus/Standard中进行ALE自适应网格划分和重映射，" Abaqus Analysis User's Guide第12.2.7节](../usb/usb-link.md#usb-anl-aalestdremesh)
- [*ADAPTIVE MESH CONTROLS](ch01abk06.md)
- [*ADAPTIVE MESH CONSTRAINT](ch01abk05.md)

### **至少需要以下参数之一：**

ELSET

将此参数设置为包含自适应网格域中所有实体元素的元素集名称。

OP

设置OP=MOD（默认值）来修改现有自适应网格域（具有相同元素集名称）的自适应网格划分的频率和强度，或定义新的自适应网格域。

如果当前生效的所有自适应网格域都应被移除，设置OP=NEW。要仅移除选定的自适应网格域，请使用OP=NEW并重新指定所有要保留的自适应网格域。

在单个step内，[*ADAPTIVE MESH](ch01abk04.md)选项的所有用途的OP参数必须相同。

### **可选参数：**

CONTROLS

将此参数设置为与此自适应网格域关联的[*ADAPTIVE MESH CONTROLS](ch01abk06.md)选项的名称。自适应网格控制可用于控制显式动态分析和隐式声学分析中的自适应网格划分，以及控制显式动态分析中应用于自适应网格域的对流算法。

FREQUENCY

将此参数设置为执行自适应网格划分的增量频率。当在显式动态分析中使用此选项进行声学分析或定义空间网格约束或Eulerian边界区域时，默认频率为1。在所有其他情况下，默认频率为10。

INITIAL MESH SWEEPS

此参数仅适用于Abaqus/Explicit分析。

将此参数设置为在此自适应网格定义处于激活状态的第一个step开始时执行的网格扫描次数。如果使用[*ADAPTIVE MESH CONTROLS](ch01abk06.md)，SMOOTHING OBJECTIVE=UNIFORM，则默认的初始网格扫描次数为5。如果使用[*ADAPTIVE MESH CONTROLS](ch01abk06.md)，SMOOTHING OBJECTIVE=GRADED，则默认的初始网格扫描次数为2。

MESH SWEEPS

将此参数设置为在每个自适应网格增量中执行的网格扫描次数。默认的网格扫描次数为1。

**此选项没有关联的数据行。**