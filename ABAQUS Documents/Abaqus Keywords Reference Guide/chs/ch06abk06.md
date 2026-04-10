# *FASTENER PROPERTY









### *FASTENER PROPERTY规定网格无关的紧固件属性。

此选项用于规定紧固件相互作用的属性。此选项必须与[*FASTENER](ch06abk05.md)选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**部件，部件实例，装配

**Abaqus/CAE：**相互作用模块

##### **参考：**

- ["网格无关的紧固件，" Abaqus分析用户指南第35.3.4节](../usb/usb-link.md#usb-cni-afastener)
- [*FASTENER](ch06abk05.md)

### **必需参数：**

NAME

将此参数设置为一个标签，用于引用紧固件属性。

### **可选参数：**

MASS

将此参数设置为将分配到紧固件节点的附加质量。

### **指定紧固件属性的数据行：**

**第一行：**

**第二行：**

根据需要重复此数据行，以指定不同自由度的约束。当在关联的[*FASTENER](ch06abk05.md)选项上指定了ORIENTATION参数时，自由度在初始配置中的指定局部系统中；否则，它们在默认局部系统中。在这两种情况下，这些方向将在大位移分析中随参考节点旋转（当[*STEP](ch18abk36.md)选项上的NLGEOM参数设置为YES时）。




