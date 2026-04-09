# 4.3.7 铸铁塑性

### 4.3.7 铸铁塑性

**产品：** Abaqus/Standard  Abaqus/Explicit

铸铁塑性本构模型旨在模拟灰铸铁的弹塑性行为。在拉伸时，灰铸铁比大多数金属更脆。这种脆性归因于材料的微观结构，其由分布在钢基体中的石墨片组成。在拉伸时，石墨片起到应力集中器的作用，导致机械性能（如屈服强度）整体下降。另一方面，在压缩时，石墨片传递应力，整体响应仅由钢基体的响应控制。上述差异表现在以下宏观性质上：（i）拉伸和压缩中不同的屈服强度，压缩中的屈服应力比拉伸中的屈服应力高3倍或更多；（ii）拉伸时存在非弹性体积变化，但压缩时几乎没有或没有非弹性体积变化；（iii）拉伸和压缩中不同的硬化行为。普遍认为（Hjelm，1992，[1994](07s01a01-References.md)），Mises型屈服条件配合相关流动规则足以在压缩加载条件下足够准确地模拟材料响应。这一假设对于拉伸加载条件不成立：需要压力相关屈服面配合非相关流动来模拟拉伸时的脆性行为。模型的详细描述见本节其余部分。
### 应变率分解

假定加性应变率分解：

![](../graphics/stm_eqn05834.gif)其中![](../graphics/stm_eqn00118.gif)是总应变率，![](../graphics/stm_eqn05527.gif)是应变率的弹性部分，![](../graphics/stm_eqn05528.gif)是非弹性（塑性）应变率。
### 弹性行为

在压缩时，灰铸铁的弹性行为与许多钢相似。它表现出定义明确的弹性刚度。在单轴拉伸时，应力/应变曲线的斜率持续降低，难以从实验结果中估计弹性模量。

Abaqus中的模型假定灰铸铁的弹性行为可以用线性各向同性弹性表示，拉伸和压缩中具有相同的刚度。
### 屈服条件

该模型利用复合屈服面来描述拉伸和压缩中不同的行为。在拉伸时，屈服假定由最大主应力控制；在压缩时，屈服假定与压力无关，仅由偏应力控制。在主应力空间中，复合屈服面由拉伸时的Rankine立方体和压缩时的Mises圆柱体组成。

材料假定为各向同性；因此，屈服面可以表示为应力张量三个不变量测度的函数：等效压力应力

![](../graphics/stm_eqn05835.gif)Mises等效应力

![](../graphics/stm_eqn05836.gif)和偏应力的第三不变量

![](../graphics/stm_eqn05837.gif)其中![](../graphics/stm_eqn00522.gif)是应力偏量，定义为

![](../graphics/stm_eqn05838.gif)![](../graphics/stm_eqn00033.gif)是Cauchy应力张量，![](../graphics/stm_eqn00064.gif)是二阶单位张量。将不变量*q*和*r*组合以定义无量纲量![](../graphics/stm_eqn03471.gif)是方便的，其中

![](../graphics/stm_eqn05839.gif)在主应力空间中，变量![](../graphics/stm_eqn03471.gif)识别给定应力状态的子午面。

在任何给定的子午面上，屈服面由两条不同的线段组成

![](../graphics/stm_eqn05840.gif)和

![](../graphics/stm_eqn05841.gif)在上述表达式中，![](../graphics/stm_eqn05842.gif)；![](../graphics/stm_eqn05843.gif)是单轴拉伸中的屈服应力，其可能依赖于单轴拉伸中的等效塑性应变![](../graphics/stm_eqn05844.gif)、温度![](../graphics/stm_eqn01111.gif)和场变量![](../graphics/stm_eqn05845.gif)（![](../graphics/stm_eqn05846.gif)）；而![](../graphics/stm_eqn05847.gif)是单轴压缩中的屈服应力，其可能依赖于单轴压缩中的等效塑性应变![](../graphics/stm_eqn05848.gif)、温度![](../graphics/stm_eqn01111.gif)和场变量![](../graphics/stm_eqn05845.gif)（![](../graphics/stm_eqn05846.gif)）。复合屈服面在[图4.3.7-1](04s03a109.md)中子午面上、在[图4.3.7-2](04s03a109.md)中偏量平面上和在[图4.3.7-3](04s03a109.md)中主应力空间中进行了说明。

图4.3.7-1 子午面上屈服面的示意图。

![](../graphics/ccastiron-yield-merid-nls.png)

