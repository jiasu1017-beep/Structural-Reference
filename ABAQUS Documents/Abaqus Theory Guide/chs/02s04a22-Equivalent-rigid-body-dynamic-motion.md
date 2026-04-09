# 2.4.4 等效刚体动力运动

### 2.4.4 等效刚体动力运动

**产品：** Abaqus/Standard

获取模型一部分（或整个模型）的等效刚体运动通常很有用：部件质心的位置和平移速度，以及关于同一质心的角旋转和速度。Abaqus/Standard基于等效动量提供此类输出。本节定义如何计算这些值。

设 *V* 是请求等效刚体运动值的部件体积。部件在其初始配置中的密度为 ![](../graphics/stm_eqn00980.gif)，其中 ![](../graphics/stm_eqn00981.gif)、![](../graphics/stm_eqn00982.gif) 是部件中的材料坐标。材料粒子在其初始配置中的空间位置为 ![](../graphics/stm_eqn00983.gif)，在当前配置中为 ![](../graphics/stm_eqn00984.gif)，导致位移为 ![](../graphics/stm_eqn00985.gif)。我们希望计算部件质心的当前空间位置 ![](../graphics/stm_eqn00986.gif)；等效刚体的平移速度 ![](../graphics/stm_eqn00987.gif]；这个等效刚体的角速度 ![](../graphics/stm_eqn00988.gif]；等效刚体运动的平移位移 ![](../graphics/stm_eqn00989.gif]；以及关于质心的等效刚体旋转 ![](../graphics/stm_eqn00990.gif]。在这些定义中，"等效刚体"意味着具有相同质量分布以及与当前配置中实际变形部件相同平移和角动量的刚体。

为符号简单起见，我们定义一些量。部件的质量为

![](../graphics/stm_eqn00991.gif)其关于原点的一阶质量矩为

![](../graphics/stm_eqn00992.gif)其关于原点的二阶质量矩为

![](../graphics/stm_eqn00993.gif)其中 ![](../graphics/stm_eqn00064.gif) 是单位矩阵。

调用关系 ![](../graphics/stm_eqn00994.gif) 是方便的（假设求和约定），其中 ![](../graphics/stm_eqn00995.gif)是与每个自由度相关的有限元插值函数，![](../graphics/stm_eqn00996.gif) 是当前节点位置向量。我们现在可以写

![](../graphics/stm_eqn00997.gif)

认识到原始质量矩阵是

![](../graphics/stm_eqn00998.gif)我们得到

![](../graphics/stm_eqn00999.gif)我们可以立即获得

![](../graphics/stm_eqn01000.gif)并且，通过将等效和实际身体的平移动量相等，

![](../graphics/stm_eqn01001.gif)

部件的角速度通过将部件和关于质心的等效刚体的角动量相等来定义：

![](../graphics/stm_eqn01002.gif)其中

![](../graphics/stm_eqn01003.gif)是部件关于其质心的二阶质量矩。

Abaqus 对低阶单元使用集中质量公式。因此，惯性二阶质量矩可能偏离理论值，特别是对于粗网格。某些Abaqus单元对这个二阶质量矩（转动惯量）产生集中或结构贡献，不显示在这些方程中。

这提供

![](../graphics/stm_eqn01004.gif)其中

![](../graphics/stm_eqn01005.gif)是部件关于原点的角动量。

等效刚体运动中质心感知到的平移运动计算为

![](../graphics/stm_eqn01006.gif)

部件相对于其质心的等效刚体旋转需要一些概念近似，如下所示。表示材料粒子相对于未变形配置和变形配置中质心的相对位置分别为 ![](../graphics/stm_eqn01007.gif) 和 ![](../graphics/stm_eqn01008.gif)。考虑配置是已知的，身体的旋转轴由单位向量 ![](../graphics/stm_eqn01009.gif) 表示。材料粒子看到相对于质心这样的旋转为

![](../graphics/stm_eqn01010.gif)其中下标 *p* 表示向量投影到垂直于 ![](../graphics/stm_eqn01009.gif) 的平面上。我们现在通过积分组成部分来推广这个概念。定义

![](../graphics/stm_eqn01011.gif)平均 Euler 旋转然后遵循方程

![](../graphics/stm_eqn01012.gif)

这些积分不容易计算，但通过以下修改，它们可以展开，使得（最初未知的）当前质心 ![](../graphics/stm_eqn00986.gif] 仅出现在与已知当前配置中粒子位置的乘积中。

上述直观推广的有效性的必要条件是，如果部件经历任意刚体旋转，公式返回旋转。这可以很容易地证明如下。每个材料粒子精确旋转角度 ![](../graphics/stm_eqn01013.gif)，方式为

![](../graphics/stm_eqn01014.gif)因此，

![](../graphics/stm_eqn01015.gif)

在所有这些方程中，方向向量 ![](../graphics/stm_eqn01009.gif) 是未知的。为了确定 ![](../graphics/stm_eqn00156.gif)，我们考虑刚体旋转位移场的特征。对于这样的场，1）粒子的位移垂直于旋转向量，2）位移垂直于运动一半时的位置向量。在变形体上下文中，我们试图通过强制这两个陈述在平均意义上成立来确定 ![](../graphics/stm_eqn00156.gif]。考虑到我们严格关注关于质心的旋转，其定义自动确保第一个陈述成立。第二个条件可以写成形式

![](../graphics/stm_eqn01016.gif)这是关于 ![](../graphics/stm_eqn00156.gif) 分量的齐次方程组，系数由已知量积分组成，可以从中求解 ![](../graphics/stm_eqn01009.gif)。然后我们可以使用

![](../graphics/stm_eqn01017.gif)计算旧位置和新位置到垂直于 ![](../graphics/stm_eqn01009.gif) 平面的投影，并通过简单代入得到

![](../graphics/stm_eqn01018.gif)其中向量 ![](../graphics/stm_eqn01019.gif) 可以从可用量容易地计算。有了已知的 ![](../graphics/stm_eqn01009.gif)，![](../graphics/stm_eqn01020.gif) 就被确定可以使用相同表达式计算量 *b*，得到

![](../graphics/stm_eqn01021.gif)一旦 ![](../graphics/stm_eqn01020.gif) 和 *b* 已知，![](../graphics/stm_eqn01022.gif) 就容易确定了。

等效刚体旋转的确定基于平均粒子平移。转动自由度在计算此变量时被忽略；假设这样的旋转将产生点的运动，这些运动将明显地有助于计算。但是，可能找到病理情况并非如此；例如，如果考虑的模型部分仅由转动惯量单元组成，计算的平均刚体旋转将被计算为零，即使单元确实已经旋转。
### 参考

### 参考

"Abaqus Analysis User's Guide" 第6.3.2节"使用直接积分的隐式动力学分析"