# 4.6.1 超弹性材料行为

### 4.6.1 超弹性材料行为

**产品：** Abaqus/Standard  Abaqus/Explicit

超弹性材料的本构行为定义为总应力-总应变关系，而不是在前几节中讨论的历史相关材料背景下的率形式。因此，超弹性公式的基本发展有些不同。此外，超弹性材料通常是不可压缩或几乎不可压缩的；因此，可以使用混合（"混合"）公式。在本节中，定义了 Abaqus 中提供的超弹性模型，并介绍了在 Abaqus/Standard 中用于处理完全不可压缩情况和几乎不可压缩情况的混合变分原理。

### 定义和基本运动学结果

我们首先介绍一些定义和基本运动学结果，这些将在本节中使用。其中一些项目已在第1章"引言和基本方程"中讨论过：为方便起见在此重复。

将物质点的当前位置写为 ![](../graphics/stm_eqn00117.gif)，同一点的参考位置写为 ![](../graphics/stm_eqn00141.gif)，变形梯度为

![](../graphics/stm_eqn06705.gif)然后 *J*，即该点的总体积变化为

![](../graphics/stm_eqn06706.gif)为简单起见，我们定义

![](../graphics/stm_eqn06707.gif)为消除体积变化的变形梯度。

然后我们引入 ![](../graphics/stm_eqn02953.gif) 的偏斜拉伸矩阵（左 Cauchy-Green 应变张量）为

![](../graphics/stm_eqn06708.gif)以便我们可以定义第一应变不变量为

![](../graphics/stm_eqn06709.gif)其中 ![](../graphics/stm_eqn00064.gif) 是单位矩阵，第二应变不变量为

![](../graphics/stm_eqn06710.gif)在后续推导中需要 ![](../graphics/stm_eqn06711.gif)、![](../graphics/stm_eqn06712.gif)、![](../graphics/stm_eqn06713.gif)、![](../graphics/stm_eqn06714.gif) 和 *J* 的变分。我们首先定义一些基本运动学量的变分，这些量将需要用于写出这些结果。

位移变分关于当前位置的梯度写为

![](../graphics/stm_eqn06715.gif)

虚变形速率是 ![](../graphics/stm_eqn03092.gif) 的对称部分：

![](../graphics/stm_eqn06716.gif)我们将其分解为每当前体积的体积变化速率（"虚体积应变率"），

![](../graphics/stm_eqn06717.gif)和虚偏斜应变率，

![](../graphics/stm_eqn06718.gif)

材料的虚旋转速率是 ![](../graphics/stm_eqn03092.gif) 的反对称部分：

![](../graphics/stm_eqn06719.gif)

![](../graphics/stm_eqn06711.gif)、![](../graphics/stm_eqn06712.gif)、![](../graphics/stm_eqn06713.gif)、![](../graphics/stm_eqn06714.gif) 和 *J* 的变分直接从上面关于这些量的定义获得

![](../graphics/stm_eqn06720.gif)其中

![](../graphics/stm_eqn06721.gif)

![](../graphics/stm_eqn06722.gif)其中

![](../graphics/stm_eqn06723.gif)

![](../graphics/stm_eqn06724.gif)

![](../graphics/stm_eqn06725.gif)和

![](../graphics/stm_eqn06726.gif)

Cauchy（"真实"）应力分量从应变能势定义如下。从虚功原理，内能变分为

![](../graphics/stm_eqn06727.gif)其中 ![](../graphics/stm_eqn00033.gif) 是 Cauchy（"真实"）应力的分量，*V* 是当前体积，![](../graphics/stm_eqn01828.gif) 是参考体积。

我们将应力分解为等效压力应力，

![](../graphics/stm_eqn06728.gif)和偏斜应力，

![](../graphics/stm_eqn06729.gif)以便内能变分可以写为

![](../graphics/stm_eqn06730.gif)

