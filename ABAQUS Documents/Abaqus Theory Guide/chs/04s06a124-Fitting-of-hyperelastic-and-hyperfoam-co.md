# 4.6.2 超弹性和超泡沫常数的拟合

### 4.6.2 超弹性和超泡沫常数的拟合

**产品：** Abaqus/Standard  Abaqus/Explicit

在本节中，我们将推导将超弹性（多项式、Ogden、Arruda-Boyce和Van der Waals形式）和超泡沫常数拟合到实验测试数据所需的方程。此外，将描述使用Drucker准则检查材料稳定性的过程。

对于超弹性模型，在将超弹性常数拟合到测试数据时，假定完全不可压缩，除了体积测试。
### 多项式应变能势的应力-应变关系

超弹性多项式形式可以由Abaqus拟合到阶![](../graphics/stm_eqn05962)。由于Mooney-Rivlin势对应于情况![](../graphics/stm_eqn05955)，这些说明也适用于通过将更高阶系数设为零来设置。能量势如下：

![](../graphics/stm_eqn06839)

变形模式以主伸长来表征。现在为多项式形式推导名义应力-应变关系，![](../graphics/stm_eqn05962)。
### 单轴模式

![](../graphics/stm_eqn06840)

偏应变不变量为

![](../graphics/stm_eqn06841)我们调用虚功原理推导名义应力-应变关系，

![](../graphics/stm_eqn06842)由此可得

![](../graphics/stm_eqn06843)
### 双轴模式

![](../graphics/stm_eqn06844)

偏应变不变量为

![](../graphics/stm_eqn06845)从虚功

![](../graphics/stm_eqn06846)由此可得

![](../graphics/stm_eqn06847)
### 平面（纯剪切）模式

![](../graphics/stm_eqn06848)

偏应变不变量为

![](../graphics/stm_eqn06849)从虚功

![](../graphics/stm_eqn06850)由此可得

![](../graphics/stm_eqn06851)
### 体积模式

![](../graphics/stm_eqn06852)

从虚功

![](../graphics/stm_eqn06853)由此可得

![](../graphics/stm_eqn06854)

![](../graphics/stm_eqn06855)
### 减缩多项式应变能势的应力-应变关系

超弹性减缩多项式形式可以由Abaqus拟合到阶![](../graphics/stm_eqn06856)。对于![](../graphics/stm_eqn06792)，减缩多项式与Yeoh模型相同，对于![](../graphics/stm_eqn05955)，保留了neo-Hookean模型；因此，以下也适用于这些形式。减缩多项式能量势如下：

![](../graphics/stm_eqn06786)遵循上一节中的论证，我们为减缩多项式推导名义应力-应变关系。
### 单轴模式

![](../graphics/stm_eqn06857)

![](../graphics/stm_eqn06858)
### 双轴模式

![](../graphics/stm_eqn06844)

![](../graphics/stm_eqn06859)
### 平面（纯剪切）模式

![](../graphics/stm_eqn06848)

![](../graphics/stm_eqn06860)
### 体积模式

![](../graphics/stm_eqn06852)

![](../graphics/stm_eqn06855)
### 超弹性Ogden应变能势的应力-应变关系

超弹性Ogden形式可以拟合到阶![](../graphics/stm_eqn06856)：

![](../graphics/stm_eqn06861)遵循与多项式形式相同的方法，我们可以推导Ogden形式的名义应力-应变方程。
### 单轴模式

![](../graphics/stm_eqn06862)

![](../graphics/stm_eqn06863)
### 双轴模式

![](../graphics/stm_eqn06864)

![](../graphics/stm_eqn06865)
### 平面（纯剪切）模式

![](../graphics/stm_eqn06848)

![](../graphics/stm_eqn06866)
### 体积模式

![](../graphics/stm_eqn06852)

![](../graphics/stm_eqn06855)
### 超弹性Arruda-Boyce应变能势的应力-应变关系

超弹性Arruda-Boyce势具有以下形式：

![](../graphics/stm_eqn06867)其中

![](../graphics/stm_eqn06868)遵循与多项式形式相同的方法，我们可以推导Arruda-Boyce势的名义应力-应变方程。
### 单轴模式

![](../graphics/stm_eqn06857)

![](../graphics/stm_eqn06869)
### 双轴模式

![](../graphics/stm_eqn06844)

![](../graphics/stm_eqn06870)
### 平面（纯剪切）模式

![](../graphics/stm_eqn06848)

![](../graphics/stm_eqn06871)
### 体积模式

