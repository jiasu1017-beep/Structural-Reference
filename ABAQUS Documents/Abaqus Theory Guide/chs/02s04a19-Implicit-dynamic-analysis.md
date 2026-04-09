# 2.4.1 隐式动力学分析

### 2.4.1 隐式动力学分析

**产品：** Abaqus/Standard

Abaqus为线性和非线性问题提供动力学分析选项。对于纯线性系统，基于系统特征模态的方法几乎总是被选择，因为它们可以提供对结构行为的洞察，而这是其他方式无法获得的，而且它们通常比通常用于非线性问题的直接积分方法更具成本效益。Abaqus/Standard中提供的线性动力学分析方法在"模态动力学"第2.5节中讨论。对于轻度非线性动力学分析问题，提供了"模态投影方法"。该方法的基础是使用线性系统的特征模态（从特征频率分析中提取）作为一组全局Ritz函数——在有限元方法的术语中一组全局插值函数——其振幅定义响应。Abaqus/Standard为此选项提供使用显式中心差分算子的直接时间积分。对于任何更严重的非线性情况，动力学响应通过直接时间积分有限元模型的所有自由度来获得。为此类分析提供的方法在本节中讨论。

在动力学分析中选择用于积分运动方程的算子受许多因素影响。Abaqus/Standard旨在分析结构部件，这意味着我们寻找结构的整体动力学响应，这与与连续体中相对局部响应相关的波传播解决方案形成对比。[Belytschko (1976)](07s01a01-References.md) 将这些标记为"惯性问题"并分类为"波效应如聚焦、反射和衍射不重要"。结构问题被认为是"惯性"的，因为所寻求的响应时间相对于波穿越结构所需的时间是较长的。

动力学积分算子广泛地表征为隐式或显式。显式方案（如在Abaqus/Explicit中使用的）完全基于时间 *t* 的可用值获得在 ![](../graphics/stm_eqn00438.gif) 处的动力学量的值。中心差分算子，这是应力分析应用中最常用的显式算子，仅条件稳定，稳定性极限大约等于弹性波穿越模型中最小单元尺寸的时间。隐式方案通过不仅基于 *t* 的值而且还基于 ![](../graphics/stm_eqn00438.gif) 处的这些相同量来求解时间 ![](../graphics/stm_eqn00438.gif) 处的动力学量来消除时间步长大小的这个上限。但是因为它们是隐式的，所以必须求解非线性方程。在结构问题中，隐式积分方案通常以通常比简单显式方案的稳定性极限大一到两个数量级的时间步长给出可接受的解，但随着时间步长 ![](../graphics/stm_eqn00883.gif) 相对于典型响应模式的周期 *T* 增加，响应预测会变差。例如，参见 [Hilber, Hughes, and Taylor (1977)](07s01a01-References.md) 和 [Hilber and Hughes (1978)](07s01a01-References.md) 讨论此类误差。选择最大允许时间步长大小时应考虑三个因素：施加荷载的变化速率、非线性阻尼和刚度特性的复杂性，以及结构的典型振动周期。通常，最大增量与周期比 ![](../graphics/stm_eqn00884.gif) 1/10 是获得可靠结果的良好经验法则。因此，两种积分技术的相对经济性取决于显式方案的稳定性极限、非线性方程对隐式算子求解的难易程度、与显式方案的稳定性极限相比隐式方案可提供可接受精度的相对时间增量大小，以及模型的大小。

在Abaqus/Standard中，隐式积分的时间步长可以基于"半增量残差"自动选择，这是 [Hibbitt and Karlsson (1979)](07s01a01-References.md) 引入的概念。通过在获得 ![](../graphics/stm_eqn00438.gif) 处的解后监测 ![](../graphics/stm_eqn00885.gif) 处平衡残差的值，可以评估解的精度并适当调整时间步长。

为了进一步讨论动力学过程，我们写出整体平衡方程中的 d'Alembert 力，[方程 2.1.1-1](02s01a13-Procedures-overview-and-basic-equations.md)。一点的体力 ![](../graphics/stm_eqn00480.gif) 可以写为外部规定的体力 ![](../graphics/stm_eqn00319.gif) 和 d'Alembert 力：

![](../graphics/stm_eqn00886.gif)其中 ![](../graphics/stm_eqn00593.gif) 是该点处材料的当前密度，![](../graphics/stm_eqn00428.gif) 是该点的位移。虚功方程中的体力项为

