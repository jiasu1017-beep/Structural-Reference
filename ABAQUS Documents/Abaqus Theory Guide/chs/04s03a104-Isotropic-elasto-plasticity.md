# 4.3.2 各向同性弹塑性

### 4.3.2 各向同性弹塑性

![](../graphics/stm_eqn05605.gif)**产品：** Abaqus/Standard  Abaqus/Explicit

此材料模型非常常用于金属塑性计算，无论是作为率相关还是率无关模型，并具有特别简单的形式。由于这种简单性，与积分模型相关的代数方程可以容易地用单个变量展开，材料刚度矩阵可以明确写出。这产生了特别高效代码。在本节中这些方程被展开。

为符号简单起见，所有未明确与时间点关联的量假定在增量结束时评估。

带相关流动的Mises屈服函数意味着没有体积塑性应变；由于弹性体积模量相当大，体积变化将很小。因此，我们可以定义体积应变为

![](../graphics/stm_eqn05605.gif)因此，偏应变为

![](../graphics/stm_eqn05606.gif)![](../graphics/stm_eqn05606.gif]
### 材料模型定义

应变率分解为

![](../graphics/stm_eqn05607.gif)使用共旋度量的标准定义，这可以写成积分形式为

![](../graphics/stm_eqn05608.gif)

![](../graphics/stm_eqn01854.gif)弹性是线性各向同性的，因此，可以用两个温度相关材料参数写为。出于此推导的目的，最合适的是选择这些参数为体积模量*K*和剪切模量*G*。这些可以从用户输入的杨氏模量*E*和泊松比![](../graphics/stm_eqn01854)计算为

![](../graphics/stm_eqn05609.gif)和

![](../graphics/stm_eqn05610.gif)

弹性可以写成分体积和偏分量如下。

体积：

![](../graphics/stm_eqn05611.gif)其中

![](../graphics/stm_eqn05612.gif)是等效压力应力。

偏量：

![](../graphics/stm_eqn05613.gif)其中![](../graphics/stm_eqn00522)是偏应力，

![](../graphics/stm_eqn05614.gif)

流动规则为

![](../graphics/stm_eqn05615.gif)其中

![](../graphics/stm_eqn05616.gif)

![](../graphics/stm_eqn05617.gif)和![](../graphics/stm_eqn05618)是（标量）等效塑性应变率。

塑性要求材料满足单轴应力塑性应变率关系。如果材料与率无关，这是屈服条件：

