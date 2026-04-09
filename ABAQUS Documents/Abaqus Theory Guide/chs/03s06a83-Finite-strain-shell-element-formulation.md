# 3.6.5 有限应变壳单元公式

### 3.6.5 有限应变壳单元公式

![](../graphics/stm_eqn04406.gif)![](../graphics/stm_eqn04404.gif)![](../graphics/stm_eqn04405.gif)![](../graphics/stm_eqn04408.gif)![](../graphics/stm_eqn04407.gif)![](../graphics/stm_eqn04242.gif)![](../graphics/stm_eqn00156.gif)![](../graphics/stm_eqn03570.gif)![](../graphics/stm_eqn04240.gif)**产品：** Abaqus/Standard  Abaqus/Explicit

本节描述四边形有限膜应变单元S4R、三角形单元S3R和通过S4R退化获得的S3，以及完全积分的有限膜应变单元S4的公式。
### 几何描述

在壳变形历史的给定阶段，壳中材料点的位置定义为

![](../graphics/stm_eqn04193.gif)其中下标*i*和其他罗马下标范围为1到3。下标![](../graphics/stm_eqn00904.gif)和其他小写希腊下标描述壳参考表面中的量，范围为1到2。在上述方程中，![](../graphics/stm_eqn04194.gif)是壳参考表面的法线。位置梯度为

![](../graphics/stm_eqn04195.gif)其中我们忽略了![](../graphics/stm_eqn04196.gif)相对于![](../graphics/stm_eqn04197.gif)的导数。注意在上述中，![](../graphics/stm_eqn04198.gif)是局部表面坐标，假定在参考状态下是正交和距离测量的。![](../graphics/stm_eqn04199.gif)是厚度方向的坐标，在参考状态中垂直于![](../graphics/stm_eqn04198.gif)的距离测量和正交。厚度增加因子![](../graphics/stm_eqn04196.gif)假定独立于![](../graphics/stm_eqn04199.gif)。

在变形状态中，我们定义局部、正交壳方向![](../graphics/stm_eqn04200.gif)，使得

![](../graphics/stm_eqn04201.gif)其中![](../graphics/stm_eqn02353.gif)是Kronecker delta，![](../graphics/stm_eqn00064.gif)是2阶单位张量。对重复下标使用求和约定。位置梯度的面内分量获得为

![](../graphics/stm_eqn04202.gif)其中我们引入了参考表面变形梯度

![](../graphics/stm_eqn04203.gif)和参考表面法线梯度

![](../graphics/stm_eqn04204.gif)

在原始（参考）配置中，我们用![](../graphics/stm_eqn00141.gif)（参考表面的![](../graphics/stm_eqn01007.gif)）表示位置，用![](../graphics/stm_eqn04205.gif)表示方向向量，这给出

![](../graphics/stm_eqn04206.gif)位置梯度为

![](../graphics/stm_eqn04207.gif)梯度的面内分量获得为

![](../graphics/stm_eqn04208.gif)其中我们假定面内方向向量从表面坐标以

![](../graphics/stm_eqn04209.gif)得出，并定义了原始参考表面法线梯度，

![](../graphics/stm_eqn04210.gif)原始参考表面法线梯度在有限元公式中从节点法线的插值和形函数获得。在变形配置中，它不是从节点法线推导的，而是基于增量旋转梯度的独立更新。
### 参数插值

壳参考表面中点的位置用参数插值函数![](../graphics/stm_eqn04211.gif)通过离散节点位置来描述。函数是![](../graphics/stm_eqn04212.gif)是非正交、非距离测量的参数坐标。因此，对于参考表面位置，一个获得

![](../graphics/stm_eqn04213.gif)相对于![](../graphics/stm_eqn04214.gif)的位置梯度为

![](../graphics/stm_eqn04215.gif)注意大写罗马上标（如*I*）表示单元的节点，重复上标意味着对单元所有节点求和。

现在考虑原始配置。壳参考表面的单位法线容易获得为

![](../graphics/stm_eqn04216.gif)随后，我们定义两个正交切线向量![](../graphics/stm_eqn02587.gif)和沿这些向量的距离测量坐标![](../graphics/stm_eqn04198.gif)。这些坐标相对于![](../graphics/stm_eqn04214.gif)的导数从

![](../graphics/stm_eqn04217.gif)得出。![](../graphics/stm_eqn01209.gif)相对于![](../graphics/stm_eqn04197.gif)的梯度容易通过求逆获得：

![](../graphics/stm_eqn04218.gif)这使得获得梯度算子

![](../graphics/stm_eqn04219.gif)原始参考表面法线梯度从节点法线![](../graphics/stm_eqn04220.gif)用

![](../graphics/stm_eqn04221.gif)获得。由于原始参考表面法线梯度是通过对正交距离测量坐标求导获得的，我们将称![](../graphics/stm_eqn04222.gif)利用这个表达式，我们可以在当前状态中定义梯度算子：

![](../graphics/stm_eqn04224.gif)当前状态中的梯度算子也可以定义为相对于沿基向量![](../graphics/stm_eqn01706.gif)因此，

![](../graphics/stm_eqn04226.gif)因此，可以为![](../graphics/stm_eqn04227.gif)因为

![](../graphics/stm_eqn04229.gif)在增量分析中，我们也可以定义增量变形张量

![](../graphics/stm_eqn04230.gif)及其逆

![](../graphics/stm_eqn04231.gif)用当前状态中定义的局部坐标系，法线的当前梯度可以变换为表面曲率：

![](../graphics/stm_eqn04232.gif)
### 方向更新

