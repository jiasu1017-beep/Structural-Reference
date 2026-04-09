# 4.5.2 混凝土和其他准脆性材料的损伤塑性模型

### 4.5.2 混凝土和其他准脆性材料的损伤塑性模型

**产品：** Abaqus/Standard  Abaqus/Explicit

本节描述Abaqus中提供的混凝土损伤塑性模型，用于混凝土和其他准脆性材料的分析。Abaqus的材料库还包括用于混凝土的其他本构模型，基于 smeared crack 方法。这些是Abaqus/Standard中的 smeared crack 模型，如"混凝土的非弹性本构模型，"第4.5.1节所述，以及Abaqus/Explicit中的脆性裂缝模型，如"混凝土和其他脆性材料的裂缝模型，"第4.5.3节所述。

混凝土损伤塑性模型主要用于混凝土结构在循环和/或动态加载下的分析。该模型也适用于其他准脆性材料（如岩石、砂浆和陶瓷）的分析；但在本节余下部分，使用混凝土的行为来说明本构理论的不同方面。在低约束压力下，混凝土表现为脆性方式；主要破坏机制是拉伸中的裂缝和压缩中的压碎。当约束压力足够大以防止裂缝扩展时，混凝土的脆性行为消失。在这些情况下，破坏是由混凝土微孔微观结构的固结和坍塌驱动的，导致类似于具有加工硬化的延性材料的宏观响应。

在塑性-损伤模型考虑范围内，建模大静水压力下的混凝土行为超出了范围。本节的本构理论旨在捕捉在相当低的约束压力下（小于单轴压缩加载中极限压缩应力的四或五倍），与混凝土和其他准脆性材料中发生的破坏机制相关的不可逆损伤的影响。这些影响表现为以下宏观性质：

拉伸和压缩中不同的屈服强度，压缩中的初始屈服应力比拉伸中的初始屈服应力高10倍或更多；

与压缩中的初始硬化然后软化相反的拉伸中的软化行为；

拉伸和压缩中弹性刚度的不同程度退化；

循环加载期间的刚度恢复效应；和

率敏感性，特别是峰值强度随应变率的增加。

Abaqus中的塑性-损伤模型基于Lubliner等（[1989](07s01a01-References.md)）和Lee与Fenves（[1998](07s01a01-References.md)）提出的模型。本节余下部分描述该模型。首先给出模型主要成分的概述，然后对本构模型的不同方面进行更详细的讨论。
### 概述

无粘性混凝土损伤塑性模型的主要成分总结如下。
### 应变率分解

对于率无关模型假定加性应变率分解：
![](../graphics/stm_eqn05834.gif)![](../graphics/stm_eqn00118.gif)![](../graphics/stm_eqn05527.gif)![](../graphics/stm_eqn05528.gif)
![](../graphics/stm_eqn05834)其中![](../graphics/stm_eqn00118)是总应变率，![](../graphics/stm_eqn05527)是应变率的弹性部分，![](../graphics/stm_eqn05528)是应变率的塑性部分。
### 应力-应变关系

![](../graphics/stm_eqn06481.gif)![](../graphics/stm_eqn06482.gif)![](../graphics/stm_eqn06483.gif)应力-应变关系由标量损伤弹性控制：

![](../graphics/stm_eqn06484.gif)![](../graphics/stm_eqn06481)其中![](../graphics/stm_eqn06482)是材料的初始（未损伤）弹性刚度；![](../graphics/stm_eqn06483)是退化弹性刚度；*d*是标量刚度退化变量，可以取从零（未损伤材料）到一（完全损伤材料）的值。与混凝土破坏机制（裂缝和压碎）相关的损伤导致弹性刚度降低。在标量损伤理论范围内，刚度退化是各向同性的，由单个退化变量*d*表征。遵循连续体损伤力学的通常概念，有效应力定义为

![](../graphics/stm_eqn06485.gif)![](../graphics/stm_eqn06486.gif)![](../graphics/stm_eqn06487.gif)![](../graphics/stm_eqn06488.gif)![](../graphics/stm_eqn00033.gif)![](../graphics/stm_eqn06489.gif)![](../graphics/stm_eqn06490.gif)![](../graphics/stm_eqn06484)Cauchy应力通过标量退化关系与有效应力相关：

