# *FABRIC









### *FABRIC指定织物的平面内响应。

此选项用于定义织物材料在平面应力条件下的平面内行为。

**产品：**Abaqus/Explicit

**类型：**模型数据

**级别：**模型

##### **参考：**

- ["织物材料行为，" Abaqus分析用户指南第23.4.1节](../usb/usb-link.md#usb-mat-cfabric)
- ["VFABRIC，" Abaqus用户子程序参考指南第1.2.4节](../sub/sub-link.md#sub-rtn-uexpfabric)
- [*DAMPING](ch04abk06.md)
- [*DENSITY](ch04abk13.md)
- [*DEPVAR](ch04abk14.md)
- [*INITIAL CONDITIONS](ch09abk18.md)
- [*ORIENTATION](ch15abk01.md)
- [*SECTION CONTROLS](ch18abk01.md)
- [*UNIAXIAL](ch20abk03.md)

### **可选参数：**

PROPERTIES

此参数只能与USER参数一起使用。

将此参数设置为用户子程序[`VFABRIC`](../sub/sub-link.md#sub-xsl-vfabric)中所需属性值的数据个数。默认值为0。

您可以使用[*DEPVAR](ch04abk14.md)选项引入状态变量，并在用户子程序[`VFABRIC`](../sub/sub-link.md#sub-xsl-vfabric)中更新这些变量。如果需要，您可以使用其中一个状态变量删除单元。

STRESS FREE INITIAL SLACK

设置 STRESS FREE INITIAL SLACK=YES（默认）以在沿纬纱和经纱方向的初始压应变区域产生零应力（这些初始压应变可能来自建模技术，如初始度量法——请参见[*INITIAL CONDITIONS](ch09abk18.md)，TYPE=REF COORDINATE）。当应变从初始压值连续恢复到无应变状态时，应力保持为零。一旦初始松弛被恢复，任何后续压应变都会根据材料定义产生应力。

设置 STRESS FREE INITIAL SLACK=NO 以根据材料定义在初始配置中产生应力，即使在承受压应变的织物区域也是如此。

Abaqus还提供了一种技术，可以在一段时间内逐渐在织物材料中引入任何初始应力（无论是拉伸还是压缩）（请参见[*SECTION CONTROLS](ch18abk01.md)）。

USER

如果根据局部系统中的总应变和增量织物应变在用户子程序[`VFABRIC`](../sub/sub-link.md#sub-xsl-vfabric)中更新织物应力，则包含此参数。

如果省略此参数，则必须包含[*UNIAXIAL](ch20abk03.md)选项，以根据织物应力和局部系统中的织物应变使用测试数据定义织物响应。

通过测试数据或用户子程序定义的织物材料的局部系统通过使用[*ORIENTATION](ch15abk01.md)选项初始化为参考配置中的纬纱和经纱方向。Abaqus随变形更新此局部系统，以跟踪当前配置中的纬纱和经纱方向。

### **为USER织物模型定义材料属性的数据行：**

**如果省略PROPERTIES参数或设置为0，则不需要数据行。否则，第一行：**

根据需要重复此数据行以定义材料属性。




