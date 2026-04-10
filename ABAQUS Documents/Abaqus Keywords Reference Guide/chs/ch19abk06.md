# *TIE





### *TIE定义基于表面的绑定和循环对称约束或耦合声-结构相互作用。

此选项用于在表面对之间施加绑定约束、循环对称约束或耦合声-结构相互作用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**部件、部件实例、装配

**Abaqus/CAE：**Interaction模块

##### **参考：**

- ["网格绑定约束," Section 35.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-ptiedconstraint)
- ["基于元素的表面定义," Section 2.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adeformablesurf)
- ["基于节点的表面定义," Section 2.3.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-anodebasedsurf)
- ["展示循环对称性的模型分析," Section 10.4.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acyclicsymmetry)
- ["声学、冲击和耦合声-结构分析," Section 6.10.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aacoustic)

### **必需参数：**

NAME

将此参数设置为一个标签，用于引用此约束。

### **可选的互斥参数：**

POSITION TOLERANCE

将此参数设置为用于确定从属表面上的哪些节点绑定到主表面的截止距离。特定从属节点与主表面之间距离的计算取决于诸如壳单元厚度、TYPE参数的设置以及所涉及表面类型等因素。不满足位置容差的从属节点不会绑定到主表面。此容许距离的默认值取决于约束中使用的公式类型和表面。

TIED NSET

将此参数设置为节点集标签，该标签包含将从属表面上将绑定到主表面的节点。包含在此节点集中的节点将被绑定。

### **可选参数：**

ADJUST

设置ADJUST=YES（默认）以将初始配置中从属表面上所有绑定节点移动到主表面上，且无任何应变。

如果从属节点不会被移动，则设置ADJUST=NO。如果从属表面属于子结构，或者其中一个或多个表面是基于梁元素的，则这是默认值。

CONSTRAINT RATIO

此参数仅在两个具有旋转自由度的表面使用偏移量绑定但使用了NO ROTATION参数时适用。

将此参数设置为翻译约束应作用的的主参考表面与从属节点之间的分数距离。默认情况下，Abaqus将尝试选择此距离，以使翻译约束恰好在界面上作用。

CYCLIC SYMMETRY

此参数仅适用于Abaqus/Standard分析。

包含此参数以调用约束循环对称结构重复扇区边界之间的约束。此参数只能与[*CYCLIC SYMMETRY MODEL](ch03abk92.md)选项一起使用。

NO ROTATION

如果旋转自由度不应被绑定，则包含此参数。如果省略此参数，除了平移自由度外，还会绑定任何现有的旋转自由度（如果适用）。

NO THICKNESS

包含此参数以忽略涉及位置容差和初始间隙调整的计算中的壳厚度效应。

TYPE

设置TYPE=SURFACE TO SURFACE（Abaqus/Standard中大多数情况的默认）以生成绑定系数，从而为指定的表面类型配对优化应力精度。

设置TYPE=NODE TO SURFACE（Abaqus/Explicit中所有情况的默认）以根据从属节点投影到主表面上的点处的插值函数生成绑定系数。

### **定义形成约束对的表面的数据行：**

**第一行：**

根据需要重复此数据行，以定义形成约束对的所有表面。每行数据定义将绑定在一起的一对表面。