![](../graphics/stm_eqn05619.gif)其中![](../graphics/stm_eqn05620)是屈服应力，由用户定义为等效塑性应变（![](../graphics/stm_eqn05621)的函数）和温度（![](../graphics/stm_eqn01111）的函数）。

如果材料是率相关的，关系是单轴流动率定义：

![](../graphics/stm_eqn05622.gif)其中*h*是一个已知函数。例如，率相关材料模型提供形式为

![](../graphics/stm_eqn05623.gif)的过应力幂律模型，其中![](../graphics/stm_eqn05624)和![](../graphics/stm_eqn05625)是用户定义的温度相关材料参数，![](../graphics/stm_eqn05620)是静屈服应力。

用后向Euler方法积分此关系给出

![](../graphics/stm_eqn05626.gif)

![](../graphics/stm_eqn05621.gif)此方程可以求逆（必要时数值地）给出*q*作为增量结束时![](../graphics/stm_eqn05621)的函数。

因此，率无关模型和积分率相关模型都给出一般单轴形式

![](../graphics/stm_eqn05627.gif)其中对于率无关模型，![](../graphics/stm_eqn05628)，对于率相关模型，![](../graphics/stm_eqn05629)由[公式4.3.2-6](04s03a104.md)的求逆获得。

![](../graphics/stm_eqn05285.gif)[公式4.3.2-1](04s03a104.md)到[公式4.3.2-7](04s03a104.md)定义材料行为。在任何发生塑性流动的增量中（由基于纯弹性响应评估*q*并发现其值超过![](../graphics/stm_eqn05285)来确定），这些方程必须被积分并求解增量结束时的状态。如"金属塑性模型，"第4.3.1节中的一般讨论，积分通过将后向Euler方法应用于流动规则（[公式4.3.2-4](04s03a104.md)）完成，给出

![](../graphics/stm_eqn05630.gif)

将其与偏弹性（[公式4.3.2-3](04s03a104.md)）和积分应变率分解（[公式4.3.2-1](04s03a104.md)）结合给出

![](../graphics/stm_eqn05631.gif)

![](../graphics/stm_eqn00483.gif)使用积分流动规则（[公式4.3.2-8](04s03a104.md)），连同Mises流动方向定义，![](../graphics/stm_eqn00483)（在[公式4.3.2-4](04s03a104.md)中），这变为

![](../graphics/stm_eqn05632.gif)

为符号简单起见，我们写成

![](../graphics/stm_eqn05633.gif)以便此方程为

![](../graphics/stm_eqn05634.gif)

取此方程与自身的内积给出

![](../graphics/stm_eqn05635.gif)其中

![](../graphics/stm_eqn05636.gif)

![](../graphics/stm_eqn00483.gif)Mises等效应力*q*必须满足[公式4.3.2-7](04s03a104.md)中定义的单轴形式，因此从[公式4.3.2-11](04s03a104.md)，

![](../graphics/stm_eqn05637.gif)

![](../graphics/stm_eqn05638.gif)![](../graphics/stm_eqn05629.gif)![](../graphics/stm_eqn05639.gif)这是一个关于![](../graphics/stm_eqn05638)的非线性方程，当![](../graphics/stm_eqn05629)依赖于等效塑性应变时（即，当材料是率相关的，或当存在非零加工硬化时）。（对于率无关完美塑性，它是关于![](../graphics/stm_eqn05639的线性。）我们用Newton方法求解：

![](../graphics/stm_eqn05640.gif)

![](../graphics/stm_eqn05641.gif)我们迭代直到收敛。

![](../graphics/stm_eqn05642.gif)一旦![](../graphics/stm_eqn05642)已知，解被完全定义：使用[公式4.3.2-5](04s03a104.md)，

![](../graphics/stm_eqn05643.gif)因此，从[公式4.3.2-10](04s03a104.md)，

![](../graphics/stm_eqn05644.gif)从[公式4.3.2-4](04s03a104.md)，

![](../graphics/stm_eqn05645.gif)因此，从[公式4.3.2-6](04s03a104.md)，

![](../graphics/stm_eqn05646.gif)

对于由运动学解提供三个直接应变分量的情况（即，除平面应力和单轴应力情况外的所有情况），[公式4.3.2-2](04s03a104.md)定义

![](../graphics/stm_eqn05647.gif)因此解被完全定义。平面应力

![](../graphics/stm_eqn02690.gif)对于平面应力，![](../graphics/stm_eqn02690)不由运动学定义，而是由平面应力约束

![](../graphics/stm_eqn05648.gif)

![](../graphics/stm_eqn05649.gif)这个附加方程（或等效地![](../graphics/stm_eqn05649)）必须与屈服条件和[公式4.3.2-9](04s03a104.md)一起求解。预测的第三应变分量

![](../graphics/stm_eqn05650.gif)其中

![](../graphics/stm_eqn05651.gif)和

![](../graphics/stm_eqn05652.gif)作为![](../graphics/stm_eqn05653)最终值的初始猜测，使得（具有正确的塑性应变）平面应力条件得以满足。单轴应力

对于仅由运动学解定义一个直接应变分量的情况（单轴变形），我们要求

![](../graphics/stm_eqn05654.gif)所以

![](../graphics/stm_eqn05655.gif)
### 材料刚度

对于这个简单的塑性模型，材料刚度矩阵可以推导而不需要矩阵求逆（如"塑性模型的积分，"第4.2.2节中描述的一般情况所需），如下。

取[公式4.3.2-10](04s03a104.md)关于增量结束时所有量的变分给出

![](../graphics/stm_eqn05656.gif)

现在，从[公式4.3.2-5](04s03a104.md)，

![](../graphics/stm_eqn05657.gif)从[公式4.3.2-11](04s03a104.md)，

![](../graphics/stm_eqn05658.gif)

结合这两个结果，

![](../graphics/stm_eqn05659.gif)其中

![](../graphics/stm_eqn05660.gif)

![](../graphics/stm_eqn05628.gif)![](../graphics/stm_eqn05627.gif)![](../graphics/stm_eqn05629.gif)![](../graphics/stm_eqn05661.gif)从![](../graphics/stm_eqn05661)的定义（见[公式4.3.2-11](04s03a104.md)），

![](../graphics/stm_eqn05662.gif)因此，

![](../graphics/stm_eqn05663.gif)

将这些结果与[公式4.3.2-14](04s03a104.md)结合给出

![](../graphics/stm_eqn05664.gif)其中![](../graphics/stm_eqn05665)、![](../graphics/stm_eqn05666)是四阶单位张量，和

![](../graphics/stm_eqn05667.gif)

对于由运动学解定义三个直接应变的所有情况，材料刚度由

![](../graphics/stm_eqn05668.gif)完成，因此

![](../graphics/stm_eqn05669.gif)和

![](../graphics/stm_eqn05670.gif)我们有

![](../graphics/stm_eqn05671.gif)平面应力

对于平面应力情况，材料刚度矩阵通过在平面应变情况获得的一般材料刚度矩阵上施加

![](../graphics/stm_eqn05672.gif)找到。单轴应力

对于单轴应力情况，材料刚度矩阵可以直接从[公式4.3.2-13](04s03a104.md)的变分获得为

![](../graphics/stm_eqn05673.gif)
### 参考

### 参考

![](../graphics/stm_eqn05620.gif)![](../graphics/stm_eqn05619.gif)![](../graphics/stm_eqn05621.gif)![](../graphics/stm_eqn01111.gif)![](../graphics/stm_eqn05617.gif)![](../graphics/stm_eqn05618.gif)"Classical metal plasticity," Section 23.2.1 of the Abaqus Analysis User's Guide
