# 5.2.1 接触压力定义

### 5.2.1 接触压力定义

**产品：** Abaqus/Standard  Abaqus/Explicit

![](../graphics/stm_eqn02386.gif)![](../graphics/stm_eqn07404.gif)![](../graphics/stm_eqn07609.gif)Abaqus中的接触建模能力允许访问"表面本构模型"库。Abaqus/Standard中该库的一部分是在点处定义两个表面之间的接触压力作为表面"过盈"的函数。提供了两种模型，如下所述。

### 硬接触

在这种情况下
![](../graphics/stm_eqn07610.gif)
接触约束通过表示接触压力的拉格朗日乘子在混合公式中强制执行。虚功贡献为

及其贡献的线性化形式为
![](../graphics/stm_eqn07611.gif)
### 使用指数压力-过盈关系的软化接触
![](../graphics/stm_eqn07612.gif)
该模型提供了指数关系，如图所示。

![](../graphics/stm_eqn02386.gif)![](../graphics/stm_eqn07404.gif)图5.2.1–1 使用指数定律的"软化"压力-过盈关系。

![](../graphics/stm_eqn07611.gif)![](../graphics/ksurfacebehavior-soft-nls.png)

用户定义初始接触距离和典型压力值，即在零过盈时的压力值。然后，我们定义 for , | for , and | for , | for . 为了避免高穿透时的数值困难，使用具有连续斜率的线性化压力-过盈关系。

![](../graphics/stm_eqn07566.gif)![](../graphics/stm_eqn07613.gif)![](../graphics/stm_eqn07418.gif)### 使用表格压力-过盈关系定义的软化接触

压力-过盈关系可以直接以表格形式输入。

![](../graphics/stm_eqn07620.gif)图5.2.1–2 以表格形式定义的"软化"压力-过盈关系。

![](../graphics/ksurfacebehavior-soft1-nls.png)
![](../graphics/stm_eqn02386.gif)![](../graphics/stm_eqn07404.gif)
### 使用线性压力-过盈关系定义的软化接触

线性压力-过盈关系类似于表格关系，只是线性形式只需要输入一个值来定义斜率，曲线始终通过原点。

### 软化接触实现

使用混合公式，因为与软化接触相关的指数刚度往往会减慢收敛，或者由于过大的接触应力可能导致发散。对于混合公式，虚功贡献为

其中是接触压力，是实际过盈，是与接触压力相关的过盈。局部牛顿循环用于计算当前值的。虚功贡献的线性化形式为

其中根据过盈评估。由于没有涉及的项，Jacobian对角线上有零。如果刚性体模式仅由接触元素约束，对角线上的零是不可取的，因为它可能导致方程求解器问题。因此，通过将接触压力分解为引入小的参考刚度：
![](../graphics/stm_eqn07621.gif)![](../graphics/stm_eqn02386.gif)![](../graphics/stm_eqn07404.gif)![](../graphics/stm_eqn07622.gif)![](../graphics/stm_eqn02386.gif)![](../graphics/stm_eqn07623.gif)![](../graphics/stm_eqn02386.gif)
其中是拉格朗日乘子，是小的参考刚度（见上图）：
![](../graphics/stm_eqn07624.gif)![](../graphics/stm_eqn07625.gif)![](../graphics/stm_eqn07623.gif)![](../graphics/stm_eqn07626.gif)![](../graphics/stm_eqn06810.gif)
将压力的表达式代入方程和，得到
![](../graphics/stm_eqn07627.gif)![](../graphics/stm_eqn02389.gif)![](../graphics/stm_eqn06810.gif)
进一步，
![](../graphics/stm_eqn07628.gif)
因此，代入中的，
![](../graphics/stm_eqn02386.gif)
因此，矩阵形式的相应方程组为
![](../graphics/stm_eqn07629.gif)
在混合公式中，实际过盈与计算过盈之间的差异将作为迭代求解过程的一部分变为零。该差异必须足够小以获得精确解。对于，中的容许误差设置为。对于，容许误差在和中线性插值，其中表示在处的容限水平；或者，用户可以将容差指定为解决方案控制的一部分。
![](../graphics/stm_eqn07630.gif)
### 粘性阻尼选项
![](../graphics/stm_eqn07631.gif)![](../graphics/stm_eqn07632.gif)
除了上述表面本构模型（接触压力是表面过盈的函数）外，Abaqus/Standard还允许定义与表面接近或分离的相对速度成正比的"粘性"压力。此选项旨在用于正则化涉及接触的snap-through问题，其中收敛困难源于接触约束的突然违反。
![](../graphics/stm_eqn07633.gif)
阻尼压力由给出
![](../graphics/stm_eqn07634.gif)
其中是阻尼系数。该系数被指定为过盈的函数，如下：
![](../graphics/stm_eqn07635.gif)![](../graphics/stm_eqn07635.gif)![](../graphics/stm_eqn07636.gif)![](../graphics/stm_eqn07637.gif)![](../graphics/stm_eqn07638.gif)![](../graphics/stm_eqn07636.gif)![](../graphics/stm_eqn07639.gif)![](../graphics/stm_eqn07639.gif)![](../graphics/stm_eqn07640.gif)
其中是零过盈时的阻尼系数值，是过盈间隔的一部分，在该间隔内阻尼系数等于。

![](../graphics/stm_eqn07641.gif)与阻尼压力相关的虚功为

![](../graphics/stm_eqn07642.gif)牛顿求解器刚度矩阵的贡献由虚功贡献的线性化形式给出：

![](../graphics/stm_eqn07643.gif)![](../graphics/stm_eqn01087.gif)![](../graphics/stm_eqn07404.gif)其中

![](../graphics/stm_eqn07644.gif)![](../graphics/stm_eqn06808.gif)![](../graphics/stm_eqn02098.gif)![](../graphics/stm_eqn07645.gif)![](../graphics/stm_eqn06808.gif)在静态分析中，速度定义为位移增量除以时间增量。因此，，刚度贡献减少为

对于使用后向欧拉时间积分算子的动力学也适用前述表达式。对于使用Hilber-Hughes-Taylor时间积分算子的动力学，刚度贡献可以写成

![](../graphics/stm_eqn01219.gif)![](../graphics/stm_eqn07651.gif)![](../graphics/stm_eqn01256.gif)![](../graphics/stm_eqn07646.gif)其中和是Hilber-Hughes-Taylor时间积分算子参数。粘性阻尼选项不能用于Riks分析，因为速度未定义。

![](../graphics/stm_eqn07647.gif)### 参考

![](../graphics/stm_eqn07648.gif)### 参考

![](../graphics/stm_eqn07649.gif)"Abaqus Analysis User's Guide"第37.1.2节"接触压力-过盈关系"