图4.3.7-2 偏量平面上屈服面的示意图。

![](../graphics/ccastiron-yield-devia-nls.png)

图4.3.7-3 主应力空间中屈服面的示意图。

![](../graphics/stmcastiron-yield-comp-nls.png)
### 流动规则

为讨论流动和硬化行为，将子午面分为两个区域是有用的，如图[图4.3.7-4](04s03a109.md)所示。

图4.3.7-4 子午面上流动势的示意图。

![](../graphics/stmcastiron-potential-nls.png)单轴压缩线左侧的区域（标记为UC）称为"拉伸区域"，单轴压缩线右侧的区域称为"压缩区域"。

塑性应变假定正交于一族自相似流动势，以势*G*的值参数化：

![](../graphics/stm_eqn05849.gif)其中![](../graphics/stm_eqn05794.gif)是非负塑性乘子。流动势![](../graphics/stm_eqn05850.gif)假定独立于第三应力不变量（独立于![](../graphics/stm_eqn03471.gif)）。它由压缩中的Mises圆柱体和拉伸中的椭圆形"帽"组成。两者之间的过渡是平滑的。流动势在偏量平面上的投影是一个圆。在子午面上，势*G*可以取两个值，![](../graphics/stm_eqn05851.gif)和![](../graphics/stm_eqn05852.gif)，由关系式定义

![](../graphics/stm_eqn05853.gif)

![](../graphics/stm_eqn05854.gif)![](../graphics/stm_eqn05851.gif)是拉伸区域中势的值，![](../graphics/stm_eqn05852.gif)是压缩区域中势的值。拉伸区域中的势是椭圆的形式，其中*a*是椭圆水平（*p*）与垂直（*q*）轴之比。椭圆的形状由*a*控制，选择它使其通过两点（![](../graphics/stm_eqn05855.gif)，![](../graphics/stm_eqn05856.gif)）和（![](../graphics/stm_eqn05857.gif)，![](../graphics/stm_eqn05858.gif)），其中![](../graphics/stm_eqn01256.gif)是控制塑性膨胀的材料参数。上述要求决定了![](../graphics/stm_eqn05859.gif)等于![](../graphics/stm_eqn05860.gif)。势*G*的值取决于当前应力点（*p*，*q*）。在压缩区域，流动势由Mises直线组成。上述流动势选择的结果是，塑性流动在拉伸区域产生非弹性体积变化，在压缩区域不产生非弹性体积变化。[图4.3.7-4](04s03a109.md)说明了*p*-*q*平面中的两个势。

可以证明对于单轴拉伸，![](../graphics/stm_eqn05861.gif)，其中![](../graphics/stm_eqn05862.gif)和![](../graphics/stm_eqn05863.gif)（称为"塑性泊松比"）等于单轴拉伸时横向与纵向塑性应变之比的绝对值。量![](../graphics/stm_eqn05864.gif)、![](../graphics/stm_eqn05865.gif)和![](../graphics/stm_eqn05863.gif)是必须由用户提供的材料性质。塑性泊松比![](../graphics/stm_eqn05863.gif)预计小于![](../graphics/stm_eqn05866.gif)，因为实验表明灰铸铁在单轴拉伸中超过屈服后体积有永久增加。此外，![](../graphics/stm_eqn05863.gif)必须大于![](../graphics/stm_eqn02916.gif)以使势有定义。对于[Coffin（1950）](07s01a01-References.md)工作中描述的灰铸铁，![](../graphics/stm_eqn05863.gif)的值约为![](../graphics/stm_eqn05867.gif)。这个估计基于在极限抗拉应力附近报告的永久体积变化值。![](../graphics/stm_eqn05863.gif)的值可能随塑性变形而变化。然而，Abaqus中的模型假定它相对于塑性变形是常数。它可以依赖于温度和场变量。

由于流动势不同于屈服面（非相关流动），材料Jacobian矩阵是非对称的。
### 硬化

Abaqus假定石墨片不影响压缩区域中的硬化行为，其中基体行为（Mises塑性）表征整体响应。在拉伸区域，塑性应变包括体积部分（对应于石墨片的张开）和偏量部分（对应于基体的非弹性剪切）。在纯静水拉伸的极限情况下，可以预期基体材料不会发生塑性响应；因此，整个塑性应变是体积的，对应于石墨片的张开。因此，在拉伸区域，我们预期塑性应变的偏量部分随着加载路径接近静水拉伸而减小，最终在静水拉伸时变为零，而塑性应变的体积部分随着加载路径接近单轴压缩而减小，在单轴压缩和高于![](../graphics/stm_eqn05857.gif)的约束压力下为零。

