# 4.8.2 有限应变粘弹性

### 4.8.2 有限应变粘弹性

![](../graphics/stm_eqn07272.gif)![](../graphics/stm_eqn07271.gif)![](../graphics/stm_eqn07267.gif)![](../graphics/stm_eqn07269.gif)![](../graphics/stm_eqn07268.gif)![](../graphics/stm_eqn07266.gif)![](../graphics/stm_eqn07270.gif)![](../graphics/stm_eqn01111.gif)![](../graphics/stm_eqn07238.gif)![](../graphics/stm_eqn07144.gif)**产品：** Abaqus/Standard  Abaqus/Explicit

### 积分公式

Abaqus中实现的有限应变粘弹性理论是超弹性或超泡沫本构模型的时间域泛化。假设材料的瞬时响应遵循超弹性本构方程：
![](../graphics/stm_eqn07225.gif)
对于可压缩材料为：
![](../graphics/stm_eqn07226.gif)![](../graphics/stm_eqn07227.gif)![](../graphics/stm_eqn07228.gif)![](../graphics/stm_eqn07229.gif)![](../graphics/stm_eqn07230.gif)![](../graphics/stm_eqn00319.gif)
对于不可压缩材料为：
![](../graphics/stm_eqn07231.gif)
其中分别是瞬时Kirchhoff应力的偏部分和静水部分。是与变形梯度相关的"畸变梯度"
![](../graphics/stm_eqn07232.gif)
其中

是体积变化。
![](../graphics/stm_eqn07233.gif)
使用分部积分和变量变换，线性各向同性粘弹性的基本遗传积分公式可以写成
![](../graphics/stm_eqn07234.gif)![](../graphics/stm_eqn01399.gif)![](../graphics/stm_eqn07235.gif)![](../graphics/stm_eqn07236.gif)![](../graphics/stm_eqn07237.gif)![](../graphics/stm_eqn07020.gif)![](../graphics/stm_eqn07159.gif)![](../graphics/stm_eqn07158.gif)
或者完全用应力表示为：
![](../graphics/stm_eqn07238.gif)![](../graphics/stm_eqn01111.gif)![](../graphics/stm_eqn07144.gif)
其中是约化时间，，且。是瞬时小应变剪切模量和体积模量，是时间相关的小应变剪切和体积松弛模量。回想约化时间代表随温度的时间偏移，通过微分方程与实际时间相关：

其中是温度，是位移函数。
![](../graphics/stm_eqn07239.gif)![](../graphics/stm_eqn07240.gif)![](../graphics/stm_eqn07241.gif)![](../graphics/stm_eqn07242.gif)![](../graphics/stm_eqn07243.gif)
使用大应变（超弹性）材料的参考配置中的体积/偏分割遗传积分，然后使用标准前推算子（见Simo, 1987），可以在当前配置中获得以下方程组：

其中是的当前状态相对于t时刻状态的畸变变形梯度。对应力进行变换，将时间的状态与时间t的状态关联起来。

![](../graphics/stm_eqn07244.gif)### 实现

![](../graphics/stm_eqn07245.gif)![](../graphics/stm_eqn05555.gif)![](../graphics/stm_eqn07246.gif)![](../graphics/stm_eqn07247.gif)![](../graphics/stm_eqn07248.gif)![](../graphics/stm_eqn07249.gif)![](../graphics/stm_eqn07250.gif)与小应变粘弹性一样，我们用Prony级数表示松弛模量

其中和是第i项的相对模量。注意。Abaqus假设松弛时间相同，因此从现在开始，我们将对体积和剪切行为求和N项。实际上，体积和剪切中的非零项数和不需要相等，除非瞬时行为基于超泡沫模型。在后一种情况下，两种变形模式密切相关，然后被假设同时相等且同时放松。

![](../graphics/stm_eqn07251.gif)将方程代入方程，我们得到

接下来，我们引入与级数各项相关的内部应力

![](../graphics/stm_eqn07252.gif)这些应力存储在每个材料点并随时间积分。我们将假设解在时间t已知，需要在时间构造解。

![](../graphics/stm_eqn07253.gif)![](../graphics/stm_eqn00438.gif)### 静水应力的积分