![](../graphics/stm_eqn06852)

![](../graphics/stm_eqn06872)
### 超弹性Van der Waals能量势的应力-应变关系

超弹性Van der Waals势，也称为Kilian模型，具有以下形式：

![](../graphics/stm_eqn06873)其中

![](../graphics/stm_eqn06820)

遵循与多项式形式相同的方法，我们可以推导Van der Waals形式的名义应力-应变关系。
### 单轴模式

![](../graphics/stm_eqn06857)

![](../graphics/stm_eqn06874)
### 双轴模式

![](../graphics/stm_eqn06844)

![](../graphics/stm_eqn06875)
### 平面（纯剪切）模式

![](../graphics/stm_eqn06848)

![](../graphics/stm_eqn06876)
### 体积模式

![](../graphics/stm_eqn06852)

![](../graphics/stm_eqn06877)
### 超泡沫应变能势的应力-应变关系

超泡沫势是Hill应变能势的修正形式，可以拟合到阶![](../graphics/stm_eqn06856)：

![](../graphics/stm_eqn06878)

变形模式以主伸长和体积比*J*来表征。弹性体泡沫是不可压缩的：![](../graphics/stm_eqn06879)。横向伸长![](../graphics/stm_eqn06880)和/或![](../graphics/stm_eqn06881)在测试数据中独立指定为单个值，取决于横向变形或通过有效泊松比的定义。
### 单轴模式

![](../graphics/stm_eqn06882)
### 双轴模式

![](../graphics/stm_eqn06883)
### 平面模式

![](../graphics/stm_eqn06884)

上述三种变形模式的通用名义应力-应变关系为