![](../graphics/stm_eqn00887.gif)d'Alembert 项可以更方便地以参考体积和参考密度 ![](../graphics/stm_eqn00888.gif) 写出为

![](../graphics/stm_eqn00889.gif)其中 ![](../graphics/stm_eqn00890.gif) 是加速度场。当使用隐式积分时，平衡方程写在时间步长结束时（在时间 ![](../graphics/stm_eqn00438.gif)），并且 ![](../graphics/stm_eqn00890.gif) 由时间积分算子计算。插值器近似点的位移为

![](../graphics/stm_eqn00891.gif)所以

![](../graphics/stm_eqn00892.gif)假设 ![](../graphics/stm_eqn00893.gif) 不依赖于位移。对于Abaqus中的大多数单元就是这种情况；对于不正确的那些情况（Hermite 三次梁，B23 和 B33）中 d'Alembert 力项所采取的形式在第3章"单元"中有详细讨论。利用这个插值假设，d'Alembert 力项为

![](../graphics/stm_eqn00894.gif)即，一致质量矩阵乘以节点变量的加速度。平衡的有限元近似，[方程 2.1.1-2](02s01a13-Procedures-overview-and-basic-equations.md)，是

![](../graphics/stm_eqn00895.gif)其中

![](../graphics/stm_eqn00896.gif)是一致质量矩阵，

![](../graphics/stm_eqn00897.gif)是内力向量，

![](../graphics/stm_eqn00898.gif)是外力向量。在这个上下文中，"矩阵"和"向量"术语指的是节点变量空间中的矩阵和向量 ![](../graphics/stm_eqn00657.gif)。

上面引入的质量矩阵定义是"一致"质量：通过一致使用插值获得的质量矩阵。Abaqus中的一阶单元都使用"集中"质量，其中质量矩阵是对角矩阵。集中矩阵通过将一致矩阵的每一行加到对角上来获得。对于这些一阶单元，集中质量矩阵在计算简单模型固有频率的数值实验中给出更准确的结果。

Abaqus/Standard中可用于动力学问题时间积分的隐式算子包括由 [Hilber, Hughes, and Taylor (1977)](07s01a01-References.md) 定义的算子和后向 Euler 算子。Hilber-Hughes-Taylor 算子是具有可控数值阻尼的 Newmark 算子的推广——阻尼在自动时间步长方案中最有价值，因为当时间步长变化时不可避免地引入的轻微高频数值噪声被少量数值阻尼快速消除。算子用时间步长结束时的 d'Alembert 力平衡和时间步长开始和结束时静态力的加权平均替换实际平衡方程（[方程 2.4.1-1](02s04a19-Implicit-dynamic-analysis.md)）：

![](../graphics/stm_eqn00899.gif)其中 ![](../graphics/stm_eqn00900.gif) 是与自由度 *N* 相关的所有拉格朗日乘子力的和。算子定义由位移和速度积分的 Newmark 公式完成：

![](../graphics/stm_eqn00901.gif)和

![](../graphics/stm_eqn00902.gif)

![](../graphics/stm_eqn00903.gif)以及

![](../graphics/stm_eqn00903.gif)

[Hilber, Hughes, and Taylor (1977)](07s01a01-References.md) 提出了令人信服的论据支持使用 [方程 2.4.1-2](02s04a19-Implicit-dynamic-analysis.md)–[方程 2.4.1-4](02s04a19-Implicit-dynamic-analysis.md) 积分结构动力学问题。该算子的主要吸引力是其可控数值阻尼以及这种阻尼采取的形式，在低频处缓慢增长，在高频处阻尼增长更快。数值阻尼量的控制由参数 ![](../graphics/stm_eqn00904.gif) 提供：随着 ![](../graphics/stm_eqn00905.gif)，没有阻尼，算子是梯形法则（Newmark，![](../graphics/stm_eqn00906.gif)）；而随着 ![](../graphics/stm_eqn00907.gif)，可以获得显著阻尼。使用此算子主要是因为它提供的轻微数值阻尼在自动时间步长方案中是需要的。每次时间步长变化都会在解中引入一些轻微的噪声或"振铃"；少量数值阻尼（![](../graphics/stm_eqn00908.gif) 看起来是个不错的选择）可以快速消除这种高频噪声，而不会对有意义的较低频率响应产生任何重大影响。提供能量内容输出，应该打印以监测整体能量平衡。这已在 [Abaqus Example Problems Guide](exa-link.md) 中的动力学示例中完成，并表明数值耗散始终相当小（不到总能量的1%）。