对于各向同性、可压缩材料，应变能 *U* 是 ![](../graphics/stm_eqn06713.gif)、![](../graphics/stm_eqn06714.gif) 和 *J* 的函数：

![](../graphics/stm_eqn06731.gif)所以

![](../graphics/stm_eqn06732.gif)因此，使用[方程 4.6.1–3](04s06a123.md)、[方程 4.6.1–4](04s06a123.md) 和[方程 4.6.1–5](04s06a123.md)，

![](../graphics/stm_eqn06733.gif)

由于应变能势的变分根据定义是每参考体积的内虚功，![](../graphics/stm_eqn06734.gif)，我们有

![](../graphics/stm_eqn06735.gif)

对于可压缩材料，应变变分是任意的，所以此方程定义了此类材料的应力分量为

![](../graphics/stm_eqn06736.gif)和

![](../graphics/stm_eqn06737.gif)

当材料响应几乎不可压缩时，纯位移公式（其中应变不变量从有限元模型的运动学变量计算）可能表现不佳。困难之一是从数值角度看，刚度矩阵几乎是奇异的，因为材料的有效体积模量相对于其有效剪切模量非常大，从而给离散化平衡方程的求解带来困难。类似地，在 Abaqus/Explicit 中，高体积模量增加了膨胀波速度，从而大大减少了稳定时间增量。另一个问题是，除非使用减缩积分技术，否则在数值积分点计算的应力在压力应力值中显示出大的振荡，因为——一般来说——单元无法准确响应，同时在所有数值积分点保持小的体积变化。为避免这些问题，Abaqus/Standard 为此类情况提供了"混合"公式。其概念是引入一个变量 ![](../graphics/stm_eqn06738.gif)，用于代替应变能势定义中的体积变化 *J*。内能积分 ![](../graphics/stm_eqn06739.gif) 通过使用拉格朗日乘子 ![](../graphics/stm_eqn06422.gif) 施加约束 ![](../graphics/stm_eqn06740.gif) 来增强，并在体积上积分：

![](../graphics/stm_eqn06741.gif)取此定义的变分，

![](../graphics/stm_eqn06742.gif)由于 ![](../graphics/stm_eqn06743.gif) 在此表达式中是一个独立变分，拉格朗日乘子为

![](../graphics/stm_eqn06744.gif)其变分为

![](../graphics/stm_eqn06745.gif)其中

![](../graphics/stm_eqn06746.gif)这些结果使我们能够将增强的内能变分写为

![](../graphics/stm_eqn06747.gif)这意味着 ![](../graphics/stm_eqn06748.gif) 跨单元的插值连续性不是必需的。

此增强公式可用于除完全不可压缩行为之外的任何可压缩性值。对于大多数单元类型，![](../graphics/stm_eqn06748.gif) 在每个单元中独立插值：Abaqus 在大多数一阶单元中使用常数 ![](../graphics/stm_eqn06738.gif)，在二阶单元中使用关于位置的线性变化的 ![](../graphics/stm_eqn06738.gif)。唯一强制执行跨单元 ![](../graphics/stm_eqn06738.gif) 插值连续性的单元类型是 C3D4H：一种一阶四面体，其 ![](../graphics/stm_eqn06738.gif) 的线性插值在跨单元时连续。

当材料完全不可压缩时，*U* 是第一和第二应变不变量的函数——![](../graphics/stm_eqn06713.gif) 和 ![](../graphics/stm_eqn06714.gif)——仅，我们将内能写为增强形式，

![](../graphics/stm_eqn06749.gif)其中 ![](../graphics/stm_eqn06422.gif) 再次是引入的拉格朗日乘子，以施加约束 ![](../graphics/stm_eqn06750.gif)，使得关于所有运动学变量可以取 ![](../graphics/stm_eqn06751.gif) 的变分，从而得到

