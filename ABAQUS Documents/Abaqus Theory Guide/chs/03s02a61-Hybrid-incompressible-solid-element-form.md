# 3.2.3 混合不可压缩实体单元公式

### 3.2.3 混合不可压缩实体单元公式

**产品：** Abaqus/Standard  Abaqus/Explicit

许多问题涉及预测几乎不可压缩材料的响应。在大应变情况下尤其如此，因为大多数固体材料在大变形下表现出相对不可压缩的行为。在本节中，我们描述了Abaqus/Standard中为此类情况提供的增强虚功基础。该方法在不可压缩弹性理论的背景下描述，因为这是它最可能使用的地方。

当材料响应不可压缩时，问题的解不能仅用位移历史来获得，因为可以添加纯静水压力而不改变位移。接近不可压缩的情况（即当体积模量远大于剪切模量或泊松比，![](../graphics/stm_eqn01854.gif)，大于0.4999999）表现出接近这个极限的行为，即非常小的位移变化会产生非常大的压力变化，因此纯位移解对数值过于敏感（例如，计算机上的舍入可能导致方法失败）。我们通过将压力应力作为独立插值的基本解变量来处理， 通过Lagrange乘子与位移解耦合本构理论和兼容条件来实现这种耦合。这种压力的独立插值是这些"混合"单元的基础。更准确地说，它们是"混合公式"单元，使用位移和应力变量的混合物以及增强的变分原理来近似平衡方程和兼容条件。混合单元还解决了体积应变"锁定"的问题，这可能发生在![](../graphics/stm_eqn01854.gif)低得多的值时（即，![](../graphics/stm_eqn02876.gif) 0.49）。如果有限元网格不能正确表示不可压缩变形，则会发生体积应变锁定。可以通过完全或选择性缩减积分来避免常规位移单元中的体积应变锁定，如"实体等参四边形和六面体，" 第3.2.4节中所述。

我们从写出内部虚功开始：

![](../graphics/stm_eqn02877.gif)其中![](../graphics/stm_eqn01596.gif)是虚应变：

![](../graphics/stm_eqn02878.gif)其中![](../graphics/stm_eqn01597.gif)是虚位移场，![](../graphics/stm_eqn00033.gif)是真实（柯西）应力，*V*是当前体积，![](../graphics/stm_eqn02879.gif)是由这个方程定义的虚功。有关虚功概念的详细讨论，请参见"平衡和虚功，" 第1.5.1节。

在基于位移的公式中，柯西应力![](../graphics/stm_eqn00033.gif)通常以率形式从变形中通过本构方程获得：

![](../graphics/stm_eqn02880.gif)其中![](../graphics/stm_eqn00162.gif)是"材料刚度矩阵"，![](../graphics/stm_eqn02881.gif)是材料的旋转率（自旋）。

我们通过引入独立的静水压力场![](../graphics/stm_eqn02882.gif)来修改柯西应力，如下所示：

![](../graphics/stm_eqn02883.gif)其中

![](../graphics/stm_eqn02884.gif)是静水压力应力，![](../graphics/stm_eqn00593.gif)是一个很小的数。如果![](../graphics/stm_eqn00593.gif)设为零，则![](../graphics/stm_eqn01727.gif)中的静水分量将与独立压力场![](../graphics/stm_eqn02882.gif)相同，对应于纯"混合"公式。选择小的非零值（![](../graphics/stm_eqn02885.gif)）是为了避免方程求解器的困难。这个关系以增量形式使用：

![](../graphics/stm_eqn02886.gif)其中![](../graphics/stm_eqn02887.gif)是增量开始时的修正柯西应力。我们在虚功表达式中使用修正柯西应力，并用Lagrange乘子强制约束![](../graphics/stm_eqn02888.gif)来增强表达式：