![](../graphics/stm_eqn06491.gif)![](../graphics/stm_eqn06492.gif)![](../graphics/stm_eqn06485)对于材料的任何给定横截面，系数![](../graphics/stm_eqn06486)表示有效承载面积（即，整体面积减去损伤面积）与整体横截面积之比。在没有损伤的情况下，![](../graphics/stm_eqn06487)，有效应力![](../graphics/stm_eqn06488)等价于Cauchy应力![](../graphics/stm_eqn00033)。然而，当损伤发生时，有效应力比Cauchy应力更具代表性，因为是有效应力面积在抵抗外部载荷。因此，方便的是将塑性问题以有效应力表示。如后面讨论的，退化变量的演化由一组硬化变量![](../graphics/stm_eqn06489)和有效应力控制；即，![](../graphics/stm_eqn06490)。
### 硬化变量
![](../graphics/stm_eqn06493.gif)
拉伸和压缩中的损伤状态分别由两个硬化变量![](../graphics/stm_eqn06491)和![](../graphics/stm_eqn06492)独立表征，它们分别被称为拉伸和压缩中的等效塑性应变。硬化变量的演化由以下形式的关系给出

![](../graphics/stm_eqn06493)如本节后面所述。
![](../graphics/stm_eqn06494.gif)
混凝土中的微裂缝和压碎由硬化变量的增加值表示。这些变量控制屈服面的演化和弹性刚度的退化。它们还与产生微裂缝所需的消散断裂能密切相关。
![](../graphics/stm_eqn06495.gif)### 屈服函数

屈服函数![](../graphics/stm_eqn06494)表示有效应力空间中的一个面，它决定失效或损伤状态。对于无粘性塑性-损伤模型

![](../graphics/stm_eqn06496.gif)![](../graphics/stm_eqn05794.gif)![](../graphics/stm_eqn06495)屈服函数的具体形式在本节后面描述。
### 流动规则

塑性流动由流动势*G*根据流动规则控制：
![](../graphics/stm_eqn06497.gif)![](../graphics/stm_eqn05794.gif)![](../graphics/stm_eqn06498.gif)![](../graphics/stm_eqn06499.gif)
![](../graphics/stm_eqn06496)其中![](../graphics/stm_eqn05794)是非负塑性乘子。塑性势在有效应力空间中定义。混凝土损伤塑性模型流动势的具体形式在本节后面讨论。该模型使用非相关塑性，因此需要求解非对称方程。
![](../graphics/stm_eqn06500.gif)### 总结

总之，混凝土损伤塑性模型的弹塑性响应以有效应力和硬化变量描述：

![](../graphics/stm_eqn06497)其中![](../graphics/stm_eqn05794)和*F*服从Kuhn-Tucker条件：![](../graphics/stm_eqn06498)Cauchy应力根据刚度退化变量![](../graphics/stm_eqn06499)和有效应力计算为
![](../graphics/stm_eqn06501.gif)![](../graphics/stm_eqn06492.gif)
![](../graphics/stm_eqn06500)

弹塑性响应的本构关系（[公式4.5.2-1](04s05a120.md)）从刚度退化响应（[公式4.5.2-2](04s05a120.md)）解耦，这使得模型对有效数值实现具有吸引力。这里总结的无粘性模型可以通过使用粘塑性正则化来允许应力位于屈服面之外，从而容易地扩展以考虑粘塑性效应。
![](../graphics/stm_eqn06502.gif)![](../graphics/stm_eqn06503.gif)![](../graphics/stm_eqn06504.gif)![](../graphics/stm_eqn06505.gif)![](../graphics/stm_eqn06506.gif)![](../graphics/stm_eqn01111.gif)![](../graphics/stm_eqn06507.gif)### 损伤和刚度退化

