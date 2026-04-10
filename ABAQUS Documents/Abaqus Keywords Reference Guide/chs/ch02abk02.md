# *BEAM FLUID INERTIA





### *BEAM FLUID INERTIA定义浸没在流体中的梁的附加惯性。

此选项与[*BEAM SECTION](ch02abk06.md)或[*BEAM GENERAL SECTION](ch02abk05.md)选项配合使用，以包含浸没在无粘性流体中的Timoshenko梁单元的附加惯性效应。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**部件、部件实例、装配

**Abaqus/CAE：**属性模块

##### **参考：**

- ["梁截面行为，" Abaqus Analysis User's Guide第29.3.5节](../usb/usb-link.md#usb-elm-ebeamsectionbehavior)
- ["声学、冲击和耦合声-结构分析，" Abaqus Analysis User's Guide第6.10.1节](../usb/usb-link.md#usb-anl-aacoustic)
- ["入射膨胀波场的载荷，" Abaqus Theory Guide第6.3.1节](../stm/stm-link.md#stm-ldc-undexloads)

### **可选的、互斥的参数：**

FULL

使用此参数指定完全浸没的梁（默认值）。

HALF

使用此参数指定半浸没的梁。

### **定义梁流体惯性的数据行：**

**第一行（也是唯一一行）：**