![](../graphics/stm_eqn02889.gif)其中*J*是体积变化比（Jacobian），![](../graphics/stm_eqn02890.gif)是其插值仍需确定的Lagrange乘子。![](../graphics/stm_eqn02891.gif)将在每个单元上插值，以便以积分（平均）意义满足约束。由于![](../graphics/stm_eqn01051.gif)是从运动学解计算出的等效压力应力增量的值，如果材料完全不可压缩，[公式3.2.3-4](03s02a61-Hybrid-incompressible-solid-element-form.md)就没有意义，因为此时![](../graphics/stm_eqn01051.gif)无法计算。出于开发目的，我们认为体积模量是有限的，我们将能够表明，当允许体积模量接近无穷大时，最终公式接近可用极限。

对于切线刚度（Jacobian）的公式，我们需要定义![](../graphics/stm_eqn02892.gif)的变化率。因此，我们用参考体积![](../graphics/stm_eqn01828.gif)重写虚功方程：

![](../graphics/stm_eqn02893.gif)然后很容易获得变化率![](../graphics/stm_eqn02894.gif)

![](../graphics/stm_eqn02895.gif)我们用当前体积重写这个表达式：

![](../graphics/stm_eqn02896.gif)其中我们使用了恒等式![](../graphics/stm_eqn02897.gif)。

修正应力的变化率来自[公式3.2.3-4](03s02a61-Hybrid-incompressible-solid-element-form.md)和本构方程：

![](../graphics/stm_eqn02898.gif)其中

![](../graphics/stm_eqn02899.gif)我们使用了![](../graphics/stm_eqn02900.gif)的事实，因为![](../graphics/stm_eqn01727.gif)和![](../graphics/stm_eqn00033.gif)仅在静水部分不同。将这些表达式代入虚功变化率的表达式得到

![](../graphics/stm_eqn02901.gif)

仍然需要选择![](../graphics/stm_eqn02890.gif)。为了获得虚功变化率的对称表达式，我们选择

![](../graphics/stm_eqn02902.gif)其中

![](../graphics/stm_eqn02903.gif)是（瞬时）体积模量。这是![](../graphics/stm_eqn02890.gif)的合适选择，因为（独立的）与![](../graphics/stm_eqn02904.gif)成比例的项确保修正增量压力场![](../graphics/stm_eqn02891.gif)被正确约束到增量压力![](../graphics/stm_eqn01051.gif)。如果我们假设体积模量![](../graphics/stm_eqn02905.gif)和*K*随应变缓慢变化并忽略体积变化，我们可以为二阶变分![](../graphics/stm_eqn02906.gif)写成：

![](../graphics/stm_eqn02907.gif)因此，我们得到虚功表达式：

![](../graphics/stm_eqn02908.gif)其中

![](../graphics/stm_eqn02909.gif)对于虚功的变化率，我们发现

![](../graphics/stm_eqn02910.gif)初始应力项可以近似为

![](../graphics/stm_eqn02911.gif)可以写成

![](../graphics/stm_eqn02912.gif)所以虚功变化率的最终表达式变为

![](../graphics/stm_eqn02913.gif)

不对称项![](../graphics/stm_eqn02914.gif)仅在大体积变化发生时才显著。因此，该项被忽略，除了对于具有体积塑性的材料模型，如（封顶）Drucker-Prager模型和Cam-clay模型。对于这些模型，本构矩阵![](../graphics/stm_eqn00162.gif)通常已经是不对称的，因此添加这个非对称项不会影响分析成本。在![](../graphics/stm_eqn02906.gif)的表达式中假设了（体积）模量仅随应变缓慢变化。对于具有体积塑性的材料模型来说并非如此，这些模量可能发生突变。这可能导致收敛缓慢甚至收敛失败。失败通常仅发生在高阶单元中，因为在低阶单元中![](../graphics/stm_eqn02915.gif)在每一点都接近零，![](../graphics/stm_eqn02906.gif)中的误差没有影响。
### 参考

### 参考

"Abaqus Analysis User's Guide"第28.1.1节"实体（连续体）单元"
