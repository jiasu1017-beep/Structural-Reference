# 15.2 Abaqus选项的变更





本节总结了在对定义Abaqus模型的选项所做的更改和添加。

| **mod** | **(E)** | [*ADAPTIVE MESH REFINEMENT](../key/key-link.md#usb-kws-hadaptivemeshrefinement) |
| --- | --- | --- |
|  |  | 使用新的COARSENING参数来指定一旦不再满足细化标准是否可以移除细化。 |
| **mod** | **(S)(E)(C)** | [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
|  |  | DEFINITION参数现在可用于通过与逻辑建模程序的协同仿真来定义振幅。 |
| **new** | **(S)** | [*BEAM SECTION OFFSET](../key/key-link.md#usb-kws-mbeamsectionoffset) |
|  |  | 定义梁截面原点的偏移。 |
| **mod** | **(S)** | [*BOUNDARY](../key/key-link.md#usb-kws-hboundary) |
|  |  | PHANTOM参数现在可以设置为EDGE，以将边界条件应用于富集元素中位于单元边缘的虚拟节点。 |
| **mod** | **(S)** | [*CFLOW](../key/key-link.md#usb-kws-hcflow) |
|  |  | PHANTOM参数现在可用于将集中流动应用于富集元素中位于单元边缘或与指定真实节点重合的虚拟节点。 |
| **new** | **(E)** | [*CHARACTERISTIC LENGTH](../key/key-link.md#usb-kws-mcharacteristiclength) |
|  |  | 在材料点定义特征单元长度。 |
| **mod** | **(S)** | [*CONTACT OUTPUT](../key/key-link.md#usb-kws-hcontactoutput) |
|  |  | SURFACE参数现在在Abaqus/Standard中可用于富集元素中裂纹表面之间的小滑动接触。 |
| **mod** | **(S)(E)** | [*CO-SIMULATION](../key/key-link.md#usb-kws-hcosimulation) |
|  |  | PROGRAM参数不再设置为LOGICAL值用于与Dymola的协同仿真。现在使用PROGRAM=MULTIPHYSICS用于Dymola协同仿真。 |
| **mod** | **(S)** | [*CREEP](../key/key-link.md#usb-kws-mcreep) |
|  |  | LAW参数现在可以设置为选择Anand定律、Darveaux定律或双功率定律。 |
| **mod** | **(S)(E)** | [*DAMAGE INITIATION](../key/key-link.md#usb-kws-mdamageinitiation) |
|  |  | R CRACK DIRECTION参数可用于计算用于获得裂纹扩展方向的平均应力/应变。 |
| **new** | **(E)** | [*DOMAIN DECOMPOSITION](../key/key-link.md#usb-kws-mdomaindecomp) |
|  |  | 定义域分解的区域和/或定义域分解上的约束。 |
| **mod** | **(S)(E)** | [*ELASTIC](../key/key-link.md#usb-kws-melastic) |
|  |  | COMPRESSION FACTOR参数现在可用于为非耦合牵引-分离弹性行为定义拉伸和压缩中的不同弹性模量。 |
| **mod** | **(S)(E)** | [*FASTENER](../key/key-link.md#usb-kws-mfastener) |
|  |  | ATTACHMENT METHOD现在可以采用CONNECTORDIRECTION值，以基于与紧固件相关联的连接器元素的轴向方向在相应表面上建立紧固点。 |
| **mod** | **(E)** | [*FILTER](../key/key-link.md#usb-kws-mfilter) |
|  |  | INVARIANT参数现在可以采用MAXP、INTERMP和MINP值，以分别将滤波应用于最大主应力、中间主应力或最小主应力。 |
| **new** | **(S)** | [*FLEXIBLE BODY](../key/key-link.md#usb-kws-hflexiblebody) |
|  |  | 从子结构生成柔性体。 |
| **mod** | **(S)** | [*FLUID CAVITY](../key/key-link.md#usb-kws-mfluidcavity) |
|  |  | ADDED VOLUME参数现在在Abaqus/Standard中可用。 |
| **mod** | **(S)(E)** | [*INITIAL CONDITIONS](../key/key-link.md#usb-kws-minitialcond) |
|  |  | TYPE参数现在支持新值DAMAGE INITIATION。新参数CRITERION可以设置为DUCTILE、SHEAR或MSFLD，以指定提供初始度量的损伤起始准则。 |
| **new** | **(S)** | [*MATRIX CHECK](../key/key-link.md#usb-kws-hmatrixcheck) |
|  |  | 检查生成的刚度矩阵和质量矩阵的质量。 |
| **mod** | **(S)** | [*MATRIX GENERATE](../key/key-link.md#usb-kws-hmatrixgenerate) |
|  |  | 使用新的可选FIELD、MPC和SOURCE参数来指示是否为模型的结构或声学部分生成矩阵，在矩阵生成期间应用多点约束，以及分别生成包括来自有限元或来自矩阵输入的贡献的矩阵。 |
| **mod** | **(C)** | [*TURBULENCE MODEL](../key/key-link.md#usb-kws-hturbulence) |
|  |  | TYPE参数现在可以设置为指定可实现的 ![](../graphics/rnb_eqn00007.gif)-![](../graphics/rnb_eqn00001.gif) 湍流模型。 |
| **mod** | **(S)** | [*USER MATERIAL](../key/key-link.md#usb-kws-musermaterial) |
|  |  | 新的HYBRID FORMULATION参数现在在Abaqus/Standard中可用。它可以设置为TOTAL或INCOMPRESSIBLE，以定义几乎不可压缩或不可压缩的非线性弹性用户材料响应。 |
| **mod** | **(S)(E)** | [*VISCOELASTIC](../key/key-link.md#usb-kws-mviscoelast) |
|  |  | LAW参数现在可以设置为选择幂律模型。 |
| **mod** | **(S)** | [*VISCOUS](../key/key-link.md#usb-kws-mviscous) |
|  |  | LAW参数可以设置为选择Anand定律、Darveaux定律或双功率定律。 |




