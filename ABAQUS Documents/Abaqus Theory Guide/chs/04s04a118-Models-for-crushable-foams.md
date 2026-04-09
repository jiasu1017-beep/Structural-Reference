# 4.4.6 可压碎泡沫模型

### 4.4.6 可压碎泡沫模型

**产品：** Abaqus/Standard  Abaqus/Explicit

Abaqus中提供的本构模型用于分析通常用于能量吸收结构的可压碎泡沫。提供了两个现象学本构模型：体积硬化模型和各向同性硬化模型。两个模型都在子午面上使用偏应力对压力应力的椭圆依赖屈服面。

体积硬化模型的提出基于实验观察：泡沫结构在压缩和拉伸中通常表现出不同的响应。在压缩中，材料体积变形能力因胞壁屈曲过程而增强，如[Gibson等（1982）](07s01a01-References.md)、[Gibson和Ashby（1982）](07s01a01-References.md)以及[Maiti等（1984）](07s01a01-References.md)所述。假定泡沫胞变形不能即时恢复，因此可以理想化为短时事件的塑性变形。另一方面，在拉伸中，胞壁容易断裂；因此，可压碎泡沫的拉伸承载能力可能显著小于其压缩承载能力。在单调加载下，体积硬化模型假定纯剪切和负静水压力应力状态为完美塑性行为，而正静水压力应力状态发生硬化。

各向同性硬化模型最初由[Deshpande和Fleck（2000）](07s01a01-References.md)为金属泡沫开发。它假定拉伸和压缩行为对称，屈服面的演化由等效塑性应变控制，该应变来自体积塑性应变和偏量塑性应变两部分。

已知可压碎泡沫的力学行为对应变率敏感。这个效应可以通过分段线性律或过应力幂律模型引入。
### 应变率分解

体积变化分解为

![](../graphics/stm_eqn06315.gif)其中*J*是当前体积与原始体积的比值，![](../graphics/stm_eqn05454.gif)是当前与原始泡沫体积比的弹性（可恢复）部分，![](../graphics/stm_eqn05453)是当前与原始泡沫体积比的塑性（不可恢复）部分。

体积应变定义为

![](../graphics/stm_eqn06316.gif)

这些定义和[公式4.4.6-1](04s04a118.md)导致体积应变的通常加性应变率分解：

![](../graphics/stm_eqn06317.gif)

模型还假定偏量应变率加性分解，因此总应变率分解为

![](../graphics/stm_eqn06318.gif)
### 弹性行为

弹性行为只能建模为线性弹性

![](../graphics/stm_eqn06319.gif)其中![](../graphics/stm_eqn05740)表示四阶弹性张量，![](../graphics/stm_eqn05741)和![](../graphics/stm_eqn06320)分别是二阶应力张量和弹性应变张量。
### 塑性行为

可压碎泡沫模型的屈服面和流动势用压力应力

![](../graphics/stm_eqn06321.gif)![](../graphics/stm_eqn06321)和Mises应力

![](../graphics/stm_eqn06322.gif)![](../graphics/stm_eqn06322)定义。屈服面定义为

![](../graphics/stm_eqn06323.gif)![](../graphics/stm_eqn06323)流动势定义为

![](../graphics/stm_eqn06324.gif)![](../graphics/stm_eqn00904.gif)![](../graphics/stm_eqn01219.gif)![](../graphics/stm_eqn01918.gif)![](../graphics/stm_eqn06324)*F*和*G*在*p*-*q*应力平面上都可以表示为椭圆，其中![](../graphics/stm_eqn00904)和![](../graphics/stm_eqn01219)分别表示屈服椭圆和流动势椭圆的形状；![](../graphics/stm_eqn01918)是屈服椭圆的中心，*B*是屈服椭圆（垂直）*q*轴的长度。流动势是一个以原点为中心的椭圆。屈服面和流动势如图[图4.4.6-1](04s04a118.md)所示。

