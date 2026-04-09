# 2.5.1 特征值提取

### 2.5.1 特征值提取

![](../graphics/stm_eqn01154.gif)**产品：** Abaqus/Standard

结构分析中有许多重要领域，提取系统特征值从而获得其固有振动频率或研究可能与运动学不稳定相关的可能分岔是必不可少的。例如，地震事件的结构评估通常基于线性分析，使用结构的模态直到某个有限的截止频率（通常取为 33 Hz（周期/秒））。一旦模态可用，它们的正交性允许将结构的线性响应构建为多个单自由度系统的响应。这为几种计算成本低廉且能提供对结构动力学行为有用洞察的响应评估方法开辟了道路。Abaqus/Standard 提供了几种此类方法并在以下章节中描述。

数学特征值问题是一个经典研究领域，已投入大量工作来提供特征值提取方法。[Wilkinson (1965)](07s01a01-References.md) 的书提供了该问题的优秀综述。有限元模型产生的特征值问题是特殊情况：它们涉及大但通常窄带状的矩阵，并且通常只需要少量特征值对。对于许多重要情况，矩阵是对称的。有限元模型小振动固有模态的特征值问题为

![](../graphics/stm_eqn01082.gif)或者，用经典矩阵符号，

![](../graphics/stm_eqn01083.gif)其中 ![](../graphics/stm_eqn01084.gif) 是质量矩阵，在此处感兴趣的问题中是对称正定的；![](../graphics/stm_eqn01085.gif) 是阻尼矩阵；![](../graphics/stm_eqn01086.gif) 是刚度矩阵，可能包括大位移效应，如"应力刚化"（初始应力项），因此可能不是正定或对称的；![](../graphics/stm_eqn01087.gif) 是特征值；![](../graphics/stm_eqn01088.gif) 是特征向量——振动模态。这个方程可以从系统的平衡方程的线性扰动立即获得。

特征系统（[方程 2.5.1-1](02s05a24-Eigenvalue-extraction.md)）通常会有复特征值和复特征向量。该系统可以通过假设 ![](../graphics/stm_eqn01086.gif) 是对称的并在特征值提取期间忽略 ![](../graphics/stm_eqn01085.gif) 来对称化。对称化系统具有实平方特征值 ![](../graphics/stm_eqn01089.gif) 和仅实特征向量。

通常，对于对称特征值问题，我们还将假设 ![](../graphics/stm_eqn01086.gif) 是半正定的。在这种情况下，![](../graphics/stm_eqn01087.gif) 成为纯虚特征值，![](../graphics/stm_eqn01090.gif)，其中 ![](../graphics/stm_eqn01091.gif) 是圆频率，特征值问题可以写为

![](../graphics/stm_eqn01092.gif)如果模型包含混合单元、接触对或接触单元，方程组包含拉格朗日乘子，刚度矩阵 ![](../graphics/stm_eqn01086.gif) 变为不定的。但是，对应于拉格朗日乘子的质量矩阵的所有项都等于零。因此，所有特征值都是纯虚的，特征值问题仍然可以写为 [方程 2.5.1-2](02s05a24-Eigenvalue-extraction.md)。

Abaqus 为对称和复特征值问题提供特征值提取过程。对于对称化特征值问题，Abaqus/Standard 提供两种方法：Lanczos 和子空间迭代方法。对于复特征值问题，使用子空间投影方法。
### 对称系统的特征值提取

自从有限元模型出现以来，结构特征值问题受到了相当多的关注。[Ramaswami (1979)](07s01a01-References.md) 总结了可用的方法：最吸引人的似乎是 Lanczos 方法（例如参见 [Newman and Pipano, 1973](07s01a01-References.md)；[Parlett, 1980](07s01a01-References.md)）和子空间迭代方法，这是由 [Bathe and Wilson (1972)](07s01a01-References.md) 引入有限元应用的经典方法。

![](../graphics/stm_eqn01100.gif)子空间迭代和 Lanczos 方法都使用 Householder 和 Q-R 算法求解简化特征值问题，已在 Abaqus/Standard 中实现。这些算法的各个部分在本节其余部分讨论。子空间迭代——基本算法

将子空间迭代方法应用于来自结构动力学行为的有限元模型的特征值问题已由多位作者讨论——参见 [Ramaswami (1979)](07s01a01-References.md) 的参考文献。基本思想是同时逆幂迭代。创建一小组基向量，从而定义一个"子空间"：然后通过迭代将此"子空间"转换为包含整个系统最低几个特征向量的空间。

