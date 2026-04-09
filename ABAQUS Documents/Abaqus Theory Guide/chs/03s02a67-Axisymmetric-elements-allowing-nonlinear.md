# 3.2.9 允许非线性弯曲的轴对称单元

### 3.2.9 允许非线性弯曲的轴对称单元

**产品：** Abaqus/Standard

Abaqus/Standard包含一组实体单元，其几何形状最初是轴对称的，允许进行可以发生关于模型柱面坐标系（*r*、*z*、![](../graphics/stm_eqn01111.gif)）中平面![](../graphics/stm_eqn03117.gif)弯曲的非线性分析。几何模型仅在*r*—*z*平面中定义。位移是相对于*r*和*z*的常规参数插值，并通过对![](../graphics/graphics/stm_eqn01111.gif)的Fourier展开来增强。因为单元编写为仅允许关于平面![](../graphics/stm_eqn03117.gif)弯曲，它们不能用于模拟关于原始对称轴的结构扭转。因为单元用于非线性应用，与Fourier模式相关的正交性质不能用于将问题简化为更小的、不耦合的情况，因为投影到Fourier模式之前的刚度不一定是恒定的。由于这个原因，这些单元比用于轴对称变形的相应轴对称单元要昂贵得多。
### 插值

与这些单元一起使用的坐标系是柱面系统（*r*、*z*、![](../graphics/stm_eqn01111.gif)），其中*r*测量点到柱面系统轴的距离，*z*测量其沿该轴的位置，![](../graphics/stm_eqn01111.gif)测量包含该点和坐标系统轴的平面与包含坐标系统轴的某个固定参考平面之间的角度。这些单元中坐标和位移的顺序基于Abaqus中轴对称单元使用的约定，因此*z*是第二个坐标。这允许这些单元与库中仅允许轴对称变形的其他单元一起使用。这个顺序与Abaqus中三维单元使用的顺序不同，其中*z*是第三个坐标，也不是柱面系统中通常使用的顺序（*r*、![](../graphics/stm_eqn01111.gif)、*z*）。

假定单元的原始几何形状是关于坐标系统轴的轴对称的，因此独立于![](../graphics/stm_eqn01111.gif)。设![](../graphics/stm_eqn03101.gif)、![](../graphics/stm_eqn03066.gif)和![](../graphics/stm_eqn03118.gif)是点在未变形状态下沿径向、轴向和周向的单位向量。点的参考位置![](../graphics/stm_eqn00141.gif)可以用原始半径*R*和轴向位置*Z*表示：

![](../graphics/stm_eqn03119.gif)类似地，点的位移![](../graphics/stm_eqn00428.gif)可以用相对于这些相同向量的分量![](../graphics/stm_eqn03055.gif)、![](../graphics/stm_eqn03056.gif)和![](../graphics/stm_eqn03120.gif)来表示，这些向量在点的原始位置处：

![](../graphics/stm_eqn03121.gif)对于小的径向和周向位移，周向位移与周向角度的变化成正比（![](../graphics/stm_eqn03122.gif)），但对于大位移，这个关系变为非线性的（![](../graphics/stm_eqn03123.gif)），如图[图3.2.9-1](03s02a67.md)所示。

图3.2.9-1 *r*—![](../graphics/stm_eqn01111.gif)平面中的位移和旋转。

![](../graphics/stmrtheta-disp-rot.png) 这种区别仅在具有径向施加集中载荷和/或滑动径向边界条件的几何非线性分析中重要。这个自由度的定义等价于对与标准连续体单元相关的全局（*x*、*y*、*z*）自由度应用变换。因此，与这些单元相关的非线性方程具有与标准连续体单元方程相同的结构。

使用相对于![](../graphics/stm_eqn01111.gif)的Fourier项的![](../graphics/stm_eqn00428.gif)的一般插值方案：

![](../graphics/stm_eqn03124.gif)其中*g*、*h*是原始*R*—*Z*平面中的参数坐标；![](../graphics/stm_eqn03125.gif)是多项式插值函数；![](../graphics/stm_eqn03126.gif)、![](../graphics/stm_eqn03127.gif)和![](../graphics/stm_eqn03128.gif)是解振幅值。*M*是用于相对于*g*、*h*插值的项数；*P*是用于相对于![](../graphics/graphics/stm_eqn01111.gif)的Fourier插值的项数。当![](../graphics/stm_eqn03129.gif)时，产生纯轴对称变形。