图4.4.6-1 可压碎泡沫模型的典型屈服面和流动势。

![](../graphics/ccrushfoam-gen-nls.png)

![](../graphics/stm_eqn01918.gif)![](../graphics/stm_eqn01917.gif)![](../graphics/stm_eqn06155.gif)屈服椭圆（[公式4.4.6-2](04s04a118.md)）的参数![](../graphics/stm_eqn01918)和*B*与静水压缩中的屈服强度![](../graphics/stm_eqn01917)、静水拉伸中的屈服强度![](../graphics/stm_eqn06155)的关系为

![](../graphics/stm_eqn06325.gif)![](../graphics/stm_eqn01917.gif)![](../graphics/stm_eqn06155.gif)![](../graphics/stm_eqn06325)其中![](../graphics/stm_eqn01917)和![](../graphics/stm_eqn06155)是正值，*A*是屈服椭圆（水平）*p*轴的长度。

![](../graphics/stm_eqn00904.gif)![](../graphics/stm_eqn06326.gif)![](../graphics/stm_eqn06327.gif)![](../graphics/stm_eqn05764.gif)形状因子![](../graphics/stm_eqn00904)在任何塑性变形过程中保持为常数。屈服椭圆的演化由塑性应变测度![](../graphics/stm_eqn06326)控制，对于体积硬化模型，它是体积压实塑性应变![](../graphics/stm_eqn06327)，对于各向同性硬化模型，它是等效塑性应变![](../graphics/stm_eqn05764)（稍后定义）。

为定义硬化行为，需要单轴压缩试验数据。必须以表格形式输入单轴Cauchy应力与轴向（对数）塑性应变的分段线性硬化曲线。
### 带体积硬化的可压碎泡沫模型

![](../graphics/stm_eqn06155.gif)体积硬化模型假定静水拉伸强度![](../graphics/stm_eqn06155)在任何塑性变形过程中保持恒定。相比之下，静水压缩强度随材料的压实（密度增加）或膨胀（密度减少）而演化：

![](../graphics/stm_eqn06328.gif)![](../graphics/stm_eqn06328)屈服面

可压碎泡沫模型的屈服面如图[图4.4.6-2](04s04a118.md)所示，

图4.4.6-2 体积硬化模型的屈服面和流动势。

![](../graphics/ccrushfoam-vol-nls.png)由以下定义

![](../graphics/stm_eqn06329.gif)![](../graphics/stm_eqn00904.gif)![](../graphics/stm_eqn06330.gif)![](../graphics/stm_eqn06331.gif)![](../graphics/stm_eqn06155.gif)![](../graphics/stm_eqn06329)其中参数![](../graphics/stm_eqn00904)表示*p*-*q*应力平面上屈服椭圆的形状，可以从单轴压缩中的初始屈服强度![](../graphics/stm_eqn06330)（取正值）、静水压缩中的初始屈服强度![](../graphics/stm_eqn06331)和静水拉伸中的屈服强度![](../graphics/stm_eqn06155)计算为

![](../graphics/stm_eqn06332.gif)![](../graphics/stm_eqn06333.gif)![](../graphics/stm_eqn06334.gif)![](../graphics/stm_eqn06335.gif)![](../graphics/stm_eqn06336.gif)![](../graphics/stm_eqn06332)其中应力比![](../graphics/stm_eqn06333)和![](../graphics/stm_eqn06334)由用户提供，可以是温度和其他场变量的函数。对于有效的屈服面，应力比的选择必须使![](../graphics/stm_eqn06335)和![](../graphics/stm_eqn06336)。屈服面在偏量应力平面上是Mises圆。
### 流动势

