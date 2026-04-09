# 1.3.1 旋转变量

### 1.3.1 旋转变量

**产品：** Abaqus/Standard  Abaqus/Explicit

由于Abaqus包含诸如梁和壳等结构单元的功能，需要定义任意大小的旋转，因此需要一种方便的方法来存储节点处的旋转。旋转向量 ![](../graphics/stm_eqn00152.gif) 的分量存储在任何需要旋转的节点的自由度4、5和6中。

有限旋转向量 ![](../graphics/stm_eqn00152.gif) 由旋转幅度 ![](../graphics/stm_eqn00153.gif) 和空间中的旋转轴或方向 ![](../graphics/stm_eqn00154.gif) 组成。从物理上讲，旋转 ![](../graphics/stm_eqn00152.gif) 被解释为绕轴 ![](../graphics/stm_eqn00156.gif) 旋转 ![](../graphics/stm_eqn00155.gif) 弧度。为了用数学方法表征这个有限旋转，旋转向量 ![](../graphics/stm_eqn00152.gif) 用于定义正交变换或旋转矩阵。为此，首先定义与 ![](../graphics/stm_eqn00152.gif) 相关的斜对称矩阵 ![](../graphics/stm_eqn00157.gif)，关系为

![](../graphics/stm_eqn00158.gif)![](../graphics/stm_eqn00152.gif) 称为斜对称矩阵 ![](../graphics/stm_eqn00157.gif) 的轴向量。在相对于标准欧几里得基的矩阵分量中，如果 ![](../graphics/stm_eqn00159.gif)，则

![](../graphics/stm_eqn00160.gif)在下面的内容中，![](../graphics/stm_eqn00161.gif) 将用于表示具有轴向量 ![](../graphics/stm_eqn00001.gif) 的斜对称矩阵。

线性代数中的一个著名结果是，斜对称矩阵 ![](../graphics/stm_eqn00157.gif) 的指数是一个正交（旋转）矩阵，产生有限旋转 ![](../graphics/stm_eqn00152.gif)。设旋转矩阵为 ![](../graphics/stm_eqn00162.gif)，使得 ![](../graphics/stm_eqn00163.gif)。则根据定义，

![](../graphics/stm_eqn00164.gif)然而，上面的无限级数有以下闭式表达式：

![](../graphics/stm_eqn00165.gif)

在分量形式中，

![](../graphics/stm_eqn00166.gif)其中 ![](../graphics/stm_eqn00167.gif) 和 ![](../graphics/stm_eqn00168.gif) 是交错张量，定义为

![](../graphics/stm_eqn00169.gif)正是这个闭式表达式允许精确且数值高效地表征有限旋转。
### 四元数参数化

即使Abaqus存储和输出旋转向量，四元数参数也被证明是计算处理有限旋转的一种高效方便的方法。设 ![](../graphics/stm_eqn00170.gif) 为标量，![](../graphics/stm_eqn00171.gif) 为向量场。四元数 ![](../graphics/stm_eqn00172.gif) 就是配对

![](../graphics/stm_eqn00173.gif)要将 ![](../graphics/stm_eqn00172.gif) 与有限旋转向量 ![](../graphics/stm_eqn00152.gif) 关联，定义以下内容：

![](../graphics/stm_eqn00174.gif)

通过三角恒等式，[方程 1.3.1-1](01s03a03-Rotation-variables.md) 中的正交矩阵 ![](../graphics/stm_eqn00175.gif) 可以用 ![](../graphics/stm_eqn00172.gif) 表示为

![](../graphics/stm_eqn00176.gif)根据上面引入的约定，![](../graphics/stm_eqn00177.gif) 是具有轴向量 ![](../graphics/stm_eqn00178.gif) 的斜对称矩阵。

关于四元数代数及其与有限旋转其他表示的关系的更详细讨论，请参见 [Spring (1986)](07s01a01-References.md) 的讨论。
### 复合旋转

复合旋转是两个或多个旋转场的连续应用。在几何线性问题中，复合旋转简单地作为各个（线性化）旋转向量的线性叠加获得。这一事实直接来自 ![](../graphics/stm_eqn00179.gif) 的级数展开。设 ![](../graphics/stm_eqn00180.gif) 和 ![](../graphics/stm_eqn00181.gif) 是无限小旋转。因此，![](../graphics/stm_eqn00182.gif)，![](../graphics/stm_eqn00183.gif)，并且

![](../graphics/stm_eqn00184.gif)在几何非线性分析中，复合旋转不再是可加的。此外，它们是不可交换的；也就是说，应用顺序很重要。一个重要的例外是当多个旋转共享相同的旋转轴时。这个特殊情况在下面进一步研究。有限复合旋转的详细示例参见 Abaqus Analysis User's Guide 第1.2.2节"约定"。