假设在第 *i* 次迭代时，存在一组 *m* 个向量，![](../graphics/stm_eqn01093.gif)、![](../graphics/stm_eqn01094.gif)，其中 *m* 小于有限元模型中的变量数。这些被视为定义 *n* 维空间中 *m* 维子空间的"基向量"，*n* 维空间由有限元模型中的变量定义。我们将这些向量排列为矩阵 ![](../graphics/stm_eqn01095.gif) 中的列。因此，![](../graphics/stm_eqn01095.gif) 的行数是完整方程组的大小（有限元模型中的变量数 *N*），列数是子空间的维数 *m*。

算法的第一步是通过求解定义一组新的基向量

![](../graphics/stm_eqn01096.gif)此操作，带有 *m* 个向量的广义"逆幂扫描"，涉及求解完整线性刚度方程组用于多个右边向量（在前一次迭代之后，使用先前分解的矩阵）。

然后将结构的刚度矩阵和质量矩阵投影到子空间上

![](../graphics/stm_eqn01097.gif)从而在子空间中定义质量矩阵 ![](../graphics/stm_eqn01098.gif) 和刚度矩阵 ![](../graphics/stm_eqn01099.gif)。这些矩阵是 *m* 乘 *m* 的。特征值问题

![](../graphics/stm_eqn01100.gif)现在使用下面讨论的 Householder 和 Q-R 方法在子空间中完全求解。

特征向量现在已在约化空间中定义，可以转换回结构问题的完整空间，定义为下一次迭代的 ![](../graphics/stm_eqn01101.gif)：

![](../graphics/stm_eqn01102.gif)其中 ![](../graphics/stm_eqn01103.gif)。这完成一次迭代。

对于 ![](../graphics/stm_eqn01104.gif)（一维子空间），该方法简化为简单的"逆幂扫描"方法（参见 [Wilkinson, 1965](07s01a01-References.md) 或 [Strang, 1976](07s01a01-References.md)）。

子空间方法的优点是在约化空间中提取特征值，这将导致快速收敛到完整空间中的特征向量。因此，迭代中携带的基向量数量和初始基向量的选择对于经济求解是重要的。特定特征值的收敛速率与 ![](../graphics/stm_eqn01105.gif) 成比例，其中 ![](../graphics/stm_eqn01106.gif) 是超出用于定义子空间的 *m* 个向量之外的下一个向量 ![](../graphics/stm_eqn01107.gif) 对应的特征值。Abaqus/Standard 使用的 *m* 的默认值是 ![](../graphics/stm_eqn01108.gif)，其中 *p* 是请求的特征向量数。如果使用更多向量，所需迭代次数减少，但每次迭代由于更多右边向量而花费更长时间。增加 *m* 有时能显著提高算法性能。

起始向量的选择也很重要。不要求这些接近特征向量以快速收敛。只要基向量跨越特征向量的空间，Householder 和 Q-R 步骤就会将向量旋转到特征向量中。Abaqus/Standard 中使用的起始向量选择方法是 [Bathe and Wilson (1972)](07s01a01-References.md) 的方法。他们建议使用对角质量项作为一个向量：其他向量是单位向量，在具有最大质量项的节点和自由度处提供一组单单位条目。进行检查以确保所有自由度在这些附加向量中都有表示。

这完成了在 Abaqus/Standard 中实现的基本子空间迭代算法的描述。必须找到所有特征值对的简化特征值问题由 Householder 和 Q-R 算法求解。这些算法在本节末尾描述。Lanczos 特征值求解器

Lanczos 特征值求解器作为提取稀疏对称广义特征值问题的极端特征值及相应特征向量的强大工具的实现已由多位作者讨论；例如参见 [Parlett (1980)](07s01a01-References.md)、[Parlett and Nour-Omid (1989)](07s01a01-References.md)、[Simon (1984)](07s01a01-References.md) 和 [Ericsson and Ruhe (1980)](07s01a01-References.md)。[Grimes, Lewis, and Simon (1994)](07s01a01-References.md) 开发和详细描述了一种移位块 Lanczos 算法。

Abaqus/Standard 中的 Lanczos 过程包括一组 Lanczos"运行"，每组执行称为步骤的迭代序列。对于每个 Lanczos 运行，应用以下谱变换：

