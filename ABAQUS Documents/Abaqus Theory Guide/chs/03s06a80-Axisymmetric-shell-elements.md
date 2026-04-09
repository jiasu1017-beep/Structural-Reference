# 3.6.2 轴对称壳单元

### 3.6.2 轴对称壳单元

**产品：** Abaqus/Standard  Abaqus/Explicit

这两个壳单元是上一节描述的壳的轴对称版本，使用[Hughes等人（1977）](07s01a01-References.md)的"缩减积分惩罚"方法。虽然这些是壳单元，它们也是二维梁单元B21和B22的简单扩展。扩展包括周向项。因此，这些单元是一维的，在径向平面中变形。该平面中的笛卡尔坐标是*r*（半径）和*z*（轴向位置）。沿这种平面中壳参考表面测量的距离由材料坐标*S*表示（见[图3.6.2-1](03s06a80-Axisymmetric-shell-elements.md)）。

图3.6.2-1 轴对称壳。

![](../graphics/stmaxishellfig-nls.png)
### 插值和积分

2节点单元（SAX1）使用线性插值函数的单点积分来分布载荷。质量矩阵是集中的。3节点单元（SAX2）使用二次插值函数的二点积分来计算刚度，三次插值函数的三个点来分布载荷。SAX2使用一致质量矩阵。所有积分使用Gauss方法。沿厚度的积分遵循Abaqus中使用的常规数值或精确方案。
### 理论

这个壳理论允许壳的有限应变和旋转。使用的应变度量被选择为对对数应变给出近似（精确到二阶项）。因此，该理论旨在直接应用于涉及非弹性或次弹性变形的情况，其中应力-应变行为以Kirchhoff应力（通常工程文献中的"真实"应力）和对数应变给出，如金属塑性。该理论是近似的，但近似没有被严格证明：它们是为了简单而引入的，似乎是合理的。这些近似如下：

做了一个"薄度"假设。这意味着在任何时候，仅包括关于厚度方向坐标直到一阶的项。

假设由平行于其参考表面拉伸引起的壳变薄在整个厚度上是均匀的，并由壳参考表面上的不可压缩条件定义。显然，这是一个相对粗略的近似，特别是在壳承受纯弯曲的情况。它被采用是因为它简单，并模拟了与膜应变相关的变薄效果：这被认为在预期的应用类型中是主要的，如承受超压的管道和容器的失效。

假设壳的变薄是平滑发生的——即，假设关于参考表面位置的变薄梯度可以忽略。这意味着局部化效应，如壳的颈缩，仅以非常粗略的方式建模。同样，采用这个近似的原因是简单——局部化效应的细节对单元设计的应用类型不重要。

除了平行于参考表面的应力外，忽略所有应力；并且对于不可忽略的应力，假设平面应力理论。与上述（c）一样，这排除了详细的局部化研究，但引入了公式化的相当大的简化。

平面保持平面。已经表明，这与我们上面的大多数材料模型的薄度假设（a）一致。这里它只是被假定而没有进一步证明。

假设横向剪切是小的，并且材料对这种变形的响应是线性弹性的。引入横向剪切是因为使用的单元是"缩减积分，惩罚"类型（例如，见[Hughes等人，1977](07s01a01-References.md)）。在这些单元中，参考表面上的位置和最初垂直于参考表面的线的旋转被独立插值：横向剪切刚度随后被视为在选定（缩减积分）点强制执行必要约束的惩罚项。这个横向剪切刚度是相对厚壳的实际弹性值。对于较薄的情况，必须为数值原因降低惩罚——这在Abaqus中以[Hughes等人（1977）](07s01a01-References.md)描述的方式完成。

现在详细描述该理论。概念取自各种来源，特别是[Budiansky和Sanders（1963）](07s01a01-References.md)和[Rodal和Witmer（1979）](07s01a01-References.md)。壳中材料点的位置为

![](../graphics/stm_eqn04024.gif)其中

![](../graphics/stm_eqn04025.gif)

是壳参考表面上一点的位置；

![](../graphics/stm_eqn04026.gif)

是"厚度"方向的单位向量，这个方向最初垂直于参考表面；

![](../graphics/stm_eqn04027.gif)

是壳在厚度方向的拉伸；

![](../graphics/stm_eqn02098.gif)

测量关于厚度方向的位置，在参考配置中；和

![](../graphics/stm_eqn04028.gif)

是参考表面中的材料坐标。

上面列出的假设意味着![](../graphics/stm_eqn04029.gif)仅为常数，且![](../graphics/stm_eqn04030.gif)是小的量。[公式3.6.2-1](03s06a80-Axisymmetric-shell-elements.md)在增量结束时写出，在增量开始时同样的方程写为

![](../graphics/stm_eqn04031.gif)增量结束时的度量为

![](../graphics/stm_eqn04032.gif)其中

![](../graphics/stm_eqn04033.gif)和

![](../graphics/stm_eqn04034.gif)是参考曲面曲率张量（二次基本形式）的近似。如果

![](../graphics/stm_eqn04036.gif)![](../graphics/stm_eqn04035.gif)将正是通常定义的曲率张量。只有对于这些单元，由于允许小的横向剪切，这近似为真。

在增量开始时，同样的量为

![](../graphics/stm_eqn04037.gif)

承受轴对称变形的轴对称壳有一个极大的简化，即主方向不旋转。因此，通过假定![](../graphics/stm_eqn04038.gif)和![](../graphics/stm_eqn04039.gif) orient in these principal directions（![](../graphics/stm_eqn04040.gif)是经向的，![](../graphics/stm_eqn03939.gif)是周向的），这些方向内发生的拉伸比在增量中写为

