# 5.1.2 可变形体之间的有限滑动相互作用

### 5.1.2 可变形体之间的有限滑动相互作用

**产品：** Abaqus/Standard

Abaqus/Standard提供了两种 formulations 用于模拟两个可变形体之间的相互作用。第一种是小滑动 formulation，其中接触表面只能发生相对较小的滑动，但允许表面的任意旋转。这种 formulation 在"物体间的小滑动相互作用"第5.1.1节中讨论。第二种是有限滑动 formulation，可能出现有限振幅的分离和滑动以及表面的任意旋转。二维和轴对称分析以及管中管分析的 formulation 在本节中讨论。

根据接触问题的类型，用户有两种方法指定有限滑动能力：（1）通过识别和配对潜在接触表面来定义可能的接触条件；（2）使用接触单元。使用第一种方法时，Abaqus会自动生成适当的接触单元。

在具有非对称变形的轴对称问题中，可以使用ISL21A和ISL22A单元来模拟与CAXA或SAXA单元的接触。管内滑动可以使用ITT21和ITT31单元来模拟。

要定义两个表面之间的滑动界面，其中一个表面（"从"表面）被ISL或ITT单元覆盖。另一个表面（"主"表面）被定义为由一系列按顺序排列的节点组成的滑线表面。滑线本身可以由线性或二次段组成。如果使用平滑，这些段用二次或三次段连接，以实现完全的斜率连续性。平滑过程在本节后面描述。

### 二维和轴对称滑线单元

考虑从表面上的节点 ![](../graphics/stm_eqn07472.gif) 与主表面段 ![](../graphics/stm_eqn07473.gif)、![](../graphics/stm_eqn07474.gif)、![](../graphics/stm_eqn04900.gif)（由节点描述）之间的接触，其中节点数量取决于段的阶数。对于线性段，节点数为2；对于二次段，节点数为3。对于线性滑线的平滑段，节点数也为3；对于二次滑线的平滑段，节点数为5。如果接触发生在两个段的（凸）顶点处，则只有一个节点将进入方程。典型的线性段如图5.1.2-1所示，二次段如图5.1.2-2所示。平滑段在本节后面显示。

为了推导控制这些单元的方程，我们考虑滑线平面中的坐标。对于轴对称单元，该平面与二维空间重合。首先，我们确定从表面上最接近点 ![](../graphics/stm_eqn07393.gif) 的段上的点 ![](../graphics/stm_eqn00117.gif)。我们还确定该点处段的法向 ![](../graphics/stm_eqn00483.gif) 和切向 ![](../graphics/stm_eqn00479.gif)。点 ![](../graphics/stm_eqn00117.gif) 和法向 ![](../graphics/stm_eqn00483.gif) 可以通过以下关系与过盈量 ![](../graphics/stm_eqn07404.gif) 相关联

![](../graphics/stm_eqn07475.gif)

图5.1.2-1 线性滑线段。

![](../graphics/stmlinear-slideline-nls.png)

图5.1.2-2 二次滑线段。

![](../graphics/stmquad-slideline-nls.png)由于 ![](../graphics/stm_eqn00117.gif) 在段上，其位置完全由该段的插值函数 ![](../graphics/stm_eqn07476.gif)、位置 ![](../graphics/stm_eqn07477.gif) 以及作为段一部分的节点位置 ![](../graphics/stm_eqn07478.gif)、![](../graphics/stm_eqn07479.gif) 定义。这允许我们写出[方程5.1.2-1](05s01a133.md)的表达式

![](../graphics/stm_eqn07480.gif)其中 ![](../graphics/stm_eqn07481.gif) 和 ![](../graphics/stm_eqn07482.gif)、![](../graphics/stm_eqn07483.gif)、![](../graphics/stm_eqn04900.gif) 是 ![](../graphics/stm_eqn07477.gif) 的函数。例如，对于线性段，你得到 ![](../graphics/stm_eqn07484.gif)、![](../graphics/stm_eqn07485.gif)。对于二次段，使用 ![](../graphics/stm_eqn07486.gif)、![](../graphics/stm_eqn07487.gif)、![](../graphics/stm_eqn07488.gif)。对于滑线的平滑段可获得类似的表达式。滑线上点 ![](../graphics/stm_eqn00117.gif) 处的切向 ![](../graphics/stm_eqn00479.gif) 通过以下方式得到

