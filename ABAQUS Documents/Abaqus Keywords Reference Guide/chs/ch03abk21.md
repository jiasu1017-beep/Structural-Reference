# *CLEARANCE






### *CLEARANCE为从节点在表面上指定特定的初始间隙值和接触方向。

此选项用于在接触从节点处精确指定初始间隙值和/或接触方向。在 Abaqus/Standard 分析中，它还可用于指定过盈值。[*CLEARANCE](ch03abk21.md) 选项只能与小滑动接触一起使用（[*CONTACT PAIR](ch03abk68.md)，SMALL SLIDING）。在 Abaqus/Explicit 中，它只能用于分析的第一个步骤。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**Abaqus/Standard 中的模型数据；Abaqus/Explicit 中的历史数据  

**级别：**Abaqus/Standard 中的模型；Abaqus/Explicit 中的步骤  

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["与 Abaqus/Standard 中接触建模相关的常见困难，" Abaqus 分析用户指南第 39.1.2 节](../usb/usb-link.md#usb-cni-acontacttrouble)
- ["与在 Abaqus/Explicit 中使用接触对进行接触建模相关的常见困难，" Abaqus 分析用户指南第 39.2.2 节](../usb/usb-link.md#usb-cni-aexpcontacttrouble)
- ["调整 Abaqus/Standard 接触对的初始表面位置并指定初始间隙，" Abaqus 分析用户指南第 36.3.5 节](../usb/usb-link.md#usb-cni-aadjustsurfaces)
- ["调整 Abaqus/Explicit 接触对的初始表面位置并指定初始间隙，" Abaqus 分析用户指南第 36.5.4 节](../usb/usb-link.md#usb-cni-aexpadjustsurfaces)

### **必需参数：**

CPSET

此参数仅适用于 Abaqus/Explicit 分析。

将此参数设置为接触对集合名称，以将这些间隙数据与相应的接触对关联。

MASTER

此参数仅适用于 Abaqus/Standard 分析。

将此参数设置为接触对主表面的名称。

SLAVE

此参数仅适用于 Abaqus/Standard 分析。

将此参数设置为接触对从表面的名称。

### **必需的互斥参数：**

TABULAR

包含此参数以在此选项的数据行上指定从节点或节点集及其对应的初始间隙/过盈值（以及所需的接触方向）。在 Abaqus/Explicit 分析中，仅允许初始间隙。

VALUE

将此参数设置为整个从节点集的初始间隙/过盈值。在 Abaqus/Standard 中，正值指定初始间隙，负值指定初始过盈。在 Abaqus/Explicit 分析中，此值必须为正，因为仅允许初始间隙。

### **包含 TABULAR 参数时的可选参数：**

BOLT

包含此参数以指示将根据螺纹几何数据以及用于在数据行上指定的螺栓和螺栓孔组件轴线上定义方向矢量的两个点，自动生成螺纹螺栓连接的适当接触法线方向。此参数仅对单螺纹螺栓有效。

INPUT

将此参数设置为包含此选项数据行的备用输入文件的名称。请参阅 ["输入语法规则，" Abaqus 分析用户指南第 1.2.1 节](../usb/usb-link.md#usb-int-iinputsyntax)，了解此类文件名的语法。备用输入文件中的数据行应与 TABULAR 参数的格式相同。

如果省略此参数且包含了 TABULAR 参数，则假定数据跟随在关键字行之后。

### **如果包含了 TABULAR 参数但没有 INPUT 参数和 BOLT 参数时的数据行：**

**第一行：**

根据需要重复上述数据行，以定义间隙值以及 Abaqus 用于测试从节点与主表面上相应最近点之间接触的方向。法向量的规范是可选的。如果给定了法向量，它应该指向主表面外向法线的方向。如果未给定法向量，Abaqus 将从主表面的几何形状计算它（请参阅 ["与 Abaqus/Standard 中接触建模相关的常见困难，" Abaqus 分析用户指南第 39.1.2 节](../usb/usb-link.md#usb-cni-acontacttrouble)，以及 ["与在 Abaqus/Explicit 中使用接触对进行接触建模相关的常见困难，" Abaqus 分析用户指南第 39.2.2 节](../usb/usb-link.md#usb-cni-aexpcontacttrouble)）。

### **如果同时包含了 TABULAR 参数和 BOLT 参数但没有 INPUT 参数时的数据行（请参阅 [图 3.21-1](ch03abk21.md#thread-bolt-connection) 和 [图 3.21-2](ch03abk21.md#thread-bolt-connection3)）：**

**第一行：**

**第二行：**

根据需要重复第二数据行，以定义间隙值以及 Abaqus 用于根据螺纹几何计算接触法线方向的螺栓和螺栓孔组件轴线上的方向矢量（请参阅 ["调整 Abaqus/Standard 接触对的初始表面位置并指定初始间隙，" Abaqus 分析用户指南第 36.3.5 节](../usb/usb-link.md#usb-cni-aadjustsurfaces)，以及 ["精确指定初始间隙值"中的"调整 Abaqus/Explicit 接触对的初始表面位置并指定初始间隙，" Abaqus 分析用户指南第 36.5.4 节](../usb/usb-link.md#usb-cni-aexpadjustsurfaces-clearance)）。

### **使用 VALUE 参数定义间隙值：**

当指定 VALUE 参数时，此选项不使用数据行。

**图 3.21-1** 螺纹几何。

![](../graphics/thread-bolt-connection.png)

**图 3.21-2** 螺栓和螺栓孔组件中心线上的点 *a* 和点 *b*。

![](../graphics/thread-bolt-connection3.png)