![](../graphics/stm_eqn04041.gif)其中从这点往后，对于指标![](../graphics/stm_eqn00904.gif)和![](../graphics/stm_eqn01219.gif)省略了求和约定。使用[公式3.6.2-3](03s06a80-Axisymmetric-shell-elements.md)和[公式3.6.2-4](03s06a80-Axisymmetric-shell-elements.md)并截断到![](../graphics/stm_eqn02098.gif)的一阶给出

![](../graphics/stm_eqn04042.gif)其中

![](../graphics/stm_eqn04043.gif)和

![](../graphics/stm_eqn04044.gif)增量应变，![](../graphics/stm_eqn04045.gif)，定义为

![](../graphics/stm_eqn04046.gif)因为这个表达式二阶项精确近似对数应变的增量，它可以被认为是变形率的核心差分近似。使用这个表达式是因为我们预期每个增量最多使用20%的应变增量：在这个幅度下，这个增量应变定义与对数应变增量之间的差异约为1%，这似乎是可以接受的（增量的4%）。在更低——可能更典型——的应变增量值下，误差更小。同样，展开到厚度方向坐标![](../graphics/stm_eqn02098.gif)的一阶，我们获得

![](../graphics/stm_eqn04047.gif)其中![](../graphics/stm_eqn04048.gif)是参考表面的增量应变——膜应变。现在考虑项

![](../graphics/stm_eqn04049.gif)写成![](../graphics/stm_eqn04050.gif)，其中*e*表示在增量内发生的每单位长度的长度变化（相对于增量开始时配置的"标称应变"）。

那么

![](../graphics/stm_eqn04051.gif)同样，如果![](../graphics/stm_eqn04052.gif)为20%，这意味着

![](../graphics/stm_eqn04053.gif)因此，再次使用实际应用将涉及不超过几个百分点的应变增量的论点，我们近似

![](../graphics/stm_eqn04054.gif)这然后给出

![](../graphics/stm_eqn04055.gif)厚度方向的拉伸比假定由参考表面上以下关系定义：

![](../graphics/stm_eqn04056.gif)其中![](../graphics/stm_eqn04057.gif是由热膨胀引起的厚度拉伸比。

从![](../graphics/stm_eqn04058.gif)的定义

![](../graphics/stm_eqn04059.gif)横向剪切应变写成

![](../graphics/stm_eqn04060.gif)使用这个简单形式是因为这些应变总是假定为很小。这完成了增量应变定义的陈述，因此连同表示平衡的虚功声明——一种理论是可用的。然而，有必要满足理论在适当运动下提供常应变这个最低要求。如果理论要适合许多实际案例，特别是涉及热加载的案例，这是必不可少的。有趣的是，[Rodal和Witmer（1979）](07s01a01-References.md)中的理论似乎违反了这个要求。为了实现这一点，定义了修正的增量曲率变化度量

![](../graphics/stm_eqn04061.gif)其中

![](../graphics/stm_eqn04062.gif)我们知道增量结束和开始时![](../graphics/stm_eqn00904.gif)线的曲率半径为

![](../graphics/stm_eqn04063.gif)和

![](../graphics/stm_eqn04064.gif)在这些表达式中，与在以下推导中一样，重复索引![](../graphics/stm_eqn00904.gif)不暗示求和。如果![](../graphics/stm_eqn00904.gif)线在增量期间被均匀拉伸![](../graphics/stm_eqn04065.gif)，我们要求

![](../graphics/stm_eqn04066.gif)并且，进一步，壳的这样均匀拉伸必须给出常应变，因此我们假定

![](../graphics/stm_eqn04067.gif)我们需要在这种情况下

![](../graphics/stm_eqn04068.gif)在这个运动中

![](../graphics/stm_eqn04069.gif)

定义

![](../graphics/stm_eqn04070.gif)并假定

![](../graphics/stm_eqn04071.gif)满足要求。[公式3.6.2-9](03s06a80-Axisymmetric-shell-elements.md)可以通过代入[公式3.6.2-7](03s06a80-Axisymmetric-shell-elements.md)中![](../graphics/stm_eqn04072.gif)的定义简化为

![](../graphics/stm_eqn04073.gif)因此

![](../graphics/stm_eqn04074.gif)

公式化通过假定虚功方程可以写成

![](../graphics/stm_eqn04075.gif)来完成，其中

![](../graphics/stm_eqn04076.gif)

是一点的Kirchhoff应力；

![](../graphics/stm_eqn04077.gif)

在壳中，由使用[公式3.6.2-10](03s06a80-Axisymmetric-shell-elements.md)中的应变增量求和定义的平面应力理论得出；

![](../graphics/stm_eqn04078.gif)

是[公式3.6.2-10](03s06a80-Axisymmetric-shell-elements.md)中应变增量的变分；

![](../graphics/stm_eqn04079.gif)

是每单位面积的横向剪切力，由![](../graphics/stm_eqn04080.gif)定义；其中

![](../graphics/stm_eqn01362.gif)

是来自[公式3.6.2-8](03s06a80-Axisymmetric-shell-elements.md)的横向剪切应变，

*h*

是壳的原始厚度，

![](../graphics/stm_eqn04081.gif)

是弹性横向剪切刚度（如果壳太薄以避免数值问题，则根据[Hughes等人（1977）](07s01a01-References.md)的建议减少）；和

![](../graphics/stm_eqn04082.gif)

是虚外部功变化率。这完成了公式化的陈述。
### 参考

### 参考

"Abaqus Analysis User's Guide"第29.6.9节"轴对称壳单元库"
