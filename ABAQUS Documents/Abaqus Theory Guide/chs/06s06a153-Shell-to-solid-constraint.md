# 6.6.2 壳到实体约束

### 6.6.2 壳到实体约束

**产品：** Abaqus/Standard  Abaqus/Explicit

壳到实体约束SS LINEAR、SS BILINEAR和SSF BILINEAR用于将壳单元连接到实体单元网格。这些MPC与滑动约束SLIDER结合使用（见"滑动约束"第6.6.1节）。SLIDER MPC通过强制初始穿过厚度的直线保持直线（尽管有旋转和位移）来保持与标准壳理论的一致性。因此，壳到实体MPC必须强制执行剩余的约束：

界面处壳节点的位移必须等于通过实体厚度节点线的加权平均位移；

界面处壳节点的旋转必须与通过厚度的相应节点线的旋转兼容。

三种MPC类型施加基本相同的约束，但使用不同的加权因子来反映实体元素中插值的性质。SS LINEAR与一阶元素一起使用；SS BILINEAR用于二阶元素的边缘；SSF BILINEAR用于二阶元素的中间。MPC可用于二维以及三维模型。自由度将自动适应问题的维度。壳到实体MPC可用于任意数量的实体厚度点。将根据此数字选择实体中节点的加权函数。

![](../graphics/stm_eqn08355.gif)壳节点位移约束通过将壳节点的位移设置为实体节点位移的加权平均来获得：

![](../graphics/stm_eqn08356.gif)![](../graphics/stm_eqn08357.gif)其中MPC根据MPC类型和节点位置选择适当的加权因子。如果SLIDER MPC用于保持实体节点在一条直线上，则加权因子的选择不影响解。

![](../graphics/stm_eqn00278.gif)![](../graphics/stm_eqn00483.gif)![](../graphics/stm_eqn08358.gif)![](../graphics/stm_eqn00278.gif)![](../graphics/stm_eqn00483.gif)![](../graphics/stm_eqn08358.gif)对于旋转约束的公式，我们假设实体上的节点保持一条线。因此，这排节点可以用未变形配置中的归一化方向和变形后的表示。设壳节点的旋转由有限旋转向量给出。然后、、和通过以下方程关联

![](../graphics/stm_eqn08359.gif)![](../graphics/stm_eqn08360.gif)![](../graphics/stm_eqn08361.gif)![](../graphics/stm_eqn08358.gif)其中是的斜对称矩阵形式。见"旋转变量"第1.3.1节获取有限旋转的更详细讨论。

![](../graphics/stm_eqn08362.gif)![](../graphics/stm_eqn08363.gif)![](../graphics/stm_eqn08358.gif)此约束方程不完全定义壳节点的旋转：方程的任何解都可以通过绕实体节点线的旋转来增加，其中可以任意选择。因此，方程仅将有限旋转向量约束在两个分量以内。旋转约束的线性化形式为

![](../graphics/stm_eqn08364.gif)![](../graphics/stm_eqn08365.gif)其中是线性化旋转。见"旋转变量"第1.3.1节获取线性化旋转的更详细讨论。

![](../graphics/stm_eqn03507.gif)![](../graphics/stm_eqn00479.gif)![](../graphics/stm_eqn03507.gif)![](../graphics/stm_eqn00479.gif)![](../graphics/stm_eqn00483.gif)![](../graphics/stm_eqn03507.gif)![](../graphics/stm_eqn00479.gif)我们现在定义两个局部方向和，使得、和形成右手、正交、局部坐标系。然后我们将投影到和上，得到

![](../graphics/stm_eqn08366.gif)通过一些标准向量代数，这些方程可以转化为

法线的变化可以用两个极端节点1和*n*之间的位移差来表示：

![](../graphics/stm_eqn08367.gif)其中是位移差，是节点之间的距离。代入得约束方程

这些约束方程用的局部分量表示。为了获得相对于全局分量的约束，我们选择一个基，它是全局基的循环排列，使得和。然后约束可以写成如下分量形式：

![](../graphics/stm_eqn08368.gif)![](../graphics/stm_eqn08369.gif)![](../graphics/stm_eqn08370.gif)从这两个方程我们求解和：

![](../graphics/stm_eqn08371.gif)上面显示的线性化约束直接用于几何线性分析、线性扰动和Abaqus/Explicit。在Abaqus/Standard的几何非线性分析中，线性化约束用于用牛顿方法求解一般非线性约束方程。当旋转较大时，排列可能改变以保持条件和。

![](../graphics/stm_eqn08365.gif)![](../graphics/stm_eqn08365.gif)![](../graphics/stm_eqn08372.gif)![](../graphics/stm_eqn08373.gif)![](../graphics/stm_eqn08374.gif)![](../graphics/stm_eqn08375.gif)### 参考

![](../graphics/stm_eqn08376.gif)### 参考

![](../graphics/stm_eqn08377.gif)![](../graphics/stm_eqn08378.gif)"Abaqus Analysis User's Guide"第35.2.2节"一般多点约束"