前面各节给出的方程对当前状态中定义的任何局部坐标系有效。分析开始时![](../graphics/stm_eqn01706.gif)向量根据标准Abaqus约定确定。在本节中，我们概述了面内坐标如何成为共旋的方式。

为了获得更新的![](../graphics/stm_eqn01706.gif)（遵循Abaqus约定）。随后，我们计算

![](../graphics/stm_eqn04234.gif)然后我们对向量应用面内旋转![](../graphics/stm_eqn04235.gif)：![](../graphics/stm_eqn04233.gif)：

![](../graphics/stm_eqn04236.gif)

![](../graphics/stm_eqn04237.gif)其中![](../graphics/stm_eqn04238.gif)是要确定的，使得结果变形张量是对称的，如

![](../graphics/stm_eqn04239.gif)由此得出

![](../graphics/stm_eqn04240.gif)因此，我们可以计算更新的局部材料方向为

![](../graphics/stm_eqn04241.gif)
### 曲率变化

![](../graphics/stm_eqn04211.gif)![](../graphics/stm_eqn03595.gif)我们假定节点自旋将用插值函数![](../graphics/stm_eqn04211.gif)有限旋转向量可以分解为旋转幅度![](../graphics/stm_eqn03570.gif)和旋转轴![](../graphics/stm_eqn00156.gif)

![](../graphics/stm_eqn04243.gif)为了旋转壳法线，我们使用四元数代数。增量节点旋转由旋转四元数![](../graphics/stm_eqn03564.gif)表示，定义为

![](../graphics/stm_eqn04244.gif)然后根据以下公式获得更新的壳法线

![](../graphics/stm_eqn04245.gif)这个更新的壳法线实际上不需要计算：它仅用于推导曲率变化表达式。它不等于下一增量开始时使用的壳法线![](../graphics/stm_eqn04246.gif)，后者将再次选择为垂直于参考表面。这里使用的更新法线将近似垂直于参考表面，取决于横向剪切变形的量。更新壳法线的梯度可以通过微分获得：

![](../graphics/stm_eqn04247.gif)右侧的第二项可以写成形式

![](../graphics/stm_eqn04248.gif)因此，前两项的标量部分相互抵消，向量部分相互增强，导致

![](../graphics/stm_eqn04249.gif)像![](../graphics/stm_eqn03564.gif)）。因此，我们可以写成

![](../graphics/stm_eqn04250.gif)其中我们形式上定义了增量梯度更新向量

![](../graphics/stm_eqn04251.gif)它必须用增量旋转梯度表示。从增量四元数![](../graphics/stm_eqn03564.gif)因此，对于![](../graphics/stm_eqn04253.gif)，再次使用增量四元数定义

![](../graphics/stm_eqn04254.gif)从![](../graphics/stm_eqn03570.gif)定义得出

![](../graphics/stm_eqn04255.gif)代入![](../graphics/stm_eqn04253.gif)注意当![](../graphics/stm_eqn03575.gif)时，![](../graphics/stm_eqn04257.gif)。

对于更新壳法线的梯度![](../graphics/stm_eqn04258.gif)，我们获得

![](../graphics/stm_eqn04259.gif)：

![](../graphics/stm_eqn04260.gif)注意![](../graphics/stm_eqn04258.gif)的*变化*独立于![](../graphics/stm_eqn04261.gif)。

![](../graphics/stm_eqn04258.gif)的计算涉及相对于参考配置求导。使用参考表面曲率张量

![](../graphics/stm_eqn04262.gif)![](../graphics/stm_eqn04263.gif)![](../graphics/stm_eqn04263.gif)使得更新方程可以写成

![](../graphics/stm_eqn04264.gif)这个表达式使得仅通过在最新更新状态中的梯度就能计算参考表面曲率的更新。
### 变形梯度

我们已经获得了参考表面变形梯度的表达式，并且我们假定厚度变化是常数：

![](../graphics/stm_eqn04265.gif)在壳的其他点，我们为面内分量获得

![](../graphics/stm_eqn04266.gif)我们忽略![](../graphics/stm_eqn04267.gif)阶的项，这给出简化关系

![](../graphics/stm_eqn04268.gif)我们可以将其写为有限膜变形和弯曲扰动的乘积：

![](../graphics/stm_eqn04269.gif)将假定弯曲引起的变形（应变和旋转）是小的，因此

![](../graphics/stm_eqn04270.gif)
### 膜应变增量

膜应变增量从增量拉伸张量![](../graphics/stm_eqn00572.gif)得出，其分量从增量变形梯度![](../graphics/stm_eqn04271.gif)得出。

设![](../graphics/stm_eqn04273.gif)和![](../graphics/stm_eqn04274.gif)分别是增量开始和结束时的变形梯度。按定义![](../graphics/stm_eqn04275.gif)。增量变形梯度得出为

![](../graphics/stm_eqn04276.gif)由于![](../graphics/stm_eqn04277.gif)是正交矩阵的分量，增量拉伸张量的平方可以通过以下获得

![](../graphics/stm_eqn04278.gif)（见"变形，" 第1.4.1节）。对数应变增量然后为

![](../graphics/stm_eqn04279.gif)平均材料旋转增量从极分解定义：

![](../graphics/stm_eqn04280.gif)由于单元基方向的选择，由此得出

![](../graphics/stm_eqn04281.gif)
### 曲率增量

![](../graphics/stm_eqn04282.gif)遵循Koiter-Sanders壳理论，并补偿基向量相对于材料的旋转，我们将物理曲率增量![](../graphics/stm_eqn04282.gif)忽略相对于![](../graphics/stm_eqn04285.gif)的![](../graphics/stm_eqn04284.gif)阶项，这个表达式可以重写为

