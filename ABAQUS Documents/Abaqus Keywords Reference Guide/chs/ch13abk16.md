# *MEMBRANE SECTION









### *MEMBRANE SECTION为膜单元指定截面属性。

此选项用于为一组膜单元分配截面属性。截面属性包括厚度、厚度变化行为、材料定义和材料方向。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**部件、部件实例  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["膜单元，" Abaqus Analysis User's Guide第29.1.1节](../usb/usb-link.md#usb-elm-emembrane)
- [*DISTRIBUTION](ch04abk29.md)

### **必需参数：**

ELSET

将此参数设置为包含正在定义截面属性的膜单元的单元集名称。

MATERIAL

将此参数设置为要与这些单元一起使用的材料名称。

### **可选参数：**

CONTROLS

在Abaqus/Explicit分析中，将此参数设置为截面控制定义的名称，用于指定非默认沙漏控制公式或比例因子。

在Abaqus/Standard分析中，将此参数设置为截面控制定义的名称，用于指定增强的沙漏控制公式或用于后续的Abaqus/Explicit导入分析。

DENSITY

将此参数设置为膜单位表面积的的质量。

如果使用此参数，则膜的质量包括此参数以及材料定义的任何贡献。

MEMBRANE THICKNESS

此参数仅适用于Abaqus/Standard分析。

将此参数设置为分布定义的名称，以定义空间变化的厚度。

用于定义膜厚度的分布必须具有默认值。默认厚度由分配给膜截面但未在分布中专门分配值的任何膜单元使用。

NODAL THICKNESS和MEMBRANE THICKNESS参数是互斥的。

NODAL THICKNESS

包含此参数以指示不应从数据行读取膜厚度，而应使用[*NODAL THICKNESS](ch14abk08.md)选项在节点处指定的厚度进行插值。

NODAL THICKNESS和MEMBRANE THICKNESS参数是互斥的。

ORIENTATION

将此参数设置为[*ORIENTATION](ch15abk01.md)选项的名称，用于定义该集合中单元材料计算的局部坐标系。

POISSON

此参数仅在大变形分析中相关。将其设置为非零值以导致厚度作为膜应变函数变化。POISSON参数的值必须介于1.0和0.5之间。值为0.5将强制单元不可压缩行为。POISSON=0.0表示厚度不会变化。

在Abaqus/Explicit分析中，将其设置为MATERIAL以导致厚度基于单元材料定义变化。

默认值为Abaqus/Standard中的POISSON=0.5和Abaqus/Explicit中的POISSON=MATERIAL。

### **恒定厚度膜的数据行：**

**第一行（也是唯一一行）：**

### **定义连续变化厚度膜：**

当指定了NODAL THICKNESS或MEMBRANE THICKNESS参数时，此选项不使用数据行；数据行上输入的任何值都将被忽略。而是使用[*NODAL THICKNESS](ch14abk08.md)或MEMBRANE THICKNESS选项来定义截面厚度。