设 ![](../graphics/stm_eqn00185.gif) 是表示复合旋转的正交变换，该复合旋转定义为一组单独或增量旋转 ![](../graphics/stm_eqn00186.gif) 的乘积，其中 ![](../graphics/stm_eqn00187.gif)。（对于指定边界条件的情况，![](../graphics/stm_eqn00185.gif) 是所有指定旋转 ![](../graphics/stm_eqn00186.gif) 经过 *i* 步后的最终乘积；对于迭代数值求解过程，![](../graphics/stm_eqn00185.gif) 是 *i* 次增量后的总旋转，其中 ![](../graphics/stm_eqn00186.gif)（对于 ![](../graphics/stm_eqn00188.gif)）是每次增量时收敛的旋转场解。）根据定义，复合旋转是乘积

![](../graphics/stm_eqn00189.gif)或等价的递归关系，

![](../graphics/stm_eqn00190.gif)重要的是要注意，![](../graphics/stm_eqn00191.gif)（解释为叠加在有限旋转 ![](../graphics/stm_eqn00162.gif) 上的有限旋转 ![](../graphics/stm_eqn00192.gif)）与 ![](../graphics/stm_eqn00193.gif)（解释为叠加在有限旋转 ![](../graphics/stm_eqn00192.gif) 上的有限旋转 ![](../graphics/stm_eqn00162.gif)）不同。

尽管复合旋转是用正交矩阵定义的，但在数值上下文中，与旋转矩阵相关的旋转向量（或等价的四元数参数）是自由度。复合旋转执行如下：给定四元数参数化 ![](../graphics/stm_eqn00194.gif) 和增量（有限）旋转 ![](../graphics/stm_eqn00195.gif)，其中 ![](../graphics/stm_eqn00196.gif) 根据 [方程 1.3.1-2](01s03a03-Rotation-variables.md) 用增量旋转向量 ![](../graphics/stm_eqn00197.gif) 定义，总旋转或复合旋转由四元数 ![](../graphics/stm_eqn00198.gif) 给出，计算如下：

![](../graphics/stm_eqn00199.gif)这里 ![](../graphics/stm_eqn00200.gif) 表示四元数乘积，定义为

![](../graphics/stm_eqn00201.gif)

[方程 1.3.1-4](01s03a03-Rotation-variables.md) 允许更新旋转场，而无需从四元数计算正交矩阵，也无需执行矩阵乘法。此外，无论增量旋转场 ![](../graphics/stm_eqn00197.gif) 的大小如何，所有操作都是无奇异的。最终（总）旋转向量可以通过反转 [方程 1.3.1-2](01s03a03-Rotation-variables.md) 从四元数 ![](../graphics/stm_eqn00202.gif) 计算。

对于复合旋转共享相同旋转轴的特殊情况，复合旋转归结为加法形式。设 ![](../graphics/stm_eqn00196.gif) 和 ![](../graphics/stm_eqn00172.gif) 具有相同的旋转轴 ![](../graphics/stm_eqn00156.gif)。则 ![](../graphics/stm_eqn00203.gif)，![](../graphics/stm_eqn00204.gif)，并且

![](../graphics/stm_eqn00205.gif)简化为

![](../graphics/stm_eqn00206.gif)
### 旋转向量提取

对于输出目的，有必要提取与给定四元数对应的旋转向量。提取过程如下：设 ![](../graphics/stm_eqn00207.gif) 是四元数，![](../graphics/stm_eqn00152.gif) 是旋转向量。因此，

![](../graphics/stm_eqn00208.gif)

重要的是要注意，从四元数提取旋转向量不是唯一的。幅度 ![](../graphics/stm_eqn00209.gif) 仅确定到加上 ![](../graphics/stm_eqn00210.gif)，![](../graphics/stm_eqn00211.gif) Abaqus将始终选择使得 ![](../graphics/stm_eqn00212.gif) 的旋转向量。
### 方向场和旋转场更新

作为四元数参数实用性的一个例子，考虑梁或壳分析中方向场的增量更新。在求解的某个阶段，方向场 ![](../graphics/stm_eqn00213.gif)、旋转场的四元数参数化 ![](../graphics/stm_eqn00214.gif) 和增量旋转场 ![](../graphics/stm_eqn00215.gif) 在增量 *i* 是已知的。要通过增量旋转更新方向场到增量 ![](../graphics/stm_eqn00216.gif)，按如下步骤进行：首先计算增量旋转的四元数参数化：

