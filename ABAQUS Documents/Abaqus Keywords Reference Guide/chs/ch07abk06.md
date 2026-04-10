# *GAP HEAT GENERATION






### *GAP HEAT GENERATION引入由于界面能量耗散而产生的热量。

此选项用于修改默认的间隙热生成模型，以耗散由非热表面相互作用（如摩擦滑动或电流）产生的能量。默认是将所有耗散的能量转换为热量，并将其均匀分配给两个相互作用的表面。

[*GAP HEAT GENERATION](ch07abk05.md) 选项必须与 [*SURFACE INTERACTION](ch18abk50.md) 选项一起使用，或在 Abaqus/Standard 分析中与 [*GAP](ch07abk01.md) 选项一起使用。

**产品：** Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：** Abaqus/Standard 中的模型数据；Abaqus/Explicit 中的历史数据  

**级别：** Abaqus/Standard 中的零件、零件实例、装配、模型；Abaqus/Explicit 中的步骤  

**Abaqus/CAE：** Interaction 模块

##### **参考文献：**

- ["摩擦行为，" Abaqus Analysis User's Guide 第 37.1.5 节](../usb/usb-link.md#usb-cni-afriction)
- ["热接触特性，" Abaqus Analysis User's Guide 第 37.2.1 节](../usb/usb-link.md#usb-cni-athermalinteraction)
- ["电接触特性，" Abaqus Analysis User's Guide 第 37.3.1 节](../usb/usb-link.md#usb-cni-ajouleheatinteraction)
- [*GAP](ch07abk01.md)
- [*INTERFACE](ch09abk22.md)
- [*SURFACE INTERACTION](ch18abk50.md)

**此选项没有关联的参数。**

### **定义间隙热生成的数据行：**

**第一（也是唯一）行：**