![](../graphics/stm_eqn04286.gif)其中使用了曲率更新公式。注意增量开始时的曲率，![](../graphics/stm_eqn04287.gif)，不出现在这个方程中。因此，不需要计算初始曲率![](../graphics/stm_eqn04288.gif)，我们可以假定![](../graphics/stm_eqn04289.gif)。因此，变形梯度也可以简化为

![](../graphics/stm_eqn04290.gif)对于壳厚度一点处的材料应变增量，Koiter-Sanders理论因此给出

![](../graphics/stm_eqn04291.gif)
### 虚功

应力的虚功贡献为

![](../graphics/stm_eqn04292.gif)我们假定应变变分可以用与应变增量相同的关系表示为膜应变变分和曲率变分：

![](../graphics/stm_eqn04293.gif)这将虚功方程变换为

![](../graphics/stm_eqn04294.gif)我们引入膜力![](../graphics/stm_eqn04295.gif)和弯矩![](../graphics/stm_eqn04296.gif)：

![](../graphics/stm_eqn04297.gif)这允许我们写成

![](../graphics/stm_eqn04298.gif)膜应变变分遵循通常的表达式

![](../graphics/stm_eqn04299.gif)其中我们使用了恒等式![](../graphics/stm_eqn04300.gif)。

通过在增量曲率上求变分来获得曲率的变分，这给出

![](../graphics/stm_eqn04301.gif)我们忽略![](../graphics/stm_eqn04282.gif)阶的项，也忽略![](../graphics/stm_eqn04302.gif)我们在当前状态（增量结束时）相对于![](../graphics/stm_eqn04304.gif)求值。因此，对于求值，我们可以假定![](../graphics/stm_eqn04305.gif)。此外，我们忽略![](../graphics/stm_eqn04306.gif)阶的项，因为它们与![](../graphics/stm_eqn04282.gif)成正比。因此，我们获得

![](../graphics/stm_eqn04307.gif)代入![](../graphics/stm_eqn04308.gif)的表达式给出

![](../graphics/stm_eqn04309.gif)
### 虚功率的变化率

为了获得虚功率变化率的表达式，我们首先将虚功方程用参考体积表示

![](../graphics/stm_eqn04310.gif)其中![](../graphics/stm_eqn04311.gif)是Kirchhoff应力张量，通过

![](../graphics/stm_eqn04312.gif)与柯西或真实应力张量相关。变化率变为

![](../graphics/stm_eqn04313.gif)这里![](../graphics/stm_eqn04314.gif)表示在材料、共旋坐标系中取的变化率。涉及应力变化率的项与材料行为相关。我们假定形式为

![](../graphics/stm_eqn04315.gif)的本构方程。代入![](../graphics/stm_eqn04316.gif)的表达式并变换回当前配置，这给出

![](../graphics/stm_eqn04317.gif)与虚功方程本身的推导一致，我们忽略![](../graphics/stm_eqn04318.gif)阶的项。因此，虚功率的变化率可以写成

![](../graphics/stm_eqn04319.gif)
### 膜应变的二阶变分

仍有待确定![](../graphics/stm_eqn04320.gif)和![](../graphics/stm_eqn04321.gif)。从一阶变分![](../graphics/stm_eqn04322.gif)得出

![](../graphics/stm_eqn04323.gif)由于![](../graphics/stm_eqn04227.gif)是![](../graphics/stm_eqn04324.gif)的逆，由此得出

![](../graphics/stm_eqn04325.gif)代入二阶变分表达式给出

![](../graphics/stm_eqn04326.gif)基向量的共旋变化率从

![](../graphics/stm_eqn04327.gif)得出。代入前一份表达式的第一项给出

![](../graphics/stm_eqn04328.gif)基向量共旋变化率的面内分量也可以用参考表面中的面内材料自旋表示：

![](../graphics/stm_eqn04329.gif)代入最后获得的![](../graphics/stm_eqn04330.gif)这个表达式与用"标准"连续体单元获得的表达式相同。
### 曲率的二阶变分

我们需要计算曲率的二阶变分以从曲率计算初始应力贡献：

![](../graphics/stm_eqn04332.gif)为了简化计算，我们依靠曲率的内在定义，并用相对于等参坐标的导数表示曲率。因此，

![](../graphics/stm_eqn04333.gif)是以正交坐标系（![](../graphics/stm_eqn04335.gif)中表示的分量，通过![](../graphics/stm_eqn04336.gif)变换。

用相对于等参坐标的导数表示为![](../graphics/stm_eqn04337.gif)，曲率的二阶变分为

![](../graphics/stm_eqn04338.gif)使用![](../graphics/stm_eqn04339.gif)和![](../graphics/stm_eqn04340.gif)的事实，我们发现

![](../graphics/stm_eqn04341.gif)这里![](../graphics/stm_eqn04342.gif)表示具有轴向量![](../graphics/stm_eqn04194.gif)的斜对称张量。
### 横向剪切处理

已经提出了几种插值方案来避免剪切锁定，这通常是当板或壳的厚度趋于零时出现的。这里我们使用基于Hu-Washizu原理的假设应变方法。这个方案源于[MacNeal（1978）](07s01a01-References.md)，随后在[Hughes和Tezduyar（1981）](07s01a01-References.md)和[MacNeal（1982）](07s01a01-References.md)中扩展和重新公式化，并在[Bathe和Dvorkin（1984）](07s01a01-References.md)中重新审视。非线性理论的计算方面在[Simo、Fox和Rifai（1989）](07s01a01-References.md)中用于完全积分的四边形壳单元。对于可同时用于隐式和显式积分的缩减积分四边形和三角形壳单元，这种假设应变方法需要修改。我们在下面总结用于完全积分单元的假设应变方法，然后是Abaqus中使用的单点积分加稳定化所需的修改。假设应变场的构造