我们通过假定弯曲仅允许关于一个平面![](../graphics/stm_eqn03117.gif)来减少此类单元中的变量数，因此平面![](../graphics/stm_eqn03130.gif)（*n*整数）是对称平面。满足此条件的唯一项是

![](../graphics/stm_eqn03131.gif)为方便起见，我们使用在模型中在![](../graphics/stm_eqn03132.gif)和![](../graphics/stm_eqn03133.gif)之间特定位置的![](../graphics/stm_eqn03072.gif)和![](../graphics/stm_eqn03056.gif)位移分量的值，而不是Fourier振幅![](../graphics/stm_eqn03134.gif)和![](../graphics/stm_eqn03135.gif)。主要原因是允许单元与界面单元（如滑移线）一起使用，界面单元需要物理位移值。只有在假定相对于![](../graphics/graphics/stm_eqn01111.gif)方向的相对位移很小，使得界面条件相对于![](../graphics/graphics/stm_eqn03055.gif)和![](../graphics/stm_eqn03056.gif)考虑时（即，在常数![](../graphics/stm_eqn01111.gif)的平面中），这才是准确的。此外，我们在周向位移表达式中省略下标*s*：![](../graphics/stm_eqn03136.gif)。因此，[公式3.2.9-1](03s02a67.md)被重写为

![](../graphics/stm_eqn03137.gif)其中![](../graphics/stm_eqn03138.gif)是三角插值函数，![](../graphics/stm_eqn03139.gif)、![](../graphics/stm_eqn03140.gif)是![](../graphics/stm_eqn03141.gif)处物理径向和轴向位移分量。

![](../graphics/stm_eqn03142.gif)在相关位置![](../graphics/stm_eqn03143.gif)的插值器取为

![](../graphics/stm_eqn03144.gif)：

![](../graphics/stm_eqn03145.gif)和

![](../graphics/stm_eqn03146.gif)

![](../graphics/stm_eqn03147.gif)：

![](../graphics/stm_eqn03148.gif)和

![](../graphics/stm_eqn03149.gif)

![](../graphics/stm_eqn03150.gif)：

![](../graphics/stm_eqn03151.gif)

![](../graphics/stm_eqn03152.gif)和

![](../graphics/stm_eqn03153.gif)

![](../graphics/stm_eqn03154.gif)：

![](../graphics/stm_eqn03155.gif)和

![](../graphics/stm_eqn03156.gif)

![](../graphics/stm_eqn03157.gif)是这些单元中提供的相对于![](../graphics/stm_eqn01111.gif)的最高阶插值：使用更高阶插值时单元变得显著更昂贵；并且假定，由于这个原因，全三维建模比使用这些单元与![](../graphics/stm_eqn03158.gif)更便宜。
### 积分

这些单元中使用的积分方案是在原始![](../graphics/stm_eqn03159.gif)—*Z*平面中的表面单元坐标的积分与相对于![](../graphics/stm_eqn01111.gif)的积分的乘积。对于前者，使用与相应纯轴对称单元相同的方案（例如，在参数四边形中完全积分或缩减高斯积分）。对于相对于![](../graphics/stm_eqn01111.gif)的积分，使用梯形法则，积分点数设置为![](../graphics/stm_eqn03160.gif)。
### 变形梯度

对于空间中的材料点，变形梯度![](../graphics/stm_eqn03161.gif)定义为当前位置![](../graphics/stm_eqn01887.gif)相对于原始位置![](../graphics/stm_eqn00141.gif)的梯度：

![](../graphics/stm_eqn03162.gif)当前位置![](../graphics/stm_eqn00117.gif)可以用原始位置![](../graphics/stm_eqn03163.gif)和位移![](../graphics/stm_eqn03164.gif)

![](../graphics/stm_eqn03165.gif)来描述，梯度算子可以用相对于柱面坐标的偏导数来描述：

![](../graphics/stm_eqn03166.gif)

由于径向和周向基向量依赖于原始周向坐标![](../graphics/stm_eqn01111.gif)：![](../graphics/stm_eqn03167.gif)、![](../graphics/stm_eqn03168.gif)，这些基向量相对于![](../graphics/stm_eqn01111.gif)的偏导数是非零的：

![](../graphics/stm_eqn03169.gif)利用这个结果，获得变形梯度为

![](../graphics/stm_eqn03170.gif)或者，可以用相对于局部参考基![](../graphics/stm_eqn03101.gif)、![](../graphics/stm_eqn03066.gif)、![](../graphics/stm_eqn03118.gif)的分量写成矩阵形式：

