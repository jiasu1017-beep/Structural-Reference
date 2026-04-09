# 4.7 Mullins效应和永久变形

### 4.7 Mullins效应和永久变形

"Mullins效应"，第4.7.1节

"永久变形"，第4.7.2节
# 4.7.1 Mullins效应

### 4.7.1 Mullins效应

**产品：** Abaqus/Standard  Abaqus/Explicit

Abaqus中提供的Mullins效应材料模型旨在模拟应力软化现象，这种现象常见于填充橡胶弹性体中，是由于与应变相关的损伤造成的。当弹性体试样从原始状态进行简单拉伸后卸载，然后重新加载时，重新加载所需的应力小于初始加载时的应力（直到初始加载达到的最大拉伸）。这种应力软化现象被称为Mullins效应（Mullins, 1947）。

![](../graphics/stm_eqn07043.gif)![](../graphics/stm_eqn07044.gif)![](../graphics/stm_eqn07044.gif)![](../graphics/stm_eqn07045.gif)![](../graphics/stm_eqn07046.gif)![](../graphics/stm_eqn07047.gif)![](../graphics/stm_eqn07047.gif)![](../graphics/stm_eqn07048.gif)![](../graphics/stm_eqn07049.gif)![](../graphics/stm_eqn07050.gif)![](../graphics/stm_eqn07049.gif)![](../graphics/stm_eqn07049.gif)![](../graphics/stm_eqn07051.gif)![](../graphics/stm_eqn07049.gif)### 材料行为

![](../graphics/stm_eqn07048.gif)以下各节详细描述Abaqus中Mullins效应模型。理想化材料行为

Mullins效应在图4.7.1–1中定性地描述。

![](../graphics/stm_eqn07052.gif)![](../graphics/stm_eqn07053.gif)![](../graphics/stm_eqn07054.gif)![](../graphics/stm_eqn02098.gif)![](../graphics/stm_eqn02098.gif)![](../graphics/stm_eqn02098.gif)图4.7.1–1 具有Mullins效应的理想化响应。

![](../graphics/stm_eqn07055.gif)![](../graphics/stm_eqn02098.gif)![](../graphics/stm_eqn02098.gif)![](../graphics/stm_eqn07054.gif)![](../graphics/stm_eqn02098.gif)![](../graphics/stm_eqn02098.gif)![](../graphics/stm_eqn07053.gif)![](../graphics/stm_eqn07056.gif)![](../graphics/stm_eqn02098.gif)![](../graphics/stm_eqn02098.gif)![](../graphics/stmmullins-idealized-response-nls.png)

本图及附带描述基于Ogden和Roxburgh的工作（Ogden and Roxburgh, 1999），该工作是Abaqus中实现的模型基础。考虑一个先前无应力材料的初始加载路径，当加载到任意点时，从该点卸载时遵循路径。当材料再次加载时，软化路径被重新追踪为。如果随后施加进一步加载，则遵循路径，其中是初始加载路径的延续（即如果没有卸载将遵循的路径）。如果现在在停止加载，则在卸载时遵循路径，然后在重新加载时重新追踪回。如果不施加超出范围的进一步加载，则曲线代表后续材料响应，此时为弹性。对于超出范围的加载，再次遵循主路径，并重复所述模式。这是Mullins效应的理想表示。关于实际行为的更多细节以及显示此类行为的测试数据如何用于校准Abaqus的Mullins效应模型，请参阅"Abaqus Analysis User's Guide"第22.6.1节的"Mullins效应"，以及"Abaqus Example Problems Guide"第3.1.7节的"带Mullins效应和永久变形的实心圆盘分析"。

![](../graphics/stm_eqn07057.gif)![](../graphics/stm_eqn07058.gif)![](../graphics/stm_eqn07059.gif)加载路径此后将被称为"主材料响应"，主响应的一般行为可以用Abaqus中超弹性模型的标准能量势函数来定义。

![](../graphics/stm_eqn07060.gif)应力软化被解释为是由于微观层面的损伤造成的。当材料被加载时，损伤通过填充颗粒与橡胶分子链之间的键断裂而发生。不同的链连接在不同的变形水平上断裂，从而导致宏观变形时持续损伤。另一种等效解释是，导致损伤所需的能量是不可恢复的。模型基本框架