![](../graphics/stm_eqn06752.gif)拉格朗日乘子 ![](../graphics/stm_eqn06422.gif) 以与几乎不可压缩行为的增强公式中 ![](../graphics/stm_eqn06738.gif) 相同的方式插值；也就是说，![](../graphics/stm_eqn06422.gif) 在大多数一阶单元中假定为常数，在二阶单元中假定为关于位置的线性变化。唯一的例外是单元类型 C3D4H，它是一种一阶四面体，其 ![](../graphics/stm_eqn06422.gif) 的线性插值在跨单元时连续。

### 内虚功的变化率

内虚功的变化率是牛顿方法所需的，Abaqus/Standard 通常使用牛顿方法求解非线性平衡方程（通过有限元离散化后）。当我们将弹性模型扩展到关于预变形状态的小（线性化）振动的粘弹性行为时，它也将被使用。

当对可压缩情况使用纯位移公式时，偏斜应力分量 ![](../graphics/stm_eqn00522.gif) 由[方程 4.6.1–8](04s06a123.md) 定义，由此我们可以表明

![](../graphics/stm_eqn06753.gif)其中材料的"有效偏斜弹性" ![](../graphics/stm_eqn06754.gif) 定义为

![](../graphics/stm_eqn06755.gif)偏斜应力率-体积应变率耦合项 ![](../graphics/stm_eqn06756.gif) 为

![](../graphics/stm_eqn06757.gif)

从[方程 4.6.1–9](04s06a123.md) 可以表明

![](../graphics/stm_eqn06758.gif)其中 *K* 是材料的有效体积模量，

![](../graphics/stm_eqn06759.gif)因此，

![](../graphics/stm_eqn06760.gif)因为

![](../graphics/stm_eqn06761.gif)

对于为几乎不可压缩材料引入的混合公式，内能增强变分的变化率，[方程 4.6.1–10](04s06a123.md)，为

![](../graphics/stm_eqn06762.gif)其中

![](../graphics/stm_eqn06763.gif)

![](../graphics/stm_eqn06764.gif)

![](../graphics/stm_eqn06765.gif)和

![](../graphics/stm_eqn06766.gif)其中

![](../graphics/stm_eqn06767.gif)

对于不可压缩材料的情况，内能增强变分的变化率类似地从[方程 4.6.1–11](04s06a123.md) 获得为

![](../graphics/stm_eqn06768.gif)

### 应变能势的特殊形式

Abaqus 中提供了几种特殊形式的应变能势。不可压缩或几乎不可压缩模型包括：

多项式形式及其特殊情况——减缩多项式形式、neo-Hookean 形式、Mooney-Rivlin 形式和 Yeoh 形式；

Ogden 形式；

Arruda-Boyce 形式；和

Van der Waals 形式。此外，还提供了一种用于高度可压缩弹性材料的超弹性模型。

多项式形式及特殊情况

给定在不可压缩或几乎不可压缩行为存在时偏斜和体积应变能贡献的各向同性和加法分解，我们通常可以将势写为

![](../graphics/stm_eqn06769.gif)设 ![](../graphics/stm_eqn06770.gif) 并将 ![](../graphics/stm_eqn06771.gif) 展开为泰勒级数，我们得到

![](../graphics/stm_eqn06772.gif)这是 Abaqus 中应变能的多项式表示。参数 *N* 可以取高达六的值；但是，当同时考虑第一和第二不变量时，*N* 大于 2 的值很少使用。![](../graphics/stm_eqn06773.gif) 和 ![](../graphics/stm_eqn06774.gif) 是温度相关的材料参数。*N* 的值以及给出 ![](../graphics/stm_eqn06773.gif) 和 ![](../graphics/stm_eqn06774.gif) 作为温度函数的表格由用户指定。弹性体积应变 ![](../graphics/stm_eqn06775.gif) 由总体积应变 *J* 和热体积应变 ![](../graphics/stm_eqn06776.gif) 通过关系式

![](../graphics/stm_eqn06777.gif)得出，![](../graphics/stm_eqn06776.gif) 由线性热膨胀 ![](../graphics/stm_eqn06778.gif) 通过