![](../graphics/stm_eqn04499.gif)![](../graphics/stm_eqn04495.gif)![](../graphics/stm_eqn04498.gif)![](../graphics/stm_eqn04500.gif)![](../graphics/stm_eqn04497.gif)![](../graphics/stm_eqn04496.gif)![](../graphics/stm_eqn00479.gif)![](../graphics/stm_eqn04489.gif)![](../graphics/stm_eqn03564.gif)![](../graphics/stm_eqn04243.gif)![](../graphics/stm_eqn04343.gif)考虑一个典型的等参有限单元，如[图3.6.5-1](03s06a83-Finite-strain-shell-element-formulation.md)所示，并用![](../graphics/stm_eqn04343.gif)![](../graphics/stm_eqn04214.gif)![](../graphics/stm_eqn04218.gif)![](../graphics/ststrain-notation.png)

使用以下假设横向剪切应变场：

![](../graphics/stm_eqn04344.gif)其中

![](../graphics/stm_eqn04345.gif)是在单元边界中点处计算的协变横向剪切应变。在上述横向剪切应变定义中，使用大写字母表示参考配置中的量，使用小写字母表示变形配置中的量。为清晰起见，我们省略了方向场中的下标3。利用双线性单元插值，由此得出

![](../graphics/stm_eqn04346.gif)其中![](../graphics/stm_eqn04347.gif)，对于![](../graphics/stm_eqn04348.gif)，是单元节点的参考表面位置向量。

通过利用沿方向场的假设应变场以及方向场的更新公式，假设协变横向剪切场可以简洁地写成矩阵符号。回想方向场更新方程和相应的线性化方向场：

![](../graphics/stm_eqn04349.gif)从单元插值得出

![](../graphics/stm_eqn04350.gif)定义以下向量：

![](../graphics/stm_eqn04351.gif)那么，线性化横向剪切应变为

![](../graphics/stm_eqn04352.gif)其中

![](../graphics/stm_eqn04353.gif)定义四个向量：

![](../graphics/stm_eqn04354.gif)那么应变/位移算子的旋转或弯曲部分写成

![](../graphics/stm_eqn04355.gif)本构关系

![](../graphics/stm_eqn04334.gif)![](../graphics/stm_eqn04333.gif)![](../graphics/stm_eqn04336.gif)![](../graphics/stm_eqn04335.gif)![](../graphics/stm_eqn04237.gif)![](../graphics/stm_eqn04238.gif)对于Kirchhoff曲线坐标分量 resultant横向剪切力的St. Venant-Kirchhoff本构模型写成横向剪切应变的形式

![](../graphics/stm_eqn04356.gif)其中![](../graphics/stm_eqn04357.gif)是曲线坐标中的横向剪切刚度。对于单个各向同性层，

![](../graphics/stm_eqn04358.gif)矩阵![](../graphics/stm_eqn04359.gif)是度量![](../graphics/stm_eqn04360.gif)的逆，其中参考配置中的度量分量![](../graphics/stm_eqn04361.gif)由内积

![](../graphics/stm_eqn04362.gif)定义。壳正交坐标系![](../graphics/stm_eqn04363.gif)中的柯西或真实横向剪切力分量用坐标变换![](../graphics/stm_eqn04364.gif)计算为

![](../graphics/stm_eqn04365.gif)![](../graphics/stm_eqn04365.gif)然后初始应力贡献写成

![](../graphics/stm_eqn04367.gif)其中![](../graphics/stm_eqn04368.gif)是当前配置中的面积度量，![](../graphics/stm_eqn04369.gif)是初始应力的（对称）横向剪切贡献，定义如下。让![](../graphics/stm_eqn00064.gif)是![](../graphics/stm_eqn04370.gif)单位矩阵；然后定义对称矩阵

![](../graphics/stm_eqn04371.gif)还定义斜对称矩阵

![](../graphics/stm_eqn04372.gif)此外，让![](../graphics/stm_eqn04373.gif)是![](../graphics/stm_eqn04370.gif)零矩阵。然后![](../graphics/stm_eqn04369.gif)写成

![](../graphics/stm_eqn04374.gif)单点积分加稳定化

对于缩减积分单元，横向剪切力分量需要在单元中心计算。考虑![](../graphics/stm_eqn04375.gif)内部能量的横向剪切贡献：

![](../graphics/stm_eqn04376.gif)参考面积度量![](../graphics/stm_eqn02623.gif)用等参坐标写成![](../graphics/stm_eqn04377.gif)，其中![](../graphics/stm_eqn04378.gif)和![](../graphics/stm_eqn04361.gif)是未变形配置中参考表面度量的分量。

这种横向剪切能可以用许多方式近似，以在单元中心产生单点积分加上沙漏稳定化。这种处理对于厚壳问题中横向剪切变形的准确表示很重要，并为歪斜单元提供稳健的性能。处理应该平滑地塌陷到三角形，这应该在塌陷期间对节点编号不敏感；也就是说，三角形的响应不应依赖于节点连接性。对于整个三角形单元网格，处理应给出收敛结果（即单元不应锁定）。此外，横向剪切处理的高频响应应该被控制，使得横向剪切响应不会支配显式动力学分析的稳定时间增量（包括对于歪斜三角形或四边形几何）。所有这些要求都体现在以下横向剪切处理中。

定义单元中心的横向剪切应变（均匀部分）和"沙漏"横向剪切应变向量为