![](../graphics/stm_eqn07489.gif)其中

![](../graphics/stm_eqn07490.gif)点 ![](../graphics/stm_eqn00117.gif) 的位置由法向和切向必须正交的条件决定，这导致以下关于 ![](../graphics/stm_eqn07477.gif) 的方程：

![](../graphics/stm_eqn07491.gif)对于线性段，这产生一个可以直接求解的线性方程。对于二次和三次段，这导致三阶或五阶方程，必须迭代求解。方程使用牛顿法求解，在使用牛顿法之前使用若干次二分法来找到真正的最小距离解。

为了获得接触/滑动方程，位置方程（[方程5.1.2-2](05s01a133.md)）被线性化。这种线性化产生

![](../graphics/stm_eqn07492.gif)其中 ![](../graphics/stm_eqn07459.gif) 是滑动量。在接触方向上，![](../graphics/stm_eqn07493.gif) 这产生

![](../graphics/stm_eqn07494.gif)而在滑动方向上，![](../graphics/stm_eqn07495.gif) 得到

![](../graphics/stm_eqn07496.gif)假设滑动仅在节点 ![](../graphics/stm_eqn07393.gif) 在滑线上时才相关；因此，假设 ![](../graphics/stm_eqn03803.gif)。由此可得

![](../graphics/stm_eqn07497.gif)为了获得初始应力刚度项，必须计算 ![](../graphics/stm_eqn07404.gif) 和 ![](../graphics/stm_eqn01604.gif) 的二阶变分。从[方程5.1.2-4](05s01a133.md)可得

![](../graphics/stm_eqn07498.gif)第一项可以借助[方程5.1.2-5](05s01a133.md)很容易地用 ![](../graphics/stm_eqn07499.gif) 表示：

![](../graphics/stm_eqn07500.gif)法向的变化率可以重新表示为

![](../graphics/stm_eqn07501.gif)在这个方程中，![](../graphics/stm_eqn07502.gif) 可以从[方程5.1.2-3](05s01a133.md)获得：

![](../graphics/stm_eqn07503.gif)其中使用了[方程5.1.2-5](05s01a133.md) 和 ![](../graphics/stm_eqn07504.gif)（段曲率）定义为

![](../graphics/stm_eqn07505.gif)对于直线段，![](../graphics/stm_eqn07504.gif) 显然为零。将[方程5.1.2-7](05s01a133.md)至[方程5.1.2-9](05s01a133.md)代入[方程5.1.2-6](05s01a133.md)得到最终结果：

![](../graphics/stm_eqn07506.gif)这个表达式是对称的，正如所预期的。![](../graphics/stm_eqn01604.gif) 的二阶变分可以沿类似路线推导：

![](../graphics/stm_eqn07507.gif)

![](../graphics/stm_eqn07508.gif)将[方程5.1.2-7](05s01a133.md)、[方程5.1.2-9](05s01a133.md) 和 [方程5.1.2-13](05s01a133.md)代入[方程5.1.2-12](05s01a133.md)得到

![](../graphics/stm_eqn07509.gif)这个表达式是非对称的。如果在滑平面内没有滑动发生，![](../graphics/stm_eqn07404.gif) 和 ![](../graphics/stm_eqn01604.gif) 的二阶变分为零 ![](../graphics/stm_eqn07510.gif)

### 管-管界面单元

在管-管界面单元的情况下，假设内管可以作为从表面，外管作为主表面。管-管界面单元与轴对称滑线单元在两个方面不同。首先，假设管之间存在有限的间隙，这使得即使发生接触，分离距离 ![](../graphics/stm_eqn07404.gif) 也是有限的。其次，对于三维单元ITT31，在管横截面平面内存在第二个可能的局部切向方向。ITT单元的推导与ISL单元的推导非常相似。接触方程可以写成形式

![](../graphics/stm_eqn07511.gif)其中 ![](../graphics/stm_eqn00117.gif) 是外管上可能与内管上点 ![](../graphics/stm_eqn07393.gif) 接触的点，如图5.1.2-3所示。

