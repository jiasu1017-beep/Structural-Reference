# *INCIDENT WAVE INTERACTION PROPERTY






### *INCIDENT WAVE INTERACTION PROPERTY定义描述入射波的几何数据和流体特性。

此选项定义用于定义入射波的几何数据和流体特性。每个 [*INCIDENT WAVE INTERACTION](ch09abk10.md) 选项必须引用一个 [*INCIDENT WAVE INTERACTION PROPERTY](ch09abk11.md) 定义。

**产品：** Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：** 模型数据  

**级别：** 模型  

**Abaqus/CAE：** Interaction 模块

##### **参考文献：**

- ["声学和冲击载荷，" Abaqus Analysis User's Guide 第 34.4.6 节](../usb/usb-link.md#usb-prc-pacoustic)
- [*INCIDENT WAVE INTERACTION](ch09abk10.md)
- [*UNDEX CHARGE PROPERTY](ch20abk02.md)
- [*CONWEP CHARGE PROPERTY](ch03abk76.md)

### **必需参数：**

NAME

将此参数设置为一个标签，用于在 [*INCIDENT WAVE INTERACTION](ch09abk10.md) 选项中引用入射波相互作用特性时进行引用。

### **可选参数：**

TYPE

设置 TYPE=PLANE（默认）以指定平面入射波。

设置 TYPE=SPHERE 以指定球形入射波。

设置 TYPE=DIFFUSE 以指定从多个角度入射的平面波场。

设置 TYPE=AIR BLAST 以指定球形爆炸波。此选项仅适用于 Abaqus/Explicit 分析。

设置 TYPE=SURFACE BLAST 以指定半球形爆炸波。此选项仅适用于 Abaqus/Explicit 分析。

### **使用 TYPE=PLANE、TYPE=SPHERE（声学衰减）或与 [*UNDEX CHARGE PROPERTY](ch20abk02.md) 选项一起使用的 TYPE=SPHERE 定义入射波相互作用特性的数据行：**

**第一（也是唯一）行：**

### **使用 TYPE=SPHERE 和广义空间衰减定义入射波相互作用特性的数据行：**

**第一（也是唯一）行：**

### **定义来自漫射源的入射波载荷的数据行（TYPE=DIFFUSE）：**

**第一（也是唯一）行：**

### **对于与 [*CONWEP CHARGE PROPERTY](ch03abk76.md) 选项一起使用的 TYPE=AIR BLAST 或 TYPE=SURFACE BLAST，不需要数据行。**