![](../graphics/stm_eqn04379.gif)单元畸变系数![](../graphics/stm_eqn04380.gif)和![](../graphics/stm_eqn04381.gif)是由单元参考几何确定的常数。对于具有恒定Jacobian变换的几何，![](../graphics/stm_eqn04382.gif)。沙漏应变向量![](../graphics/stm_eqn04383.gif)的分量定义为边应变的形式

![](../graphics/stm_eqn04384.gif)系数![](../graphics/stm_eqn04385.gif)、![](../graphics/stm_eqn04386.gif)、![](../graphics/stm_eqn04387.gif)和![](../graphics/stm_eqn04388.gif)是由单元参考几何确定的常数。对于矩形单元，![](../graphics/stm_eqn04389.gif)、![](../graphics/stm_eqn04390.gif)、![](../graphics/stm_eqn04391.gif)、![](../graphics/stm_eqn04392.gif)和![](../graphics/stm_eqn04393.gif)可以被识别为与旋转"蝴蝶"变形模式相关的应变。我们称![](../graphics/stm_eqn04394.gif)中添加crop circle应变![](../graphics/stm_eqn04394.gif)有两个重要后果。首先，它使横向剪切响应对三角形单元的节点连接性不敏感。也就是说，当四边形单元的一边塌陷形成三角形时，单元的响应与节点编号的选择无关。其次，对于显式动力学分析，系数![](../graphics/stm_eqn04380.gif)和![](../graphics/stm_eqn04381.gif)被选择为使横向剪切响应均匀部分相关的最高频率最小化。

为了说明crop circle和蝴蝶横向剪切模式，考虑一个方形、初始平坦的单元。此外，考虑板理论运动学；即，节点处的两个旋转和一个垂直偏转。crop circle模式在节点处有零垂直偏转，节点旋转向量模式如图[图3.6.5-2](03s06a83-Finite-strain-shell-element-formulation.md)所示。

图3.6.5-2 Crop circle模式：零偏转和圆对称旋转。

![](../graphics/stmcrop-circle.png)蝴蝶模式具有对应于交叉对角弯曲的垂直偏转；也就是说，沿对角线在两个节点上有两个相等的偏转，在剩余两个节点上有相等且相反的偏转。节点旋转以反对参考表面弯曲运动的方式发展；也就是说，旋转与该位移模式产生的弯曲旋转相反。蝴蝶模式的节点垂直偏转和旋转向量模式如图[图3.6.5-3](03s06a83-Finite-strain-shell-element-formulation.md)所示。

图3.6.5-3 蝴蝶模式：垂直偏转和旋转向量。

![](../graphics/stmbutterfly.png)设参考单元面积为![](../graphics/stm_eqn04396.gif)。横向剪切能可以近似为中心点值加上稳定化项：

![](../graphics/stm_eqn04397.gif)其中![](../graphics/stm_eqn04398.gif)是在单元中心计算的横向剪切刚度，沙漏刚度![](../graphics/stm_eqn00677.gif)是對角矩阵

![](../graphics/stm_eqn04399.gif)有效刚度![](../graphics/stm_eqn04400.gif)是横向剪切刚度的平均直接分量，![](../graphics/stm_eqn04401.gif)。

横向剪切的均匀部分的公式有两种贡献：从单元跨越的平均应变，加上单元畸变项。平均应变处理本质上与前面给出的MacNeal等人的假设应变公式相同，在单元中心（![](../graphics/stm_eqn04402.gif)和![](../graphics/stm_eqn04403.gif)）求值。这个部分的细节被省略；只有单元畸变项被详细给出。均匀横向剪切应变的变化可以写成

![](../graphics/stm_eqn04404.gif)其中![](../graphics/stm_eqn04405.gif)和![](../graphics/stm_eqn04406.gif)是![](../graphics/stm_eqn04407.gif)和![](../graphics/stm_eqn04408.gif)在单元中心求值，

![](../graphics/stm_eqn04409.gif)和

![](../graphics/stm_eqn04410.gif)

稳定化项具有类似的公式。沙漏应变的变化为

![](../graphics/stm_eqn04411.gif)其中

![](../graphics/stm_eqn04412.gif)和

![](../graphics/stm_eqn04413.gif)

沙漏力分量![](../graphics/stm_eqn04414.gif)和![](../graphics/stm_eqn04415.gif)由本构关系给出

![](../graphics/stm_eqn04416.gif)关于稳定化的说明

（1）蝴蝶模式![](../graphics/stm_eqn04393.gif)应用"大"或物理沙漏刚度。对于具有恒定Jacobian的参考几何，蝴蝶稳定化项可以从横向剪切能的假设应变公式的精确积分推导。用高刚度应用这个约束以防止四边形单元的过度柔性响应是重要的。crop circle模式应用"小"或弱刚度。虽然这个模式可以传播，但它很少有问题，经常被边界条件阻止。

（2）当四边形单元退化为三角形时，两个沙漏约束收敛为单个约束：crop circle约束。然而，正如所知，对于常应变三角形，单元将在具有三个横向剪切约束的某些网格上锁定。因此，在三角形的情况下，（强）蝴蝶模式稳定化不应用。只有（弱）crop circle模式稳定化被应用。因此，除了两个均匀横向剪切应变外，三角形有一个弱约束以防止伪零能模式，但在大多数情况下避免锁定。

来自稳定化项的初始应力贡献采用以下形式：

![](../graphics/stm_eqn04417.gif)其中![](../graphics/stm_eqn04418.gif)是初始应力的（对称）横向剪切稳定化贡献。定义对称矩阵

![](../graphics/stm_eqn04419.gif)还定义斜对称矩阵