![](../graphics/stm_eqn03171.gif)

为了能够分析近似不可压缩材料行为，完全积分的4节点四边形中的体积变化假定在*R*—*Z*平面中独立于*g*和![](../graphics/stm_eqn03079.gif)。因此，![](../graphics/stm_eqn03172.gif)根据以下方式修改

![](../graphics/stm_eqn03173.gif)其中![](../graphics/stm_eqn03174.gif)是积分点处的体积变化，![](../graphics/stm_eqn03175.gif)是单元*R*—*Z*平面上的平均体积变化。此外，不依赖于![](../graphics/stm_eqn01111.gif)的轴对称周向应变部分被弄得独立于*g*和*h*。经验表明，这大大提高了轴对称问题的解精度。因此，我们使用

![](../graphics/stm_eqn03176.gif)其中

![](../graphics/stm_eqn03177.gif)![](../graphics/stm_eqn03178.gif)是![](../graphics/stm_eqn03179.gif)中的主导（常数）项。
### 应变和旋转增量

应变和旋转增量从积分速度梯度矩阵![](../graphics/stm_eqn03180.gif)计算，定义为

![](../graphics/stm_eqn03181.gif)其中![](../graphics/stm_eqn03182.gif)。这个表达式不容易直接计算，因为位于未变形形状中*R*—*Z*平面上的点在变形后将不再位于同一平面。相反，我们计算相对于参考状态的![](../graphics/stm_eqn03183.gif)的梯度，并通过变换获得![](../graphics/stm_eqn03180.gif)

![](../graphics/stm_eqn03184.gif)以矩阵形式，这可以写成

![](../graphics/stm_eqn03185.gif)其中

![](../graphics/stm_eqn03186.gif)

应变增量近似为![](../graphics/stm_eqn03180.gif)的对称部分：

![](../graphics/stm_eqn03187.gif)与变形梯度的情况一样，我们修改完全积分的4节点四边形中的体积应变增量，使其在*R*—*Z*平面中独立于*g*和*h*，这给出

![](../graphics/stm_eqn03188.gif)其中![](../graphics/stm_eqn03189.gif)是单位矩阵，![](../graphics/stm_eqn03190.gif)是积分点处的体积应变增量，![](../graphics/stm_eqn03191.gif)是单元*R*—*Z*平面上的平均体积应变增量。此外，我们使用近似

![](../graphics/stm_eqn03192.gif)

自旋增量，![](../graphics/stm_eqn03193.gif)，近似为![](../graphics/stm_eqn03194.gif)的反对称部分，以矩阵形式变为

![](../graphics/stm_eqn03195.gif)
### 虚功

平衡（虚功）的公式需要当前状态中应变-位移关系的线性化。对于完全积分的4节点单元，体积应变修改提供

![](../graphics/stm_eqn03196.gif)其中

![](../graphics/stm_eqn03197.gif)和

![](../graphics/stm_eqn03198.gif)与应变增量的情况一样，线性化应变-位移关系涉及在变形形状（![](../graphics/stm_eqn03199.gif)）中取导数，这是麻烦的，因为位于未变形形状中*R*—*Z*平面上的点在变形后将不再位于同一平面。因此，![](../graphics/stm_eqn03092.gif)以类似于![](../graphics/stm_eqn03180.gif)的方式计算：

![](../graphics/stm_eqn03200.gif)以矩阵形式，这可以写成

![](../graphics/stm_eqn03201.gif)其中

![](../graphics/stm_eqn03202.gif)

对于完全积分的4节点四边形，我们再次使用近似

![](../graphics/stm_eqn03203.gif)

位移，因此位移变分，用[公式3.2.9-2](03s02a67.md)中的节点位移变分来插值。位移相对于![](../graphics/stm_eqn03159.gif)、*Z*和![](../graphics/stm_eqn03077.gif)的导数容易从这些表达式中获得：

![](../graphics/stm_eqn03204.gif)
### 当前状态的刚度

因为单元用位移的笛卡尔分量来公式化，"实体单元公式，" 第3.2.2节中给出的方程适用。对于4节点四边形，我们可以将[公式3.2.2-1](03s02a60.md)适配到平均体积变化公式，这给出

![](../graphics/stm_eqn03205.gif)![](../graphics/stm_eqn03206.gif)的二阶变分用标准过程获得

