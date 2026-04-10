# *INCIDENT WAVE INTERACTION






### *INCIDENT WAVE INTERACTION为表面上的爆炸或散射载荷定义入射波载荷。

此选项用于施加入射波载荷。[*INCIDENT WAVE INTERACTION PROPERTY](ch09abk11.md) 选项必须与 [*INCIDENT WAVE INTERACTION](ch09abk10.md) 选项一起使用。如果入射波场包括从网格边界外平面的反射，则可以使用 [*INCIDENT WAVE REFLECTION](ch09abk13.md) 选项对此效应进行建模。入射波相互作用可用于稳态动态步骤，以定义来自漫射源的单个波源或载荷。

**产品：** Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：** 历史数据  

**级别：** 步骤  

**Abaqus/CAE：** Interaction 模块

##### **参考文献：**

- ["声学、冲击和耦合声-结构分析，" Abaqus Analysis User's Guide 第 6.10.1 节](../usb/usb-link.md#usb-anl-aacoustic)
- ["声学和冲击载荷，" Abaqus Analysis User's Guide 第 34.4.6 节](../usb/usb-link.md#usb-prc-pacoustic)
- [*INCIDENT WAVE INTERACTION PROPERTY](ch09abk11.md)
- [*INCIDENT WAVE REFLECTION](ch09abk13.md)

### **必需参数：**

PROPERTY

将此参数设置为定义入射波场的 [*INCIDENT WAVE INTERACTION PROPERTY](ch09abk11.md) 选项的名称。

### **必需的、互斥的参数：**

ACCELERATION AMPLITUDE

将此参数设置为定义 standoff 点处流体粒子加速度时间历史的振幅曲线名称（["振幅曲线，" Abaqus Analysis User's Guide 第 34.1.2 节](../usb/usb-link.md#usb-prc-pamplitude)）。此振幅曲线将仅用于计算流体牵引力：如果使用了 ACCELERATION AMPLITUDE 参数，则不能在 [*INCIDENT WAVE INTERACTION](ch09abk10.md) 选项的数据行上指定需要压力载荷的固体表面。

此参数仅对使用 [*INCIDENT WAVE INTERACTION PROPERTY](ch09abk11.md), TYPE=PLANE 选项的瞬态平面入射波有效。在这种情况下，不允许使用 [*INCIDENT WAVE REFLECTION](ch09abk13.md) 选项的反射载荷。

CONWEP

此参数仅适用于 Abaqus/Explicit 分析。

包含此参数以使用 [*CONWEP CHARGE PROPERTY](ch03abk76.md) 选项定义入射波。此参数仅对使用 [*INCIDENT WAVE INTERACTION PROPERTY](ch09abk11.md), TYPE=AIR BLAST 或 TYPE=SURFACE BLAST 选项的爆炸波有效。

PRESSURE AMPLITUDE

将此参数设置为定义 standoff 点处流体压力时间历史的振幅曲线名称（["振幅曲线，" Abaqus Analysis User's Guide 第 34.1.2 节](../usb/usb-link.md#usb-prc-pamplitude)）。如果需要，相应的流体牵引力将从压力振幅参考计算。

UNDEX

包含此参数以使用 [*UNDEX CHARGE PROPERTY](ch20abk02.md) 选项定义球形入射波。此参数仅对使用 [*INCIDENT WAVE INTERACTION PROPERTY](ch09abk11.md), TYPE=SPHERE 选项的球形入射波有效。

### **矩阵生成和稳态动态分析（直接或子空间）的可选、互斥参数：**

IMAGINARY

包含此参数以定义 standoff 点处载荷的虚部（异相）。

REAL

包含此参数（默认）以定义 standoff 点处载荷的实部（同相）。

### **当省略 CONWEP 参数时定义入射波的数据行：**

**第一（也是唯一）行：**

### **当包含 CONWEP 参数时定义入射波的数据行：**

**第一（也是唯一）行：**




