# *KINEMATIC






### *KINEMATIC定义运动耦合约束。

此选项用于定义运动耦合约束。它必须与 [*COUPLING](ch03abk83.md) 选项一起使用。

**产品：** Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：** 模型数据  

**级别：** 零件、零件实例、装配  

**Abaqus/CAE：** Interaction 模块

##### **参考文献：**

- ["耦合约束，" Abaqus Analysis User's Guide 第 35.3.2 节](../usb/usb-link.md#usb-cni-pcoupling)
- [*COUPLING](ch03abk83.md)

**此选项没有关联的参数。**

### **指定要约束的自由度的数据行：**

**第一行：**

根据需要重复此数据行，以指定不同自由度的约束。当在关联的 [*COUPLING](ch03abk83.md) 选项上指定了 ORIENTATION 参数时，自由度位于初始配置中的参考局部系统中；否则，它们位于全局系统中。在这两种情况下，这些方向将在大位移分析中随参考节点旋转（当在 [*STEP](ch18abk36.md) 选项上包含 NLGEOM 参数时）。