![](../graphics/stm_eqn04488.gif)![](../graphics/stm_eqn04490.gif)![](../graphics/stm_eqn04420.gif)然后![](../graphics/stm_eqn04418.gif)注意一旦在![](../graphics/stm_eqn04418.gif)中定义了矩阵条目，![](../graphics/stm_eqn04418.gif)就像从![](../graphics/stm_eqn04369.gif)一样填充。

来自均匀部分的初始应力贡献包括两项，一项来自假设应变公式（在![](../graphics/stm_eqn04422.gif)处求值），另一项来自crop circle模式添加。这两项可以写成

![](../graphics/stm_eqn04423.gif)其中![](../graphics/stm_eqn04424.gif)和![](../graphics/stm_eqn04425.gif)是剪切力和在单元中心求值的矩阵![](../graphics/stm_eqn04369.gif)。![](../graphics/stm_eqn04426.gif)的矩阵表达式类似于来自稳定化项的![](../graphics/stm_eqn04418.gif)。
### 面内位移沙漏控制

面内位移沙漏控制以与Abaqus膜单元相同的方式应用。沙漏应变定义为

![](../graphics/stm_eqn04427.gif)其中![](../graphics/stm_eqn04428.gif)是沙漏模式。这个模式通过使"常规"沙漏模式![](../graphics/stm_eqn04429.gif)与单元未变形形状中的均匀变形模式正交来获得。最后一个条件可以写成

![](../graphics/stm_eqn04430.gif)观察

![](../graphics/stm_eqn04431.gif)因此，

![](../graphics/stm_eqn04432.gif)这个表达式可以进一步计算。我们定义投影节点坐标

![](../graphics/stm_eqn04433.gif)和投影单元面积

![](../graphics/stm_eqn04434.gif)然后沙漏模式可以写成形式

![](../graphics/stm_eqn04435.gif)沙漏刚度选择等于

![](../graphics/stm_eqn04436.gif)其中*G*是剪切模量，![](../graphics/stm_eqn04437.gif)是一个小数，在Abaqus/Standard中选择为0.005，在Abaqus/Explicit中选择为0.05。当沙漏控制基于假设增强应变时，人工刚度因子被替换为从三场变分原理推导的系数。那么与*z*共轭的沙漏力*Z*等于

![](../graphics/stm_eqn04438.gif)对于虚功，我们需要沙漏应变的一阶变分。从应变表达式立即得出

![](../graphics/stm_eqn04439.gif)注意在初始配置中第二项为零，因为![](../graphics/stm_eqn04440.gif)。Jacobian需要二阶变分。从一阶变分立即得出

![](../graphics/stm_eqn04441.gif)二阶变分在初始配置中不贡献，因为最初![](../graphics/stm_eqn04442.gif)。
### 旋转沙漏控制

曲率变化、横向剪切约束和钻孔模式约束的表达式仍然留下三个非均匀旋转模式未约束。这些模式对应于边中点处的零旋转和质心处的零梯度。因此，它们对应于熟悉的![](../graphics/stm_eqn04429.gif)沙漏模式。为了精确通过曲率分片测试，有必要使用为面内沙漏控制推导的正交化沙漏模式。

最后一个方面意味着旋转沙漏模式对应于质心处旋转的混合导数：

![](../graphics/stm_eqn04443.gif)

我们不能直接在适用于多个有限旋转增量的公式中使用上述公式。因此，我们使用与曲率变化计算相同的方法。出于计算目的，我们定义更新的壳方向向量

![](../graphics/stm_eqn04444.gif)更新的壳方向向量实际上不需要存储：它们仅用于推导沙漏应变表达式。我们现在形式上定义沙漏应变张量为

![](../graphics/stm_eqn04445.gif)观察

![](../graphics/stm_eqn04446.gif)出于沙漏应变计算的目的，我们假定所有相对于![](../graphics/stm_eqn04447.gif)和![](../graphics/stm_eqn04448.gif)的一阶导数乘积可以忽略。因此，

![](../graphics/stm_eqn04449.gif)因此，

![](../graphics/stm_eqn04450.gif)是斜对称的。观察![](../graphics/stm_eqn04200.gif)的混合导数可以用沙漏应变张量表示为

![](../graphics/stm_eqn04451.gif)在未变形配置中，我们假定![](../graphics/stm_eqn04452.gif)。![](../graphics/stm_eqn04453.gif)的随后值增量获得。从![](../graphics/stm_eqn04454.gif)在这个表达式中，我们还忽略包含相对于![](../graphics/stm_eqn04447.gif)和![](../graphics/stm_eqn04448.gif)导数乘积的所有项。因此，上述表达式简化为

![](../graphics/stm_eqn04456.gif)右侧的第二项可以写成形式

![](../graphics/stm_eqn04457.gif)因此，前两项的标量部分相互抵消，向量部分相互增强，导致

![](../graphics/stm_eqn04458.gif)像![](../graphics/stm_eqn03564.gif)）；因此，我们可以写成

![](../graphics/stm_eqn04459.gif)其中我们形式上定义了增量沙漏更新向量

![](../graphics/stm_eqn04460.gif)它必须用增量旋转沙漏模式表示。从增量四元数![](../graphics/stm_eqn03564.gif)定义得出，同时忽略![](../graphics/stm_eqn04447.gif)和![](../graphics/stm_eqn04448.gif)导数的乘积：

![](../graphics/stm_eqn04461.gif)因此，对于![](../graphics/stm_eqn04462.gif)，再次使用增量四元数定义

![](../graphics/stm_eqn04463.gif)从![](../graphics/stm_eqn03570.gif)和![](../graphics/stm_eqn00156.gif)定义得出，再次忽略一阶导数的乘积