体积硬化模型的塑性应变率假定为
![](../graphics/stm_eqn06337.gif)![](../graphics/stm_eqn06338.gif)
![](../graphics/stm_eqn06337)其中![](../graphics/stm_eqn06338)是等效塑性应变率，定义为
![](../graphics/stm_eqn06339.gif)
![](../graphics/stm_eqn06339)且*G*是流动势，在此模型中选择为
![](../graphics/stm_eqn06340.gif)![](../graphics/stm_eqn06341.gif)
![](../graphics/stm_eqn06340.gif)![](../graphics/stm_eqn06341.gif)![](../graphics/stm_eqn06340)此势是[公式4.4.6-3](04s04a118.md)的一个特例，其中![](../graphics/stm_eqn06341)。*p*-*q*应力平面上流动势的几何表示如图[图4.4.6-2](04s04a118.md)所示。

[公式4.4.6-4](04s04a118.md)给出的流动方向与径向路径的应力方向相同。这基于[Bilkhu（1987）](07s01a01-References.md)进行的简单实验室实验的启示，表明在任何主方向上的加载会在其他方向引起可忽略的变形。因此，塑性流动是非相关的。因此，使用此泡沫模型通常需要求解非对称方程。
![](../graphics/stm_eqn06342.gif)![](../graphics/stm_eqn01917.gif)![](../graphics/stm_eqn06155.gif)![](../graphics/stm_eqn01917.gif)![](../graphics/stm_eqn06343.gif)![](../graphics/stm_eqn06344.gif)![](../graphics/stm_eqn06155.gif)### 硬化

![](../graphics/stm_eqn06345.gif)![](../graphics/stm_eqn06346.gif)![](../graphics/stm_eqn06347.gif)屈服面在*p*轴上与![](../graphics/stm_eqn06342)和![](../graphics/stm_eqn01917)相交。我们假定![](../graphics/stm_eqn06155)在任何塑性变形过程中保持固定。相比之下，压缩强度![](../graphics/stm_eqn01917)随材料的压实（密度增加）或膨胀（密度减少）而演化。屈服面的演化可以通过屈服面在静水应力轴上的大小![](../graphics/stm_eqn06343)的演化来表达，作为体积压实塑性应变值![](../graphics/stm_eqn06344)的函数。由于![](../graphics/stm_eqn06155)恒定，这个关系可以从用户提供的单轴压缩试验数据使用

![](../graphics/stm_eqn06345)连同在单轴压缩中![](../graphics/stm_eqn06346)（由于零塑性泊松比）的事实获得。因此，用户仅通过以通常的表格形式指定单轴压缩中屈服应力作为轴向塑性应变绝对值的函数来向硬化律提供输入。表格必须从零塑性应变开始（对应材料的原始状态），表格条目必须按![](../graphics/stm_eqn06347)的升序列出。如果需要，屈服应力也可以是温度和其他预定义场变量的函数。
### 带各向同性硬化的可压碎泡沫模型

各向同性硬化模型最初由[Deshpande和Fleck（2000）](07s01a01-References.md)为金属泡沫开发。该模型假定拉伸和压缩行为相似。屈服面是一个以*p*-*q*应力平面上原点为中心的椭圆，并以由等效塑性应变控制的自相似方式演化。
### 屈服面
![](../graphics/stm_eqn06348.gif)
各向同性硬化模型的屈服面定义为
![](../graphics/stm_eqn06349.gif)![](../graphics/stm_eqn00904.gif)![](../graphics/stm_eqn01917.gif)![](../graphics/stm_eqn05864.gif)
![](../graphics/stm_eqn06348)其中

![](../graphics/stm_eqn06349)![](../graphics/stm_eqn00904)表示*p*-*q*应力平面上屈服椭圆的形状，*B*定义屈服椭圆的大小，![](../graphics/stm_eqn01917)是静水压缩中的屈服强度，![](../graphics/stm_eqn05864)是单轴压缩中屈服强度的绝对值。屈服面在偏量应力平面上是Mises圆，在子午面上是椭圆，如图[图4.4.6-3](04s04a118.md)所示。