![](../graphics/stm_eqn00909.gif)![](../graphics/stm_eqn00910.gif)![](../graphics/stm_eqn00911.gif)![](../graphics/stm_eqn00904.gif)![](../graphics/stm_eqn00438.gif)![](../graphics/stm_eqn00883.gif)在隐式动力学计算期间对旋转的积分是为了在旋转惯性在不同方向上不同的情况下保持精度而进行的。为此，加速度在身体轴系统中积分，使得 Newmark 公式给出速度变化为

![](../graphics/stm_eqn00909.gif)其中 ![](../graphics/stm_eqn00910.gif) 是节点的角速度，![](../graphics/stm_eqn00911.gif) 是其角加速度，两者都在时间 *t* 或时间 ![](../graphics/stm_eqn00438.gif) 处 ![](../graphics/stm_eqn00904.gif) 身体轴的当前方向中取得；![](../graphics/stm_eqn00883.gif) 是时间增量。

![](../graphics/stm_eqn00912.gif)![](../graphics/stm_eqn00913.gif)在全局系统中这是

![](../graphics/stm_eqn00912.gif)其中 ![](../graphics/stm_eqn00913.gif) 是定义身体轴系统的标准正交基向量。因为这些是标准正交向量，所以可以重写为

![](../graphics/stm_eqn00914.gif)其中 ![](../graphics/stm_eqn00915.gif) 是增量旋转矩阵。设 ![](../graphics/stm_eqn00916.gif) 是从时间 *t* 到 ![](../graphics/stm_eqn00917.gif) 的旋转增量。然后 ![](../graphics/stm_eqn00915.gif) 是

![](../graphics/stm_eqn00918.gif)其中 ![](../graphics/stm_eqn00919.gif) 是具有轴向量 ![](../graphics/stm_eqn00920.gif) 的斜对称矩阵。关于旋转变量、旋转矩阵和斜对称矩阵的指数映射的讨论，请参见"旋转变量"第1.3.1节。

![](../graphics/stm_eqn00921.gif)![](../graphics/stm_eqn00922.gif)![](../graphics/stm_eqn00923.gif)![](../graphics/stm_eqn00917.gif)Newmark 关于身体轴系统中旋转增量的时间积分公式给出

![](../graphics/stm_eqn00921.gif)由于 ![](../graphics/stm_eqn00922.gif)，分量 ![](../graphics/stm_eqn00923.gif) 在时间 *t* 或 ![](../graphics/stm_eqn00917.gif) 相对于身体轴是相同的。在全局系统中这是

![](../graphics/stm_eqn00924.gif)求解时间 ![](../graphics/stm_eqn00917.gif) 处的未知速度和加速度，速度更新方程为

![](../graphics/stm_eqn00925.gif)加速度更新方程变为

![](../graphics/stm_eqn00926.gif)

![](../graphics/stm_eqn00927.gif)后向 Euler 算子求解时间步长结束时的平衡方程（[方程 2.4.1-1](02s04a19-Implicit-dynamic-analysis.md)）并使用

![](../graphics/stm_eqn00927.gif)和

![](../graphics/stm_eqn00928.gif)

更新位移和速度。

Abaqus 中动力学问题的自动时间步长基于 [Hibbitt and Karlsson (1979)](07s01a01-References.md) 首次提出的半增量残差。这个概念在直觉上很有吸引力。在每个时间步长结束时满足 [方程 2.4.1-1](02s04a19-Implicit-dynamic-analysis.md)（或者实际上是 Hilber-Hughes-Taylor 形式，[方程 2.4.1-2](02s04a19-Implicit-dynamic-analysis.md)）确保在这些时间点的有限元模型的离散意义上平衡，但并没有说明中间时间点平衡质量的信息。半增量残差的思想是计算某个中间时间点（选择为 ![](../graphics/stm_eqn00885.gif)）处平衡残差误差（[方程 2.4.1-1](02s04a19-Implicit-dynamic-analysis.md) 的左边）的大小，并通过该误差的大小评估动力学响应预测的误差。