![](../graphics/stm_eqn00217.gif)然后 ![](../graphics/stm_eqn00216.gif) 处的方向场定义为 ![](../graphics/stm_eqn00218.gif)，其中 ![](../graphics/stm_eqn00219.gif) 根据 [方程 1.3.1-3](01s03a03-Rotation-variables.md) 计算。因此，方向直接由四元数计算为

![](../graphics/stm_eqn00220.gif)此外，旋转场的更新通过四元数乘法 ![](../graphics/stm_eqn00221.gif) 获得，定义为

![](../graphics/stm_eqn00222.gif)
### 旋转场的变分

在平衡方程的推导中，有必要计算旋转场的变分。考虑向量场 ![](../graphics/stm_eqn00001.gif)，它是通过旋转参考向量场 ![](../graphics/stm_eqn00007.gif) 获得的：

![](../graphics/stm_eqn00223.gif)该场的变分 ![](../graphics/stm_eqn00224.gif) 获取为

![](../graphics/stm_eqn00225.gif)其中 ![](../graphics/stm_eqn00226.gif) 是线性化旋转矩阵；也就是说，正交张量 ![](../graphics/stm_eqn00162.gif) 的变分。另一方面，变分可以用线性化旋转场 ![](../graphics/stm_eqn00227.gif) 来定义：

![](../graphics/stm_eqn00228.gif)因此，可得

![](../graphics/stm_eqn00229.gif)重要的是要注意，线性化旋转 ![](../graphics/stm_eqn00227.gif)（类似于动力学中的角速度）*不是*旋转向量 ![](../graphics/stm_eqn00152.gif) 的变分。通过直接（但复杂）的计算，可以证明旋转向量的变分（![](../graphics/stm_eqn00230.gif)）与线性化旋转 ![](../graphics/stm_eqn00227.gif) 的关系为

![](../graphics/stm_eqn00231.gif)其中

![](../graphics/stm_eqn00232.gif)![](../graphics/stm_eqn00233.gif) 的逆是

![](../graphics/stm_eqn00234.gif)

设 ![](../graphics/stm_eqn00235.gif) 表示旋转场的无限小变化。![](../graphics/stm_eqn00236.gif) 变分的直接计算（等于 ![](../graphics/stm_eqn00162.gif) 或 ![](../graphics/stm_eqn00001.gif) 的二阶变分）导致表达式在变分 ![](../graphics/stm_eqn00227.gif) 和变化 ![](../graphics/stm_eqn00236.gif) 方面不是对称的。然而，在 [Simo (1992)](07s01a01-References.md) 中表明，正确地定义Hessian算子——即平衡方程弱形式的"协变"导数——只需要二阶变分的（关于变分的）对称部分。因此，在不失一般性的情况下，我们可以写成

![](../graphics/stm_eqn00237.gif)类似地，被 ![](../graphics/stm_eqn00162.gif) 旋转的向量场的二阶变分可以写成

![](../graphics/stm_eqn00238.gif)
### 速度和加速度

对旋转矩阵取时间导数，使用与计算变分相同的论证，我们发现

![](../graphics/stm_eqn00239.gif)其中 ![](../graphics/stm_eqn00240.gif) 是角速度矩阵。等价地，![](../graphics/stm_eqn00001.gif) 的一阶和二阶时间导数写为

![](../graphics/stm_eqn00241.gif)瞬时角速度向量 ![](../graphics/stm_eqn00242.gif) 与旋转向量时间变化率的关系为

![](../graphics/stm_eqn00243.gif)其中 ![](../graphics/stm_eqn00233.gif) 由 [方程 1.3.1-6](01s03a03-Rotation-variables.md) 给出。

在动力平衡方程的线性化中，有必要计算角速度的变分 ![](../graphics/stm_eqn00244.gif)。然而，这个量只能通过线性化用于时间积分动态方程的特定算法来计算。
### 旋转耦合：恒速万向节

接下来，对 Abaqus User Subroutines Reference Guide 第1.1.14节"MPC"中描述的二维恒速万向节的更严格处理进行介绍。这个推导例证了有限旋转处理相关的一些问题。"直管和弯管段的均匀屈曲"，Abaqus Benchmarks Guide 第1.1.5节，处理了不同的有限旋转约束并解决了额外的复杂性。

设 *a*、*b*、*c*（参见 [图 1.3.1-1](01s03a03-Rotation-variables.md)）是组成万向节的节点，*a* 是从属节点。

图 1.3.1-1 非线性MPC示例——恒速万向节。

![](../graphics/umpc-const-vel-joint.png)万向节通过在 *c* 处指定轴向旋转 ![](../graphics/stm_eqn00245.gif) 和在 *b* 处指定面外旋转 ![](../graphics/stm_eqn00246.gif) 来操作。这两个指定旋转场的复合将决定 *a* 处的总旋转。我们可以正式地将此约束写为：

