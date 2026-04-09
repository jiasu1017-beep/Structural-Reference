# 3.2.8 轴对称单元

### 3.2.8 轴对称单元

**产品：** Abaqus/Standard  Abaqus/Explicit

Abaqus包含两个实体单元库，CAX和CGAX，其几何形状是轴对称的（旋转体），可以承受轴对称加载条件。此外，CGAX单元支持扭转加载。因此，CGAX单元被称为广义轴对称单元，CAX单元被称为无扭转轴对称单元。在两种情况下，旋转体通过将平面横截面绕轴（对称轴）旋转而生成，可以用柱面极坐标*r*、*z*和![](../graphics/stm_eqn01111.gif)容易地描述。该横截面上一点的位置用径向坐标*r*和轴向坐标*z*表示。在![](../graphics/stm_eqn03054.gif)处，径向和轴向坐标与全局笛卡尔*X*-和*Y*-坐标重合。

如果载荷由独立于![](../graphics/stm_eqn01111.gif)的径向和轴向分量组成，且材料是各向同性或正交各向异性的，![](../graphics/stm_eqn01111.gif)是主材料方向，则任何点的位移将仅具有径向（![](../graphics/stm_eqn03055.gif)）和轴向（![](../graphics/stm_eqn03056.gif)）分量，唯一非零的应力分量将是![](../graphics/stm_eqn03057.gif)、![](../graphics/stm_eqn03058.gif)、![](../graphics/stm_eqn03059.gif)和![](../graphics/stm_eqn03060.gif)。此外，任何*r*—*z*平面的变形完全定义了物体中的应力和应变状态。因此，几何模型通过在![](../graphics/stm_eqn03054.gif)处离散参考横截面来描述。

如果允许载荷有周向分量（独立于![](../graphics/stm_eqn01111.gif)）且材料为一般各向异性，位移和应力场变为三维的，但问题保持轴对称，因为解不随![](../graphics/stm_eqn01111.gif)变化，参考*r*—*z*横截面的变形仍然表征整个物体中的变形。任何点的运动除了上述径向和轴向位移外，还有关于*z*轴的扭转![](../graphics/stm_eqn00155.gif)（弧度），它独立于![](../graphics/stm_eqn01111.gif)。

本节描述广义轴对称单元的公式。无扭转轴对称单元的公式是此公式的一个子集。
### 运动学描述

与两类单元一起使用的坐标系是柱面坐标系（*r*、*z*、![](../graphics/stm_eqn01111.gif)），其中*r*测量点到柱面系统轴的距离，*z*测量其沿该轴的位置，![](../graphics/stm_eqn01111.gif)测量包含该点和坐标系统轴的平面与包含坐标系统轴的某个固定参考平面之间的角度。这些单元中坐标和位移的顺序基于*z*是第二个坐标的约定。这个顺序与Abaqus中三维单元使用的顺序不同，其中*z*是第三个坐标，也不是柱面系统中通常使用的顺序（*r*、![](../graphics/stm_eqn01111.gif)、*z*）。

设![](../graphics/stm_eqn03061.gif)、![](../graphics/stm_eqn03062.gif)和![](../graphics/stm_eqn03063.gif)是点在未变形状态下沿径向、轴向和周向的单位向量，如图[图3.2.8-1](03s02a66.md)所示。

图3.2.8-1 柱面坐标系和位置向量定义。

![](../graphics/stmcylsys.png)点的参考位置![](../graphics/stm_eqn00141.gif)可以用原始半径*R*和轴向位置*Z*表示：

![](../graphics/stm_eqn03064.gif)同样，设![](../graphics/stm_eqn03065.gif)、![](../graphics/stm_eqn03066.gif)和![](../graphics/stm_eqn03067.gif)是点在变形状态下沿径向、轴向和周向的单位向量。如[图3.2.8-1](03s02a66.md)所示，径向和周向基向量依赖于![](../graphics/stm_eqn01111.gif)坐标：![](../graphics/stm_eqn03068.gif)和![](../graphics/stm_eqn03069.gif)。点的当前位置![](../graphics/stm_eqn00117.gif)可以用当前半径*r*和当前轴向位置*z*表示：

![](../graphics/stm_eqn03070.gif)

一点的广义轴对称运动可以描述为

![](../graphics/stm_eqn03071.gif)如上所述，自由度![](../graphics/stm_eqn03072.gif)、![](../graphics/stm_eqn03056.gif)和![](../graphics/stm_eqn03073.gif)独立于![](../graphics/stm_eqn03074.gif)。此外，感兴趣的参考横截面在![](../graphics/stm_eqn03075.gif)，但为了后续数学分析的利益，![](../graphics/stm_eqn03076.gif)在上述![](../graphics/stm_eqn03077.gif)的表达式中必须是非零的很重要。
### 参数插值和积分

