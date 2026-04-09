# 4.8 粘弹性

### 4.8 粘弹性

"粘弹性"，第4.8.1节

"有限应变粘弹性"，第4.8.2节

![](../graphics/stm_eqn07139.gif)![](../graphics/stm_eqn02228.gif)![](../graphics/stm_eqn07140.gif)![](../graphics/stm_eqn01399.gif)![](../graphics/stm_eqn07141.gif)![](../graphics/stm_eqn07142.gif)"频域粘弹性"，第4.8.3节
# 4.8.1 粘弹性

### 4.8.1 粘弹性
![](../graphics/stm_eqn07143.gif)![](../graphics/stm_eqn01111.gif)![](../graphics/stm_eqn07144.gif)![](../graphics/stm_eqn07145.gif)![](../graphics/stm_eqn07146.gif)
**产品：** Abaqus/Standard  Abaqus/Explicit
![](../graphics/stm_eqn07147.gif)![](../graphics/stm_eqn07148.gif)![](../graphics/stm_eqn07149.gif)![](../graphics/stm_eqn07150.gif)![](../graphics/stm_eqn07151.gif)![](../graphics/stm_eqn07148.gif)![](../graphics/stm_eqn07149.gif)![](../graphics/stm_eqn07150.gif)
线性各向同性粘弹性的基本遗传积分公式为：

这里是机械偏体积应变和体积应变；K是体积模量，G是剪切模量，它们是约化时间的函数；表示对时间的微分。
![](../graphics/stm_eqn07152.gif)![](../graphics/stm_eqn05040.gif)![](../graphics/stm_eqn07153.gif)![](../graphics/stm_eqn07154.gif)![](../graphics/stm_eqn07148.gif)![](../graphics/stm_eqn07149.gif)![](../graphics/stm_eqn07153.gif)![](../graphics/stm_eqn07154.gif)
约化时间通过积分微分方程与实际时间相关：
![](../graphics/stm_eqn07155.gif)![](../graphics/stm_eqn07156.gif)![](../graphics/stm_eqn07157.gif)
其中是温度，是位移函数。（因此，如果，则。）常用的位移函数是Williams-Landel-Ferry（WLF）方程，其形式如下：
![](../graphics/stm_eqn07158.gif)![](../graphics/stm_eqn07159.gif)
其中和是常数，是"玻璃"转变温度。这原则上是材料行为从玻璃态转变为橡胶态的温度。如果，形变将是弹性的。和曾经被认为是"通用"常数，其值是在获得的，但已表明这些常数因聚合物不同而略有不同。
![](../graphics/stm_eqn07160.gif)![](../graphics/stm_eqn07161.gif)![](../graphics/stm_eqn07162.gif)![](../graphics/stm_eqn07163.gif)![](../graphics/stm_eqn07164.gif)![](../graphics/stm_eqn07165.gif)![](../graphics/stm_eqn07166.gif)![](../graphics/stm_eqn07167.gif)![](../graphics/stm_eqn07168.gif)
Abaqus允许使用任何方便的温度（而非玻璃转变温度）作为参考温度来使用WLF方程。方程的形式保持不变，但常数不同。即：

其中是参考温度，是参考温度下的校准常数。与参考温度下的"通用"常数和相关的如下：
![](../graphics/stm_eqn07169.gif)
其他形式的也被使用，例如关于的多项式级数。Abaqus允许通过用户子程序UTRS对位移函数进行一般定义。
![](../graphics/stm_eqn07170.gif)![](../graphics/stm_eqn07171.gif)![](../graphics/stm_eqn07172.gif)
松弛函数和可以用一系列称为Prony级数的指数项单独定义：
![](../graphics/stm_eqn07173.gif)![](../graphics/stm_eqn02228.gif)![](../graphics/stm_eqn01399.gif)![](../graphics/stm_eqn07174.gif)
其中和表示长期体积模量和剪切模量。通常，松弛时间和不需要彼此相等；但Abaqus假设。另一方面，体积和剪切中的项数和不需要彼此相等；实际上，在许多实际情况下可以假设。因此，我们现在集中讨论偏体积行为。体积项的方程可以类似地推导。
![](../graphics/stm_eqn07175.gif)
偏体积积分方程为：
![](../graphics/stm_eqn07176.gif)![](../graphics/stm_eqn07177.gif)
我们将此方程改写为：
![](../graphics/stm_eqn07178.gif)![](../graphics/stm_eqn07179.gif)![](../graphics/stm_eqn07179.gif)
其中是瞬时剪切模量，是第i项的相对模量，
![](../graphics/stm_eqn07180.gif)![](../graphics/stm_eqn07181.gif)
是每项中的粘性（蠕变）应变。对于有限元分析，必须在有限时间增量内积分此方程。为了执行此积分，我们将假设在增量期间随线性变化；因此，。为了使用此关系，我们将方程分成两部分：
![](../graphics/stm_eqn07182.gif)![](../graphics/stm_eqn07183.gif)
现在观察

