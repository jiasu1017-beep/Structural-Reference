# 3.5.3 Euler-Bernoulli梁单元

### 3.5.3 Euler-Bernoulli梁单元

**产品：** Abaqus/Standard

在这些单元中，假定内部虚功率仅与轴向应变和扭转剪切相关。此外，假定横截面在其平面内不变形或在其平面外翘曲，并且这个横截面平面保持垂直于梁轴线。这些是Euler-Bernoulli梁理论的经典假设，为细长梁提供了令人满意的结果。

设![](../graphics/stm_eqn03804.gif)是材料坐标，使得*S*定位梁轴线上的点，![](../graphics/stm_eqn03805.gif)测量横截面中的距离。此外，设![](../graphics/stm_eqn03806.gif)是垂直于当前配置中梁轴线的单位向量：![](../graphics/stm_eqn03807.gif)。那么梁上一点在当前配置中的位置为

![](../graphics/stm_eqn03808.gif)其中![](../graphics/stm_eqn03809.gif)是包含![](../graphics/stm_eqn03810.gif)的截面梁轴线上的点。那么

![](../graphics/stm_eqn03811.gif)因此，在![](../graphics/stm_eqn03804.gif)处的纤维长度在当前配置中测量为

![](../graphics/stm_eqn03812.gif)现在由于梁是细长的，我们将忽略*g*和*h*（横截面中测量距离的材料坐标）的二阶项。因此，

![](../graphics/stm_eqn03813.gif)
### 应变度量

与轴向应力相关的内部虚功率为

![](../graphics/stm_eqn03814.gif)其中![](../graphics/stm_eqn03815.gif)和![](../graphics/stm_eqn03816.gif)是在梁的点![](../graphics/stm_eqn03804.gif)处与轴向变形相关的任何材料应力和应变度量，因为假定应变很小。为此，我们将使用Green应变，所以

![](../graphics/graphics/stm_eqn03817.gif)其中![](../graphics/stm_eqn03818.gif)是当前配置长度与纤维轴向上参考配置长度之比的平方。从[公式3.5.3-1](03s05a75.md)及其在参考配置中的等价物，我们有

![](../graphics/stm_eqn03819.gif)同样，由于细长假设忽略*g*和*h*中除一阶外的所有项，这变为

![](../graphics/stm_eqn03820.gif)其中

![](../graphics/stm_eqn03821.gif)这简化了我们能够将内部虚功率写成与轴向应力相关为

![](../graphics/stm_eqn03822.gif)其中

![](../graphics/stm_eqn03823.gif)具有

![](../graphics/stm_eqn03824.gif)和

![](../graphics/stm_eqn03825.gif)现在横截面基向量![](../graphics/stm_eqn03500.gif)和![](../graphics/stm_eqn03501.gif)假定保持垂直于梁轴线，所以

![](../graphics/stm_eqn03826.gif)因此，

![](../graphics/stm_eqn03827.gif)所以我们有

![](../graphics/stm_eqn03828.gif)和

![](../graphics/stm_eqn03829.gif)

这定义了与轴向拉伸相关的广义应变。对于扭转应变，内部虚功率为

![](../graphics/stm_eqn03830.gif)其中

![](../graphics/stm_eqn03831.gif)![](../graphics/stm_eqn03741.gif)是剪切应变与扭转应变之间的比例常数（详见"梁单元公式，" 第3.5.2节）。为计算简单，扭转应变的形式取为

![](../graphics/stm_eqn03832.gif)其中

![](../graphics/stm_eqn03833.gif)和

![](../graphics/stm_eqn03834.gif)这假定旋转![](../graphics/stm_eqn03835.gif)沿梁线性插值。因此，这些梁的广义应变度量为

![](../graphics/stm_eqn00377.gif)

轴向应变，

![](../graphics/stm_eqn03836.gif)和![](../graphics/stm_eqn03837.gif)

梁曲率变化度量，和

![](../graphics/stm_eqn03838.gif)

扭转应变。有了这些度量，内部虚功率可以写成

![](../graphics/stm_eqn03839.gif)
### 内部虚功率Jacobian

对于总体牛顿法的Jacobian矩阵，[公式2.1.1-3](02s01a13.md)，必须形成关于节点位移变分的内部功变分的变分。本构理论写成

![](../graphics/stm_eqn03840.gif)所以

![](../graphics/stm_eqn03841.gif)

![](../graphics/stm_eqn03842.gif)其中![](../graphics/stm_eqn03843.gif)是通过横截面积分获得的截面刚度矩阵。有关截面积分的更多信息，请参见"梁单元公式，" 第3.5.2节。
### 应变的一阶变分

取上述应变定义的变分直接给出

![](../graphics/stm_eqn03844.gif)在这些表达式中，我们需要![](../graphics/stm_eqn03845.gif)和![](../graphics/stm_eqn03846.gif)以及![](../graphics/stm_eqn03847.gif)；这些现在被推导。从![](../graphics/stm_eqn03848.gif)的表达式，即

![](../graphics/stm_eqn03849.gif)另一个垂直于切线的辅助向量![](../graphics/stm_eqn03850.gif)定义为

![](../graphics/stm_eqn03851.gif)使得

![](../graphics/stm_eqn03852.gif)此外，

![](../graphics/stm_eqn03853.gif)所以

