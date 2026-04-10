# *GAP RADIATION






### *GAP RADIATION在表面之间引入热辐射。

此选项用于在紧密相邻的表面之间提供辐射热传递。它必须与 [*SURFACE INTERACTION](ch18abk50.md) 选项一起使用，或在 Abaqus/Standard 分析中与 [*GAP](ch07abk01.md) 选项一起使用。

**产品：** Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：** Abaqus/Standard 中的模型数据；Abaqus/Explicit 中的历史数据  

**级别：** Abaqus/Standard 中的零件、零件实例、装配、模型；Abaqus/Explicit 中的步骤  

**Abaqus/CAE：** Interaction 模块

##### **参考文献：**

- ["热接触特性，" Abaqus Analysis User's Guide 第 37.2.1 节](../usb/usb-link.md#usb-cni-athermalinteraction)
- [*GAP](ch07abk01.md)
- [*INTERFACE](ch09abk22.md)
- [*SURFACE INTERACTION](ch18abk50.md)

**此选项没有关联的参数。**

### **定义辐射热传递的表面常数的数据行：**

**第一行：**

**第二行：**

根据需要重复此数据行，以定义视角因子对间隙的依赖关系。




