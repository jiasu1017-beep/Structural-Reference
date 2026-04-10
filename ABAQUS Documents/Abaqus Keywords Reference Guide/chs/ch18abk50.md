# *SURFACE INTERACTION





### *SURFACE INTERACTION定义表面相互作用属性。

此选项用于创建表面相互作用属性定义。表面相互作用属性将控制任何引用此表面相互作用的接触相互作用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**Abaqus/Standard中的模型数据；Abaqus/Explicit中的模型或历史数据

**级别：**Abaqus/Standard中的模型；Abaqus/Explicit中的模型或步

**Abaqus/CAE：**Interaction模块

##### **参考：**

- ["Assigning surface properties for contact pairs in Abaqus/Explicit," Section 36.5.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactpairsurfaces)
- ["Mechanical contact properties: overview," Section 37.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactmechanical)
- ["Contact pressure-overclosure relationships," Section 37.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-anormalinteraction)
- ["Contact damping," Section 37.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactdamping)
- ["Frictional behavior," Section 37.1.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-afriction)
- ["User-defined interfacial constitutive behavior," Section 37.1.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-auserinteraction)
- ["Breakable bonds," Section 37.1.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-aspotweld)
- ["Thermal contact properties," Section 37.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-athermalinteraction)
- ["Electrical contact properties," Section 37.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-ajouleheatinteraction)
- ["Pore fluid contact properties," Section 37.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-aporefluidinteraction)
- ["UINTER," Section 1.1.39 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uuinter)
- ["VUINTER," Section 1.2.18 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uexpinter)
- ["VUINTERACTION," Section 1.2.19 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uexpuinteraction)

### **必需参数：**

NAME

将此参数设置为一个标签，用于引用此表面相互作用属性。

在[*CONTACT PAIR](ch03abk68.md)选项的INTERACTION参数上（用于Abaqus/Standard接触分析或使用接触对算法的Abaqus/Explicit分析）或在[*CONTACT PROPERTY ASSIGNMENT](ch03abk71.md)选项的数据行上（用于使用通用接触算法的Abaqus/Explicit分析）使用此标签，以将表面相互作用属性分配给接触相互作用。

### **可选参数：**

DEPVAR

此参数仅在包含USER参数时相关。

将DEPVAR设置为用户子程序[`UINTER`](../sub/sub-link.md#sub-xsl-uinter)（Abaqus/Standard分析）或用户子程序[`VUINTER`](../sub/sub-link.md#sub-xsl-vuinter)或[`VUINTERACTION`](../sub/sub-link.md#sub-xsl-vuinteraction)（Abaqus/Explicit分析）所需的状态相关变量数量。默认值为DEPVAR=0。

PAD THICKNESS

此参数仅适用于使用接触对算法的Abaqus/Explicit分析。

将此参数设置为接触表面之间界面层的厚度。该值可以是正的或负的。

PROPERTIES

此参数仅在包含USER参数时相关。

将此参数设置为在用户子程序[`UINTER`](../sub/sub-link.md#sub-xsl-uinter)（Abaqus/Standard分析）或用户子程序[`VUINTER`](../sub/sub-link.md#sub-xsl-vuinter)或[`VUINTERACTION`](../sub/sub-link.md#sub-xsl-vuinteraction)（Abaqus/Explicit分析）中定义表面相互作用模型所需的数据属性值数量。默认值为PROPERTIES=0。

当此选项与连接器单元一起使用时，此参数被忽略。

TRACKING THICKNESS

将此参数设置为决定要跟踪的接触表面的厚度。

在Abaqus/Standard中，跟踪范围将至少与此参数的设置一样大；如果此参数设置小于默认值，则内部计算的默认值将继续生效。在Abaqus/Standard中，此参数扩展了为分离表面提供接触开口距离（COPEN）输出的范围。

在Abaqus/Explicit中，此参数仅在用户子程序[`VUINTER`](../sub/sub-link.md#sub-xsl-vuinter)或[`VUINTERACTION`](../sub/sub-link.md#sub-xsl-vuinteraction)也生效时适用。只有距离在此厚度内的接触表面可用于用户定义的相互作用。此参数仅影响节点到表面的接触，且此参数的输入值不能为负。如果输入零值或省略参数，则使用内部默认值。

UNSYMM

此参数仅适用于包含USER参数的Abaqus/Standard分析。

当界面刚度矩阵不对称时包含此参数。此参数导致Abaqus/Standard使用其非对称方程求解过程。

USER

在Abaqus/Standard分析中，如果表面相互作用模型将在用户子程序[`UINTER`](../sub/sub-link.md#sub-xsl-uinter)中定义，则包含此参数。

在Abaqus/Explicit分析中，如果表面相互作用模型将在用户子程序[`VUINTER`](../sub/sub-link.md#sub-xsl-vuinter)中定义，则包含此参数而不带任何赋值；如果表面相互作用模型将在用户子程序[`VUINTERACTION`](../sub/sub-link.md#sub-xsl-vuinteraction)中定义，则设置USER=INTERACTION。[`VUINTER`](../sub/sub-link.md#sub-xsl-vuinter)适用于接触对，而[`VUINTERACTION`](../sub/sub-link.md#sub-xsl-vuinteraction)适用于通用接触。

当包含此参数时，[*SURFACE BEHAVIOR](ch18abk48.md)选项及其各种子选项不能在同一相互作用定义下使用。

### **如果省略USER参数，对于Abaqus/Standard中的二维模型或涉及Abaqus/Standard中基于节点的表面的接触对的可选数据行：**

**第一行（也是唯一行）：**

### **如果使用USER参数，在Abaqus/Standard分析中定义表面相互作用的数据行：**

**第一行：**

**第二行（仅在使用PROPERTIES参数时需要）：**

根据需要重复此数据行以定义所有材料常数。

### **如果使用PROPERTIES参数，在Abaqus/Explicit分析中定义表面相互作用的数据行：**

**第一行：**

**第二行：**

根据需要重复此数据行以定义所有材料常数。