![](../graphics/stm_eqn04464.gif)代入![](../graphics/stm_eqn04462.gif)的表达式并经过一些代数运算后获得

![](../graphics/stm_eqn04465.gif)注意当![](../graphics/stm_eqn03575.gif)时，![](../graphics/stm_eqn04466.gif)。对于更新的沙漏张量，一个容易获得

![](../graphics/stm_eqn04467.gif)这个表达式通过引入沙漏向量

![](../graphics/stm_eqn04468.gif)进一步简化，这给出更新公式

![](../graphics/stm_eqn04469.gif)一阶和二阶变分完全以与曲率变化的一阶和二阶变分相同的方式获得。对于一阶变分，我们忽略![](../graphics/stm_eqn04462.gif)阶的项并获得

![](../graphics/stm_eqn04470.gif)对于二阶变分，我们另外忽略![](../graphics/stm_eqn04471.gif)和![](../graphics/stm_eqn04472.gif)阶的项，最终结果为

![](../graphics/stm_eqn04473.gif)
### 退化单元

在一般网格中，可能需要将至少一些四边形单元塌陷为三角形，或使用三角形单元S3或S3R，它实际上是内部塌陷的S4R单元。对于这种情况，膜应变和曲率变化的计算沿着与之前相同的路线进行。横向剪切现在在退化边上为零。最后，所有沙漏约束的计算将被省略。
### 显式动力学的旋转惯性缩放

为了在显式动力学分析中的数值效率，期望稳定时间增量由结构的膜响应决定。由于这个原因，基于单元参考几何的旋转惯性缩放包含在Abaqus/Explicit中。

在显式动力学分析中，稳定时间增量与单元的最高频率成正比。因此，我们必须确保横向剪切响应的最高频率不超过膜响应的最高频率。对于厚单元（即，厚度相对于单元中特征长度为一阶的单元），膜频率是主要的。选择适当缩放的主要考虑是，当单元的厚度趋于零时，横向剪切频率保持在膜频率以下。回想一下，对于一维弹簧-质量振荡器，自然频率![](../graphics/stm_eqn01091.gif)可以用刚度*K*和质量*M*表示为

![](../graphics/stm_eqn04474.gif)对于横向剪切响应，与厚度的立方成正比的旋转惯性，起着系统质量的作用。所有其他量——膜刚度、与膜变形相关的质量、以及横向剪切刚度——都与厚度成正比。因此，当单元的厚度趋于零时，与横向剪切相关的频率趋于无穷大，与厚度成反比，而膜频率保持不变。如果没有缩放，当厚度变小时，稳定时间增量将趋于零。旋转惯性缩放

对于薄单元，旋转惯性（可忽略）相对于节点处质量关于通过单元中心的轴旋转的惯性很小。因此，我们选择旋转惯性的缩放，使其永远不会小于通过单元中心的轴旋转的节点处质量惯性的固定（小）百分比。

设*R*是无量纲旋转惯性缩放，其中![](../graphics/stm_eqn04475.gif)。当![](../graphics/stm_eqn04476.gif)时，使用真实旋转惯性。考虑4节点单元的集中质量矩阵，并设单元是平坦正方形的。对于关于单元平面中平行于单元边、穿过中心的轴的旋转，节点处质量的旋转惯性贡献为

![](../graphics/stm_eqn04477.gif)其中*A*是单元面积，*L*是边长，![](../graphics/stm_eqn00593.gif)是质量密度。四个节点处旋转惯性的和为

![](../graphics/stm_eqn04478.gif)面内贡献与旋转贡献的比值为

![](../graphics/stm_eqn04479.gif)为了使旋转惯性保持在厚度趋于零时作为质量贡献的固定分数——比如说![](../graphics/stm_eqn02163.gif)——渐近地*R*必须与![](../graphics/stm_eqn04480.gif)成正比；即，

![](../graphics/stm_eqn04481.gif)

对于具有沿法线方向的单元方向的平面几何，最高膜和横向剪切频率可能有闭合形式表达式。在这种情况下，长度参数*L*被解释为取决于单元畸变的特征单元长度。为了处理任意形状的曲线单元，单元频率的精确计算变得困难。然而，我们可以通过在以下缩放中选择适当的*L*来安全地限定频率：

![](../graphics/stm_eqn04482.gif)其中![](../graphics/stm_eqn04483.gif)。对于三角形单元，特征长度，![](../graphics/stm_eqn04484.gif)*R*定义中的因子16用于防止在承受导致壳厚度增加的载荷的非常细网格中由弯曲频率决定稳定时间增量。
### 显式动力学的旋转体积粘度

对于位移自由度，体积粘度引入与体积应变相关的阻尼。线性体积粘度或截断频率阻尼用于阻尼导致解中不需要的噪声或响应幅度中的伪超调的高频振铃。出于同样原因，在壳中，我们需要用作用于平均曲率应变率的线性体积粘度阻尼旋转自由度中的高频振铃。这种阻尼产生体积粘度"压力矩"，*m*，它线性于平均曲率应变率：

![](../graphics/stm_eqn04486.gif)其中*b*是阻尼系数（默认= 0.06），![](../graphics/stm_eqn01077.gif)是原始厚度，![](../graphics/stm_eqn00593.gif)是质量密度，![](../graphics/stm_eqn01078.gif)是当前膨胀波速，*L*是用于旋转惯性缩放的特征长度，![](../graphics/stm_eqn01079.gif)平均曲率增量两倍。膨胀波速用有效的Lam常数表示为