超弹性材料用应变能势函数来描述，该函数定义了单位参考体积（初始配置中的体积）中材料存储的应变能量。可以是变形梯度张量或其他适当的应变度量。为了考虑Mullins效应，Ogden和Roxburgh提出了一种基于形式为的能量函数的材料描述，其中是一个标量变量。这个标量变量通过使材料响应能够由与初始加载路径不同的卸载和后续亚最大再加载时的能量函数来控制，从而控制材料性能。由于的解释和影响，将不再适合将U视为存储的弹性势能。实际上，部分能量以应变能的形式存储，而其余部分则因损伤而耗散。图4.7.1–1中的阴影区域表示因损伤而耗散的能量，而无阴影部分表示应变能量的可恢复部分。正如Ogden和Roxburgh所指出的，由于平衡，包含导致以下附加方程：

![](../graphics/stm_eqn07061.gif)![](../graphics/stm_eqn07062.gif)![](../graphics/stm_eqn07063.gif)![](../graphics/stm_eqn07064.gif)![](../graphics/stm_eqn07065.gif)![](../graphics/stm_eqn07010.gif)![](../graphics/stm_eqn07066.gif)![](../graphics/stm_eqn02098.gif)![](../graphics/stm_eqn02098.gif)![](../graphics/stm_eqn07067.gif)![](../graphics/stm_eqn07068.gif)![](../graphics/stm_eqn07069.gif)![](../graphics/stm_eqn02098.gif)![](../graphics/stm_eqn02098.gif)上述方程决定了在变形过程中变量的演化。在变形过程中，变量可以是活跃的或非活跃的，并且可以从非活跃切换到活跃或反之亦然，以便它始终连续变化。当它不活跃时，材料表现为具有应变能的弹性材料，其中保持不变。然而，当活跃时，它由前述方程隐式地确定为的函数。材料再次表现为具有不同应变能函数的弹性材料。当参数从活跃切换到非活跃或反之时，能量以及相关应力保持连续。当不活跃时，假设其值为1且没有一般性损失。主超弹性行为

在编写Mullins效应的本构方程之前，将主材料响应的总应变能密度的偏体积和体积部分分开是有用的

![](../graphics/stm_eqn07070.gif)![](../graphics/stm_eqn07071.gif)![](../graphics/stm_eqn07064.gif)![](../graphics/stm_eqn07072.gif)![](../graphics/stm_eqn07010.gif)![](../graphics/stm_eqn02098.gif)![](../graphics/stm_eqn07073.gif)![](../graphics/stm_eqn07074.gif)![](../graphics/stm_eqn07075.gif)在上述方程中，是总应变能密度，分别是偏应变能密度和体积应变能密度。Abaqus中所有超弹性模型使用的应变能势函数已经分为偏体积和体积部分。例如，多项式模型使用形式为的应变能势

![](../graphics/stm_eqn02098.gif)![](../graphics/stm_eqn07066.gif)其中符号具有通常的解释。右边第一项表示偏体积部分，第二项表示弹性应变能密度函数的体积部分。增强应变能密度函数

![](../graphics/stm_eqn07076.gif)![](../graphics/stm_eqn02098.gif)![](../graphics/stm_eqn07077.gif)![](../graphics/stm_eqn02098.gif)![](../graphics/stm_eqn07078.gif)![](../graphics/stm_eqn07079.gif)![](../graphics/stm_eqn07080.gif)![](../graphics/stm_eqn07066.gif)![](../graphics/stm_eqn07081.gif)Mullins效应通过使用增强能量函数来考虑

![](../graphics/stm_eqn07082.gif)![](../graphics/stm_eqn07083.gif)![](../graphics/stm_eqn07084.gif)![](../graphics/stm_eqn02098.gif)![](../graphics/stm_eqn07085.gif)其中是主材料响应应变能密度的偏体积部分，例如由上面给出的多项式应变能函数右边的第一项定义；是体积应变能密度，例如由上面给出的多项式应变能函数右边的第二项定义；表示主拉伸；表示弹性体积比。函数是损伤变量的连续函数，被称为"损伤函数"。如上表达式所示，增强能量函数的偏体积部分与主响应偏能量部分通过缩放因子相关。增强能量函数的体积部分与主响应相同。上述增强能量函数形式的结果是Mullins效应仅与变形的偏体积部分相关。当要求时，增强能量函数简化为主材料响应的应变能密度函数。如前所述，这种情况对应于不活跃，物理上表示主曲线上材料点的能量。在变形继续进行时，的值连续变化。上述能量函数形式是Ogden和Roxburgh提出的形式的扩展，以考虑材料可压缩性。应力计算

