# 2.14.1 子结构与子结构分析

### 2.14.1 子结构与子结构分析

**产品：** Abaqus/Standard

![](../graphics/stm_eqn02501.gif)基本的子结构思想是分别考虑"子结构"（模型的一部分），并消除除了连接这部分到模型其余部分所需的自由度之外的所有自由度，以便子结构在模型中显示为"子结构"：一组有限单元，其响应由这些保留自由度（由向量![](../graphics/stm_eqn02501.gif)示）的刚度（和质量）定义。

![](../graphics/stm_eqn01621.gif)![](../graphics/stm_eqn02502.gif)![](../graphics/stm_eqn01077.gif)在Abaqus/Standard中，子结构内的响应一旦被缩减为子结构，就被认为是其成为子结构时状态上的线性摄动。因此，当子结构成为子结构时，它处于平衡状态，其应力为![](../graphics/stm_eqn01621.gif)位移为![](../graphics/stm_eqn02502.gif)以及其他状态变量![](../graphics/stm_eqn01077.gif)然后，每当它作为子结构响应时，子结构内某点处位移或应力分量的总值为

![](../graphics/stm_eqn02503.gif)![](../graphics/stm_eqn02504.gif)![](../graphics/stm_eqn02505.gif)![](../graphics/stm_eqn02506.gif)![](../graphics/stm_eqn02507.gif)![](../graphics/stm_eqn02508.gif)![](../graphics/stm_eqn02503.gif)中![](../graphics/stm_eqn02504.gif)![](../graphics/stm_eqn02505.gif)子结构保留自由度与所考虑位移或应力分量之间的线性变换。子结构在成为子结构时必须处于自平衡状态（除了施加到子结构内部自由度的规定边界条件上的反作用力）。如果子结构已被加载到以其一些保留自由度固定而导致的非零状态，这些约束在其成为子结构时被释放，它们上面的任何反作用力被转换为集中荷载，成为预荷载状态的一部分。这意味着子结构对模型整体平衡的贡献完全由其线性响应定义。由于子结构技术的目的是让子结构仅对保留自由度贡献项，我们需要定义其外部荷载向量![](../graphics/stm_eqn02506.gif)由施加到子结构的非零子结构荷载情况形成，以及其内力向量![](../graphics/stm_eqn02507.gif)作为保留变量![](../graphics/stm_eqn02508.gif)其速度和加速度的线性变换之和：

![](../graphics/stm_eqn02509.gif)![](../graphics/stm_eqn02510.gif)![](../graphics/stm_eqn02511.gif)![](../graphics/stm_eqn02512.gif)![](../graphics/stm_eqn02509.gif)们将![](../graphics/stm_eqn02510.gif)为子结构的缩减质量矩阵，![](../graphics/stm_eqn02511.gif)其缩减阻尼矩阵，![](../graphics/stm_eqn02512.gif)其缩减刚度。这些"缩减的"质量、阻尼和刚度矩阵仅连接保留自由度。

当仅考虑静态响应时，缩减刚度矩阵很容易推导。由于子结构的响应完全是线性的，其对模型虚功方程的贡献为

![](../graphics/stm_eqn02513.gif)![](../graphics/stm_eqn02514.gif)![](../graphics/stm_eqn02515.gif)![](../graphics/stm_eqn02513.gif)中![](../graphics/stm_eqn02514.gif)![](../graphics/stm_eqn02515.gif)在其作为子结构加载期间施加到子结构的一致节点力（它们不包括子结构的自平衡预加载）

![](../graphics/stm_eqn02516.gif)![](../graphics/stm_eqn02516.gif)其切线刚度矩阵。

![](../graphics/stm_eqn02517.gif)![](../graphics/stm_eqn02518.gif)由于子结构内部的自由度![](../graphics/stm_eqn02517.gif)出现在子结构内部，因此与上述虚功方程贡献中![](../graphics/stm_eqn02518.gif)轭的平衡方程在子结构内部是完整的，因此

![](../graphics/stm_eqn02519.gif)![](../graphics/stm_eqn02520.gif)![](../graphics/stm_eqn02519.gif)些方程可以重写为将![](../graphics/stm_eqn02520.gif)义为