![](../graphics/stm_eqn04487.gif)结果压力矩![](../graphics/stm_eqn01081.gif)，其中*h*是当前厚度，被加到矩直接分量上。
### 完全积分的有限膜应变壳公式

单元S4是一个完全积分的有限膜应变壳单元。由于单元刚度是完全积分的，不存在伪膜或弯曲零能模式，也不使用膜或弯曲模式沙漏稳定化。但是，需要钻孔旋转控制。单元S4使用与单元S4R相同的钻孔刚度公式。类似地，单元S4假定横向剪切应变（和力，因为横向剪切处理是基于材料的初始弹性模量的弹性）在整个单元上是常数。因此，四个刚度积分位置将具有相同的横向剪切应变、横向剪切截面力和横向剪切应力分布。S4的横向剪切处理与S4R的相同。

众所周知，标准位移公式将表现出受面内弯曲变形支配的应用的剪切锁定。然而，弯曲刚度的标准位移公式不受类似锁定响应的影响。因此，S4对单元的弯曲刚度使用标准位移公式，上面给出的旋转运动学和弯曲应变度量公式适用于S4。S4和S4R单元公式之间的主要区别在于膜应变场的处理。以下讨论是这个公式的主题。

用于S4的膜公式不依赖于S4是壳单元的事实。因此，下面的讨论从膜响应受平面应力状态三维体平衡支配的角度详细阐述公式。

![](../graphics/stm_eqn04488.gif)![](../graphics/stm_eqn00424.gif)![](../graphics/stm_eqn04489.gif)考虑变形率张量![](../graphics/stm_eqn00424.gif)*增强*![](../graphics/stm_eqn04488.gif)我们引入增强的变形率张量，![](../graphics/stm_eqn04489.gif)为

![](../graphics/stm_eqn04488.gif)![](../graphics/stm_eqn04490.gif)其中![](../graphics/stm_eqn04488.gif)后定义。

还引入变形率的允许变分

![](../graphics/stm_eqn04491.gif)其中

![](../graphics/stm_eqn04492.gif)

![](../graphics/stm_eqn00424.gif)![](../graphics/stm_eqn04493.gif)我们现在引入对增强![](../graphics/stm_eqn00424.gif)![](../graphics/stm_eqn04493.gif)约束：

![](../graphics/stm_eqn04494.gif)以便修改的虚功声明可以写成形式

![](../graphics/stm_eqn04295.gif)其中![](../graphics/stm_eqn00479.gif)![](../graphics/stm_eqn04496.gif)上的给定牵引，和![](../graphics/stm_eqn04497.gif)![](../graphics/stm_eqn04498.gif)。![](../graphics/stm_eqn04499.gif)任意应力场，本构方程![](../graphics/stm_eqn04500.gif)（![](../graphics/stm_eqn04489.gif)逐点强制执行。

![](../graphics/stm_eqn04489.gif)![](../graphics/stm_eqn00424.gif)![](../graphics/stm_eqn04501.gif)![](../graphics/stm_eqn00503.gif)![](../graphics/stm_eqn00117.gif)![](../graphics/stm_eqn04502.gif)![](../graphics/stm_eqn04499.gif)在修改的虚功声明中，所有运动量和相应变分（![](../graphics/stm_eqn04489.gif)![](../graphics/stm_eqn00424.gif)![](../graphics/stm_eqn04501.gif)![](../graphics/stm_eqn00503.gif)都是![](../graphics/stm_eqn00117.gif)![](../graphics/stm_eqn04502.gif)参考配置的已知函数。公式有效性的基本要求是修改的虚功声明导致适当的平衡方程。如果![](../graphics/stm_eqn04499.gif)任意的，约束方程可以重写为

![](../graphics/stm_eqn04503.gif)将这两个关系代入修改的虚功方程给出

![](../graphics/stm_eqn04504.gif)其中我们使用了本构方程![](../graphics/stm_eqn04500.gif) ![](../graphics/stm_eqn04505.gif)。我们认识到这个变分声明是通常的虚功方程，直接应用散度定理导致标准平衡方程。

![](../graphics/stm_eqn04499.gif)![](../graphics/stm_eqn04506.gif)在实际实现中，我们选择仅对分段恒定应力场![](../graphics/stm_eqn04499.gif)足约束。因此，在单元域![](../graphics/stm_eqn04506.gif)我们要求

![](../graphics/stm_eqn04507.gif)选择增强![](../graphics/stm_eqn04488.gif)![](../graphics/stm_eqn04508.gif)得它们消除面内弯曲的剪切锁定。此外，直接应变场被增强以近似由弯曲中的泊松效应引起的应变。分片测试

为了通过分片测试，增强![](../graphics/stm_eqn04488.gif)选择不能是任意的。满足分片测试的充分条件是对于均匀变形，我们有![](../graphics/stm_eqn04509.gif)或点态![](../graphics/stm_eqn04510.gif)。在那种情况下![](../graphics/stm_eqn04511.gif)，应力是均匀的。因为应力是均匀的，它可以移到修改虚功声明中的体积积分外部。![](../graphics/stm_eqn04512.gif)体积积分条件意味着该表达式与增强无关，并导致标准位移公式，已知它满足分片测试。
### 参考

### 参考

"Abaqus Analysis User's Guide"第29.6.1节"壳单元：概述"

![](../graphics/stm_eqn04418.gif)![](../graphics/stm_eqn04421.gif)![](../graphics/stm_eqn04369.gif)![](../graphics/stm_eqn04330.gif)![](../graphics/stm_eqn04329.gif)![](../graphics/stm_eqn04229.gif)"Abaqus Analysis User's Guide"第29.6.4节"壳截面行为"