![](../graphics/stm_eqn06779.gif)得出，其中 ![](../graphics/stm_eqn06778.gif) 取决于温度和用户定义的各向同性热膨胀系数。

![](../graphics/stm_eqn06774.gif) 的值决定了材料的可压缩性：如果所有 ![](../graphics/stm_eqn06774.gif) 为零，则材料被视为完全不可压缩。如果 ![](../graphics/stm_eqn06780.gif)，则所有 ![](../graphics/stm_eqn06774.gif) 必须为零。

无论 *N* 的值如何，初始剪切模量 ![](../graphics/stm_eqn06781.gif) 和体积模量 ![](../graphics/stm_eqn06782.gif) 仅取决于阶数为 ![](../graphics/stm_eqn05955.gif) 的多项式系数：

![](../graphics/stm_eqn06783.gif)

如果 ![](../graphics/stm_eqn05955.gif)，即仅保留偏斜应变能中的线性项，则获得 Mooney-Rivlin 形式：

![](../graphics/stm_eqn06784.gif)Mooney-Rivlin 形式可以被视为 neo-Hookean 形式（在下面讨论）的扩展，因为它添加了依赖于左 Cauchy-Green 张量第二不变量的项。在某些情况下，这种形式比 neo-Hookean 形式能更准确地拟合实验数据；然而，通常两种模型给出相似的精度，因为它们仅使用不变量的线性函数。这些函数不允许表示应力-应变曲线在较高应变水平的"上翘"。

多项式模型的特殊形式也可以通过将特定系数设置为零来获得。如果所有 ![](../graphics/stm_eqn06773.gif) 当 ![](../graphics/stm_eqn06785.gif) 时设置为零，则获得减缩多项式形式：

![](../graphics/stm_eqn06786.gif)遵循 [Yeoh (1993)](07s01a01-References.md)，通过忽略对第二不变量的依赖来减少一般多项式级数展开的理由来自以下观察。应变能函数对第二不变量变化的敏感性通常远小于对第一不变量变化的敏感性。此外，![](../graphics/stm_eqn06714.gif) 依赖性难以测量，因此可能最好忽略它，而不是基于可能不准确的测量来计算它。最后，似乎如果仅知道特定变形模式的数据，忽略对第二不变量的依赖可能会增强对其他变形状态的预测。这一猜想通过在几乎不可压缩行为存在下调查所谓的减缩应力得到支持：

![](../graphics/stm_eqn06787.gif)其中 ![](../graphics/stm_eqn06788.gif)、![](../graphics/stm_eqn06789.gif) 表示主 Cauchy（"真实"）应力。如果省略关于 ![](../graphics/stm_eqn06714.gif) 的导数，并考虑不同的应力状态——单轴、双轴和平面——减缩应力具有与应力状态无关的相同形式。

[kawabata、Yamashita 等人（1995）](07s01a01-References.md) 提供了证实这些发现的碳黑增强橡胶硫化物的 ![](../graphics/stm_eqn06714.gif) 依赖性测量。[Kaliske 和 Rothert (1997)](07s01a01-References.md) 的论文也支持这样一种观点：通常基于单轴测量预测一般变形状态只能通过忽略 ![](../graphics/stm_eqn06714.gif) 依赖性来增强。

在此背景下，值得注意的是，Arruda-Boyce 模型的数学结构可以被视为五阶减缩多项式，其中五个系数 ![](../graphics/stm_eqn06790.gif) 是 Arruda-Boyce 形式中两个参数 ![](../graphics/stm_eqn01087.gif) 和 ![](../graphics/stm_eqn06791.gif) 的隐式非线性函数。然而，Arruda-Boyce 模型提供了参数物理解释，这是一般五阶减缩多项式无法提供的。

Yeoh 形式（[Yeoh, 1993](07s01a01-References.md)）可以被视为减缩多项式的特殊情况，其中 ![](../graphics/stm_eqn06792.gif)：