图5.1.2-3 管-管接触。

![](../graphics/stmtube-tube-contact-nls.png)

在这个方程中，![](../graphics/stm_eqn07512.gif) 是管之间的（正）径向间隙。与ISL单元类似的方式，接触方程可以写成形式

![](../graphics/stm_eqn07513.gif)与[方程5.1.2-2](05s01a133.md) 相比，符号反转与作为内部接触性质相对于常规滑线单元的外部接触性质有关。[方程5.1.2-16](05s01a133.md) 的线性化形式为

![](../graphics/stm_eqn07514.gif)与之前一样，我们假设在接触期间 ![](../graphics/stm_eqn03803.gif)。在接触方向上，这产生

![](../graphics/stm_eqn07515.gif)而在沿管道方向上，

![](../graphics/stm_eqn07516.gif)使用 ![](../graphics/stm_eqn07517.gif)，很容易得到

![](../graphics/stm_eqn07518.gif)它将[方程5.1.2-18](05s01a133.md)转化为

![](../graphics/stm_eqn07519.gif)其中 ![](../graphics/stm_eqn07504.gif) 是由[方程5.1.2-10](05s01a133.md)定义的段曲率。对于三维管-管界面单元，可以定义横向局部切向方向 ![](../graphics/stm_eqn07520.gif)，这产生

![](../graphics/stm_eqn07521.gif)

初始应力刚度项再次通过对 ![](../graphics/stm_eqn07512.gif)、![](../graphics/stm_eqn01604.gif) 和 ![](../graphics/stm_eqn02295.gif) 的二阶变分得到。从[方程5.1.2-17](05s01a133.md)可得

![](../graphics/stm_eqn07522.gif)并结合[方程5.1.2-19](05s01a133.md) 和 [方程5.1.2-21](05s01a133.md) 可得

![](../graphics/stm_eqn07523.gif)

将[方程5.1.2-20](05s01a133.md) 和 [方程5.1.2-23](05s01a133.md)代入[方程5.1.2-22](05s01a133.md)得到

![](../graphics/stm_eqn07524.gif)这个表达式是对称的。在 ![](../graphics/stm_eqn00479.gif) 方向上，虚功项具有形式

![](../graphics/stm_eqn07525.gif)结合[方程5.1.2-18](05s01a133.md)这产生

![](../graphics/stm_eqn07526.gif)对于二阶变分可得

![](../graphics/stm_eqn07527.gif)

![](../graphics/stm_eqn07528.gif)其中横向段曲率 ![](../graphics/stm_eqn07529.gif) 定义为

![](../graphics/stm_eqn07530.gif)在这个表达式中，涉及 ![](../graphics/stm_eqn03507.gif) 的项对于单元类型ITT21为零。将[方程5.1.2-20](05s01a133.md) 和 [方程5.1.2-27](05s01a133.md)代入[方程5.1.2-26](05s01a133.md)得到

![](../graphics/stm_eqn07531.gif)在 ![](../graphics/stm_eqn03507.gif) 方向上，只需考虑 ![](../graphics/stm_eqn07468.gif) 的一阶变分：

![](../graphics/stm_eqn07532.gif)

![](../graphics/stm_eqn07533.gif)结合[方程5.1.2-20](05s01a133.md)、[方程5.1.2-23](05s01a133.md) 和 [方程5.1.2-27](05s01a133.md) 可得

![](../graphics/stm_eqn07534.gif)代入[方程5.1.2-30](05s01a133.md)这产生

![](../graphics/stm_eqn07535.gif)

### 滑线平滑

在沿滑线的两个段的交界处，可能出现斜率不连续。这种不连续可能导致收敛问题，因为在迭代期间接触点可能在两个段之间来回移动。因此，平滑段之间的过渡是有用的。首先考虑两个线性段之间的过渡（图5.1.2-4）。

图5.1.2-4 线性段之间的过渡。

![](../graphics/stmlinear-transition.png)

两个段的交界处由位于段上的点 ![](../graphics/stm_eqn07536.gif) 和 ![](../graphics/stm_eqn07537.gif) 之间的Hermite多项式连接：

![](../graphics/stm_eqn07538.gif)

