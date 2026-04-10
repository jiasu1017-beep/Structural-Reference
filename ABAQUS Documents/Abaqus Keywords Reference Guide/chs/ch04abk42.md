# *DSLOAD





### *DSLOAD指定分布表面载荷。

此选项用于指定分布表面载荷。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**类型：**历史数据 

**级别：**步骤

**Abaqus/CAE：**载荷模块

##### **参考：**

- ["分布载荷，" Abaqus分析用户指南第34.4.3节](../usb/usb-link.md#usb-prc-ploaddistributed)
- ["DLOAD，" Abaqus用户子程序参考指南第1.1.5节](../sub/sub-link.md#sub-rtn-udload)
- ["分析呈现循环对称性的模型，" Abaqus分析用户指南第10.4.3节](../usb/usb-link.md#usb-anl-acyclicsymmetry)
- ["子模型：概述，" Abaqus分析用户指南第10.2.1节](../usb/usb-link.md#usb-anl-asubmodeloverview)
- ["基于表面的子模型，" Abaqus分析用户指南第10.2.3节](../usb/usb-link.md#usb-anl-asubmodelstress)
- ["使用扩展有限元方法将不连续性建模为富集特征，" Abaqus分析用户指南第10.7.1节](../usb/usb-link.md#usb-anl-aenrichment)

### 应用分布载荷

### **循环对称模型在稳态动力学分析中的必需参数：**

CYCLIC MODE

将此参数设置为在当前稳态动力学过程中施加的载荷的循环对称模式号。

### **可选参数：**

AMPLITUDE

将此参数设置为振幅曲线的名称，该曲线定义步骤期间载荷大小的变化。

对于Abaqus/Standard中的均匀载荷类型，如果省略此参数，则参考值将在步骤开始时立即应用或线性地跨越步骤应用，具体取决于分配给 [*STEP](ch18abk36.md) 选项上 AMPLITUDE 参数的值（请参见["定义分析，" Abaqus分析用户指南第6.1.2节](../usb/usb-link.md#usb-anl-aover)）。如果在Abaqus/Explicit分析中省略此参数，则参考值将在步骤开始时立即应用。

对于在用户子程序 [`DLOAD`](../sub/sub-link.md#sub-xsl-dload) 中给出的非均匀载荷，振幅引用将在Abaqus/Standard分析中被忽略。振幅引用将在Abaqus/Explicit分析中传递到用户子程序 [`VDLOAD`](../sub/sub-link.md#sub-xsl-vdload)。

只有载荷大小随时间变化。静水压力载荷中的流体表面水平等量不会改变。

CONSTANT RESULTANT

如果表面牵引向量、边缘牵引向量或边缘力矩将在当前配置中的表面上积分，则设置 CONSTANT RESULTANT=NO（默认）。

如果表面牵引向量、边缘牵引向量或边缘力矩将在参考配置中的表面上积分，则设置 CONSTANT RESULTANT=YES。

CONSTANT RESULTANT 参数仅对均匀和非均匀表面牵引和边缘载荷（包括边缘力矩）有效；对于所有其他载荷类型将被忽略。

FOLLOWER

如果规定的牵引或壳边缘载荷在大位移分析中随表面或壳边缘旋转（活载荷），则设置 FOLLOWER=YES（默认）。

如果规定的牵引或边缘载荷在大位移分析中保持固定（死载荷），则设置 FOLLOWER=NO。

FOLLOWER 参数仅对牵引和边缘载荷标签 TRVEC、TRVECNU、EDLD 和 EDLDNU 有效；对于所有其他载荷标签将被忽略。

OP

设置 OP=MOD（默认）以保留现有的 [*DSLOAD](ch04abk42.md)s，此选项修改现有分布载荷或定义额外分布载荷。

如果应该移除模型上所有现有的 [*DSLOAD](ch04abk42.md)s，设置 OP=NEW。可以定义新的分布载荷。

ORIENTATION

将此参数设置为用于 [*ORIENTATION](ch15abk01.md) 选项（["方向，" Abaqus分析用户指南第2.2.5节](../usb/usb-link.md#usb-int-corientation)）的名称，用于指定在其中给出牵引或壳边缘载荷分量的局部坐标。

ORIENTATION 参数仅对牵引和边缘载荷标签 TRSHR、TRSHRNU、TRVEC、TRVECNU、EDLD 和 EDLDNU 有效；对于所有其他载荷标签将被忽略。

REF NODE

此参数仅适用于Abaqus/Explicit分析，仅在与参考节点处的速度一起使用时适用于粘性和滞止压力载荷。

将此参数设置为您包含参考节点的节点集合的名称或参考节点的节点编号。如果选择节点集合名称，则该节点集合必须恰好包含一个节点。如果省略此参数，则假定参考速度为零。

### **矩阵生成和稳态动力学分析（直接、模态或子空间）的可选、互斥参数：**

IMAGINARY

包含此参数以定义载荷的虚部（异相）。

REAL

包含此参数（默认）以定义载荷的实部（同相）。

### **定义分布表面压力的数据行：**

**第一行：**

根据需要重复此数据行，以定义不同表面上的分布载荷。

### **定义静水压力（Abaqus/Standard仅限）的数据行：**

**第一行：**

根据需要重复此数据行，以定义不同表面上的静水压力载荷。

### **定义一般表面牵引向量、表面剪切牵引向量或一般壳边缘牵引向量的数据行：**

**第一行：**

对于二维或轴对称分析，只需指定牵引向量方向的前两个分量。对于剪切牵引载荷标签 TRSHR 和 TRSHRNU，载荷方向通过将指定的牵引向量方向投影到参考配置中的表面上来计算。对于Abaqus/Standard中的非均匀载荷，大小和牵引向量方向必须在用户子程序 [`UTRACLOAD`](../sub/sub-link.md#sub-xsl-utracload) 中定义。如果给出，则大小和向量将在Abaqus/Standard分析中传递到用户子程序。

根据需要重复此数据行，以定义不同表面上的牵引向量。

### **定义表面法向牵引向量、壳边缘牵引向量（法向、横向或切向）或壳边缘力矩的数据行：**

**第一行：**

根据需要重复此数据行，以定义不同表面上的牵引向量。

### **定义滞止压力载荷（Abaqus/Explicit仅限）的数据行：**

**第一行：**

根据需要重复此数据行，以定义不同表面上的滞止压力载荷。

### **应用子模型边界条件（Abaqus/Standard仅限）**

### **必需参数：**

STEP

将此参数设置为全局分析中的步骤编号，在该步骤的子模型分析期间将读取驱动应力的值。

SUBMODEL

包含此参数以指定分布载荷是子模型分析中的"驱动载荷"。此选项中使用的表面必须列在 [*SUBMODEL](ch18abk38.md) 模型定义选项中。

### **可选参数：**

INC

此参数仅可用于静态线性扰动步骤（["一般和线性扰动过程，" Abaqus分析用户指南第6.1.3节](../usb/usb-link.md#usb-anl-alinearnonlinear)）。

将此参数设置为全局分析选定步骤中的增量，在该增量处将使用解来指定驱动应力的值。默认情况下，Abaqus/Standard使用选定步骤最后增量的解。

OP

设置 OP=MOD（默认）以保留现有的 [*DSLOAD](ch04abk42.md)s，此选项修改现有分布载荷或定义额外分布载荷。

如果应该移除模型上所有现有的 [*DSLOAD](ch04abk42.md)s，设置 OP=NEW。可以定义新的分布载荷。

### **定义子模型载荷的数据行：**

**第一行：**

根据需要重复此数据行，以指定不同表面上的子模型分布载荷。




