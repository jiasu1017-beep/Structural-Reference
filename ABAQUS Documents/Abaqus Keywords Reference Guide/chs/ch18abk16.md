# *SIMPEDANCE





### *SIMPEDANCE定义声学表面的阻抗。

此选项用于为声学和耦合声学-结构分析提供表面阻抗信息或非反射边界。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**历史数据

**级别：**步

**Abaqus/CAE：**Interaction模块

##### **参考：**

- ["Acoustic, shock, and coupled acoustic-structural analysis," Section 6.10.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aacoustic)
- ["Acoustic and shock loads," Section 34.4.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pacoustic)
- [*IMPEDANCE](ch09abk01.md)
- [*IMPEDANCE PROPERTY](ch09abk02.md)

### **必需的互斥参数：**

PROPERTY

将此参数设置为[*IMPEDANCE PROPERTY](ch09abk02.md)选项的名称，该选项定义要使用的阻抗表。

NONREFLECTING

设置NONREFLECTING=PLANAR（默认）以指定对应于正入射平面波的阻抗。

设置NONREFLECTING=IMPROVED以指定对应于任意入射角平面波的阻抗。此参数仅可用于瞬态动力学。

设置NONREFLECTING=CIRCULAR以指定适用于二维圆形边界或三维正圆柱体的辐射条件。

设置NONREFLECTING=SPHERICAL以指定适用于球形边界的辐射条件。

设置NONREFLECTING=ELLIPTICAL以指定适用于二维椭圆边界或三维正椭圆圆柱体的辐射条件。

设置NONREFLECTING=PROLATE SPHEROIDAL以指定适用于长球面边界的辐射条件。

### **可选参数：**

OP

设置OP=MOD（默认）以修改现有阻抗或定义附加阻抗。

如果应删除应用于模型的所有现有阻抗，则设置OP=NEW。要仅删除选定的阻抗，请使用OP=NEW并重新指定要保留的所有阻抗。

### **为PROPERTY、NONREFLECTING=PLANAR或NONREFLECTING=IMPROVED定义阻抗的数据行：**

**第一行（也是唯一行）：**

### **为NONREFLECTING=CIRCULAR或NONREFLECTING=SPHERICAL定义吸收边界阻抗的数据行：**

**第一行（也是唯一行）：**

### **为NONREFLECTING=ELLIPTICAL或NONREFLECTING=PROLATE SPHEROIDAL定义吸收边界阻抗的数据行：**

**第一行（也是唯一行）：**