因此，![](../graphics/stm_eqn07536.gif) 和 ![](../graphics/stm_eqn07537.gif) 的位置由用户直接指定范围内的平滑因子 ![](../graphics/stm_eqn00904.gif) ![](../graphics/stm_eqn07539.gif) 决定。

我们选择 ![](../graphics/stm_eqn07477.gif) 作为平滑段上的参数坐标，其中 ![](../graphics/stm_eqn07540.gif)。在 ![](../graphics/stm_eqn07477.gif) 的极值处，坐标为 ![](../graphics/stm_eqn07536.gif) 和 ![](../graphics/stm_eqn07537.gif)，对于坐标导数，我们选择

![](../graphics/stm_eqn07541.gif)利用Hermite插值函数，我们可以计算段上点 ![](../graphics/stm_eqn00117.gif) 的位置作为 ![](../graphics/stm_eqn07477.gif) 的函数：

![](../graphics/stm_eqn07542.gif)合并上述方程得到

![](../graphics/stm_eqn07543.gif)

平滑实际上是用二阶多项式完成的。在界面接触和摩擦方程的 formulation 中，平滑段的处理与常规段的处理相同。二次段之间的过渡如图5.1.2-5所示。

图5.1.2-5 二次段之间的过渡。

![](../graphics/stmquad-transition.png)可以容易地确定，在这种情况下

![](../graphics/stm_eqn07544.gif)对于坐标导数，我们选择

![](../graphics/stm_eqn07545.gif)与之前一样，![](../graphics/stm_eqn00904.gif) 由用户直接指定。将这些方程代入Hermite形状函数得到

![](../graphics/stm_eqn07546.gif)如果 ![](../graphics/stm_eqn07547.gif) 和 ![](../graphics/stm_eqn07548.gif)，这些方程简化为用于线性段之间平滑的相同方程。

对于具有节点 ![](../graphics/stm_eqn07394.gif) 和 ![](../graphics/stm_eqn07549.gif) 的线性段与具有节点 ![](../graphics/stm_eqn07549.gif)、![](../graphics/stm_eqn07550.gif) 和 ![](../graphics/stm_eqn07551.gif) 的二次段之间的过渡，公式变为

![](../graphics/stm_eqn07552.gif)坐标导数为

![](../graphics/stm_eqn07553.gif)因此，

![](../graphics/stm_eqn07554.gif)

对于具有节点 ![](../graphics/stm_eqn07394.gif)、![](../graphics/stm_eqn07555.gif) 和 ![](../graphics/stm_eqn07549.gif) 的二次段与具有节点 ![](../graphics/stm_eqn07549.gif) 和 ![](../graphics/stm_eqn07551.gif) 的线性段之间的过渡，公式变为

![](../graphics/stm_eqn07556.gif)坐标导数为

![](../graphics/stm_eqn07557.gif)因此，

![](../graphics/stm_eqn07558.gif)

与"纯"线性-线性和二次-二次段过渡相比，在"混合"线性-二次和二次-线性情况下，只有交界节点 ![](../graphics/stm_eqn07549.gif) 项发生变化。

### 自接触

自接触可用于表面折叠并接触自身的情况。为表面上的每个节点内部生成适当的接触单元。一个节点允许与表面的所有段接触，但与该节点相邻的段除外。由于一个节点同时是主和从（产生对称的主-从关系），如果接口两侧的网格完全匹配，则会发生过度约束。例如，如果在二维中只有一对节点匹配，由于在接口主侧进行的平滑，不会出现问题。为了避免因过度约束导致的求解器问题，三维自接触仅在使用惩罚型接触时激活。

接触单元的数学处理与上述描述相同，在二维中有一些修改。当表面的两个相邻段形成尖锐裂纹时，接触算法变为纯主-从而不是对称的，以防止冗余接触约束。任意选择这两个段中最短的为从，最长的为主。

### 参考

### 参考

"Abaqus/Standard中的接触 formulations，" Abaqus Analysis User's Guide 第38.1.1节

"管-管接触单元，" Abaqus Analysis User's Guide 第40.3.1节

"滑线接触单元，" Abaqus Analysis User's Guide 第40.4.1节