![](../graphics/stm_eqn01109.gif)其中 ![](../graphics/stm_eqn01110.gif) 是移位，![](../graphics/stm_eqn01111.gif) 是特征值，![](../graphics/stm_eqn01088.gif) 是特征向量。此变换允许快速收敛到期望的特征值。对称化问题（[方程 2.5.1-2](02s05a24-Eigenvalue-extraction.md)）和变换问题（[方程 2.5.1-5](02s05a24-Eigenvalue-extraction.md)）的特征向量相同，而原始问题和变换问题的特征值以下列方式相关：

![](../graphics/stm_eqn01112.gif)

当继续被认为效率低下时，Lanczos 运行将终止。通常，在单个 Lanczos 运行中仅计算数十个特征值（最接近移位值）。通过使用不同移位值执行多次运行来计算许多特征模态的可能性是 Lanczos 特征值求解器的重要特征。

在每次运行中，创建 Krylov 子空间的序列，并在一系列"步骤"中计算每个子空间上特征向量的最佳可能近似。这与子空间迭代方法形成对比，在子空间迭代方法中，用于近似特征向量的子空间维数是固定的。

理论上，基本 Lanczos 过程（在"精确"计算假设下不考虑舍入误差）能够仅确定简单特征值。移位策略（及其一部分的 Sturm 序列检查）检测缺失的模态，并在后续 Lanczos 运行期间强制计算所有模态。然而，如果某些特征值的重数很高，此策略则昂贵。因此，在 Abaqus/Standard 中实现了 Lanczos 算法的"块"版本。这个想法是从一组正交向量开始，并在每个 Lanczos 步骤上以块大小增加 Krylov 子空间的维数。如果最大重数不超过块大小，这种方法允许自动计算所有重特征值。块 Lanczos 方法的另一个重要优点是它允许高效实现昂贵的计算内核，如矩阵-块向量乘法、块回代和块向量乘积。

如上所述，Lanczos 过程包括多个 Lanczos 运行。每个 Lanczos 运行与某个在运行期间保持恒定的移位值相关联。初始移位值 ![](../graphics/stm_eqn01113.gif)（通过启发式方法确定）使用 Gershgorin 圆中心的几何平均值来确定，称为"问题尺度"。在每个 Lanczos 运行开始时，执行移位矩阵 ![](../graphics/stm_eqn01114.gif)（其中 *p* 是运行号）的分解，然后执行一系列 Lanczos 步骤。

![](../graphics/stm_eqn01119.gif)![](../graphics/stm_eqn01121.gif)![](../graphics/stm_eqn01122.gif)![](../graphics/stm_eqn01120.gif)![](../graphics/stm_eqn01082.gif)每个块 Lanczos 步骤 *i* 在 Abaqus/Standard 中以下列方式实现：

使用分解的移位矩阵求解具有 *b* 个右边向量（*b* 是 Lanczos 块大小）的线性方程组：

![](../graphics/stm_eqn01115.gif)其中 ![](../graphics/stm_eqn01095.gif) 是 Lanczos 向量块。![](../graphics/stm_eqn01095.gif) 的行数是有限元模型中的变量数，列数是 Lanczos 块大小 *b*。初始向量块 ![](../graphics/stm_eqn01116.gif) 是一组随机向量，使用过程进行正交归一化：![](../graphics/stm_eqn01117.gif) 其中 ![](../graphics/stm_eqn01118.gif) 是单位矩阵。

设置辅助向量块：

![](../graphics/stm_eqn01119.gif)其中 ![](../graphics/stm_eqn01120.gif) 是 ![](../graphics/stm_eqn01121.gif) 上三角矩阵。![](../graphics/stm_eqn01122.gif)。

计算大小为 *b* 的对称矩阵 ![](../graphics/stm_eqn01123.gif)：

![](../graphics/stm_eqn01124.gif)

制定 Lanczos 残差：

![](../graphics/stm_eqn01125.gif)

归一化残差。计算一组向量 ![](../graphics/stm_eqn01126.gif)，使得

![](../graphics/stm_eqn01127.gif)和

![](../graphics/stm_eqn01128.gif)其中 ![](../graphics/stm_eqn01129.gif) 是 ![](../graphics/stm_eqn01121.gif) 上三角矩阵。