时间处的内部静水应力来自
![](../graphics/stm_eqn07254.gif)![](../graphics/stm_eqn00438.gif)
具有和，可得
![](../graphics/stm_eqn07255.gif)![](../graphics/stm_eqn07256.gif)![](../graphics/stm_eqn07257.gif)
由此与方程一起得出
![](../graphics/stm_eqn07258.gif)
为了积分方程中的第一个积分，我们假设在增量期间随约化时间线性变化
![](../graphics/stm_eqn07259.gif)
代入方程得
![](../graphics/stm_eqn07260.gif)![](../graphics/stm_eqn07261.gif)
积分很容易计算，提供增量结束时的解
![](../graphics/stm_eqn07262.gif)
或者，用稍微不同的形式
![](../graphics/stm_eqn07263.gif)
其中

注意对于，，和。对于，，和。
![](../graphics/stm_eqn07264.gif)
### 偏应力的积分
![](../graphics/stm_eqn07265.gif)
时间处的内部偏应力来自
![](../graphics/stm_eqn07266.gif)![](../graphics/stm_eqn07267.gif)![](../graphics/stm_eqn07268.gif)![](../graphics/stm_eqn07269.gif)![](../graphics/stm_eqn07270.gif)![](../graphics/stm_eqn07271.gif)![](../graphics/stm_eqn07272.gif)
观察

![](../graphics/stm_eqn07273.gif)![](../graphics/stm_eqn07274.gif)及其逆

![](../graphics/stm_eqn07275.gif)代入方程，和，给出

现在引入变量

![](../graphics/stm_eqn07276.gif)注意

![](../graphics/stm_eqn07277.gif)![](../graphics/stm_eqn07278.gif)![](../graphics/stm_eqn07279.gif)然后我们也可以引入

![](../graphics/stm_eqn07280.gif)![](../graphics/stm_eqn07281.gif)![](../graphics/stm_eqn07282.gif)将方程、和代入方程得

![](../graphics/stm_eqn07283.gif)为了积分方程中的第一个积分，我们假设在增量期间随约化时间线性变化：

它与方程变为

![](../graphics/stm_eqn07284.gif)偏应力的方程与静水应力的方程完全相同。因此，积分后我们得到

![](../graphics/stm_eqn07285.gif)其中

![](../graphics/stm_eqn07286.gif)因此，方程、和提供了直接的积分格式。

增量结束时的总应力变为

![](../graphics/stm_eqn07287.gif)它与方程和也可以写成

### 速率方程

![](../graphics/stm_eqn07288.gif)为了求解由本构方程生成的非线性方程组，我们需要生成共旋转本构速率方程。从方程可得

![](../graphics/stm_eqn07289.gif)![](../graphics/stm_eqn07261.gif)其中是共旋转（Jaumann）应力速率。上述方程的速率形式用于计算Jacobian。

![](../graphics/stm_eqn07290.gif)### Cauchy应力与Kirchhoff应力

![](../graphics/stm_eqn07291.gif)所有方程都是用Kirchhoff应力表示的。然而，Abaqus的实现使用Cauchy应力。为了转换到Cauchy应力，我们使用关系

使用，这允许我们将方程、、、和写成以下形式：

![](../graphics/stm_eqn07292.gif)虚功和虚功速率方程是相对于当前体积编写的。因此，共旋转应力速率是映射到当前配置中的Kirchhoff应力速率，并以与应力本身相同的方式进行变换。

![](../graphics/stm_eqn07293.gif)这组方程与、和的表达式结合，描述了位移公式中超粘弹性模型的完整实现。

速率方程可以写成与"超弹性材料行为"第4.6.1节类似的形式。引入

![](../graphics/stm_eqn07294.gif)其中和是瞬时模量，对应于"超弹性材料行为"第4.6.1节中的和。因此，所有速率方程可以通过将替换为和替换为获得。

![](../graphics/stm_eqn07295.gif)### 参考

### 参考

![](../graphics/stm_eqn00438.gif)![](../graphics/stm_eqn07254.gif)![](../graphics/stm_eqn07225.gif)"Abaqus Analysis User's Guide"第22.7.1节"时域粘弹性"
![](../graphics/stm_eqn07296.gif)![](../graphics/stm_eqn07297.gif)