硬化变量![](../graphics/stm_eqn06501)和![](../graphics/stm_eqn06492)的演化方程通过首先考虑单轴加载条件然后扩展到多轴条件来方便地制定。
### 单轴条件
![](../graphics/stm_eqn06508.gif)![](../graphics/stm_eqn05858.gif)![](../graphics/stm_eqn06509.gif)
假定单轴应力-应变曲线可以转换为如下形式的应力与塑性应变曲线
![](../graphics/stm_eqn06510.gif)![](../graphics/stm_eqn06511.gif)
![](../graphics/stm_eqn06502)其中下标*t*和*c*分别指拉伸和压缩；![](../graphics/stm_eqn06503)和![](../graphics/stm_eqn06504)是等效塑性应变率，![](../graphics/stm_eqn06505)和![](../graphics/stm_eqn06506)是等效塑性应变，![](../graphics/stm_eqn01111)是温度，![](../graphics/stm_eqn06507)是其他预定义场变量。
![](../graphics/stm_eqn06512.gif)
在单轴加载条件下，有效塑性应变率给出为

![](../graphics/stm_eqn06508)在本节余下部分，我们采用约定，![](../graphics/stm_eqn05858)是一个正值，表示单轴压缩应力的大小；即，![](../graphics/stm_eqn06509)。

如图[图4.5.2-1](04s05a120.md)所示，当混凝土试样从应力-应变曲线应变软化分支上的任何点卸载时，卸载响应被观察到弱化：材料的弹性刚度似乎受损（或退化）。弹性刚度的退化在拉伸和压缩试验之间显著不同；在任一情况下，随着塑性应变的增加，效应更明显。混凝土的退化响应由两个独立的单轴损伤变量![](../graphics/stm_eqn06510)和![](../graphics/stm_eqn06511)表征，它们假定为塑性应变、温度和场变量的函数：
![](../graphics/stm_eqn06513.gif)
![](../graphics/stm_eqn06512)
![](../graphics/stm_eqn06514.gif)![](../graphics/stm_eqn06515.gif)![](../graphics/stm_eqn06516.gif)
图4.5.2-1 混凝土对单轴加载在拉伸（a）和压缩（b）中的响应。
![](../graphics/stm_eqn06517.gif)
![](../graphics/cconcretedamaged-uniaxial.png)单轴退化变量是等效塑性应变的递增函数。它们可以取从零（对于未损伤材料）到一（对于完全损伤材料）的值。

如果![](../graphics/stm_eqn06513)是材料的初始（未损伤）弹性刚度，则单轴拉伸和压缩加载下的应力-应变关系分别为：

![](../graphics/stm_eqn06514)在单轴加载条件下，裂缝沿垂直于应力方向扩展。因此，裂缝的形核和扩展导致可用承载面积的减少，这又导致有效应力的增加。在压缩加载下效应不太明显，因为裂缝平行于加载方向扩展；然而，在大量压碎之后，有效承载面积也显著减少。有效单轴内聚应力![](../graphics/stm_eqn06515)和![](../graphics/stm_eqn06516)给出为
![](../graphics/stm_eqn06518.gif)![](../graphics/stm_eqn06513.gif)
![](../graphics/stm_eqn06517)有效单轴内聚应力决定屈服（或破坏）面的大小。
![](../graphics/stm_eqn06519.gif)![](../graphics/stm_eqn06520.gif)![](../graphics/stm_eqn06510.gif)![](../graphics/stm_eqn06511.gif)### 单轴循环条件

![](../graphics/stm_eqn06521.gif)![](../graphics/stm_eqn06522.gif)![](../graphics/stm_eqn06523.gif)在单轴循环加载条件下，退化机制相当复杂，涉及先前形成的微裂缝的张开和闭合，以及它们的相互作用。实验上，观察到在单轴循环试验中当载荷改变符号时弹性刚度有一些恢复。刚度恢复效应，也称为"单侧效应"，是混凝土在循环加载下行为的一个重要方面。效应通常在载荷从拉伸变为压缩时更明显，导致拉伸裂缝闭合，从而恢复压缩刚度。

![](../graphics/stm_eqn06524.gif)混凝土损伤塑性模型假定弹性模量的降低以标量退化变量*d*给出，如

![](../graphics/stm_eqn06525.gif)![](../graphics/stm_eqn06526.gif)![](../graphics/stm_eqn06527.gif)![](../graphics/stm_eqn06528.gif)![](../graphics/stm_eqn06529.gif)![](../graphics/stm_eqn06518)其中![](../graphics/stm_eqn06513)是材料的初始（未损伤）模量。

