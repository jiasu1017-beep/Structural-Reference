# *INCIDENT WAVE PROPERTY






### *INCIDENT WAVE PROPERTY定义描述入射波的几何数据。

定义入射波几何数据的首选界面是使用 [*INCIDENT WAVE INTERACTION PROPERTY](ch09abk11.md) 选项的 [*INCIDENT WAVE INTERACTION](ch09abk10.md) 选项。替代界面使用 [*INCIDENT WAVE PROPERTY](ch09abk12.md) 选项来定义入射波的几何数据。

每个 [*INCIDENT WAVE](ch09abk08.md) 选项必须引用一个 [*INCIDENT WAVE PROPERTY](ch09abk12.md) 定义。[*INCIDENT WAVE PROPERTY](ch09abk12.md) 选项之后必须跟有 [*INCIDENT WAVE FLUID PROPERTY](ch09abk09.md) 选项，该选项定义入射波载荷中使用的流体特性。

**产品：** Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：** 模型数据  

**级别：** 模型  

**Abaqus/CAE：** 不支持；此选项已被入射波相互作用特性取代。

##### **参考文献：**

- ["声学和冲击载荷，" Abaqus Analysis User's Guide 第 34.4.6 节](../usb/usb-link.md#usb-prc-pacoustic)
- [*INCIDENT WAVE](ch09abk08.md)
- [*INCIDENT WAVE FLUID PROPERTY](ch09abk09.md)

### **必需参数：**

NAME

将此参数设置为一个标签，用于在 [*INCIDENT WAVE](ch09abk08.md) 选项中引用入射波特性时进行引用。

### **可选参数：**

TYPE

设置 TYPE=PLANE（默认）以指定平面入射波。

设置 TYPE=SPHERE 以指定球形入射波。

### **定义入射波特性的数据行：**

**第一行：**

**第二行：**

如果 TYPE=PLANE，则从 ![](../graphics/key_eqn00833.gif) 到 ![](../graphics/key_eqn00831.gif) 的向量定义入射波的方向；两点之间的距离不重要。对于使用气泡振幅的入射波载荷，用户使用 [*INCIDENT WAVE PROPERTY](ch09abk12.md) 选项定义的源位置被解释为源的初始位置。