![](../graphics/stm_eqn00247.gif)约束可以用旋转矩阵写成

![](../graphics/stm_eqn00248.gif)利用先前定义的变分表达式，约束可以线性化为

![](../graphics/stm_eqn00249.gif)通过右乘表达式 ![](../graphics/stm_eqn00250.gif) 并利用约束 [方程 1.3.1-7](01s03a03-Rotation-variables.md)，可以简化此表达式

![](../graphics/stm_eqn00251.gif)可以写成向量形式

![](../graphics/stm_eqn00252.gif)由于

![](../graphics/stm_eqn00253.gif)线性化约束确实与 Abaqus Analysis User's Guide 中基于简单线性考虑推导的约束相同。

线性化约束用于平衡计算。它也可以用于恢复从属旋转 ![](../graphics/stm_eqn00254.gif)，如 Abaqus Analysis User's Guide 中所做。结果旋转将近似满足约束（除非角度 ![](../graphics/stm_eqn00255.gif) 或 ![](../graphics/stm_eqn00256.gif) 之一是常数，在这种情况下约束是线性的，恢复是精确的）。

要精确执行约束，用户子程序MPC必须精确定义总旋转向量 ![](../graphics/stm_eqn00254.gif) 的分量。为此，![](../graphics/stm_eqn00254.gif) 必须根据 ![](../graphics/stm_eqn00257.gif) 和 ![](../graphics/stm_eqn00258.gif) 的当前值进行更新。这最容易通过四元数参数来实现。设 ![](../graphics/stm_eqn00259.gif) 和 ![](../graphics/stm_eqn00260.gif) 是与有限旋转向量 ![](../graphics/stm_eqn00257.gif) 和 ![](../graphics/stm_eqn00258.gif) 关联的四元数参数化。总复合旋转 ![](../graphics/stm_eqn00254.gif) 由四元数 ![](../graphics/stm_eqn00261.gif) 给出，其中

![](../graphics/stm_eqn00262.gif)根据四元数复合公式 [方程 1.3.1-4](01s03a03-Rotation-variables.md)。旋转向量 ![](../graphics/stm_eqn00254.gif) 从四元数 ![](../graphics/stm_eqn00263.gif) 提取如下：

![](../graphics/stm_eqn00264.gif)其中 ![](../graphics/stm_eqn00265.gif) 是向量 ![](../graphics/stm_eqn00266.gif) 的范数。

Abaqus User Subroutines Reference Guide 第1.1.14节"MPC"展示了用户子程序MPC中约束线性化形式的实现。下面展示了精确非线性约束的实现：

```fortran
SUBROUTINE MPC(UE,A,JDOF,MDOF,N,JTYPE,X,U,UINIT,MAXDOF,LMPC,
* KSTEP,KINC,TIME,NT,NF,TEMP,FIELD)
C
INCLUDE 'ABA_PARAM.INC'
C
DIMENSION UE(MDOF), A(MDOF,MDOF,N), JDOF(MDOF,N), X(6,N),
* U(MAXDOF,N), UINIT(MAXDOF,N), TIME(2), TEMP(NT,N),
* FIELD(NF,NT,N)
PARAMETER( SMALL = 1.E-14 )
C
IF ( JTYPE .EQ. 1 ) THEN
A(1,1,1) =  1.
A(2,2,1) =  1.
A(3,3,1) =  1.
A(3,1,2) = -1.
A(1,1,3) = -COS(U(6,2))
A(2,1,3) = -SIN(U(6,2))
C
JDOF(1,1) = 4
JDOF(2,1) = 5
JDOF(3,1) = 6
JDOF(1,2) = 6
JDOF(1,3) = 4
C
CPHIB = COS(0.5*U(6,2))
SPHIB = SIN(0.5*U(6,2))
CPHIC = COS(0.5*U(4,3))
SPHIC = SIN(0.5*U(4,3))
C
QA0 = CPHIB*CPHIC
QAX = CPHIB*SPHIC
QAY = SPHIB*SPHIC
QAZ = CPHIB*SPHIC
C
QAMAG = SQRT( QAX*QAX + QAY*QAY + QAZ*QAZ )
IF ( QAMAG .GT. SMALL ) THEN
PHIA  = 2.*ATAN2( QAMAG , QA0 )
UE(1) = PHIA*QAX/QAMAG
UE(2) = PHIA*QAY/QAMAG
UE(3) = PHIA*QAZ/QAMAG
ELSE
UE(1) = 0.
UE(2) = 0.
UE(3) = 0.
END IF
END IF
C
RETURN
END
```
### 参考

### 参考

"Abaqus Analysis User's Guide" 第1.2.2节"约定"