![](../graphics/stm_eqn02521.gif)![](../graphics/stm_eqn02521.gif)此，子结构对静力平衡方程的贡献为

![](../graphics/stm_eqn02522.gif)![](../graphics/stm_eqn02522.gif)此，对于静态分析，子结构的缩减刚度为

![](../graphics/stm_eqn02523.gif)![](../graphics/stm_eqn02523.gif)加到子结构的子结构荷载情况的贡献为荷载向量

![](../graphics/stm_eqn02524.gif)![](../graphics/stm_eqn02524.gif)

![](../graphics/stm_eqn02525.gif)![](../graphics/stm_eqn02526.gif)![](../graphics/stm_eqn02527.gif)[方程2.14.1-1](02s14a50-Substructuring-and-substructure-analysis.md)定义的静态模态可能不足以准确描述子结构的动态响应。子结构的动态表示可以通过保留额外的自由度来改进，这些自由度不是连接子结构到模型其余部分所需的；即，一些![](../graphics/stm_eqn02525.gif)以移入![](../graphics/stm_eqn02526.gif)这项技术称为Guyan缩减。一种额外的且通常更有效的技术是通过包含与子结构固有模态相关的一些广义自由度![](../graphics/stm_eqn02527.gif)增强子结构内的响应。最简单的方法是从子结构中提取一些固有模态，同时约束所有保留自由度，使得[方程2.14.1-1](02s14a50-Substructuring-and-substructure-analysis.md)被增强为

![](../graphics/stm_eqn02528.gif)![](../graphics/stm_eqn02528.gif)分为

![](../graphics/stm_eqn02529.gif)![](../graphics/stm_eqn02529.gif)间导数为

![](../graphics/stm_eqn02530.gif)![](../graphics/stm_eqn02531.gif)![](../graphics/stm_eqn02527.gif)![](../graphics/stm_eqn02530.gif)![](../graphics/stm_eqn02531.gif)子结构的特征模态，在所有保留自由度被约束时获得，![](../graphics/stm_eqn02527.gif)广义位移——这些正常模态中响应的幅度。

子结构对动态情况虚功方程的贡献为

![](../graphics/stm_eqn02532.gif)![](../graphics/stm_eqn02532.gif)中

![](../graphics/stm_eqn02533.gif)![](../graphics/stm_eqn02533.gif)子结构的质量矩阵，

![](../graphics/stm_eqn02534.gif)![](../graphics/stm_eqn02535.gif)![](../graphics/stm_eqn02535.gif)子结构中的节点力向量。

![](../graphics/stm_eqn02520.gif)凭借子结构内假定的动态响应，此贡献中的内部自由度（![](../graphics/stm_eqn02520.gif)其时间导数）可以转换为保留自由度和正常模态振幅，将系统缩减为

![](../graphics/stm_eqn02536.gif)![](../graphics/stm_eqn02536.gif)中

![](../graphics/stm_eqn02537.gif)![](../graphics/stm_eqn02538.gif)![](../graphics/stm_eqn02539.gif)![](../graphics/stm_eqn01118.gif)![](../graphics/stm_eqn02540.gif)![](../graphics/stm_eqn02537.gif)中![](../graphics/stm_eqn02538.gif)特征向量矩阵，![](../graphics/stm_eqn02539.gif)广义自由度向量，![](../graphics/stm_eqn01118.gif)单位矩阵，![](../graphics/stm_eqn02541.gif)![](../graphics/stm_eqn02542.gif)![](../graphics/stm_eqn02543.gif)![](../graphics/stm_eqn02544.gif)![](../graphics/stm_eqn02545.gif)![](../graphics/stm_eqn02546.gif)大旋转子结构首先需要计算与子结构运动相关的等效刚体旋转矩阵![](../graphics/stm_eqn02541.gif)由于子结构仅表现出小变形，可以使用两个节点在二维分析中或三个节点在三维分析中的原始位置和当前位置来计算两个矩形局部系统，然后计算旋转矩阵。例如，在三维中，Abaqus/Standard使用原始配置中的三个节点计算一个参考（平均）点。第一个单位方向向量![](../graphics/stm_eqn02544.gif)单地是第三和第一方向的叉乘。在当前位置中重复该过程以计算局部系统![](../graphics/stm_eqn02545.gif)然后旋转矩阵可以容易地计算为![](../graphics/stm_eqn02546.gif)