使用此表达式以及增量期间的近似，可得

该表达式的第一项和最后一项易于计算，而根据方程，第二项表示增量开始时项中的粘性应变。因此，项的粘性应变变化为：
![](../graphics/stm_eqn07184.gif)![](../graphics/stm_eqn07185.gif)
如果趋于零，此表达式可近似为：
![](../graphics/stm_eqn07186.gif)
最后一种形式用于计算如果。
![](../graphics/stm_eqn07187.gif)![](../graphics/stm_eqn00883.gif)![](../graphics/stm_eqn07144.gif)![](../graphics/stm_eqn07144.gif)![](../graphics/stm_eqn07156.gif)![](../graphics/stm_eqn01111.gif)
因此，在增量中，使用方程计算粘性应变的新值。然后使用方程获取应力的新值。
![](../graphics/stm_eqn07188.gif)
通过对应力增量进行微分，可以从这些方程容易地推导出切线模量，即
![](../graphics/stm_eqn07189.gif)
由于方程是线性的，模量仅取决于约化时间步长：
![](../graphics/stm_eqn07190.gif)
最后，需要约化时间增量与实际时间增量之间的关系。为此，我们观察到随温度变化非常非线性；因此，任何直接的近似都可能导致大误差。另一方面，通常是一个随温度平滑变化的函数，在增量期间可以很好地用温度的线性函数近似。如果我们进一步假设增量期间温度是时间t的线性函数，则发现关系
![](../graphics/stm_eqn07191.gif)
或
![](../graphics/stm_eqn07192.gif)
其中

这产生了关系

![](../graphics/stm_eqn07193.gif)![](../graphics/stm_eqn07194.gif)![](../graphics/stm_eqn07195.gif)此表达式也可以写成

![](../graphics/stm_eqn07196.gif)![](../graphics/stm_eqn07197.gif)### 应力状态简化

![](../graphics/stm_eqn07198.gif)到目前为止，我们讨论了完全三轴应力状态。如果应力状态被简化（即平面应力或单轴应力），则此处推导的方程不能直接使用，因为只有总应力状态被简化，而不是级数中的各项。因此，我们使用以下程序。

![](../graphics/stm_eqn07199.gif)![](../graphics/stm_eqn07200.gif)![](../graphics/stm_eqn07201.gif)对于平面应力，让第三个分量为零应力分量。在增量开始时，我们可能知道体积弹性应变、体积粘性应变以及与Prony级数相关的体积粘性应变。总应变能通过将弹性体积应变与体积粘性应变相加获得

![](../graphics/stm_eqn07202.gif)3方向的偏应变来自关系得出：

![](../graphics/stm_eqn07203.gif)增量结束时的面外偏应力为

![](../graphics/stm_eqn07204.gif)代入方程，设，并收集项得

![](../graphics/stm_eqn07205.gif)![](../graphics/stm_eqn07206.gif)静水应力的推导类似为

![](../graphics/stm_eqn07207.gif)![](../graphics/stm_eqn03570.gif)![](../graphics/stm_eqn07208.gif)![](../graphics/stm_eqn07209.gif)![](../graphics/stm_eqn07210.gif)![](../graphics/stm_eqn07211.gif)我们可以将这些方程写成形式

![](../graphics/stm_eqn07212.gif)![](../graphics/stm_eqn07213.gif)![](../graphics/stm_eqn07214.gif)![](../graphics/stm_eqn07215.gif)在第三个方向上，偏应力减去静水压力为零；因此，

![](../graphics/stm_eqn07216.gif)![](../graphics/stm_eqn07217.gif)![](../graphics/stm_eqn06584.gif)![](../graphics/stm_eqn07218.gif)由于，可得

![](../graphics/stm_eqn07219.gif)由此可以求解。然后我们也可以计算和，并使用方程或更新偏粘性应变。体积应变通过与方程类似的方程获得。

对于单轴应力状态，使用类似的过程。如前，从方程得出，和从得出：

方程和方程可用于计算和，这再次导致方程。在处应用方程
![](../graphics/stm_eqn07220.gif)
之后，可以按照与平面应力相同的过程进行。
![](../graphics/stm_eqn07221.gif)
### 自动时间步进程序
![](../graphics/stm_eqn07222.gif)
为了在Abaqus/Standard中创建自动时间步进程序，我们希望比较增量开始和结束时的粘性应变率。各项应变率在增量开始时可以直接通过取增量应变的极限获得：
![](../graphics/stm_eqn07223.gif)
可以为增量结束时的应变率导出类似的表达式：
![](../graphics/stm_eqn07224.gif)
如果我们使用这些表达式来计算估计的总粘性应变增量的差异，则发现

这个表达式很容易计算。可以为体积应变计算类似的表达式，并从这两个量构造合适的标量度量；例如，

与用户指定的应变增量容差进行比较允许构建自动时间步进方案。

### 参考

### 参考

"Abaqus Analysis User's Guide"第22.7.1节"时域粘弹性"