![](../graphics/stm_eqn03207.gif)其中![](../graphics/stm_eqn03208.gif)与![](../graphics/stm_eqn03209.gif)具有相同的形式。引入共旋转应力率![](../graphics/stm_eqn03210.gif)后，这给出

![](../graphics/stm_eqn03211.gif)这可以用前一段关于虚功中获得![](../graphics/stm_eqn03092.gif)和![](../graphics/stm_eqn03212.gif)的表达式以节点自由度来计算。
### 沙漏控制

在4节点缩减积分单元中，必须控制沙漏模式。这些模式类似于常规轴对称单元中的模式，但有一些额外的特征。

沙漏模式可以沿圆周变化，这需要在圆周上的多个点施加沙漏刚度。

沙漏也可能发生在周向。因此，在圆周上每个积分点处，我们计算沙漏应变

![](../graphics/stm_eqn03213.gif)这里![](../graphics/stm_eqn00319.gif)是[公式3.2.9-3](03s02a67.md)给出的变形梯度，![](../graphics/stm_eqn03214.gif)和![](../graphics/stm_eqn03215.gif)分别是变形和未变形几何形状中的沙漏模式：

![](../graphics/stm_eqn03216.gif)其中![](../graphics/stm_eqn03217.gif)是与4节点轴对称连续体单元使用的相同沙漏算子，![](../graphics/stm_eqn03218.gif)和![](../graphics/stm_eqn03219.gif)是变形和未变形状态中角度![](../graphics/stm_eqn01111.gif)处的节点位置。注意，因为初始几何是轴对称的，![](../graphics/stm_eqn03219.gif)独立于![](../graphics/stm_eqn01111.gif)：

![](../graphics/stm_eqn03220.gif)在变形状态中，我们写成

![](../graphics/stm_eqn03221.gif)利用[公式3.2.9-2](03s02a67.md)，这变为

![](../graphics/stm_eqn03222.gif)沙漏"应变"通过沙漏刚度*c*转变为沙漏"力"：

![](../graphics/stm_eqn03223.gif)这个沙漏刚度可以用与常规轴对称单元相同的过程获得，唯一不同的是需要比例因子，以反映每个点仅反映圆周的一部分这一事实。![](../graphics/stm_eqn00178.gif)的一阶变分容易获得为

![](../graphics/stm_eqn03224.gif)

这里![](../graphics/stm_eqn03225.gif)来自[公式3.2.9-7](03s02a67.md)，对于![](../graphics/stm_eqn03226.gif)，我们获得

![](../graphics/stm_eqn03227.gif)

类似地，我们获得二阶变分

![](../graphics/stm_eqn03228.gif)其中![](../graphics/stm_eqn03229.gif)和![](../graphics/stm_eqn03230.gif)使用与一阶变分相同的表达式。
### 压力载荷和载荷刚度

对于几何线性问题，由于几何是轴对称的，施加表面压力和体力产生的等效节点载荷容易计算。对于几何非线性问题，体力处理不会改变，因为力的方向是固定的，且力与体积成正比，体积假定变化可以忽略不计。然而，对于表面压力，必须考虑非轴对称变形。

与表面压力*p*相关的等效节点载荷可以通过考虑虚功贡献获得

![](../graphics/stm_eqn03231.gif)其中![](../graphics/stm_eqn01040.gif)是*R*—*Z*平面中的参数表面坐标

![](../graphics/stm_eqn03232.gif)其中![](../graphics/stm_eqn03233.gif)和![](../graphics/stm_eqn03234.gif)。因此，点的当前位置可以用表面插值器![](../graphics/stm_eqn03235.gif)和标准周向插值器表示：

![](../graphics/stm_eqn03236.gif)

[公式3.2.9-8](03s02a67.md)中的项可以如下计算：

![](../graphics/stm_eqn03237.gif)因此，

![](../graphics/stm_eqn03238.gif)

因此，我们获得虚功贡献

![](../graphics/stm_eqn03239.gif)

利用插值函数，我们因此获得等效节点力：

![](../graphics/stm_eqn03240.gif)

![](../graphics/stm_eqn03241.gif)对于几何线性分析，这简化为标准轴对称等效节点载荷

![](../graphics/stm_eqn03242.gif)载荷刚度矩阵通过线性化获得：

![](../graphics/stm_eqn03243.gif)

![](../graphics/stm_eqn03244.gif)

![](../graphics/stm_eqn03245.gif)

![](../graphics/stm_eqn03246.gif)

![](../graphics/stm_eqn03247.gif)