![](../graphics/stm_eqn02541.gif)![](../graphics/stm_eqn02541.gif)Abaqus/Standard自动从子结构的保留节点中选择用于计算旋转矩阵![](../graphics/stm_eqn02541.gif)两个或三个节点。在大多数情况下，只有至少保留所有平移自由度的保留节点才有资格。例如，在三维分析中，用于等效刚体计算的第一个节点被选择为子结构中刚度最大（对角线值最大）的节点。第二个节点被选择为与第一个节点相距最远的保留节点，条件是其节点刚度足够高（至少为第一个节点刚度的0.01%）。第三个节点被选择为与第一和第二个节点定义的线距离最大的保留节点（与第二个节点相同的刚度要求）。在极少数情况下，当保留的有效候选节点少于三个（在三维分析中）时，![](../graphics/stm_eqn02541.gif)阵直接从具有所有旋转自由度保留的最刚性节点的节点旋转计算。

![](../graphics/stm_eqn02547.gif)为了计算与大旋转子结构相关的内力，Abaqus/Standard通过从子结构的节点位移/旋转"减去"刚体运动来计算应变引起的位移/旋转。对于平移自由度，节点处的应变引起位移![](../graphics/stm_eqn02547.gif)以使用

![](../graphics/stm_eqn02548.gif)![](../graphics/stm_eqn02549.gif)![](../graphics/stm_eqn02550.gif)![](../graphics/stm_eqn02551.gif)![](../graphics/stm_eqn02552.gif)![](../graphics/stm_eqn02553.gif)![](../graphics/stm_eqn02548.gif)算，其中![](../graphics/stm_eqn02549.gif)![](../graphics/stm_eqn02550.gif)节点的原始和当前位置，![](../graphics/stm_eqn02551.gif)![](../graphics/stm_eqn02552.gif)平均点的原始和当前坐标（按上述计算）。对于旋转自由度，节点处的总旋转矩阵（![](../graphics/stm_eqn02553.gif)是应变引起旋转矩阵与刚体旋转之间的复合旋转

![](../graphics/stm_eqn02554.gif)![](../graphics/stm_eqn02555.gif)![](../graphics/stm_eqn02554.gif)后可以容易地提取应变引起旋转![](../graphics/stm_eqn02555.gif)因此，子结构中的内力可以写为

![](../graphics/stm_eqn02556.gif)![](../graphics/stm_eqn02556.gif)中

![](../graphics/stm_eqn02557.gif)![](../graphics/stm_eqn02557.gif)刚体旋转刚度矩阵，

![](../graphics/stm_eqn02558.gif)![](../graphics/stm_eqn02558.gif)应变引起位移-旋转向量。

类似地，在动力学中，缩减质量（包括节点位移/旋转与特征模态贡献之间的耦合）在任何质量贡献被包含在子结构相关的虚功中之前被刚体旋转。
### 固定方向重力荷载

![](../graphics/stm_eqn02541.gif)![](../graphics/stm_eqn02559.gif)![](../graphics/stm_eqn02560.gif)![](../graphics/stm_eqn02561.gif)当定义了在固定方向上作用的重力荷载时，Abaqus/Standard将在生成级别内部创建若干荷载情况（二维分析中为两个，三维分析中为三个），对应于子结构方向上的单位重力荷载。在使用级别，首先使用子结构![](../graphics/stm_eqn02541.gif)总旋转矩阵（包括用户指定的旋转/镜像和非线性几何分析中子结构的旋转）将用户指定的单位方向![](../graphics/stm_eqn02559.gif)转回来。因此，用户指定的方向现在在子结构相关的局部（旋转）系统中表示（![](../graphics/stm_eqn02560.gif)然后，内部生成的单位荷载情况按![](../graphics/stm_eqn02561.gif)量和适当的幅值和振幅进行缩放，然后添加到模型中的外力。
### 参考

### 参考

"Abaqus Analysis User's Guide"第10.1节"子结构"