![](../graphics/stm_eqn06793.gif)通常，如果 ![](../graphics/stm_eqn06794.gif)，第二系数将为负且小一至两个数量级[即 ![](../graphics/stm_eqn06795.gif) 是 ![](../graphics/stm_eqn06796.gif) 到 ![](../graphics/stm_eqn06797.gif)]，而第三系数 ![](../graphics/stm_eqn06798.gif) 再次小一至两个数量级但为正[即 ![](../graphics/stm_eqn06798.gif) 是 ![](../graphics/stm_eqn06799.gif) 到 ![](../graphics/stm_eqn06800.gif)]。这些量级将产生橡胶应力-应变行为的典型 S 形；在低应变时 ![](../graphics/stm_eqn06801.gif) 表示初始剪切模量，由于负第二系数 ![](../graphics/stm_eqn06795.gif) 的影响在中等应变时软化，然后由于正第三系数 ![](../graphics/stm_eqn06798.gif) 在大应变时出现上翘。因此，Yeoh 模型通常在大应变范围内提供准确的拟合。

如果通过设 ![](../graphics/stm_eqn05955.gif) 进一步简化减缩多项式应变能函数，则获得 neo-Hookean 形式：

![](../graphics/stm_eqn06802.gif)这是最简单的超弹性模型，在没有准确材料数据时通常用作弹性体材料的原型。它也有一定的理论相关性，因为数学表示类似于理想气体：neo-Hookean 势代表具有高斯链长分布的分子网络的 Helmholtz 自由能（见 [Treloar, 1975](07s01a01-References.md)）。

用户可以请求 Abaqus 从简单实验中的标称应力和应变测量值计算 ![](../graphics/stm_eqn06773.gif) 和 ![](../graphics/stm_eqn06774.gif) 值。此计算的基础在"超弹性和超泡沫常数的拟合"第 4.6.2 节中描述。

### Ogden 形式

Ogden 应变能势用主拉伸表示。在 Abaqus 中使用以下公式：

![](../graphics/stm_eqn06803.gif)其中

![](../graphics/stm_eqn06804.gif)因此，Ogden 应变能函数的第一部分仅取决于 ![](../graphics/stm_eqn06713.gif) 和 ![](../graphics/stm_eqn06714.gif)。Ogden 的能量函数不能明确地用 ![](../graphics/stm_eqn06713.gif) 和 ![](../graphics/stm_eqn06714.gif) 表示。但是，可以获得 *U* 关于 ![](../graphics/stm_eqn06713.gif) 和 ![](../graphics/stm_eqn06714.gif) 导数的闭合形式表达式。

*N* 的值以及给出 ![](../graphics/stm_eqn06805.gif) 和 ![](../graphics/stm_eqn01123.gif) 作为温度函数的表格由用户指定。如果 ![](../graphics/stm_eqn05962.gif)，![](../graphics/stm_eqn06806.gif)，和 ![](../graphics/stm_eqn06807.gif)，则获得 Mooney-Rivlin 模型。如果 ![](../graphics/stm_eqn05955.gif) 和 ![](../graphics/stm_eqn06806.gif)，Ogden 模型退化为 neo-Hookean 材料模型。在 Ogden 形式中，初始剪切模量 ![](../graphics/stm_eqn06808.gif) 取决于所有系数：

![](../graphics/stm_eqn06809.gif)初始体积模量 ![](../graphics/stm_eqn06810.gif) 如前所述取决于 ![](../graphics/stm_eqn06811.gif)。用户可以请求 Abaqus 从标称应力和应变的测量值计算 ![](../graphics/stm_eqn06805.gif) 和 ![](../graphics/stm_eqn01123.gif) 值。

### Arruda-Boyce 形式

超弹性 Arruda-Boyce 势具有以下形式：

![](../graphics/stm_eqn06812.gif)其中