使用部分重正交化技术估计 ![](../graphics/stm_eqn01126.gif) 和 ![](../graphics/stm_eqn01130.gif) 之间在 ![](../graphics/stm_eqn01131.gif) 的正交性损失；如有必要，执行重正交化（参见 [Simon, 1984](07s01a01-References.md)；[Grimes, Lewis, and Simon, 1994](07s01a01-References.md)）。

执行"局部重正交化"：重新计算 ![](../graphics/stm_eqn01126.gif) 以提供

![](../graphics/stm_eqn01132.gif)

求解以下简化特征值问题带状矩阵 ![](../graphics/stm_eqn01133.gif)：

![](../graphics/stm_eqn01134.gif)其中

![](../graphics/stm_eqn01135.gif)![](../graphics/stm_eqn01136.gif) 和 ![](../graphics/stm_eqn01137.gif) 分别是包含简化特征值问题的特征向量和特征值的矩阵。此问题由下面讨论的 Householder 和 Q-R 算法求解。

确定对称化特征值问题（[方程 2.5.1-2](02s05a24-Eigenvalue-extraction.md)）中特征值近似的误差界限（参见 [Parlett, 1980](07s01a01-References.md)；[Grimes, Lewis, and Simon, 1994](07s01a01-References.md)）。检查 Lanczos 运行的终止条件。Lanczos 运行在满足以下条件之一时终止：

当前运行所需的所有特征值已被提取。

三角矩阵 ![](../graphics/stm_eqn01129.gif) 是奇异的或病态的。

Lanczos 步骤数超过允许的最大数。

评估继续当前运行是低效的。这个决定基于对未来几步每特征值"成本"的估计（只要每特征值成本在下降，Lanczos 运行就继续）。

在每个 Lanczos 运行终止后，使用向量块 ![](../graphics/stm_eqn01138.gif) 和特征向量 ![](../graphics/stm_eqn01136.gif) 恢复对称化问题（[方程 2.5.1-2](02s05a24-Eigenvalue-extraction.md)）的收敛特征向量。

一旦移位 ![](../graphics/stm_eqn01139.gif) 的 Lanczos 运行完成，使用所有先前 Lanczos 运行的结果计算移位值 ![](../graphics/stm_eqn01140.gif]。为了描述移位更新策略，引入以下概念：

"计算区间"是感兴趣最小和最大特征值之间的区间。此区间可以是有限的（两端都有限）、半无限的（仅一端有限）或无限的（两端都无限）。"中心点"是计算区间中最接近期望特征值的点。

实数非奇异对称矩阵 ![](../graphics/stm_eqn00147.gif) 的 Sturm 序列数 ![](../graphics/stm_eqn01141.gif) 是负特征值的个数。这个数等于 Cholesky 分解 ![](../graphics/stm_eqn01143.gif) 的对角矩阵 ![](../graphics/stm_eqn01142.gif) 中负项的个数，因此可在 Cholesky 分解完成后获得。

设 ![](../graphics/stm_eqn01113.gif) 和 ![](../graphics/stm_eqn01144.gif) 是两个移位值，使得 ![](../graphics/stm_eqn01145.gif) 则对称化问题（[方程 2.5.1-2](02s05a24-Eigenvalue-extraction.md)，假设 ![](../graphics/stm_eqn01084.gif) 是正定或半正定）在区间 ![](../graphics/stm_eqn01146.gif) 中的特征值个数等于 ![](../graphics/stm_eqn01147.gif) 如果这个数等于 Lanczos 算法实际确定的特征值个数，区间 ![](../graphics/stm_eqn01146.gif) 被称为"信任区间"。包含中心点的信任区间被称为"主要信任区间"（在消息文件中打印的信任区间列表中用加号"+"表示）。移位策略旨在在包含所需特征值数量最接近中心点的计算区间内构建主要信任区间。

移位更新策略制定中最重要的特征之一是"哨兵"的概念。哨兵是仅包含收敛特征值最接近当前移位值（在每个方向上）的区间端点。哨兵在每个 Lanczos 运行期间计算，并在每个步骤的特征值分析完成约化矩阵 ![](../graphics/stm_eqn01133.gif) 后更新。基本假设是在哨兵内部没有缺失的特征值；因此，它们被排除在即将到来的 Lanczos 运行计算区间之外。稍后基于 Sturm 序列检查验证此假设，如果某些特征值缺失，则激活特殊程序。如果没有检测到缺失的特征值，哨兵直接转换为相应的信任区间。