![](../graphics/stm_eqn00438.gif)![](../graphics/stm_eqn00438.gif)半增量残差基于加速度在时间间隔上线性变化的假设（这是 Newmark 公式的基础），所以对于任何节点位移或旋转分量 *u*：

![](../graphics/stm_eqn00929.gif)

在已经求解了 ![](../graphics/stm_eqn00438.gif) 处的状态后，此方程与现在为从 *t* 到 ![](../graphics/stm_eqn00438.gif) 的时间间隔写的 Newmark 公式一起，要求

![](../graphics/stm_eqn00930.gif)其中

![](../graphics/stm_eqn00931.gif)是时间为步长获得的位移增量，![](../graphics/stm_eqn00883.gif)。

![](../graphics/stm_eqn00933.gif)![](../graphics/stm_eqn00934.gif)![](../graphics/stm_eqn00935.gif)![](../graphics/stm_eqn00885.gif)利用这些方程，可以评估步长内任何时间的平衡残差。显然，如果解是准确的，此残差将与问题中的重要力相比较小。时间步长结束时的残差为

![](../graphics/stm_eqn00932.gif)步长开始时的残差为

![](../graphics/stm_eqn00933.gif)其中 ![](../graphics/stm_eqn00934.gif) 是前一步长开始时的时间，或者如果是初始加速或冲击计算后的第一个增量，则为 ![](../graphics/stm_eqn00935.gif)。然后 ![](../graphics/stm_eqn00885.gif) 处的残差定义为

![](../graphics/stm_eqn00936.gif)其中 ![](../graphics/stm_eqn00937.gif) 等是为时间 ![](../graphics/stm_eqn00717.gif) 处的条件计算的，

![](../graphics/stm_eqn00938.gif)"半增量残差" ![](../graphics/stm_eqn00939.gif) 定义为 ![](../graphics/stm_eqn00940.gif) 中最大条目的大小，并提供时间步长解精度的度量。

![](../graphics/stm_eqn00942.gif)半增量残差计算背后的动机是提供给定时间步长解精度的度量。数值测试表明它提供了对动力学解的敏感精度检查，并表明如果 *P* 是无阻尼弹性系统（必须相当准确地模拟高频响应）中真实力的典型大小，那么

如果 ![](../graphics/stm_eqn00941.gif) 持续地，时间步长解具有高精度；

如果 ![](../graphics/stm_eqn00942.gif) 持续地，时间步长解具有中等良好精度；

如果 ![](../graphics/stm_eqn00943.gif) 持续地，时间步长解相当粗糙。

![](../graphics/stm_eqn00944.gif)具有大量自然能量耗散的问题，如弹塑性系统，通常对时间步长选择不如纯弹性问题敏感，因为出现在较高频率模式中的能量会快速耗散。在这种情况下，典型力 1-10 倍范围内的最大半增量残差表示对大多数研究来说精度相当可接受，甚至 10-100 倍典型力的值也可以为总体变形等主要效应提供有用的结果。因此，该方法可以为高度耗散系统提供相对经济高效的解决方案，而我们只需要对整体响应进行适度准确的预测。

半增量残差是自适应时间增量方案的基础。如果半增量残差很小，则表明解的精度很高，可以安全地增加时间步长；相反，如果半增量计算显示解粗糙，则应减少所用时间步长。该算法在"Abaqus Analysis User's Guide"第7.2.4节"瞬态问题中的时间积分精度"中有详细描述。该算法本质上是经验性的，但经验表明它相当有效 [(Hibbitt and Karlsson, 1979)](07s01a01-References.md)，特别是在具有高耗散的初始激发问题中，如冲击加载问题（或短持续时间强迫问题）伴有广泛塑性。在这些情况下，该方案是经济的，因为时间步长随着求解的进行自然增加，而高频响应被耗散。

上述观察基于使用 Hilber-Hughes-Taylor 算子，![](../graphics/stm_eqn00944.gif)。算子引入的轻微数值阻尼消除了当时间步长变化时不可避免地进入解的噪声。即使在相当长的问题中，基于模型中物理机制计算的总体能量也很好地平衡。能量平衡计算有助于评估解——例如，可以测量塑性消耗的能量——建议用户在用Abaqus进行任何分析时请求偶尔打印能量平衡计算。
### 参考

### 参考

"Abaqus Analysis User's Guide" 第6.3.2节"使用直接积分的隐式动力学分析"