![](../graphics/stm_eqn06813.gif)应变能密度的偏斜部分来自 [Arruda 和 Boyce (1993)](07s01a01-References.md)。该模型也称为八链模型，因为它是从一个代表体积元开发的，其中八个弹簧从立方体中心延伸到其角落。系数 ![](../graphics/stm_eqn06814.gif) 的值来自于非高斯链统计处理中出现的逆 Langevin 函数的级数展开。级数展开在第五项之后截断。系数 ![](../graphics/stm_eqn06791.gif) 被称为锁定拉伸。大约在这个拉伸处，应力-应变曲线的斜率将显著上升。初始剪切模量 ![](../graphics/stm_eqn06808.gif) 通过表达式与 ![](../graphics/stm_eqn01087.gif) 相关

![](../graphics/stm_eqn06815.gif) ![](../graphics/stm_eqn06791.gif) 的典型值为 7，对于该值 ![](../graphics/stm_eqn06816.gif)。

初始体积模量获得为 ![](../graphics/stm_eqn06817.gif)。我们向应变能密度的偏斜部分添加体积应变能密度的简化表示，这只需要一个材料参数，以便即使对材料行为了解有限也能轻松估计所有材料参数。[Kaliske 和 Rothert (1997)](07s01a01-References.md) 成功使用了这种体积表示，并为大多数工程弹性材料提供了足够的精度。

Arruda-Boyce 势仅取决于第一不变量。物理解释是，八个链在一般变形状态下被均匀拉伸。第一不变量 ![](../graphics/stm_eqn06818.gif) 直接代表这种伸长。

选择 Arruda-Boyce 形式时，用户可以指定系数作为温度的函数；或者，Abaqus 可以拟合用户指定的测试数据以确定系数。

### Van der Waals 形式

超弹性 Van der Waals 势，也称为 Kilian 模型，具有以下形式：

![](../graphics/stm_eqn06819.gif)其中

![](../graphics/stm_eqn06820.gif)"Van der Waals"这个名称借鉴了橡胶和气体状态方程热力学解释的类比。虽然 neo-Hookean 模型可以与理想气体进行比较，因为它从没有"准粒子"之间相互干扰的高斯网络开始（Kilian，1981），但 Van der Waals 应变能势类似于真实气体的状态方程。这引入了两个额外的材料参数：锁定拉伸 ![](../graphics/stm_eqn06791.gif) 和全局相互作用参数 *a*。（类似地，真实气体的 Van der Waals 方程引入了两个参数来考虑排斥体积和粒子之间动量交换的修改。）

锁定拉伸 ![](../graphics/stm_eqn06791.gif) 考虑了非高斯链网络的有限可伸展性。与 Arruda-Boyce 模型相比，Van der Waals 势的数学结构使得应变能在达到锁定拉伸 ![](../graphics/stm_eqn06791.gif) 时趋于无穷大；更准确地说，当 ![](../graphics/stm_eqn06821.gif) 时。因此，Van der Waals 势不能在大于锁定拉伸的拉伸下使用。

全局相互作用参数 *a* 模拟链之间的相互作用；它很难估计。Kilian 等人（1986）指出，给定 Mooney-Rivlin 系数和锁定拉伸 ![](../graphics/stm_eqn06791.gif)，全局相互作用参数的合适值为

![](../graphics/stm_eqn06822.gif)其中 ![](../graphics/stm_eqn01087.gif) 是低应变时的初始剪切模量，![](../graphics/stm_eqn06823.gif) 是第二 Mooney-Rivlin 参数。给定正初始剪切模量 ![](../graphics/stm_eqn01087.gif) 和锁定拉伸 ![](../graphics/stm_eqn06791.gif)，太大的正相互作用参数 *a* 将导致拉伸范围内的 Drucker 不稳定。全局相互作用参数 *a* 的现实值将有助于橡胶在中间应变范围内拉伸应力-应变曲线特征 S 形的形成，因为在接近锁定拉伸时的最终上翘之前，而不引起不稳定性。