图4.4.6-3 各向同性硬化模型的屈服面和流动势。
![](../graphics/stm_eqn00904.gif)![](../graphics/stm_eqn06330.gif)![](../graphics/stm_eqn06331.gif)
![](../graphics/ccrushfoam-iso-nls.png)
![](../graphics/stm_eqn06350.gif)![](../graphics/stm_eqn00904.gif)![](../graphics/stm_eqn06351.gif)
参数![](../graphics/stm_eqn00904)可以使用单轴压缩中的初始屈服应力![](../graphics/stm_eqn06330)和静水压缩中的初始屈服应力![](../graphics/stm_eqn06331)计算为

![](../graphics/stm_eqn06350)强度比*k*由用户提供，必须在0到3的范围内。对于许多低密度泡沫，初始屈服面在*p*-*q*应力平面上接近一个圆，这表明![](../graphics/stm_eqn00904)的值大约为1。![](../graphics/stm_eqn06351)的特殊情况对应Mises屈服面。
![](../graphics/stm_eqn06352.gif)![](../graphics/stm_eqn01219.gif)![](../graphics/stm_eqn06353.gif)### 流动势

![](../graphics/stm_eqn06354.gif)![](../graphics/stm_eqn06355.gif)各向同性硬化模型的流动势选择为

![](../graphics/stm_eqn06352)其中![](../graphics/stm_eqn01219)表示*p*-*q*应力平面上流动势的形状，并与塑性泊松比![](../graphics/stm_eqn06353)相关，关系为

![](../graphics/stm_eqn06356.gif)![](../graphics/stm_eqn06357.gif)![](../graphics/stm_eqn06358.gif)![](../graphics/stm_eqn05764.gif)![](../graphics/stm_eqn05764.gif)![](../graphics/stm_eqn06354)塑性泊松比，即单轴压缩中横向与纵向塑性应变之比，应由用户定义；它必须在1到0.5的范围内。上限![](../graphics/stm_eqn06355)对应不可压缩塑性流动。

![](../graphics/stm_eqn06359.gif)塑性应变假定正交于一族自相似流动势，以势*G*的值参数化

![](../graphics/stm_eqn01219.gif)![](../graphics/stm_eqn00904.gif)![](../graphics/stm_eqn06360.gif)![](../graphics/stm_eqn06356)其中![](../graphics/stm_eqn06357)是非负塑性流动乘子。泡沫的硬化通过![](../graphics/stm_eqn06358)描述，其中![](../graphics/stm_eqn05764)是等效塑性应变。![](../graphics/stm_eqn05764)的演化假定由等效塑性功表达式控制，即

![](../graphics/stm_eqn06347.gif)![](../graphics/stm_eqn06359)等效塑性应变等于单轴拉伸或压缩中轴向塑性应变的绝对值。

当![](../graphics/stm_eqn01219)的值与![](../graphics/stm_eqn00904)的值相同时，塑性流动是相关的。一般来说，塑性流动是非相关的，以允许对屈服面形状和塑性泊松比进行独立校准。对于许多低密度泡沫，塑性泊松比几乎为零，对应于![](../graphics/stm_eqn06360)的值。
### 硬化

简单的单轴压缩试验足以定义屈服面的演化。硬化律将单轴压缩中的屈服应力值定义为轴向塑性应变绝对值的函数。分段线性关系以表格形式输入。表格必须从零塑性应变开始（对应材料的原始状态），必须按![](../graphics/stm_eqn06347)的升序列出。如果需要，屈服应力也可以是温度和其他预定义场变量的函数。
### 参考

### 参考

![](../graphics/stm_eqn06319.gif)![](../graphics/stm_eqn05740.gif)![](../graphics/stm_eqn05741.gif)![](../graphics/stm_eqn06320.gif)"Crushable foam plasticity models,"  Section 23.3.5 of the Abaqus Analysis User's Guide
