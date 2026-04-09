# 4.3.5 经受循环加载的金属模型

### 4.3.5 经受循环加载的金属模型

**产品：** Abaqus/Standard  Abaqus/Explicit

Abaqus中的运动硬化模型旨在模拟经受循环加载的金属的行为。这些模型通常应用于低周疲劳和棘轮效应研究。这些模型的基本概念是屈服面在应力空间中移动，使得在一个方向上的应变降低相反方向的屈服应力，从而模拟Bauschinger效应和由加工硬化引起的各向异性。

Abaqus中提供了两种运动硬化模型。最简单的模型提供线性运动硬化，因此主要用于低周疲劳评估。如果在塑性范围内将单轴行为线性化（恒定加工硬化斜率），此模型会产生物理上合理的结果。这通常最好通过猜测问题中将达到的应变水平并相应地线性化实际材料行为来完成。认识到该理论提供合理结果的能力方面的这一限制并相应地提供材料数据是很重要的。此模型可用于Mises或Hill屈服面。

组合各向同性/运动硬化模型是线性模型的扩展。它比对线性模型提供对应力-应变关系更准确的近似。它还建模其他现象——如棘轮效应、平均应力松弛和循环硬化——这些是经受循环加载材料的典型现象。此外，可以叠加几个运动硬化模型，当应变变化范围显著时，这通常会产生更准确的结果，并允许更准确地建模棘轮效应。此模型仅适用于Mises屈服面。

本节首先描述两个模型公式共同的方面；然后给出每个模型的具体公式。
### 应变率分解

总应变率![](../graphics/stm_eqn05737)用弹性和塑性应变率写为

![](../graphics/stm_eqn05738)
### 弹性行为

弹性行为只能建模为线性弹性

![](../graphics/stm_eqn05739)其中![](../graphics/stm_eqn05740)表示四阶弹性张量，![](../graphics/stm_eqn05741)和![](../graphics/stm_eqn05742)分别是二阶应力张量和应变张量。
### 塑性行为

这些模型是压力无关塑性模型。对于两个模型，屈服面由函数

![](../graphics/stm_eqn05743)定义，其中![](../graphics/stm_eqn05744)是关于背应力或"运动偏移"![](../graphics/stm_eqn05745)的等效Mises应力或Hill势，![](../graphics/stm_eqn05285)是屈服面的大小。例如，等效Mises应力定义为

![](../graphics/stm_eqn05746)其中![](../graphics/stm_eqn05747)是背应力的偏量部分，![](../graphics/stm_eqn05748)是偏应力张量。

这些模型假设相关的塑性流动：

![](../graphics/stm_eqn05749)其中![](../graphics/stm_eqn05750表示塑性流动率，![](../graphics/stm_eqn05751是等效塑性应变率，![](../graphics/stm_eqn05752)
### 线性运动硬化模型

此模型是Abaqus中提供的两种运动硬化模型中较简单的一种。屈服面的大小![](../graphics/stm_eqn05753)对于此模型只能是温度的函数。![](../graphics/stm_eqn05754的演化由Ziegler硬化规则定义，在非等温情况下推广为

![](../graphics/stm_eqn05755)其中![](../graphics/stm_eqn05756是硬化参数（![](../graphics/stm_eqn05756)是等温单轴应力-应变响应的加工硬化斜率，![](../graphics/stm_eqn05757)，在不同温度下取得），![](../graphics/stm_eqn05758是*C*随时间的变化率。这种![](../graphics/stm_eqn05754演化律形式定义屈服面中心![](../graphics/stm_eqn05759的当前半径向量方向上塑性应变的![](../graphics/stm_eqn05754变化率，温度变化导致的变化率朝向应力空间原点。![](../graphics/stm_eqn05758项在![](../graphics/stm_eqn05754演化中的包含确保材料响应对温度历史无关，因此，可以用等温数据表征。[Rice（1975）](07s01a01-References.md)相当一般地写道

![](../graphics/stm_eqn05760)假设了上述[公式4.3.5-6](04s03a107.md)中![](../graphics/stm_eqn05761)和![](../graphics/stm_eqn05762的特定识别，因此材料行为仅由等温单轴加工硬化数据![](../graphics/stm_eqn05756定义。
### 非线性各向同性/运动硬化模型

此模型基于[Lemaitre和Chaboche（1990）](07s01a01-References.md)的工作。屈服面的大小![](../graphics/stm_eqn05763定义为等效塑性应变![](../graphics/stm_eqn05764、温度![](../graphics/stm_eqn01111)和场变量![](../graphics/stm_eqn01501的函数。这种依赖性可以直接提供，可以在用户子程序UHARD中编码，或者可以用对于循环硬化或软化材料简单指数律建模为

![](../graphics/stm_eqn05765)其中![](../graphics/stm_eqn05766是零塑性应变时的屈服面大小，![](../graphics/stm_eqn05767和![](../graphics/stm_eqn05768是必须从循环测试数据校准的附加材料参数。

总体背应力由多个背应力分量组成，其中模型背应力分量的演化定义为

![](../graphics/stm_eqn05769)和总体背应力从关系

![](../graphics/stm_eqn05770)计算，其中*N*是背应力数量，![](../graphics/stm_eqn05771和![](../graphics/stm_eqn05772是材料参数，![](../graphics/stm_eqn05773是![](../graphics/stm_eqn05771)随温度和场变量的变化率。这个方程是基本Ziegler律，推广以考虑![](../graphics/stm_eqn05771的温度和场变量依赖性，并添加了"回忆"项![](../graphics/stm_eqn05774。回忆项在演化律中引入非线性。![](../graphics/stm_eqn05772)随温度和场变量的变化率在![](../graphics/stm_eqn05775的演化律中不考虑。因此，如果![](../graphics/stm_eqn05772)随温度变化，模型预测的材料响应将对温度历史敏感。然而，可以表明这种对温度历史的依赖性很小，随塑性变形的增加而消失。对于完全的温度历史无关行为，条件是使用![](../graphics/stm_eqn05772)的恒定值）。

背应力和各向同性硬化的演化在[图4.3.5-1](04s03a107.md)中针对单向加载说明，在[图4.3.5-2](04s03a107.md)中针对多轴加载说明。

图4.3.5-1 非线性模型的一维表示。

![](../graphics/chardening-comb-1d-rep.png)

图4.3.5-2 非线性模型的三维表示。

![](../graphics/chardening-comb-3d-rep-nls.png)屈服面的中心包含在半径为![](../graphics/stm_eqn05776的圆柱内，这直接从[公式4.3.5-10](04s03a107.md)得出。因此，屈服面包含在图中所示的极限面（半径![](../graphics/stm_eqn05777）内。通过设置![](../graphics/stm_eqn05778)和![](../graphics/stm_eqn05779对于![](../graphics/stm_eqn05780，此模型可以退化为上述线性运动模型。

此模型可以捕捉的物理行为及其局限性在Abaqus Analysis User's Guide中详细描述。
### 参考

### 参考

"Models for metals subjected to cyclic loading," Section 23.2.2 of the Abaqus Analysis User's Guide
