# 3.5.6 网格化梁横截面

### 3.5.6 网格化梁横截面

**产品：** Abaqus/Standard
### 概述

"梁单元公式，" 第3.5.2节中介绍的梁理论适用于均匀梁（由单一材料制成），并假定梁横截面的剪切中心是已知的或可以容易计算的。然而，如果梁横截面是任意形状的，和/或梁由多于一种材料层制成，找到横截面剪切中心和翘曲函数不再是简单任务。为了执行这些任务，横截面必须使用有限元离散化在二维横截面区域上进行数值积分。有限元横截面模型的节点自由度代表翘曲位移（通常，面内和面外翘曲自由度），允许确定剪切中心和梁扭转刚度。这种网格化截面的数值积分也提供刚度和惯性统计：积分轴向刚度![](../graphics/stm_eqn03970.gif)，积分弯曲刚度![](../graphics/stm_eqn03971.gif)，积分剪切刚度![](../graphics/stm_eqn03972.gif)，每单位长度总质量![](../graphics/stm_eqn03973.gif)，以及旋转惯性![](../graphics/stm_eqn03974.gif)。

翘曲函数和剪切中心在以下假设下为剪切柔性Timoshenko梁推导：

横截面是实心的或闭合薄壁的，扭转常数与截面极惯性矩具有相同数量级。因此，在弹性范围内，翘曲很小，假定端部翘曲约束可以被忽略。假定轴向翘曲应力可以忽略不计，但假定扭转剪切应力与轴向力和弯矩引起的应力具有相同数量级。在这种情况下，翘曲依赖于扭转，可以作为独立变量消除，这导致了相当简化的公式。因此，该理论基于具有无约束翘曲的实心截面。使用"梁单元公式，" 第3.5.2节中的符号，我们假定![](../graphics/stm_eqn03680.gif)，并且翘曲引起的轴向应变可以忽略不计：![](../graphics/stm_eqn03751.gif)。

梁可以由线性弹性材料制成，具有各向同性属性或由两个剪切模量![](../graphics/stm_eqn03975.gif)和![](../graphics/stm_eqn03976.gif)在两个垂直方向上给出的正交剪切属性。梁横截面轴中弹性正交材料的应力-应变关系给出

![](../graphics/stm_eqn03977.gif)其中![](../graphics/stm_eqn03978.gif)代表梁的轴向应力，![](../graphics/stm_eqn03979.gif)和![](../graphics/stm_eqn03980.gif)代表两个剪切应力，角度![](../graphics/stm_eqn00904.gif)是用户定义的材料方向。对于各向同性材料属性，上述关系变为

![](../graphics/stm_eqn03981.gif)

材料纤维与梁轴线对齐或垂直；因此，面内翘曲可以忽略不计，面外自由度是唯一的未知翘曲值。如果梁由具有非常不同 stiffness 属性的材料制成，这个假设可能不准确。
### 定义剪切中心和翘曲函数

在梁变形历史的给定阶段，横截面中材料点的位置由表达式

![](../graphics/stm_eqn03496.gif)给出。应用网格化截面的假设，轴向和横向剪切应变分量的表达式简化为

![](../graphics/stm_eqn03982.gif)

![](../graphics/stm_eqn03983.gif)将这些应变分量分别相对于质心和剪切中心应变表示为

![](../graphics/stm_eqn03984.gif)

![](../graphics/stm_eqn03985.gif)其中![](../graphics/stm_eqn03986.gif)是横截面质心，![](../graphics/stm_eqn03987.gif)是横截面剪切中心，![](../graphics/stm_eqn03988.gif)是质心处的轴向应变，![](../graphics/stm_eqn03989.gif)是剪切中心处的剪切应变。

梁中的弹性能量为

![](../graphics/stm_eqn03990.gif)

使用相对于质心和剪切中心处截面的应变定义，弹性能量可以写成

![](../graphics/stm_eqn03991.gif)

虽然我们假定没有翘曲约束（即，![](../graphics/stm_eqn03992.gif))，但上述能量导致以下条件，要求翘曲函数与轴向和弯曲能量正交：

![](../graphics/stm_eqn03993.gif)横截面质心定义为关于该点轴向和弯曲之间的耦合消失。因此，质心位置从

![](../graphics/stm_eqn03994.gif)和

![](../graphics/stm_eqn03995.gif)得出。剪切中心定义为关于该点扭转和横向剪切之间的耦合消失。因此，以下项在弹性能量中为零：

![](../graphics/stm_eqn03996.gif)

让我们将翘曲函数表示为三部分之和：叠加在未知刚性平移![](../graphics/stm_eqn03998.gif)和关于未知剪切中心![](../graphics/stm_eqn03999.gif)的刚性旋转上的翘曲函数![](../graphics/stm_eqn03997.gif)。这个假设可以写成

![](../graphics/stm_eqn04000.gif)将以上代入弹性能量表达式，使用剪切中心的性质，并相对于翘曲函数最小化能量，我们得到

![](../graphics/stm_eqn04001.gif)这个方程在网格化截面上数值求解，并给出![](../graphics/stm_eqn04002.gif)的值。

回想翘曲函数满足正交条件

![](../graphics/stm_eqn04003.gif)代入![](../graphics/stm_eqn02064.gif)，分组轴向和弯曲项，并使用质心定义，我们得到

![](../graphics/stm_eqn04004.gif)这个表达式必须对轴向应变![](../graphics/stm_eqn04005.gif)和曲率![](../graphics/stm_eqn04006.gif)的任何值为真，因此我们可以写成两个单独的方程，提供常数![](../graphics/stm_eqn03998.gif)和剪切中心分量![](../graphics/stm_eqn03987.gif)：

![](../graphics/stm_eqn04007.gif)

![](../graphics/stm_eqn04008.gif)因此，

![](../graphics/stm_eqn04009.gif)

![](../graphics/stm_eqn04010.gif)最后，截面积分刚度属性定义为

![](../graphics/stm_eqn04011.gif)

![](../graphics/stm_eqn04012.gif)

![](../graphics/stm_eqn04013.gif)

![](../graphics/stm_eqn04014.gif)积分惯性属性为

![](../graphics/stm_eqn04015.gif)

![](../graphics/stm_eqn04016.gif)其中![](../graphics/stm_eqn04017.gif)是质量中心，由方程

![](../graphics/stm_eqn04018.gif)给出。

我们假定横向剪切中的弹性截面行为，我们忽略个别材料点的影响（剪切应变和应力在截面上平均）。这导致横向剪切刚度的以下关系：

![](../graphics/stm_eqn04019.gif)

![](../graphics/stm_eqn04020.gif)

![](../graphics/stm_eqn04021.gif)

![](../graphics/stm_eqn04022.gif)其中*k*对于网格化截面等于1.0，![](../graphics/stm_eqn01040.gif)取决于有限元插值。
