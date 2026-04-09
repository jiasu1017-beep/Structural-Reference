# 1.4.4 加法应变率分解

### 1.4.4 加法应变率分解

**产品：** Abaqus/Standard  Abaqus/Explicit

许多有用的材料，如传统结构金属，只能承受非常小的弹性应变（弹性模量通常比屈服应力大二到三个数量级）。我们可以利用这种行为来简化此类材料变形的描述。由于这种行为非常普遍，弹性应变始终很小的假设构成了Abaqus中提供的几乎所有非弹性材料模型的基础。本节讨论这种情况下变形的描述。

我们首先假设材料在变形过程中的任何时候都有一个自然的弹性参考状态，在这个意义上，我们可以想象隔离材料中单个点的直接邻域，防止任何进一步的非弹性变形，从隔离的部分移除所有外力，并允许材料卸载：与这种卸载相关的变形将是 ![](../graphics/stm_eqn00455.gif)，即弹性变形的反向。原始参考状态和这个弹性卸载状态之间的变形就是非弹性变形 ![](../graphics/stm_eqn00456.gif)：

![](../graphics/stm_eqn00457.gif)总变形因此可以分解为

![](../graphics/stm_eqn00458.gif)由此我们可以获得相对于当前配置中位置的速度梯度 ![](../graphics/stm_eqn00459.gif) 为

![](../graphics/stm_eqn00460.gif)我们将其写成

![](../graphics/stm_eqn00461.gif)通过定义弹性和塑性速度梯度 ![](../graphics/stm_eqn00462.gif) 和 ![](../graphics/stm_eqn00463.gif)，类比于总速度梯度的定义。

对于我们关注的材料，我们现在假设弹性应变 ![](../graphics/stm_eqn00464.gif) 与1相比非常小。利用这一点以及弹性变形的左极分解，我们可以写成

![](../graphics/stm_eqn00465.gif)其中 ![](../graphics/stm_eqn00466.gif)、![](../graphics/stm_eqn00467.gif) 和 ![](../graphics/stm_eqn00468.gif)。我们现在使用 [方程 1.4.4-2](01s04a07.md) 中 ![](../graphics/stm_eqn00469.gif) 的这个分解来获得

![](../graphics/stm_eqn00470.gif)我们现在定义

![](../graphics/stm_eqn00471.gif)其中 ![](../graphics/stm_eqn00424.gif) 和 ![](../graphics/stm_eqn00472.gif) 分别表示每个速度梯度的对称和反对称部分。使用这些定义并忽略高阶项，速度梯度现在可以表示为

![](../graphics/stm_eqn00473.gif)取这个表达式的对称部分得到

![](../graphics/stm_eqn00474.gif)

我们现在做出假设 ![](../graphics/stm_eqn00475.gif)，这各向同性成立；最后一个表达式简化为

![](../graphics/stm_eqn00476.gif)其中我们引入符号 ![](../graphics/stm_eqn00477.gif)。[方程 1.4.4-3](01s04a07.md) 是塑性理论中经典的"加法率变形分解"——例如参见 [Aravas (1991)](07s01a01-References.md)。我们看到，当我们对当前位置的速度梯度的对称部分使用，并且当总弹性应变始终比1小时，它来自一般分解（[方程 1.4.4-1](01s04a07.md)）。率变形分解以这种形式用于Abaqus中几乎所有的非弹性本构模型，它表示为 ![](../graphics/stm_eqn00478.gif)。
### 参考

### 参考

"Abaqus Analysis User's Guide" 第23.1.1节"非弹性行为"