新移位值基于 Lanczos 运行终止后未收敛的特征值近似来选择。假设即将到来的运行具有相同的收敛属性，新移位值的选择方式是：预计在即将到来的运行中找到的特征值数量将接近前一次运行相应哨兵内找到的特征值数量。带四分之一旋转的 Householder 方法

Householder 方法用于将一般矩阵简化为对称三对角形式。三对角矩阵是其唯一非零条目在对角线上或紧邻对角线的矩阵。第一步是将 [方程 2.5.1-4](02s05a24-Eigenvalue-extraction.md) 变换为形式

![](../graphics/stm_eqn01148.gif)其中 ![](../graphics/stm_eqn01118.gif) 是单位矩阵。

这是通过使用 ![](../graphics/stm_eqn01098.gif) 的 Cholesky 分解然后将 ![](../graphics/stm_eqn01099.gif) 左乘和右乘以下方式获得的矩阵的逆来完成的：

![](../graphics/stm_eqn01149.gif)其中

![](../graphics/stm_eqn01150.gif)

为了保持 ![](../graphics/stm_eqn00147.gif) 的对称性，![](../graphics/stm_eqn01098.gif) 的分解必须产生两个互为转置的矩阵。Cholesky 分解产生所需结果，但增加了矩阵 ![](../graphics/stm_eqn01098.gif) 必须是正定的要求。如果定义子空间的基向量在 ![](../graphics/stm_eqn01084.gif) 上不是线性相关的，![](../graphics/stm_eqn01098.gif) 应该始终是正定的（因为在所有此处考虑的问题中 ![](../graphics/stm_eqn01084.gif) 是正定的）。在实践中，为基向量起始值所做的选择通常满足此要求，尽管有时可能不是这样。然后 Abaqus/Standard 将减少子空间的维数以获得正定的 ![](../graphics/stm_eqn01098.gif)。

Householder 变换从矩阵 ![](../graphics/stm_eqn00147.gif) 开始，一次一列地将矩阵三对角部分之外的所有条目归零

![](../graphics/stm_eqn01151.gif)矩阵 ![](../graphics/stm_eqn01152.gif) 的形式为

![](../graphics/stm_eqn01153.gif)

对于第一次变换，![](../graphics/stm_eqn01154.gif) 与 ![](../graphics/stm_eqn00147.gif) 和 ![](../graphics/stm_eqn01152.gif) 阶数相同；即 ![](../graphics/stm_eqn01155.gif)，子空间的维数。然而，每次变换将 ![](../graphics/stm_eqn01154.gif) 的阶数减一，![](../graphics/stm_eqn01152.gif) 的前导部分在对角线上为1，在对角线外为0，如上所示。

矩阵 ![](../graphics/stm_eqn01154.gif) 通过以下算法获得：

如果这是第 *k* 次迭代，将 ![](../graphics/stm_eqn01156.gif) 第 *k* 列在对角线下方写为

![](../graphics/stm_eqn01157.gif)

计算范数 ![](../graphics/stm_eqn01158.gif)

定义向量，

![](../graphics/stm_eqn01159.gif)

然后，