![](../graphics/stm_eqn03854.gif)由于![](../graphics/stm_eqn03855.gif)形成正交标架，

![](../graphics/stm_eqn03856.gif)因为![](../graphics/stm_eqn03857.gif)。从![](../graphics/stm_eqn03858.gif)的定义，可以直接表明

![](../graphics/stm_eqn03859.gif)所以

![](../graphics/stm_eqn03860.gif)和

![](../graphics/stm_eqn03861.gif)因此，

![](../graphics/stm_eqn03862.gif)我们还可以写成

![](../graphics/stm_eqn03863.gif)和

![](../graphics/stm_eqn03864.gif)适当组合项，

![](../graphics/stm_eqn03865.gif)因此，从[公式3.5.3-2](03s05a75.md)

![](../graphics/stm_eqn03866.gif)以类似方式，可以表明

![](../graphics/stm_eqn03867.gif)应变的一阶变分变为

![](../graphics/stm_eqn03868.gif)所以

![](../graphics/stm_eqn03869.gif)此外，

![](../graphics/stm_eqn03853.gif)所以

![](../graphics/stm_eqn03870.gif)因为![](../graphics/stm_eqn03871.gif)形成正交标架，

![](../graphics/stm_eqn03872.gif)因为

![](../graphics/stm_eqn03873.gif)
### 应变的二阶变分

轴向应变的二阶变分简单地为

![](../graphics/stm_eqn03874.gif)为了计算弯曲应变的二阶变分，我们需要![](../graphics/stm_eqn03875.gif)的表达式。这些通过近似

![](../graphics/stm_eqn03876.gif)获得，由此

![](../graphics/stm_eqn03877.gif)使用这些表达式，弯曲应变的二阶变分写成

![](../graphics/stm_eqn03878.gif)和

![](../graphics/stm_eqn03879.gif)对于扭转应变对初始应力矩阵的贡献，我们近似

![](../graphics/stm_eqn03880.gif)这个矩阵再次是非对称的。
### 插值

在虚功方程中，应变包括位移的二阶导数。因此，需要旋转以及位移的连续性，使得Hermite多项式插值函数成为所需的最小插值阶数。这里使用这些函数。Hermite三次方程用区间端点处的函数值及其导数写成：

![](../graphics/stm_eqn03881.gif)节点1在![](../graphics/stm_eqn03882.gif)，节点2在![](../graphics/stm_eqn03450.gif)。

这些函数在Abaqus中用于插值位移分量![](../graphics/stm_eqn02547.gif)和初始位置向量![](../graphics/stm_eqn02550.gif)，因此单元基本上是等参的。此外，![](../graphics/stm_eqn03883.gif)关于梁轴线![](../graphics/stm_eqn03884.gif)的旋转是线性插值的。这种插值对用户来说是不令人满意的，因为节点变量是

![](../graphics/stm_eqn03885.gif)这些变量的最后四个是很难处理的；此外，使它们在共享同一节点的所有单元中相同会导致这些单元中轴向拉伸的过度约束，特别是如果梁轴线通过节点不连续，如在框架结构或"T" junction中。

为避免这个困难，采用以下过程。在节点处，梁轴线的切线为

![](../graphics/stm_eqn03886.gif)所以

![](../graphics/stm_eqn03887.gif)现在假设我们存储为节点处的自由度，

![](../graphics/stm_eqn03888.gif)其中![](../graphics/stm_eqn03889.gif)是上面介绍的旋转定义。由于初始几何形状从而![](../graphics/stm_eqn00553.gif)是已知的，即梁轴线的初始方向，![](../graphics/stm_eqn03890.gif)其中![](../graphics/stm_eqn00162.gif)是由![](../graphics/stm_eqn03889.gif)定义的旋转矩阵，因此

![](../graphics/stm_eqn03891.gif)由这些变量和初始几何定义。此外，![](../graphics/stm_eqn03884.gif)可直接从![](../graphics/stm_eqn03889.gif)和![](../graphics/stm_eqn00479.gif)获得。因此，上述集合是一组令人满意的节点变量。为了消除不需要的轴向应变约束，在Abaqus中，每个这种单元的节点处的拉伸![](../graphics/stm_eqn03892.gif)被作为单元的内部变量（为此创建了第三个内部节点，因此它不与相邻单元共享。）

应该指出，上述变换（[公式3.5.3-3](03s05a75.md)）是非线性的。这导致一些复杂性——例如，d'Alembert力不再具有简单形式![](../graphics/stm_eqn03893.gif)，而是矩阵![](../graphics/stm_eqn03894.gif)替换![](../graphics/stm_eqn03895.gif)，其中![](../graphics/stm_eqn03896.gif)和![](../graphics/stm_eqn03897.gif)使用变换（[公式3.5.3-3](03s05a75.md)）及其适当的时间导数。所得Jacobian是非对称的；Abaqus忽略非对称项。
### 积分

横截面积分已在剪切梁的背景下讨论过——对这些梁来说是一样的。沿梁轴线，积分方案如下所述。

**刚度和内力**

使用三个Gauss点。两个Gauss点是不够的，因为扭转应变不是独立的。

**质量和分布载荷**

使用三个Gauss点。旋转惯性不包括在质量中，除了关于梁轴线的截面旋转，但在完全直梁中为避免奇异性而包括它。
### 参考

### 参考

"Abaqus Analysis User's Guide"第29.3.1节"梁建模：概述"