模型的硬化由![](../graphics/stm_eqn05868.gif)和![](../graphics/stm_eqn05869.gif)的演化控制。为建立硬化模型，我们需要找到等效塑性应变![](../graphics/stm_eqn05844.gif)和![](../graphics/stm_eqn05848.gif)作为塑性应变张量![](../graphics/stm_eqn05870.gif)函数的表达式。为简化讨论，我们假定温度![](../graphics/stm_eqn01111.gif)和场变量![](../graphics/stm_eqn05845.gif)（![](../graphics/stm_eqn05846.gif)）是常数，因此屈服应力仅作为相应等效应变的函数。此外，将塑性应变率分解为体积和偏量分量是方便的：

![](../graphics/stm_eqn05871.gif)

![](../graphics/stm_eqn05872.gif)其中![](../graphics/stm_eqn05873.gif)是偏量平面中的流动方向。为找到将![](../graphics/stm_eqn05848.gif)与![](../graphics/stm_eqn05870.gif)联系起来的表达式，我们使用等效塑性功表达式

![](../graphics/stm_eqn05874.gif)利用流动势的定义，然后可得（给定在压缩中![](../graphics/stm_eqn05875.gif)和![](../graphics/stm_eqn05876.gif)）

![](../graphics/stm_eqn05877.gif)此表达式用于更新所有加载条件下的![](../graphics/stm_eqn05878.gif)，包括拉伸加载条件。接下来，我们找到将![](../graphics/stm_eqn05844.gif)与![](../graphics/stm_eqn05870.gif)联系起来的表达式。利用等效塑性功表达式

![](../graphics/stm_eqn05879.gif)和流动势的定义，可得

![](../graphics/stm_eqn05880.gif)此表达式用于更新所有加载条件下的屈服应力![](../graphics/stm_eqn05881.gif)，包括压缩加载条件。

在主要压缩加载条件下，![](../graphics/stm_eqn05875.gif)、![](../graphics/stm_eqn05882.gif)和![](../graphics/stm_eqn05883.gif)。因此，![](../graphics/stm_eqn05864.gif)和![](../graphics/stm_eqn05865.gif)都仅基于偏量塑性应变![](../graphics/stm_eqn05884.gif)更新。这种行为在[图4.3.7-5](04s03a109.md)中描述。

图4.3.7-5 压缩加载期间的硬化。

![](../graphics/stmcastiron-harden1-nls.png)在另一个极端，在静水拉伸下（见[图4.3.7-6](04s03a109.md)）![](../graphics/stm_eqn05885.gif)。

图4.3.7-6 静水拉伸导致的硬化（![](../graphics/stm_eqn05886.gif)和![](../graphics/stm_eqn05887.gif)）。

![](../graphics/stmcastiron-harden2-nls.png)因此，![](../graphics/stm_eqn05888.gif)，且![](../graphics/stm_eqn05889.gif)。从而，![](../graphics/stm_eqn05864.gif)不演化，但![](../graphics/stm_eqn05865.gif)基于![](../graphics/stm_eqn05890.gif)演化。对于拉伸区域中的所有其他加载路径，![](../graphics/stm_eqn05890.gif)和![](../graphics/stm_eqn05891.gif)都是非零的。在这种情况下，![](../graphics/stm_eqn05864.gif)仅基于偏量塑性应变![](../graphics/stm_eqn05884.gif)更新，而![](../graphics/stm_eqn05865.gif)基于![](../graphics/stm_eqn05892.gif)和![](../graphics/stm_eqn05884.gif)两者更新（见[图4.3.7-5](04s03a109.md)）。鉴于灰铸铁变形的微观力学，这种行为似乎是合理的，尽管似乎没有实验证据证实上述硬化行为。

由于灰铸铁的基体行为与钢相似，可以合理预期在加载反向时，组合运动学和"准各向同性"硬化方案可能更合适来模拟，例如，Bauschinger效应。此外，在拉伸后的压缩加载中，我们预期在石墨片处张开的部分孔洞可能闭合。因此，在高约束压力下，屈服面中的帽可能是合适的。然而，文献中只有有限的信息。Abaqus中的模型不涉及与加载反向相关的这些问题，因此，应仅用于基本单调加载条件。
### 参考

### 参考

"Cast iron plasticity,"  Section 23.2.10 of the Abaqus Analysis User's Guide