参数 ![](../graphics/stm_eqn01219.gif) 表示线性混合参数，将两个不变量 ![](../graphics/stm_eqn06713.gif) 和 ![](../graphics/stm_eqn06714.gif) 组合成 ![](../graphics/stm_eqn06824.gif)；对于 ![](../graphics/stm_eqn06825.gif)，Van der Waals 势将仅依赖于第一不变量。此参数的容许值为 ![](../graphics/stm_eqn06826.gif)。

选择 Van der Waals 势时，用户可以指定系数作为温度的函数；或者，可以从用户定义的测试数据拟合参数。数据拟合过程不一定会在零和一之间产生 ![](../graphics/stm_eqn01219.gif) 的值。如果在曲线拟合过程中参数 ![](../graphics/stm_eqn01219.gif) 离开容许范围，曲线拟合过程将中止，并使用固定值 ![](../graphics/stm_eqn06825.gif) 重新开始。或者，曲线拟合过程可以与用户定义的 ![](../graphics/stm_eqn01219.gif) 值一起使用。

### 高度可压缩弹性体的应变能势

虽然前面的形式适用于不可压缩或几乎不可压缩的材料，但弹性泡沫能量函数设计用于描述高度可压缩的弹性体（[Storkers, 1986](07s01a01-References.md)）。这个能量函数具有以下形式

![](../graphics/stm_eqn06827.gif)其中

![](../graphics/stm_eqn06828.gif)体积和偏斜贡献在此表达式中是耦合的，这可以通过将其写为以下形式来清楚地证明

![](../graphics/stm_eqn06829.gif)关于 ![](../graphics/stm_eqn06830.gif) 展开最后两项的级数表明，一阶项消失，二阶项的系数等于 ![](../graphics/stm_eqn06831.gif)。因此，如果 ![](../graphics/stm_eqn06832.gif)，则获得稳定材料。对于能量函数中的每一项，系数 ![](../graphics/stm_eqn01120.gif) 决定可压缩程度。![](../graphics/stm_eqn01120.gif) 通过以下表达式与泊松比 ![](../graphics/stm_eqn06833.gif) 相关：

![](../graphics/stm_eqn06834.gif)因此，如果 ![](../graphics/stm_eqn01120.gif) 对所有项相同，我们有一个单一有效泊松比 ![](../graphics/stm_eqn01854.gif)。*N* 的值以及给出 ![](../graphics/stm_eqn06805.gif)、![](../graphics/stm_eqn01123.gif) 和 ![](../graphics/stm_eqn06833.gif) 作为温度函数的表格由用户为超泡沫材料模型指定。泊松比适用于对数主应变 ![](../graphics/stm_eqn06835.gif) 的有限值；在单轴拉伸中 ![](../graphics/stm_eqn06836.gif)。对于 ![](../graphics/stm_eqn06837.gif)，没有泊松效应。初始剪切模量 ![](../graphics/stm_eqn06808.gif) 再次由

![](../graphics/stm_eqn06809.gif)得出，初始体积模量由

![](../graphics/stm_eqn06838.gif)得出。

如果泊松比是常数且已知，Abaqus 可以像之前一样从标称应力和拉伸的测量值计算 ![](../graphics/stm_eqn06805.gif) 和 ![](../graphics/stm_eqn01123.gif)。如果泊松比取决于应变水平，Abaqus 也可以从标称横向应变计算 ![](../graphics/stm_eqn01120.gif)。

### 子程序 UHYPER

Abaqus/Standard 还允许通过用户子程序 UHYPER 为各向同性材料定义其他形式的应变能势，方法是在该子程序中对 *U* 关于 ![](../graphics/stm_eqn06713.gif)、![](../graphics/stm_eqn06714.gif) 和 *J* 的一阶和二阶导数进行编程。

### 参考

### 参考

"Rubberlike materials behavior," Abaqus Analysis User's Guide 第 22.5.1 节

"Elastomeric foams hyperelastic behavior," Abaqus Analysis User's Guide 第 22.5.2 节
