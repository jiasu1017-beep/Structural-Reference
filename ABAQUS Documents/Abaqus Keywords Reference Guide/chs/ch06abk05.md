# *FASTENER









### *FASTENER定义网格无关的紧固件。

此选项用于定义网格无关的紧固件。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**部件，部件实例，装配

**Abaqus/CAE：**相互作用模块

##### **参考：**

- ["网格无关的紧固件，" Abaqus分析用户指南第35.3.4节](../usb/usb-link.md#usb-cni-afastener)
- [*FASTENER PROPERTY](ch06abk06.md)

### **必需参数：**

INTERACTION NAME

将此参数设置为一个标签，用于引用紧固件相互作用。

PROPERTY

将此参数设置为此紧固件定义要使用的属性名称。

### **至少需要以下参数之一：**

ELSET

此参数仅在紧固件使用连接器单元建模时适用。

如果连接器单元是显式定义的，则将此参数设置为包含连接器单元的单元集名称。如果连接器单元要由Abaqus内部生成，则将此参数设置为一个空的单元集名称。

REFERENCE NODE SET

如果要使用内部生成的连接器单元来模拟紧固件，请将此参数与ELSET参数一起使用。如果要使用内部生成的刚性梁MPC来模拟紧固件，请不带ELSET参数使用此参数。

将此参数设置为包含此紧固件定义的参考节点的节点集名称。

### **可选参数：**

ADJUST ORIENTATION

设置 ADJUST ORIENTATION=YES（默认）以使Abaqus调整用户定义的方向，使得每个紧固件的局部z轴垂直于最接近该紧固件参考节点的表面。

设置 ADJUST ORIENTATION=NO 以精确定义局部方向。

ATTACHMENT METHOD

将此参数设置为用于找到紧固件紧固点的投影方法。

设置 ATTACHMENT METHOD=FACETOFACE（默认）以选择在指定表面或多个表面上定位紧固点的默认投影方法。定位点被投影到最近的表面以创建第一个紧固点，并使用法向投影来找到后续紧固点。

设置 ATTACHMENT METHOD=FACETOEDGE 以通过在最近表面上投影法向来找到第一个紧固点，并在指定表面或多个表面上以最近的点找到后续紧固点。

设置 ATTACHMENT METHOD=EDGETOFACE 以将最近表面上的最近点作为第一个紧固点，并通过在剩余表面上的法向投影找到后续紧固点。

设置 ATTACHMENT METHOD=EDGETOEDGE 以在指定表面或多个表面上找到最近的紧固点。

设置 ATTACHMENT METHOD=CONNECTORDIRECTION 以基于与紧固件关联的连接器单元的轴向来建立各个表面上的紧固点。此选项仅在指定了ELSET参数但未指定REFERENCE NODE SET参数且连接器单元的指定节点位置不重合时有效。

COUPLING

将此参数设置为用于将每个紧固点的位移和旋转耦合到紧固件投影点影响半径内表面节点平均运动的方法。

设置 COUPLING=CONTINUUM（默认）以将每个紧固点的位移和旋转耦合到影响半径内表面节点的平均位移。

设置 COUPLING=STRUCTURAL 以将每个紧固点的位移和旋转耦合到影响半径内表面节点的平均位移和旋转。

NUMBER OF LAYERS

将此参数设置为每个紧固件的层数。如果省略此参数且用户未指定表面或用户指定了单个表面，Abaqus将为每个紧固件形成最大可能的层数。

如果数据行上指定了多个表面，则忽略此参数。

ORIENTATION

将此参数设置为定义紧固件方向的方向定义名称（请参见["方向，" Abaqus分析用户指南第2.2.5节](../usb/usb-link.md#usb-int-corientation)）。如果省略此参数，则每个紧固件的方向由最接近该紧固件参考节点的表面（请参见["惯例，" Abaqus分析用户指南第1.2.2节](../usb/usb-link.md#usb-int-iconventions)）的默认局部方向决定。

紧固件仅支持矩形、圆柱形和球形方向定义。作为方向定义一部分的其他旋转将被忽略。

RADIUS OF INFLUENCE

将此参数设置为从连接表面上的投影点到该表面上的节点必须位于其中以贡献投影点运动的最大距离。如果省略此参数，Abaqus将根据紧固件直径和表面面片长度在内部计算默认的影响半径值。

SEARCH RADIUS

将此参数设置为参考节点必须位于其中的连接点的距离。如果省略此参数且用户未指定表面或用户指定了单个表面，Abaqus将基于每个定位点附近的面片厚度（对于壳单元面片）或特征面片长度（对于非壳单元面片）计算默认搜索半径。

UNSORTED

如果省略此参数，则紧固点的连通性由它们关联的表面沿紧固件投影方向的相对位置定义。

如果包含此参数，则紧固点的连通性由关联表面在数据行上出现的顺序定义。

如果数据行上未指定表面，则忽略此参数。

WEIGHTING METHOD

将此参数设置为用于对影响半径内表面节点位移对紧固件投影点运动的贡献进行加权的加权方案。

设置 WEIGHTING METHOD=UNIFORM（默认）以选择均匀权重分布。

设置 WEIGHTING METHOD=LINEAR 以选择线性递减权重分布。

设置 WEIGHTING METHOD=QUADRATIC 以选择二次多项式递减权重分布。

设置 WEIGHTING METHOD=CUBIC 以选择三次多项式单调递减权重分布。

### **如果使用默认投影方向（ATTACHMENT METHOD=FACETOFACE）定义紧固件的数据行：**

**第一行（可选）：**

**后续行（可选；如果省略，Abaqus将在定位点的搜索半径内所有单元面片上搜索紧固点）：**

根据需要重复此数据行，以定义此紧固件相互作用要连接的所有表面。

### **如果由用户指定第一个紧固点的投影方向，则定义紧固件的数据行：**

**第一行：**

**后续行（可选；如果省略，Abaqus将在定位点的搜索半径内所有单元面片上搜索紧固点）：**

根据需要重复此数据行，以定义此紧固件相互作用要连接的所有表面。




