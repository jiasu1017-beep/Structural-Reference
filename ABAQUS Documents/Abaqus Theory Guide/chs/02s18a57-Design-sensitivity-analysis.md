# 2.18.1 设计灵敏度分析

### 2.18.1 设计灵敏度分析

**产品：** Abaqus/Design

Abaqus/Design支持静态应力和频率问题的设计灵敏度分析（DSA）。DSA提供某些响应量相对于指定输入量的导数。这些导数被称为*灵敏度*。可用于DSA的响应是Abaqus输出变量列表的一个子集，被称为*设计响应*；指定的输入量被称为*设计参数*。作为设计参数函数的量被称为设计依赖的。DSA理论从分析计算所需导数的角度提出，首先针对静态应力分析，然后针对频率分析。在每节末尾讨论基于该理论的替代数值方法。
### 静态应力分析的DSA

DSA的方程可以基于总位移公式或增量位移公式推导。总位移公式适用于历史无关问题，其中问题的当前状态仅取决于总位移。增量公式适用于历史相关问题，其中问题的当前状态取决于增量开始时的状态和增量位移。
### 非线性平衡问题的总位移DSA公式

设*R*和*P*分别是设计响应和设计参数的数量。设每个响应![](../graphics/stm_eqn02773)、![](../graphics/stm_eqn02774)是设计参数![](../graphics/stm_eqn02775)、![](../graphics/stm_eqn02776的函数，既通过它们显式依赖，也通过此处由节点位移向量![](../graphics/stm_eqn00657表示的位移场间接依赖（见"过程：概述和基本方程"第2.1.1节中有限元插值的定义），

![](../graphics/stm_eqn02777)依赖![](../graphics/stm_eqn02778)仅为隐式；即，它仅由其解为![](../graphics/stm_eqn00657的平衡方程组中系数的的设计依赖性暗示。

假设我们已在增量结束时求解了由[方程2.1.1-2](02s01a13-Procedures-overview-and-basic-equations.md)定义的平衡问题，并且我们有了收敛解![](../graphics/stm_eqn00657以及所有响应的值。响应![](../graphics/stm_eqn02779)相对于设计参数![](../graphics/stm_eqn02780的灵敏度定义为

![](../graphics/stm_eqn02781)上述方程中除了一项外，所有量都可以从平衡解显式确定。唯一的未知是![](../graphics/stm_eqn02782；要计算它，必须求解一个额外的方程组。

将[方程2.1.1-2](02s01a13-Procedures-overview-and-basic-equations.md)重写为

![](../graphics/stm_eqn02783)其中

![](../graphics/stm_eqn02784)上述方程中的所有量都假设依赖于设计参数![](../graphics/stm_eqn02780显式或通过位移场![](../graphics/stm_eqn00657依赖。对设计参数求导上述两方程导致以下方程：

![](../graphics/stm_eqn02785)其中

![](../graphics/stm_eqn02786)是[方程2.1.1-4](02s01a13-Procedures-overview-and-basic-equations.md)中定义的切线刚度（Jacobian）矩阵，![](../graphics/stm_eqn02787是显式可确定的量。将[方程2.18.1-3](02s18a57-Design-sensitivity-analysis.md)代入[方程2.18.1-1](02s18a57-Design-sensitivity-analysis.md)，我们获得

![](../graphics/stm_eqn02788)这是总位移DSA问题的解。

Abaqus中使用的DSA算法被称为*直接微分法*（DDM），包括以下操作。获得收敛平衡解后，必须以逐单元方式计算三个数组![](../graphics/stm_eqn02789)、![](../graphics/stm_eqn02790)和![](../graphics/stm_eqn02791)。![](../graphics/stm_eqn02791通常被称为伪荷载，因为它成为DSA问题的右边。最终DSA解通过对每个![](../graphics/stm_eqn02776)求解[方程2.18.1-3](02s18a57-Design-sensitivity-analysis.md)的方程组获得，涉及节点位移灵敏度向量![](../graphics/stm_eqn02792的未知数。然后将位移灵敏度代入[方程2.18.1-1](02s18a57-Design-sensitivity-analysis.md)计算![](../graphics/stm_eqn02793)。

DSA计算中使用的系数矩阵![](../graphics/stm_eqn02794)仅仅是平衡迭代算法中使用的最新切线刚度矩阵。在DSA计算阶段，这个矩阵仍然以分解形式可用，可以轻松检索以对DSA右边向量执行回代。这使得DSA模块成为平衡分析的高效附加组件，能够以相对较低的成本进行灵敏度计算。
### 历史相关平衡问题的增量位移DSA公式

上面提出的DSA公式简要介绍了DSA在Abaqus中的实现方式；然而，由于一些简化，讨论与大量非线性力学问题无关，特别是那些涉及所建模结构的历史相关行为的问题。在这类问题中的主要困难是，计算[方程2.18.1-2](02s18a57-Design-sensitivity-analysis.md)中残差![](../graphics/stm_eqn00694或定义设计响应所需的许多量不能表示为总位移![](../graphics/stm_eqn00657的函数。相反，在每个时间增量，它们是增量开始时某些状态变量（称为时间*t*）和增量位移![](../graphics/stm_eqn02795的函数：

![](../graphics/stm_eqn02796)

![](../graphics/stm_eqn02797)例如，见[Kleiber et al. (1997)](07s01a01-References.md)。符号![](../graphics/stm_eqn02798表示状态变量集![](../graphics/stm_eqn02799，这些可能包括张量（应力、背应力等）以及在时间*t*为特定材料点定义的标量（等效塑性应变等）。一些响应也可能直接依赖于位移![](../graphics/stm_eqn00657，而![](../graphics/stm_eqn00657增量开始时的值通常也会进入集合![](../graphics/stm_eqn02798。

在这种情况下，[方程2.18.1-4](02s18a57-Design-sensitivity-analysis.md)取以下形式：

![](../graphics/stm_eqn02800)其中

![](../graphics/stm_eqn02801)表示量![](../graphics/stm_eqn02802的*显式设计导数*。

从DSA求解算法的角度来看，总方法和增量方法之间的根本区别在于，在后一种情况下，所有状态变量![](../graphics/stm_eqn02799有效地成为额外的或*内部*设计响应，其灵敏度必须在每个时间增量结束时计算和更新，以便在下一个增量中进行DSA。这类内部响应的数量可能很大，对计算时间和内存需求有明显影响。

DSA求解过程类似于总位移方法。平衡计算完成后，在单元循环中组装显式设计导数数组![](../graphics/stm_eqn02803)、![](../graphics/stm_eqn02804)（伪荷载）以及相对于位移的导数![](../graphics/stm_eqn02805。设计响应集![](../graphics/stm_eqn02773)、![](../graphics/stm_eqn02774在这种情况下包括所有标量和![](../graphics/stm_eqn02799的张量分量。在直接微分法中，对每个设计参数![](../graphics/stm_eqn02780求解以下方程组：

![](../graphics/stm_eqn02806)然后将解向量代入[方程2.18.1-5](02s18a57-Design-sensitivity-analysis.md)。
### 计算方法

DSA所需的导数可以分析或数值计算。在分析方法中，有限元方程根据前几节描述的理论精确微分。这种方法实现困难，但高效并产生精确灵敏度。在数值方法中，一些或所有所需导数使用有限差分技术计算。数值方法可以进一步分为*整体*或*全局*有限差分方法和*半解析*方法。在全局有限差分方法中，响应灵敏度相对于特定设计参数通过扰动该设计参数多次（取决于有限差分技术）获得，并对每个扰动执行整个平衡分析。为每个分析保留响应，然后差分以获得响应灵敏度。这种方法计算成本高，因为必须为每个扰动求解整个平衡问题，但它易于实现。半解析方法在Abaqus中使用，可以视为分析和全局有限差分方法之间的折衷。在半解析方法中，DSA单元向量通过差分获得；但与分析方法一样，DSA解通过回代相对于![](../graphics/stm_eqn02794获得。半解析方法的优点是比分析方法更容易实现，比全局有限差分方法更高效。该方法的细节在以下段落中描述。

半解析方法的目的是通过有限差分数值计算DSA向量![](../graphics/stm_eqn02804)和![](../graphics/stm_eqn02807。为简单起见，假设有限差分技术是中心差分，这样对于给定函数![](../graphics/stm_eqn02808，*A*相对于*x*的导数为

![](../graphics/stm_eqn02809)其中![](../graphics/stm_eqn02810)是*x*的扰动。

为了一般性，考虑历史相关情况。为了近似![](../graphics/stm_eqn02811的显式设计导数，当保持增量位移恒定，同时对每个设计参数![](../graphics/stm_eqn02780施加正扰动![](../graphics/stm_eqn02812。以这种方式获得![](../graphics/stm_eqn02811的扰动值

![](../graphics/stm_eqn02813)对应于设计参数扰动的状态变化近似为

![](../graphics/stm_eqn02814)对负扰动（![](../graphics/stm_eqn02815)重复上述过程，然后将结果差分以获得显式设计导数![](../graphics/stm_eqn02804。

一旦找到（增量）位移灵敏度，可以使用

![](../graphics/stm_eqn02817)其中

![](../graphics/stm_eqn02818)获得响应灵敏度![](../graphics/stm_eqn02816。对设计参数![](../graphics/stm_eqn02780的负扰动重复该过程，然后将结果差分。

必须仔细选择有限差分区间。如果区间太小，由于差分操作期间精度丢失，会发生舍入或*消除*错误。另一方面，如果区间太大，可能会发生*截断*错误。截断错误源于差分公式基于截断的Taylor级数展开这一事实。Abaqus将自动选择提供消除和截断错误最佳折衷的扰动大小。
### 频率分析的DSA

本讨论将建立在上述概念和术语的基础上，因此建议先阅读上一节。下面的讨论根据特征值问题的特性分为两部分：distinct 特征值和重复特征值。
### Distinct 特征值情况

下面提出的理论假设所有特征值都是 distinct 的（即，没有重复特征值）。如果并非如此，需要进行额外操作以获得与重复特征值对应的特征值和特征向量灵敏度，以下灵敏度的方程将不正确。重复特征值情况将在下一节中考虑。

执行频率分析意味着求解以下特征值问题（见"特征值提取"第2.5.1节）：

![](../graphics/stm_eqn02819)其中![](../graphics/stm_eqn00280表示特征值，![](../graphics/stm_eqn02820表示特征向量，![](../graphics/stm_eqn01186是质量矩阵。此外，特征向量被缩放使得对于每个模态

![](../graphics/stm_eqn02821)或

![](../graphics/stm_eqn02822)。默认是第一种缩放方案。为了获得特征值和特征向量灵敏度，首先对设计参数![](../graphics/stm_eqn02780微分[方程2.18.1-6](02s18a57-Design-sensitivity-analysis.md)获得以下方程：

![](../graphics/stm_eqn02823)其中![](../graphics/stm_eqn00904表示特定模态编号。

左乘![](../graphics/stm_eqn02824，利用[方程2.18.1-6](02s18a57-Design-sensitivity-analysis.md)，并操作结果给出特征值灵敏度：

![](../graphics/stm_eqn02825)除了质量和刚度导数外，该方程中的所有量在特征值问题求解后都是已知的。
### 重复特征值情况

本节概述用于获得重复特征值特征值灵敏度的公式。更多信息可以在[Mills-Curran](07s01a01-References.md)（1988）和[Shaw](07s01a01-References.md)（1991）的论文中找到。当特征值![](../graphics/stm_eqn00280重复*R*次时，与![](../graphics/stm_eqn00280关联的特征向量![](../graphics/stm_eqn02826是线性无关但不唯一——这些特征向量的任何线性组合也是特征向量。由于这种非唯一性，特征向量可能不是设计参数中的连续或可微分函数。然而，可以通过正交变换获得一组*R*连续和可微分的特征向量![](../graphics/stm_eqn02827：

![](../graphics/stm_eqn02828其中![](../graphics/stm_eqn02829，而![](../graphics/stm_eqn00007是要确定的。用特征向量![](../graphics/stm_eqn02831替换[方程2.18.1-9](02s18a57-Design-sensitivity-analysis.md)中的特征向量![](../graphics/stm_eqn02830并左乘![](../graphics/stm_eqn02832，在矩阵表示中产生：

![](../graphics/stm_eqn02833其中![](../graphics/stm_eqn02834、![](../graphics/stm_eqn02835是一个对角矩阵，

![](../graphics/stm_eqn02836和

![](../graphics/stm_eqn02837)[方程2.18.1-12](02s18a57-Design-sensitivity-analysis.md)被识别为一个![](../graphics/stm_eqn02838缩减特征值问题，其*R*特征值![](../graphics/stm_eqn02835是与重复特征值![](../graphics/stm_eqn00280关联的特征值灵敏度，其特征向量为![](../graphics/stm_eqn00007。对于单个特征值![](../graphics/stm_eqn00280获得*N*个灵敏度。其物理解释是，设计参数的扰动可能导致原始重复模态分叉成多达*N*个 distinct 模态（想象一个具有圆形横截面的梁扰动成椭圆形截面；与截面原始对称性关联的重复模态现在分裂为与椭圆短轴和长轴关联的 distinct 模态）。
### 计算方法

使用半解析方法计算特征值灵敏度。正如静态DSA部分概述的，该方法的基本思想是使用有限差分计算一些所需的中间导数。在频率过程DSA的背景下，这意味着质量和刚度矩阵的导数使用有限差分计算。
### 选择有限差分区间

Abaqus使用启发式算法自动确定差分方案中使用的扰动大小。该算法的目标是选择能导致准确计算导数的扰动大小。这是在逐单元基础上完成的，因此对于给定设计参数，一个单元的扰动大小可能与另一个单元的扰动大小不同。扰动大小的选择基于每个设计参数![](../graphics/stm_eqn02780的标量度量![](../graphics/stm_eqn02839的行为。该度量必须既方便又代表数值差分的项。选择如下：

静态步骤。对于静态步骤，标量度量选择为单元伪荷载的范数：

![](../graphics/stm_eqn02840由于获得准确灵敏度解需要准确的伪荷载，伪荷载的范数是![](../graphics/stm_eqn02839的适当选择。这个选择也是方便的，因为伪荷载无论如何都必须计算。

频率步骤。对于频率步骤，标量度量选择为矩阵![](../graphics/stm_eqn02841到特征向量![](../graphics/stm_eqn02842的投影：

![](../graphics/stm_eqn02843)的选择取决于给定模态![](../graphics/stm_eqn00904)是具有 distinct 特征值还是与重复特征值关联。

如果模态![](../graphics/stm_eqn00904)具有 distinct 特征值，![](../graphics/stm_eqn02842取为![](../graphics/stm_eqn02824。因此，![](../graphics/stm_eqn02839变得仅仅是[方程2.18.1-10](02s18a57-Design-sensitivity-analysis.md)分子的简化。因此，![](../graphics/stm_eqn02839是特征值灵敏度大小的直接度量，也是方便的，因为这个项已经必须计算以获得特征值灵敏度。

与distinct 特征值情况不同，重复特征值的灵敏度不能独立处理。重复特征值的灵敏度从相同的缩减特征值系统同时提取，并且该系统通过数值差分获得（回想[方程2.18.1-12](02s18a57-Design-sensitivity-analysis.md)和[方程2.18.1-13](02s18a57-Design-sensitivity-analysis.md)）。因此，必须使用单个扰动大小（对于每个设计参数）来获得重复特征值的所有灵敏度。为了计算单个扰动大小，通过将![](../graphics/stm_eqn02842作为与重复特征值关联的特征向量之和来获得单个标量度量。![](../graphics/stm_eqn02839的计算类似于矩阵![](../graphics/stm_eqn02644的计算（通过数值差分获得的缩减特征值系统中的唯一项）；因此，这个选择![](../graphics/stm_eqn02839既代表重复特征值情况，又涉及已经正在执行以获得缩减特征值系统的差分计算。

算法的基本思想是针对一系列扰动大小![](../graphics/stm_eqn02844)、![](../graphics/stm_eqn02845计算标量度量![](../graphics/stm_eqn02839，它们相差数量级。对于每个![](../graphics/stm_eqn02844，计算相应的![](../graphics/stm_eqn02846。在连续扰动大小之间![](../graphics/stm_eqn02839的相对变化，计算为![](../graphics/stm_eqn02847，用于测量扰动大小接近最优的程度。在这些扰动大小中，产生最小相对变化的一个，记为![](../graphics/stm_eqn02848，被确定为最佳扰动大小，![](../graphics/stm_eqn02849。如果![](../graphics/stm_eqn02848不小于指定的容差，则扩大扰动大小范围（直到某个限制），并继续测试。重要的是要认识到，![](../graphics/stm_eqn02850不直接用于评估数值微分的准确性，而是作为确定最佳扰动大小的一种手段。因此，对![](../graphics/stm_eqn02848设置更严格的容差会导致算法投入更多努力寻找最佳扰动大小，但不保证更准确的灵敏度。
### 参考

### 参考

"Abaqus Analysis User's Guide"第19.1.1节"设计灵敏度分析"
