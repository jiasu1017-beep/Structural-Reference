# *SHELL TO SOLID COUPLING





### *SHELL TO SOLID COUPLING定义壳边缘与实体面之间的基于表面的耦合。

此基于表面的选项允许在三维分析中从壳单元建模过渡到实体单元建模。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**部件、部件实例、装配

**Abaqus/CAE：**Interaction模块

##### **参考：**

- ["Element-based surface definition," Section 2.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adeformablesurf)
- ["Node-based surface definition," Section 2.3.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-anodebasedsurf)
- ["Shell-to-solid coupling," Section 35.3.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-pshelltosolidcoup)

### **必需参数：**

CONSTRAINT NAME

将此参数设置为将用于引用此约束的标签。

### **可选参数：**

INFLUENCE DISTANCE

将此参数设置为从边缘基准面的垂直距离，实体面上所有节点或单元面（取决于实体表面类型）必须位于此距离范围内才能包含在耦合约束中。默认值是用于定义边缘基准面的壳厚度的一半。

POSITION TOLERANCE

将此参数设置为边缘基准面上的节点必须位于实体表面的距离范围内才能包含在耦合定义中。默认容差是壳边缘上典型面长度的5%。

### **定义形成耦合定义的表面的数据行：**

**第一行：**

根据需要重复此数据行以定义形成耦合定义的所有表面。每一数据行定义一对将被耦合的表面。