运动使用以下参数插值方案：

![](../graphics/stm_eqn03078.gif)其中*g*、![](../graphics/stm_eqn03079.gif)是参考![](../graphics/stm_eqn03080.gif)—*z*横截面在![](../graphics/stm_eqn03075.gif)中的参数坐标，![](../graphics/stm_eqn03081.gif)、![](../graphics/stm_eqn03082.gif)、![](../graphics/stm_eqn03083.gif)是节点自由度。插值函数![](../graphics/stm_eqn02852.gif)是"实体等参四边形和六面体，" 第3.2.4节中描述的那些，其中也讨论了等参实体单元的积分方案。
### 变形梯度

对于空间中的材料点，变形梯度![](../graphics/stm_eqn00319.gif)定义为当前位置![](../graphics/stm_eqn00117.gif)相对于原始位置![](../graphics/stm_eqn00141.gif)的梯度：

![](../graphics/stm_eqn03084.gif)当前位置![](../graphics/stm_eqn00117.gif)由[公式3.2.8-1](03s02a66.md)给出，梯度算子可以用相对于柱面坐标的偏导数来描述：

![](../graphics/stm_eqn03085.gif)由于径向和周向基向量依赖于原始周向坐标![](../graphics/stm_eqn01111.gif)，这些基向量相对于![](../graphics/stm_eqn01111.gif)的偏导数是非零的：

![](../graphics/stm_eqn03086.gif)因此，链式法则允许我们写成

![](../graphics/stm_eqn03087.gif)利用这些结果，获得变形梯度为

![](../graphics/stm_eqn03088.gif)

或者，可以写成矩阵形式

![](../graphics/stm_eqn03089.gif)其中[公式3.2.8-2](03s02a66.md)给出的运动被明确使用。

类似地，逆变形梯度![](../graphics/stm_eqn03090.gif)容易获得为

![](../graphics/stm_eqn03091.gif)
### 虚功

如"平衡和虚功，" 第1.5.1节所讨论的，平衡（虚功）公式需要虚速度梯度![](../graphics/stm_eqn03092.gif)，这是相对于当前状态的位置梯度的变分。这个张量为

![](../graphics/stm_eqn03093.gif)其中![](../graphics/stm_eqn03094.gif)是线性化变形梯度。

Abaqus用相对于轴对称扭转自由度的固定空间基来公式化有限元方程。因此，[公式3.2.8-4](03s02a66.md)中![](../graphics/stm_eqn03094.gif)所需的结果不能简单地遵循[公式3.2.8-3](03s02a66.md)的线性化得到。也就是说，有必要消除来自变分

![](../graphics/stm_eqn03095.gif)的贡献。为此，![](../graphics/stm_eqn00319.gif)可以按以下方式修改

![](../graphics/stm_eqn03096.gif)其中![](../graphics/stm_eqn03097.gif)瞬时是![](../graphics/stm_eqn03097.gif)，但其变分为

![](../graphics/stm_eqn03098.gif)其中![](../graphics/stm_eqn03099.gif)是相对于![](../graphics/stm_eqn03075.gif)处基![](../graphics/stm_eqn03101.gif)、![](../graphics/stm_eqn03066.gif)和![](../graphics/stm_eqn03067.gif)的反对称分量

![](../graphics/stm_eqn03100.gif)。

通过这种修改，共旋转虚变形梯度给出为

![](../graphics/stm_eqn03102.gif)共旋转虚速度梯度为

![](../graphics/stm_eqn03103.gif)或

![](../graphics/stm_eqn03104.gif)

修正虚变形率张量和自旋简单地为

![](../graphics/stm_eqn03105.gif)
### 当前状态的刚度

如"过程：概述和基本方程，" 第2.1.1节所示，内部功项对Abaqus/Standard中用于实体单元公式的牛顿法Jacobian矩阵的贡献是

![](../graphics/stm_eqn03106.gif)![](../graphics/stm_eqn03107.gif)的二阶变分获得为

![](../graphics/stm_eqn03108.gif)其中![](../graphics/stm_eqn03109.gif)与[公式3.2.8-5](03s02a66.md)中![](../graphics/stm_eqn03110.gif)具有相同的形式。此外，在这个公式中![](../graphics/stm_eqn03111.gif)是非零的，可以利用"旋转变量，" 第1.3.1节证明![](../graphics/stm_eqn03112.gif)具有形式

![](../graphics/stm_eqn03113.gif)分量形式为

![](../graphics/stm_eqn03114.gif)引入共旋转应力率

![](../graphics/stm_eqn03115.gif)得到更熟悉的形式

![](../graphics/stm_eqn03116.gif)
### 参考

### 参考

"Abaqus Analysis User's Guide"第28.1.6节"轴对称实体单元库"