![](../graphics/stm_eqn06885)其中![](../graphics/stm_eqn06886是名义应力，![](../graphics/stm_eqn06887)是加载方向的伸长。
### 简单剪切模式

简单剪切变形用变形梯度描述，

![](../graphics/stm_eqn06888)其中![](../graphics/stm_eqn01256)是剪切应变。还要注意对于这个变形，![](../graphics/stm_eqn06889)。名义剪切应力![](../graphics/stm_eqn06890)是

![](../graphics/stm_eqn06891)其中![](../graphics/stm_eqn06887)是剪切平面中的主伸长，与剪切应变![](../graphics/stm_eqn01256)关系如下：

![](../graphics/stm_eqn06892)垂直于剪切平面的方向的伸长为![](../graphics/stm_eqn06893)。

简单剪切变形过程中产生的横向应力![](../graphics/stm_eqn06894)（作为Poynting效应的结果）是

![](../graphics/stm_eqn06895)
### 体积模式

体积变形描述为

![](../graphics/stm_eqn06896)压力*p*通过以下关系与体积比*J*相关

![](../graphics/stm_eqn06897)
### 最小二乘拟合

给定实验数据，材料常数通过最小二乘拟合程序确定，该程序最小化应力相对误差。对于*n*个名义应力-名义应变数据对，相对误差测度*E*被最小化，

![](../graphics/stm_eqn06898)其中![](../graphics/stm_eqn06899)是测试数据的应力值，![](../graphics/stm_eqn06900来自上面推导的名义应力表达式之一。

多项式势关于常数![](../graphics/stm_eqn06773)是线性的；因此，可以使用线性最小二乘程序。Ogden、Arruda-Boyce和Van der Waals势在其某些系数中是非线性的，因此需要使用非线性最小二乘程序。
### 多项式模型的线性最小二乘拟合

对于完整多项式模型，我们可以将上面推导的![](../graphics/stm_eqn06901表达式重写为

![](../graphics/stm_eqn06902)其中![](../graphics/stm_eqn06903)是依赖于应力状态（单轴、双轴或平面）的函数，如上所述。![](../graphics/stm_eqn05955)对于一阶多项式（或Mooney-Rivlin形式），![](../graphics/stm_eqn05962)对于二阶多项式。为最小化相对误差，我们需要设置

![](../graphics/stm_eqn06904)这导致以下一组*M*个方程：

![](../graphics/stm_eqn06906)这个*M*方程的线性组可以容易地求解以定义系数![](../graphics/stm_eqn06773)。

为拟合体积系数，需要求解*N*个方程组

![](../graphics/stm_eqn06907)其中

![](../graphics/stm_eqn06908)

![](../graphics/stm_eqn06909)由用户给出。这个方程组可以容易地求解![](../graphics/stm_eqn06774)。
### 减缩多项式模型的线性最小二乘拟合

对于减缩多项式模型，我们可以将上面推导的![](../graphics/stm_eqn06901表达式重写为

![](../graphics/stm_eqn06910)其中函数![](../graphics/stm_eqn06911)再次依赖于应力状态和伸长，如上所述，*N*是减缩多项式的阶数，可以取直到![](../graphics/stm_eqn06856)的值。以下也适用于Yeoh和neo-Hookean形式，因为这些模型是减缩多项式的特例，![](../graphics/stm_eqn06792)和![](../graphics/stm_eqn05955)分别为。

遵循与完整多项式相同的论证，我们得到*N*个方程组

![](../graphics/stm_eqn06912)这个方程组可以容易地求解系数![](../graphics/stm_eqn06913)。体积系数使用与通用多项式模型相同的程序拟合。
### 非线性最小二乘拟合

Ogden、Arruda-Boyce和Van der Waals势在其某些系数中是非线性的；因此，需要非线性最小二乘拟合程序。我们使用[Twizell和Ogden（1986）](07s01a01-References.md)公式中的Marquard-Levenberg算法。设![](../graphics/stm_eqn06914)、![](../graphics/stm_eqn06915)为这些超弹性模型的系数，其中*m*是贡献偏量行为的系数数量。具体来说，对于Ogden模型，![](../graphics/stm_eqn06916)，对于Arruda-Boyce模型，![](../graphics/stm_eqn06917)，对于Van der Waals模型，![](../graphics/stm_eqn06918)。系数通过迭代方程找到

![](../graphics/stm_eqn06919)其中*r*是迭代计数，*n*是数据点数量，

![](../graphics/stm_eqn06920)是相对误差向量，

![](../graphics/stm_eqn06921)是相对误差向量关于系数![](../graphics/stm_eqn06914)的导数。

对于![](../graphics/stm_eqn02157)，获得Newton算法；对于非常小的值![](../graphics/stm_eqn01256)，获得最速下降法。因此，Marquard-Levenberg算法代表了这两种方法之间的折衷：如果误差增大则增加![](../graphics/stm_eqn06922)的值，否则减少。
### Ogden模型的非线性最小二乘拟合

在初始化![](../graphics/stm_eqn06923)后，参数![](../graphics/stm_eqn06924)用线性最小二乘拟合获得。在上述迭代程序中，使用以下导数：

![](../graphics/stm_eqn06925)其中

![](../graphics/stm_eqn06926)
### Arruda-Boyce模型的非线性最小二乘拟合

Arruda-Boyce模型关于剪切模量![](../graphics/stm_eqn01087)是线性的，但关于锁定伸长![](../graphics/stm_eqn06791)是非线性的。锁定伸长初始化为![](../graphics/stm_eqn06927)，其中![](../graphics/stm_eqn06928)是用户指定测试数据中的最大伸长。给定这个锁定伸长，初始剪切模量![](../graphics/stm_eqn06929)用线性最小二乘拟合获得。

在上述迭代程序中，使用以下导数：

![](../graphics/stm_eqn06930)

![](../graphics/stm_eqn06931)
### Van der Waals模型的非线性最小二乘拟合

Van der Waals模型关于剪切模量![](../graphics/stm_eqn01087)是线性的，但关于锁定伸长![](../graphics/stm_eqn06791)、全局交互参数*a*和混合参数![](../graphics/stm_eqn01219)是非线性的。锁定伸长初始化为![](../graphics/stm_eqn06932)，其中![](../graphics/stm_eqn06928)是用户指定测试数据中的最大伸长。给定锁定伸长的这个猜测，我们利用[Kilian等（1986）](07s01a01-References.md)提出的表达式来初始化全局交互参数

![](../graphics/stm_eqn06933)不变量混合参数初始化为![](../graphics/stm_eqn06934)。给定这些初始值，剪切模量![](../graphics/stm_eqn06929)使用线性最小二乘拟合程序初始化。

在上述迭代程序中，使用以下导数：

![](../graphics/stm_eqn06935)

![](../graphics/stm_eqn06936)

![](../graphics/stm_eqn06937)

![](../graphics/stm_eqn06938)

在![](../graphics/stm_eqn06939)的导数中

![](../graphics/stm_eqn06940)和

![](../graphics/stm_eqn06941)

在平面情况下![](../graphics/stm_eqn06942)；因此，![](../graphics/stm_eqn06939)消失。
### Drucker稳定性检查

Abaqus检查上述三种变形模式的材料Drucker稳定性。Drucker稳定性条件要求从对数应变![](../graphics/stm_eqn06115)的无穷小变化得出的Kirchhoff应力![](../graphics/stm_eqn06943)的变化满足不等式

![](../graphics/stm_eqn06944)

使用![](../graphics/stm_eqn06945)，不等式变为

![](../graphics/stm_eqn06946)因此要求切向材料刚度![](../graphics/stm_eqn00424)对于材料稳定性满足是正定的。

对于这里考虑的各向同性弹性公式，不等式可以用主应力和应变表示：

![](../graphics/stm_eqn06947)
### 多项式形式

对于两个超弹性模型，假定不可压缩，Kirchhoff应力等于Cauchy应力：![](../graphics/stm_eqn06948)，因此

![](../graphics/stm_eqn06949)此外，我们可以为静水压力选择任何值而不影响应变。对于稳定性计算，一个方便的选择是![](../graphics/stm_eqn06950)，这给出我们

![](../graphics/stm_eqn06951)无穷小应变变化通过以下方程与伸长率的变化相关

![](../graphics/stm_eqn06952)应力来自应变能，而应变能又来自应变不变量或伸长的变化。

应力变化和应变变化之间的关系由矩阵方程描述

![](../graphics/stm_eqn06953)其中

![](../graphics/stm_eqn06954)

![](../graphics/stm_eqn06955)

![](../graphics/stm_eqn06956)

对于材料稳定性，![](../graphics/stm_eqn00424)必须是正定的；因此有必要

![](../graphics/stm_eqn06957)

![](../graphics/stm_eqn06958)对于所有相关的![](../graphics/stm_eqn06959)、![](../graphics/stm_eqn06880)和![](../graphics/stm_eqn06881)值。
### Ogden形式

对于Ogden形式，我们遵循与多项式形式相同的方法。使用![](../graphics/stm_eqn06960)，我们有

![](../graphics/stm_eqn06961)

![](../graphics/stm_eqn06962)

![](../graphics/stm_eqn06963)我们检查其正定性的材料刚度![](../graphics/stm_eqn00424)是

![](../graphics/stm_eqn06964)
### Arruda-Boyce形式

对于剪切模量![](../graphics/stm_eqn01087)和锁定伸长![](../graphics/stm_eqn06791)的正值，Arruda-Boyce形式始终是稳定的。因此，只需检查系数即可确定材料是否满足Drucker稳定性。
### Van der Waals形式

当Van der Waals模型在其由![](../graphics/stm_eqn06965)给出的 admissible 伸长范围内使用时，其稳定性取决于全局交互参数*a*，对于初始剪切模量![](../graphics/stm_eqn01087)和锁定伸长![](../graphics/stm_eqn06791的正值。为验证Van der Waals模型的Drucker稳定性，我们可以利用以下事实使用为多项式模型推导的方程

![](../graphics/stm_eqn06966)为确定 admissible 伸长范围，我们需要找到方程

![](../graphics/stm_eqn06967)对于每种应力状态——单轴、双轴和平面——的![](../graphics/stm_eqn00381)相邻的两个正实根，使用简单的二分法。
### 超泡沫

对于单轴、双轴、平面和体积变形模式，Kirchhoff应力-应变关系为

![](../graphics/stm_eqn06968)取![](../graphics/stm_eqn06969)的全微分并使用![](../graphics/stm_eqn06970)，

![](../graphics/stm_eqn06971)由于我们不能使用不可压缩性假设，我们必须使用所有三个主应力和应变分量以及![](../graphics/stm_eqn00335)![](../graphics/stm_eqn00424)矩阵，

![](../graphics/stm_eqn06972)具体地，

![](../graphics/stm_eqn06973)其中![](../graphics/stm_eqn06974)，

对于简单剪切情况，主伸长![](../graphics/stm_eqn06959)和![](../graphics/stm_eqn06880)从剪切应变![](../graphics/stm_eqn01256)计算（如前所述）。因此，在检查简单剪切变形期间的材料稳定性时使用相同形式的方程。

对于材料稳定性（即![](../graphics/stm_eqn00424)为正定的）必须满足以下条件：

![](../graphics/stm_eqn06975)

![](../graphics/stm_eqn06976)

![](../graphics/stm_eqn06977)
### 参考

### 参考

"Hyperelastic behavior of rubberlike materials,"  Section 22.5.1 of the Abaqus Analysis User's Guide

"Hyperelastic behavior in elastomeric foams,"  Section 22.5.2 of the Abaqus Analysis User's Guide
