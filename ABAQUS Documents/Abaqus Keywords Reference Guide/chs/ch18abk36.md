# *SUBMODEL





### *SUBMODEL在子模型分析中指定驱动边界节点。

此选项用于指定子模型的"驱动区域"总列表。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**部件、部件实例、装配

**Abaqus/CAE：**Load模块和模型属性

##### **参考：**

- ["Submodeling: overview," Section 10.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asubmodeloverview)

### **可选的互斥参数：**

ACOUSTIC TO STRUCTURE

如果子模型将在指定表面被全局耦合声学-结构模型的声压驱动，则包含此参数。

SHELL TO SOLID

如果实体单元子模型将被全局壳模型驱动，则包含此参数。如果包含此参数，所有驱动节点必须在实体单元上，且必须位于全局模型中用壳单元建模的区域中。如果在任何[*SUBMODEL](ch18abk38.md)选项上包含了此参数，则必须在输入文件的所有[*SUBMODEL](ch18abk38.md)选项上包含此参数。

### **SHELL TO SOLID子模型时的必需参数：**

SHELL THICKNESS

如果在全局模型的[*SHELL SECTION](ch18abk15.md)或[*SHELL GENERAL SECTION](ch18abk14.md)选项上未使用OFFSET参数，则将此参数设置为全局模型中壳厚度的最大值（以模型使用的单位给出）。如果在全局模型中使用了OFFSET参数，则将此参数设置为从参考表面到顶部或底部壳表面的最大距离的两倍。

### **可选参数：**

ABSOLUTE EXTERIOR TOLERANCE

将此参数设置为子模型的驱动节点可能位于全局模型元素区域外部的绝对值（以模型使用的单位给出）。如果未使用此参数或其值为0.0，则适用EXTERIOR TOLERANCE。对于壳到实体子模型，驱动节点可以位于由SHELL THICKNESS参数值的一半加上外部容差定义的区域内。

EXTERIOR TOLERANCE

将此参数设置为全局模型中平均单元尺寸的分数，子模型的驱动节点可能位于全局模型元素区域外部。默认值为0.05。对于壳到实体子模型，驱动节点可以位于由SHELL THICKNESS参数值的一半加上外部容差定义的区域内。

如果用户指定了两个容差参数，Abaqus使用更严格的容差。

GLOBAL ELSET

将此参数设置为全局模型中将搜索其响应将用于驱动子模型的元素的单元集名称。如果省略此参数，Abaqus将搜索位于子模型附近的所有全局模型元素。

当声压作用于壳的两侧时，此参数必须与ACOUSTIC TO STRUCTURE参数一起使用。

INTERSECTION ONLY

包含此参数以指定Abaqus忽略在考虑外部搜索容差后发现位于全局模型元素区域外部的驱动节点。

此参数只能与TYPE=NODE一起使用。此参数不能与ACOUSTIC TO STRUCTURE或SHELL TO SOLID参数一起使用。

TYPE

此参数仅适用于Abaqus/Standard分析。它决定全局模型到子模型的通信是通过节点还是通过表面进行。

设置TYPE=NODE（默认）用于基于节点的子模型。基于节点的子模型定义将伴随[*BOUNDARY](ch02abk12.md)，SUBMODEL定义。

设置TYPE=SURFACE用于基于表面的子模型。此参数设置不能与ACOUSTIC TO STRUCTURE、SHELL TO SOLID或SHELL THICKNESS参数一起使用。基于表面的子模型定义将伴随[*DSLOAD](ch04abk42.md)，SUBMODEL定义。

### **定义一般和壳到实体子模型驱动边界的数据行：**

**第一行：**

根据需要重复此数据行。

### **定义声学到结构子模型驱动边界的数据行：**

**第一行：**

根据需要重复此数据行。

### **定义基于表面子模型驱动表面的数据行：**

**第一行：**

根据需要重复此数据行。




