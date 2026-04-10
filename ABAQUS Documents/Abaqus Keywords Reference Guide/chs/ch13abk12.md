# *MATRIX GENERATE









### *MATRIX GENERATE生成全局或单元矩阵。

此选项用于生成表示模型中刚度矩阵、质量矩阵、粘性阻尼矩阵、结构阻尼矩阵或荷载向量的矩阵。

**产品：**Abaqus/Standard  

**类型：**历史数据  

**级别：**步骤

##### **参考：**

- ["生成矩阵，" Abaqus Analysis User's Guide第10.3.1节](../usb/usb-link.md#usb-anl-amtxgenerationperturbation)

### **至少需要以下参数之一：**

STIFFNESS

包含此参数以生成刚度矩阵。

MASS

包含此参数以生成质量矩阵。

VISCOUS DAMPING

包含此参数以生成粘性阻尼矩阵。

STRUCTURAL DAMPING

包含此参数以生成结构阻尼矩阵。

LOAD

包含此参数以生成荷载矩阵。

### **如果模型包含实体连续无限单元，则需要以下参数：**

SOLID INFINITE FORMULATION

将此参数设置为STATIC以选择实体无限单元的静态公式。

将此参数设置为DYNAMIC以选择实体无限单元的动态公式。

### **可选参数：**

ELEMENT BY ELEMENT

包含此参数以生成局部单元矩阵。默认情况下，生成全局组装矩阵。

ELSET

使用此参数为模型的一部分生成矩阵。将此参数设置为包含模型所选部分中所有元素的元素集名称。默认情况下，为整个模型生成矩阵。

FIELD

设置FIELD=ALL（默认）以指示为模型的结构和声学部分生成矩阵。

设置FIELD=MECHANICAL以指示仅为模型的结构部分生成矩阵。

设置FIELD=ACOUSTIC以指示仅为模型的声学部分生成矩阵。

MPC

设置MPC=YES（默认）以使用施加的多点约束生成矩阵。生成的矩阵将仅包含独立自由度对应的条目。

设置MPC=NO以在矩阵生成期间跳过应用多点约束。矩阵将包含模型中所有活动自由度对应的条目。

PROPERTY EVALUATION

将此参数设置为在矩阵生成期间评估粘弹性、弹簧和阻尼器频率相关属性的频率。如果省略此参数，Abaqus/Standard将在零频率下评估与频率相关弹簧和阻尼器相关的刚度，并且不会考虑频域粘弹性的刚度贡献。

PUBLIC NODES

使用此参数指定哪些节点将在矩阵使用模型中可见。将此参数设置为包含将在矩阵输入期间作为用户定义节点呈现的所有节点的节点集名称；所有其他节点被指定为内部节点并被有效地隐藏。默认情况下，所有用户定义节点在矩阵使用模型中可见。

SOURCE

设置SOURCE=ALL（默认）以生成包括来自有限元和矩阵输入贡献的矩阵。

设置SOURCE=ELEMENTS以生成仅包括来自有限元的贡献的矩阵。

设置SOURCE=MATRIX INPUT以生成仅包括来自矩阵输入的贡献的矩阵。ELSET和SOURCE=MATRIX INPUT参数是互斥的。

**此选项没有关联的数据行。**