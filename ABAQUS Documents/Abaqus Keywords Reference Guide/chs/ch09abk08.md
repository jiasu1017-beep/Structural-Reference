# *INCIDENT WAVE






### *INCIDENT WAVE为边界上的爆炸或散射载荷定义入射波载荷。

应用入射波载荷的首选界面是使用 [*INCIDENT WAVE INTERACTION PROPERTY](ch09abk11.md) 选项的 [*INCIDENT WAVE INTERACTION](ch09abk10.md) 选项。替代界面使用 [*INCIDENT WAVE](ch09abk08.md) 选项来施加入射波载荷。

[*INCIDENT WAVE PROPERTY](ch09abk12.md) 选项必须与 [*INCIDENT WAVE](ch09abk08.md) 选项一起使用。如果入射波场包括从网格边界外平面的反射，则可以使用 [*INCIDENT WAVE REFLECTION](ch09abk13.md) 选项对此效应进行建模。

**产品：** Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：** 历史数据  

**级别：** 步骤  

**Abaqus/CAE：** 不支持；此选项已被入射波相互作用取代。

##### **参考文献：**

- ["声学、冲击和耦合声-结构分析，" Abaqus Analysis User's Guide 第 6.10.1 节](../usb/usb-link.md#usb-anl-aacoustic)
- ["声学和冲击载荷，" Abaqus Analysis User's Guide 第 34.4.6 节](../usb/usb-link.md#usb-prc-pacoustic)
- [*INCIDENT WAVE PROPERTY](ch09abk12.md)
- [*INCIDENT WAVE REFLECTION](ch09abk13.md)

### **必需参数：**

PROPERTY

将此参数设置为定义入射波场的 [*INCIDENT WAVE PROPERTY](ch09abk12.md) 选项的名称。

### **必需的、互斥的参数：**

ACCELERATION AMPLITUDE

将此参数设置为定义 standoff 点处流体粒子加速度时间历史的振幅曲线名称（["振幅曲线，" Abaqus Analysis User's Guide 第 34.1.2 节](../usb/usb-link.md#usb-prc-pamplitude)）。此振幅曲线将仅用于计算流体牵引力：如果使用了 ACCELERATION AMPLITUDE 参数，则不能在 [*INCIDENT WAVE](ch09abk08.md) 选项的数据行上指定需要压力载荷的固体表面。

此参数仅对使用 [*INCIDENT WAVE PROPERTY](ch09abk12.md), TYPE=PLANE 选项的平面入射波有效。在这种情况下，不允许使用 [*INCIDENT WAVE REFLECTION](ch09abk13.md) 选项的反射载荷。

PRESSURE AMPLITUDE

将此参数设置为定义 standoff 点处流体压力时间历史的振幅曲线名称（["振幅曲线，" Abaqus Analysis User's Guide 第 34.1.2 节](../usb/usb-link.md#usb-prc-pamplitude)）。如果需要，相应的流体牵引力将从压力振幅参考计算。

### **定义入射波的数据行：**

**第一行：**

根据需要重复此数据行，以描述由于入射波导致的表面载荷。在涉及流体-固体边界的问题中，构成边界的流体表面和固体表面都必须指定入射波载荷，使用适当的载荷类型。