![](../graphics/stm_eqn06530.gif)![](../graphics/stm_eqn06531.gif)![](../graphics/stm_eqn06532.gif)![](../graphics/stm_eqn06533.gif)![](../graphics/stm_eqn06534.gif)![](../graphics/stm_eqn06535.gif)![](../graphics/stm_eqn06536.gif)![](../graphics/stm_eqn06537.gif)![](../graphics/stm_eqn06487.gif)![](../graphics/stm_eqn06538.gif)![](../graphics/stm_eqn06539.gif)![](../graphics/stm_eqn06533.gif)![](../graphics/stm_eqn06527.gif)该表达式在循环的拉伸侧（![](../graphics/stm_eqn06519）和压缩侧（![](../graphics/stm_eqn06520）都适用。刚度降低变量*d*是应力状态和单轴损伤变量![](../graphics/stm_eqn06510)和![](../graphics/stm_eqn06511)的函数。对于单轴循环条件，Abaqus假定

![](../graphics/stm_eqn06527.gif)![](../graphics/stm_eqn06521)其中![](../graphics/stm_eqn06522)和![](../graphics/stm_eqn06523)是引入的表示与应力反向相关刚度恢复效应的应力状态函数。它们根据以下定义

![](../graphics/stm_eqn06524)其中

![](../graphics/stm_eqn06525)权重因子![](../graphics/stm_eqn06526)和![](../graphics/stm_eqn06527)，假定为材料属性，控制拉伸和压缩刚度在载荷反向时的恢复。为了说明这一点，考虑[图4.5.2-2](04s05a120.md)中的示例，其中载荷从拉伸变为压缩。假定材料先前没有压缩损伤（压碎）；即，![](../graphics/stm_eqn06528)和![](../graphics/stm_eqn06529)。那么

![](../graphics/stm_eqn06540.gif)![](../graphics/stm_eqn06530)在拉伸中（![](../graphics/stm_eqn06531)，![](../graphics/stm_eqn06532)；因此，![](../graphics/stm_eqn06533) as expected. 在压缩中（![](../graphics/stm_eqn06534)，![](../graphics/stm_eqn06535)，且![](../graphics/stm_eqn06536)。如果![](../graphics/stm_eqn06537)，则![](../graphics/stm_eqn06487)；因此，材料完全恢复压缩刚度（在本例中是初始未损伤刚度，![](../graphics/stm_eqn06538)。另一方面，如果![](../graphics/stm_eqn06539)，则![](../graphics/stm_eqn06533)且没有刚度恢复。![](../graphics/stm_eqn06527)的中间值导致刚度部分恢复。

图4.5.2-2 压缩刚度恢复参数![](../graphics/stm_eqn06527)效应的说明。

![](../graphics/stm_eqn06541.gif)![](../graphics/stm_eqn06542.gif)![](../graphics/stm_eqn06543.gif)![](../graphics/stm_eqn05528.gif)![](../graphics/cconcretedamaged-wc-nls.png)

![](../graphics/stm_eqn06544.gif)![](../graphics/stm_eqn06545.gif)![](../graphics/stm_eqn06546.gif)![](../graphics/stm_eqn06547.gif)![](../graphics/stm_eqn06548.gif)![](../graphics/stm_eqn06549.gif)等效塑性应变率的演化方程也推广到单轴循环条件为

![](../graphics/stm_eqn06550.gif)![](../graphics/stm_eqn06551.gif)![](../graphics/stm_eqn06540)这在循环的拉伸和压缩阶段简化为[公式4.5.2-4](04s05a120.md)。
### 多轴条件
![](../graphics/stm_eqn06552.gif)
硬化变量的演化方程必须推广到一般多轴条件。基于Lee和Fenves（[1998](07s01a01-References.md)），我们假定等效塑性应变率根据以下表达式评估
![](../graphics/stm_eqn06553.gif)
![](../graphics/stm_eqn06541)其中![](../graphics/stm_eqn06542)和![](../graphics/stm_eqn06543)分别是塑性应变率张量![](../graphics/stm_eqn05528)的最大和最小特征值，且
![](../graphics/stm_eqn06554.gif)
![](../graphics/stm_eqn06544)是一个应力权重因子，如果所有主应力![](../graphics/stm_eqn06545都为正且相等则等于一，如果它们为负则等于零。Macauley括号![](../graphics/stm_eqn06546)定义为![](../graphics/stm_eqn06547)。在单轴加载条件下，[公式4.5.2-8](04s05a120.md)简化为单轴定义[公式4.5.2-4](04s05a120.md)和[公式4.5.2-7](04s05a120.md)，因为在拉伸中![](../graphics/stm_eqn06548)，在压缩中![](../graphics/stm_eqn06549)。

如果塑性应变率张量的特征值（![](../graphics/stm_eqn06550）被排序使得![](../graphics/stm_eqn06551)，则一般多轴应力条件下演化方程可以表达为以下矩阵形式：
![](../graphics/stm_eqn06555.gif)![](../graphics/stm_eqn06510.gif)![](../graphics/stm_eqn06511.gif)
![](../graphics/stm_eqn06552)其中
![](../graphics/stm_eqn06556.gif)![](../graphics/stm_eqn06522.gif)![](../graphics/stm_eqn06523.gif)![](../graphics/stm_eqn06557.gif)
![](../graphics/stm_eqn06553)且
![](../graphics/stm_eqn06558.gif)
![](../graphics/stm_eqn06554)
### 弹性刚度退化

![](../graphics/stm_eqn06559.gif)![](../graphics/stm_eqn06537.gif)塑性-损伤混凝土模型假定弹性刚度退化是各向同性的，由单个标量变量*d*表征：

![](../graphics/stm_eqn06559.gif)![](../graphics/stm_eqn06537.gif)![](../graphics/stm_eqn06555)标量退化变量*d*的定义必须与单轴单调响应（![](../graphics/stm_eqn06510)和![](../graphics/stm_eqn06511)）一致，而且还应捕捉循环加载下退化机制的复杂性。对于一般多轴应力条件，Abaqus假定

![](../graphics/stm_eqn06556)类似于单轴循环情况，只是![](../graphics/stm_eqn06522)和![](../graphics/stm_eqn06523)现在根据函数![](../graphics/stm_eqn06557给出为

![](../graphics/stm_eqn06558)

可以容易地验证[公式4.5.2-10](04s05a120.md)中标量退化变量的定义与单轴响应一致。
![](../graphics/stm_eqn06560.gif)![](../graphics/stm_eqn00904.gif)![](../graphics/stm_eqn01256.gif)
大多数准脆性材料（包括混凝土）的实验观察是，当载荷从拉伸变为压缩时，压缩刚度在裂缝闭合时恢复。另一方面，一旦形成压碎微裂缝，拉伸刚度在载荷从压缩变为拉伸时不会恢复。这种行为对应于![](../graphics/stm_eqn06559)和![](../graphics/stm_eqn06537)，是Abaqus使用的默认值。[图4.5.2-3](04s05a120.md)展示了一个单轴载荷循环，假定刚度恢复因子使用默认值：![](../graphics/stm_eqn06559)和![](../graphics/stm_eqn06537)。
![](../graphics/stm_eqn06561.gif)
图4.5.2-3 单轴载荷循环（拉-压-拉），假定刚度恢复因子使用默认值。
![](../graphics/stm_eqn06562.gif)
![](../graphics/cconcretedamaged-cycle.png)
![](../graphics/stm_eqn06563.gif)![](../graphics/stm_eqn06488.gif)![](../graphics/stm_eqn06564.gif)![](../graphics/stm_eqn06488.gif)![](../graphics/stm_eqn06565.gif)### 屈服条件

![](../graphics/stm_eqn06566.gif)![](../graphics/stm_eqn06515.gif)![](../graphics/stm_eqn06516.gif)塑性-损伤混凝土模型使用基于Lubliner等（[1989](07s01a01-References.md)）提出的屈服函数屈服条件，并结合Lee和Fenves（[1998](07s01a01-References.md)）提出的修改以考虑拉伸和压缩下强度的不同演化。以有效应力表示，屈服函数取形式

![](../graphics/stm_eqn06567.gif)![](../graphics/stm_eqn00904.gif)![](../graphics/stm_eqn06568.gif)![](../graphics/stm_eqn06569.gif)![](../graphics/stm_eqn06560)其中![](../graphics/stm_eqn00904)和![](../graphics/stm_eqn01256)是无量纲材料常数；

![](../graphics/stm_eqn06570.gif)![](../graphics/stm_eqn06571.gif)![](../graphics/stm_eqn00904.gif)![](../graphics/stm_eqn06561)是有效静水压力；

![](../graphics/stm_eqn01256.gif)![](../graphics/stm_eqn06572.gif)![](../graphics/stm_eqn06573.gif)![](../graphics/stm_eqn06574.gif)![](../graphics/stm_eqn06575.gif)![](../graphics/stm_eqn06576.gif)![](../graphics/stm_eqn06577.gif)![](../graphics/stm_eqn06578.gif)![](../graphics/stm_eqn06579.gif)![](../graphics/stm_eqn06580.gif)![](../graphics/stm_eqn06562)是Mises等效有效应力；

![](../graphics/stm_eqn06581.gif)![](../graphics/stm_eqn06563)是有效应力张量![](../graphics/stm_eqn06488)的偏量部分；且![](../graphics/stm_eqn06564)是![](../graphics/stm_eqn06488)的代数最大特征值。函数![](../graphics/stm_eqn06565)给出为

![](../graphics/stm_eqn06582.gif)![](../graphics/stm_eqn06583.gif)![](../graphics/stm_eqn06584.gif)![](../graphics/stm_eqn06580.gif)![](../graphics/stm_eqn06566)其中![](../graphics/stm_eqn06515)和![](../graphics/stm_eqn06516)分别是有效拉伸和压缩内聚应力。

![](../graphics/stm_eqn06585.gif)![](../graphics/stm_eqn06586.gif)![](../graphics/stm_eqn01256.gif)在双轴压缩中，当![](../graphics/stm_eqn06567)，[公式4.5.2-11](04s05a120.md)简化为著名的Drucker-Prager屈服条件。系数![](../graphics/stm_eqn00904)可以从初始等双轴和单轴压缩屈服应力![](../graphics/stm_eqn06568)和![](../graphics/stm_eqn06569)确定为

![](../graphics/stm_eqn06587.gif)![](../graphics/stm_eqn06588.gif)![](../graphics/stm_eqn06589.gif)![](../graphics/stm_eqn06570)混凝土的典型实验值。![](../graphics/stm_eqn06571)的比值在1.10到1.16之间，产生![](../graphics/stm_eqn00904)在0.08到0.12之间的值（[Lubliner等，1989](07s01a01-References.md)）。

![](../graphics/stm_eqn06590.gif)系数![](../graphics/stm_eqn01256)仅在三轴压缩应力状态下进入屈服函数，当![](../graphics/stm_eqn06572)时。该系数可以通过比较拉伸和压缩子午线上的屈服条件来确定。*拉伸子午线*（TM）定义为满足条件![](../graphics/stm_eqn06573)的应力状态轨迹，*压缩子午线*（CM）是满足条件![](../graphics/stm_eqn06574)的应力状态轨迹，其中![](../graphics/stm_eqn06575)、![](../graphics/stm_eqn06576)和![](../graphics/stm_eqn06577)是有效应力张量的特征值。可以容易地表明，沿拉伸和压缩子午线分别有![](../graphics/stm_eqn06578)和![](../graphics/stm_eqn06579)。当![](../graphics/stm_eqn06580)时，相应的屈服条件为

![](../graphics/stm_eqn06591.gif)![](../graphics/stm_eqn06581)

![](../graphics/stm_eqn06592.gif)![](../graphics/stm_eqn06593.gif)![](../graphics/stm_eqn06584.gif)![](../graphics/stm_eqn06590.gif)![](../graphics/stm_eqn06582)设对于任何给定的静水压力值![](../graphics/stm_eqn06584)与![](../graphics/stm_eqn06580)，![](../graphics/stm_eqn06583)；则

![](../graphics/stm_eqn06594.gif)![](../graphics/stm_eqn06585)![](../graphics/stm_eqn06586)是常数这一事实似乎没有被实验证据反驳（[Lubliner等，1989](07s01a01-References.md)）。因此，系数![](../graphics/stm_eqn01256)计算为

![](../graphics/stm_eqn06587)值为![](../graphics/stm_eqn06588)（对混凝土典型）给出![](../graphics/stm_eqn06589)

![](../graphics/stm_eqn06586.gif)如果![](../graphics/stm_eqn06590)，则沿拉伸和压缩子午线的屈服条件简化为

![](../graphics/stm_eqn06591)

![](../graphics/stm_eqn06592)设对于任何给定的静水压力值![](../graphics/stm_eqn06584)与![](../graphics/stm_eqn06590)，![](../graphics/stm_eqn06593)；则

![](../graphics/stm_eqn06594)

典型屈服面在偏量平面中如图[图4.5.2-4](04s05a120.md)所示，平面应力条件下如图[图4.5.2-5](04s05a120.md)所示。

图4.5.2-4 偏量平面中的屈服面，对应于![](../graphics/stm_eqn06586)的不同值。
![](../graphics/stm_eqn06595.gif)
![](../graphics/cconcretedamaged-deviatoric.png)
![](../graphics/stm_eqn06596.gif)![](../graphics/stm_eqn02064.gif)![](../graphics/stm_eqn06597.gif)![](../graphics/stm_eqn02163.gif)
图4.5.2-5 平面应力中的屈服面。

![](../graphics/cconcretedamaged-yield-nls.png)
### 流动规则
![](../graphics/stm_eqn06598.gif)
塑性-损伤模型假定非相关势流动，
![](../graphics/stm_eqn06599.gif)![](../graphics/stm_eqn01087.gif)![](../graphics/stm_eqn05870.gif)
![](../graphics/stm_eqn06595)为该模型选择的流动势*G*是Drucker-Prager双曲函数：
![](../graphics/stm_eqn06600.gif)
![](../graphics/stm_eqn06596)其中![](../graphics/stm_eqn02064是在高约束压力下在*p*-*q*平面中测得的膨胀角；![](../graphics/stm_eqn06597)是失效时的单轴拉伸应力；且![](../graphics/stm_eqn02163)是一个参数，称为偏心率，定义函数接近渐近线的速率（当偏心率趋于零时，流动势趋于直线）。此流动势是连续且平滑的，确保流动方向被唯一确定。该函数在高约束压力应力下渐近接近线性Drucker-Prager流动势，并以90度角与静水压力轴相交。见"颗粒或聚合物行为模型，"第4.4.2节对该势的进一步讨论。
![](../graphics/stm_eqn06601.gif)
因为塑性流动是非相关的，使用塑性-损伤混凝土模型需要求解非对称方程。
![](../graphics/stm_eqn06602.gif)### 粘塑性正则化

![](../graphics/stm_eqn06603.gif)表现出软化行为和刚度退化的材料模型通常在隐式分析程序中导致严重的收敛困难。可以通过使用本构方程的粘塑性正则化来克服一些这些收敛困难。混凝土损伤塑性模型可以使用粘塑性进行正则化，因此允许应力位于屈服面之外。我们使用Duvaut-Lions正则化的推广，其中粘塑性应变率张量![](../graphics/stm_eqn06598定义为

![](../graphics/stm_eqn06599)这里![](../graphics/stm_eqn01087)是表示粘塑性系统松弛时间的粘度参数，![](../graphics/stm_eqn05870是在无粘性主干模型中评估的塑性应变。

类似地，粘塑性系统的粘性刚度退化变量![](../graphics/stm_eqn06600)定义为

![](../graphics/stm_eqn06601)其中*d*是在无粘性主干模型中评估的退化变量。粘塑性模型的应力-应变关系给出为

![](../graphics/stm_eqn06602)

粘塑性系统的解在![](../graphics/stm_eqn06603)（其中*t*表示时间）时松弛到无粘性情况。当粘度参数取值较小（与特征时间增量相比）时，使用粘塑性正则化通常有助于提高模型在软化状态下的收敛率，而不会影响结果。
### 模型积分

该模型使用Abaqus中通常与塑性模型一起使用的后向Euler方法积分。使用与该积分算子一致的材料Jacobian进行平衡迭代。
### 参考

### 参考

"Concrete damaged plasticity,"  Section 23.6.3 of the Abaqus Analysis User's Guide