![](../graphics/stm_eqn01160.gif)该算法在 [Strang's (1976)](07s01a01-References.md) 的书中有详细推导。

![](../graphics/stm_eqn01180.gif)![](../graphics/stm_eqn01181.gif)Householder 算法产生一个对称三对角矩阵，它具有与原始矩阵相同的特征值，因为变换（[方程 2.5.1-6](02s05a24-Eigenvalue-extraction.md)）不改变特征值。

下一步是计算三对角矩阵的特征值。这通过 Q-R 算法完成。在这种方法中，现在已是三对角（尽管这不是方法工作的要求）的矩阵 ![](../graphics/stm_eqn00147.gif) 被分解为 ![](../graphics/stm_eqn01161.gif)，其中 ![](../graphics/stm_eqn01162.gif) 是正交矩阵（即 ![](../graphics/stm_eqn01163.gif)），![](../graphics/stm_eqn01164.gif) 是上三角矩阵（即 ![](../graphics/stm_eqn01164.gif) 中对角线以下的项都为零）。

迭代中的下一个矩阵通过左乘和右乘 ![](../graphics/stm_eqn00147.gif) 由 ![](../graphics/stm_eqn01162.gif) 获得：

![](../graphics/stm_eqn01165.gif)因为 ![](../graphics/stm_eqn01162.gif) 是正交的，这将不影响特征值。这个过程逐渐减少 ![](../graphics/stm_eqn00147.gif) 的非对角项，使对角项接近特征值。为了加速收敛，引入了移位方法，产生以下迭代循环：

![](../graphics/stm_eqn01166.gif)

![](../graphics/stm_eqn01167.gif)

![](../graphics/stm_eqn01168.gif)

![](../graphics/stm_eqn01169.gif)

在迭代收敛到特征值之前不能使用移位；但一旦明显，即将移位值 ![](../graphics/stm_eqn01123.gif) 设置为期望的特征值。这将显著提高收敛速率。如果移位做得太早，值不在特征值附近，过程很可能收敛到错误的数字。Q-R 过程将按升序收敛到特征值；一旦获得特征值，矩阵的阶数可以减少一。

获得特征值后的最后一步是通过使用逆幂法求解给定任意右边的特征向量来计算特征向量：

![](../graphics/stm_eqn01170.gif)其中 ![](../graphics/stm_eqn00280.gif) 是刚获得的特征值，![](../graphics/stm_eqn01171.gif) 是任意向量。因为左手边矩阵在特征向量 ![](../graphics/stm_eqn01088.gif) 的方向上是奇异的，所以无论右边向量 ![](../graphics/stm_eqn01171.gif) 如何，只要 ![](../graphics/stm_eqn01171.gif) 与特征向量不正交，就会获得此向量。为了确保连续向量是正交的，特别是在重特征值的情况下，![](../graphics/stm_eqn01171.gif) 始终选择与先前提取的特征向量正交。因为 ![](../graphics/stm_eqn01172.gif) 是奇异的，必须包含轻微的数值移位来分解它，从而求解 ![](../graphics/stm_eqn01088.gif)。在本指南使用的标准符号中，特征向量矩阵 ![](../graphics/stm_eqn01173.gif) 写为 ![](../graphics/stm_eqn01174.gif)，其中 N 指问题中的节点变量，![](../graphics/stm_eqn01175.gif) 是模态号。
### 复特征值提取

![](../graphics/stm_eqn01086.gif)![](../graphics/stm_eqn01092.gif)Abaqus/Standard 提供子空间投影方法用于求解原始特征值问题（[方程 2.5.1-1](02s05a24-Eigenvalue-extraction.md)）的复特征值和右特征向量。子空间投影方法

在子空间投影方法中，原始特征系统（[方程 2.5.1-1](02s05a24-Eigenvalue-extraction.md)）被投影到由无阻尼对称系统（[方程 2.5.1-2](02s05a24-Eigenvalue-extraction.md)）的特征向量跨越的子空间上。因此，必须在复特征值提取过程之前求解对称化特征值问题，以创建原始系统将被投影到的子空间。接下来，将原始质量、阻尼和刚度矩阵投影到 *N* 个特征向量的子空间上：

![](../graphics/stm_eqn01176.gif)

![](../graphics/stm_eqn01177.gif)

![](../graphics/stm_eqn01178.gif)然后，我们得到以下特征值问题：

![](../graphics/stm_eqn01179.gif)通常，特征向量数量相对较小；几百个是常见的。这个小型复特征值系统使用广义非对称特征值问题的标准 QZ 方法求解。投影系统的复特征值是原始系统（[方程 2.5.1-1](02s05a24-Eigenvalue-extraction.md)）特征值的近似，但需要恢复原始系统的右特征向量：

![](../graphics/stm_eqn01180.gif)其中 ![](../graphics/stm_eqn01181.gif) 是原始系统第 *k* 个右特征向量的近似。

特征值提取过程中计算的仅能量密度是弹性应变能密度，对于复特征值提取，定义如下：

![](../graphics/stm_eqn01182.gif)其中 ![](../graphics/stm_eqn01183.gif) 是特征应力张量的实部和虚部，![](../graphics/stm_eqn01184.gif) 是特征应变张量的实部和虚部。
### 参考文献

### 参考文献

"Abaqus Analysis User's Guide" 第6.2.3节"特征值屈曲预测"

![](../graphics/stm_eqn01103.gif)![](../graphics/stm_eqn01102.gif)"Abaqus Analysis User's Guide" 第6.3.5节"固有频率提取"

"Abaqus Analysis User's Guide" 第6.3.6节"复特征值提取"