![](../graphics/stm_eqn03248.gif)

![](../graphics/stm_eqn03249.gif)

![](../graphics/stm_eqn03250.gif)

对于静水压力（*p*依赖于*z*）的情况，出现一些额外的项。这些项容易从表达式

![](../graphics/stm_eqn03251.gif)

中获得。利用插值函数，我们因此获得额外的载荷刚度贡献：

![](../graphics/stm_eqn03252.gif)
### 质量矩阵

在每个材料点处，三个方向（径向、轴向、周向）中的位移分量仅依赖于相应的节点位移分量。因此，质量矩阵不涉及径向、轴向和周向自由度之间的任何耦合，我们可以将质量矩阵写成三个独立表达式的形式：

![](../graphics/stm_eqn03253.gif)这里上标*m*和*n*指*r*—*z*平面中的特定节点，上标*p*和*q*指沿圆周的特定位置。插值函数![](../graphics/stm_eqn03254.gif)、![](../graphics/stm_eqn03255.gif)和![](../graphics/stm_eqn03256.gif)是*r*—*z*平面中的插值函数![](../graphics/stm_eqn03257.gif)和![](../graphics/stm_eqn01111.gif)方向上插值函数的乘积：

![](../graphics/stm_eqn03258.gif)用于形成质量矩阵的体积积分可以分成对*r*—*z*横截面的积分和对圆周的积分。对于质量矩阵的*r*—*r*分量，这给出

![](../graphics/stm_eqn03259.gif)通过定义原始质量矩阵，这个矩阵可以写成方便的形式

![](../graphics/stm_eqn03260.gif)这个原始质量矩阵与用于常规轴对称单元的质量矩阵相同。我们还可以定义周向分布矩阵

![](../graphics/stm_eqn03261.gif)那么质量矩阵的径向、轴向和周向分量取形式

![](../graphics/stm_eqn03262.gif)

周向分布矩阵可以为Fourier级数中项数*P*的各种值进行计算。经过一些计算，获得以下结果：

![](../graphics/stm_eqn03144.gif)：

![](../graphics/stm_eqn03263.gif)

![](../graphics/stm_eqn03147.gif)：

![](../graphics/stm_eqn03264.gif)

![](../graphics/stm_eqn03265.gif)：

![](../graphics/stm_eqn03266.gif)

![](../graphics/stm_eqn03267.gif)：

![](../graphics/stm_eqn03268.gif)
### 混合和孔隙压力单元

对于混合和孔隙压力单元，添加了额外的自由度*p*。在混合单元中，这些自由度是单元内部的，代表材料中的静水压力。在孔隙压力单元中，自由度代表从外部用户定义节点的压力变量插值的流体中的静水压力。设*r*—*z*平面中（静水或孔隙）压力的插值函数表示为![](../graphics/stm_eqn03269.gif)。插值函数与常规轴对称混合和孔隙压力单元的插值函数相同。沿圆周，我们观察到，在几何线性公式中，体积应变![](../graphics/stm_eqn00155.gif)仅显示余弦依赖：

![](../graphics/stm_eqn03270.gif)因此，我们选择静水/孔隙压力仅具有余弦依赖：

![](../graphics/stm_eqn03271.gif)在非线性情况下，![](../graphics/stm_eqn00155.gif)将表现出![](../graphics/stm_eqn01111.gif)中更高阶的变化。对于近似不可压缩材料，这些高阶项可能导致有限元网格对于非轴对称变形发生"锁定"。然而，在混合公式中，![](../graphics/stm_eqn00155.gif)中的高阶项不用于静水压力计算：仅使用用于*p*插值的余弦项。因此，混合单元还可以防止非轴对称模式以及轴对称模式中的锁定。
### 孔隙压力梯度

对于孔隙压力单元中空间中的材料点，孔隙压力梯度计算涉及取孔隙压力相对于当前位置![](../graphics/stm_eqn00117.gif)的导数。同样，我们不直接计算梯度，而是相对于原始位置![](../graphics/stm_eqn00141.gif)计算，通过以下变换：

![](../graphics/stm_eqn03272.gif)其中![](../graphics/stm_eqn00319.gif)是变形梯度，孔隙压力相对于![](../graphics/stm_eqn00141.gif)的标量梯度的柱面分量容易从以下表达式获得：

![](../graphics/stm_eqn03273.gif)
### 参考

### 参考

"Abaqus Analysis User's Guide"第28.1.7节"具有非线性非对称变形的轴对称实体单元"