![](../graphics/stm_eqn07086.gif)![](../graphics/stm_eqn07066.gif)![](../graphics/stm_eqn07085.gif)![](../graphics/stm_eqn07087.gif)通过对能量函数以通常方式求导得到的应力为

![](../graphics/stm_eqn07088.gif)其中是对应于当前偏变形水平的主材料响应的偏应力，是当前体积变形水平的主材料响应的静水压力。因此，由于Mullins效应，偏应力通过将主材料响应的偏应力与损伤变量进行简单缩放来获得。对于上述方程预测应力软化，需要在卸载（和亚最大再加载）路径上。此外，假设如此偏应力保持为正直到达到。增强响应的压力应力与主响应相同。该模型预测从任何给定应变水平沿单一曲线（通常与主加载曲线不同）进行卸载-再加载，该曲线通过应力-应变图的原点。它无法捕获卸载后的永久应变。该模型还预测，纯体积变形不会有任何相关的损伤或Mullins效应。损伤函数和损伤变量

![](../graphics/stm_eqn07089.gif)![](../graphics/stm_eqn07049.gif)![](../graphics/stm_eqn00155.gif)![](../graphics/stm_eqn07090.gif)![](../graphics/stm_eqn00155.gif)由于假定的形式和的演化方程，函数满足

![](../graphics/stm_eqn07091.gif)![](../graphics/stm_eqn07092.gif)![](../graphics/stm_eqn07093.gif)![](../graphics/stm_eqn07094.gif)![](../graphics/stm_eqn07083.gif)![](../graphics/stm_eqn07066.gif)只要函数是其参数的单调函数，上述方程就隐式地将损伤参数定义为变形的函数。从上述方程推导出的值将取决于在主加载路径上达到的主拉伸的最大值，以及所使用的函数和的具体形式。在初始加载路径上开始卸载的任何点，上式简化为

![](../graphics/stm_eqn07095.gif)![](../graphics/stm_eqn07067.gif)![](../graphics/stm_eqn07096.gif)![](../graphics/stm_eqn07097.gif)其中定义了符号。另一方面，当材料完全卸载且达到其最小值时：

![](../graphics/stm_eqn07098.gif)![](../graphics/stm_eqn01219.gif)![](../graphics/stm_eqn07099.gif)从前述两个方程可以看出，函数和量都取决于开始卸载的点。

![](../graphics/stm_eqn07100.gif)![](../graphics/stm_eqn07097.gif)![](../graphics/stm_eqn07101.gif)当材料处于完全卸载状态时，增强能量函数具有残余值

![](../graphics/stm_eqn07097.gif)![](../graphics/stm_eqn07102.gif)![](../graphics/stm_eqn02098.gif)可将其解释为材料中因损伤而耗散的能量。在诸如简单拉伸的单轴测试中，此量表示主加载曲线与相关卸载-再加载曲线之间的面积（对于直到的变形，图4.7.1–1中的阴影区域）。回想函数通过依赖于开始卸载的点，可以按照Ogden和Roxburgh的方式构造函数，使用

![](../graphics/stm_eqn07103.gif)![](../graphics/stm_eqn02098.gif)![](../graphics/stm_eqn07104.gif)![](../graphics/stm_eqn07090.gif)![](../graphics/stm_eqn01219.gif)![](../graphics/stm_eqn01219.gif)其中函数必须满足和。对于给定的，上述方程可以积分得到，如下所示：

![](../graphics/stm_eqn07105.gif)![](../graphics/stm_eqn07106.gif)![](../graphics/stm_eqn07107.gif)![](../graphics/stm_eqn07085.gif)![](../graphics/stm_eqn07108.gif)![](../graphics/stm_eqn07109.gif)![](../graphics/stm_eqn02098.gif)![](../graphics/stm_eqn07085.gif)![](../graphics/stm_eqn07110.gif)在主路径上，上述方程满足要求。Abaqus使用以下特定选择，它具有所需属性

其中r、m和是材料常数，是误差函数的反函数，其中误差函数定义为
![](../graphics/stm_eqn07111.gif)![](../graphics/stm_eqn07111.gif)![](../graphics/stm_eqn07107.gif)
上述选择当简化Ogden和Roxburgh提出的形式。
![](../graphics/stm_eqn07112.gif)
将上述形式的代入方程，可以证明损伤变量随变形按下式变化：
![](../graphics/stm_eqn07113.gif)
上述方程定义了损伤变量的演化，它是材料点在变形历史中经历的最大偏应变能密度以及材料常数r、m和的函数。当对应于主曲线上的一点，；另一方面，当移除变形时，达到其最小值。对于的所有中间值，在和之间单调变化。材料切线刚度
![](../graphics/stm_eqn07114.gif)![](../graphics/stm_eqn07111.gif)
Abaqus/Standard中的非线性求解过程需要材料切线刚度或材料Jacobian。材料切线刚度的推导遵循"超弹性材料行为"第4.6.1节中概述的程序。由于Mullins效应，的表达式被修改。其余项相同。为了确定的形式，可以注意到具有Mullins效应的偏应力可以用主材料响应的偏应力和损伤变量表示为

![](../graphics/stm_eqn07115.gif)![](../graphics/stm_eqn07097.gif)![](../graphics/stm_eqn02098.gif)![](../graphics/stm_eqn07116.gif)![](../graphics/stm_eqn07066.gif)从上述方程可得

![](../graphics/stm_eqn07117.gif)![](../graphics/stm_eqn07118.gif)![](../graphics/stm_eqn07085.gif)![](../graphics/stm_eqn07108.gif)![](../graphics/stm_eqn02098.gif)经过一些处理，可以证明

![](../graphics/stm_eqn07119.gif)![](../graphics/stm_eqn07120.gif)它决定了。损伤耗散

![](../graphics/stm_eqn07121.gif)![](../graphics/stm_eqn07122.gif)![](../graphics/stm_eqn07123.gif)![](../graphics/stm_eqn07115.gif)![](../graphics/stm_eqn07124.gif)![](../graphics/stm_eqn07090.gif)![](../graphics/stm_eqn01219.gif)![](../graphics/stm_eqn07125.gif)![](../graphics/stm_eqn07126.gif)![](../graphics/stm_eqn07127.gif)![](../graphics/stm_eqn07124.gif)如前所述，量决定了因损伤而耗散的能量。可以通过将积分变量从到的变量替换来积分解析地积分方程，得到函数的以下表达式：

![](../graphics/stm_eqn07128.gif)![](../graphics/stm_eqn07129.gif)![](../graphics/stm_eqn07130.gif)![](../graphics/stm_eqn07131.gif)![](../graphics/stm_eqn07129.gif)损伤耗散可以通过代入（其中通过在表达式中设置获得）从上述表达式获得，如下所示：

应变能量的可恢复部分可以通过从总增强能量中减去损伤耗散来获得

当材料完全或几乎不可压缩时，我们可以假设，并且沿主曲线最大变形的总能量为以下讨论涉及上述极限。从损伤耗散的表达式，可以注意到当，耗散与的比值是一个仅取决于材料参数r和的常数。特别地，该比值与无关，表明耗散与总能量的比值是一个与变形水平无关的常数。对于非零m，上述情况仅在时成立，这对应于相对较大的变形水平。在这种情况下当，能量耗散为零。因此，m的值（零和非零）可以被认为是为总变形应变能量水平提供的标度，超过该水平就会发生耗散。特别是当时，耗散发生在低应变水平。

上述行为在图4.7.1–2中描述，其中显示了归一化耗散与变形的比值的关系图，对于非零m和固定的参数值。当比值较小时，耗散趋于零，而当比值较大时，归一化耗散接近一个常数渐近值。

图4.7.1–2 归一化耗散与变形的关系。

![](../graphics/stmmullins-dissip.png)
### 参考

### 参考

"Abaqus Analysis User's Guide"第22.6.1节的"Mullins效应"
