# 6.6.4 万向节

### 6.6.4 万向节

**产品：** Abaqus/Standard  Abaqus/Explicit

万向节是两个节点之间的关节，包含正交铰链，提供关节中两个轴的相对旋转。

![](../graphics/stm_eqn08381.gif)![](../graphics/stm_eqn08397.gif)![](../graphics/stm_eqn08398.gif)![](../graphics/stm_eqn05355.gif)![](../graphics/stm_eqn08399.gif)![](../graphics/stm_eqn05349.gif)![](../graphics/stm_eqn05355.gif)万向节在Abaqus/Standard中实现为多点约束，将约束节点（MPC的第一个节点）的总旋转定义为"主节点"（MPC的第二个节点）的总旋转，然后是绕关节第一轴的相对旋转，然后是绕第二轴的相对旋转（与正交）：

![](../graphics/stm_eqn08400.gif)![](../graphics/stm_eqn05355.gif)第一关节轴随主节点的旋转而旋转：

![](../graphics/stm_eqn08401.gif)第二关节轴具有第一关节轴的旋转加上绕第一关节轴的旋转：

![](../graphics/stm_eqn08402.gif)从节点的角速度为

旋转的虚变分为

![](../graphics/stm_eqn08403.gif)因此，关节施加了三个约束（从节点角速度的每个分量都受到约束），但引入了两个额外自由度，形式为相对旋转。这意味着如果未规定和，关节总共提供一个约束；如果规定了，最多三个约束。

![](../graphics/stm_eqn08404.gif)![](../graphics/stm_eqn08398.gif)![](../graphics/stm_eqn08399.gif)![](../graphics/stm_eqn08398.gif)![](../graphics/stm_eqn08399.gif)关节的虚功贡献为

其中是节点S处的总力矩，是节点M处的总力矩，和是关节铰链处的力矩。施加约束（方程），得

![](../graphics/stm_eqn08405.gif)![](../graphics/stm_eqn08389.gif)![](../graphics/stm_eqn08390.gif)![](../graphics/stm_eqn05299.gif)![](../graphics/stm_eqn05300.gif)如果没有与关节节点相关的进一步约束，和，和是独立变分，使得约束虚功方程意味着

![](../graphics/stm_eqn08406.gif)![](../graphics/stm_eqn08393.gif)![](../graphics/stm_eqn08407.gif)![](../graphics/stm_eqn08408.gif)和

![](../graphics/stm_eqn08409.gif)和

![](../graphics/stm_eqn08410.gif)由于万向节以这种方式实现，关节中的相对旋转和作为模型中的自由度出现（MPC第三个和第四个节点处的自由度6）。因此，可以分别通过将值指定为集中载荷来在关节处施加力矩和；可以通过指定边界条件来给出和随时间的规定变化；或者可以通过将弹簧和/或阻尼器连接到地面与这些自由度关联来将刚度和/或阻尼与关节的相对旋转关联（使用连接到地面的弹簧或阻尼器，因为变量是相对旋转）。

![](../graphics/stm_eqn08411.gif)### 参考

![](../graphics/stm_eqn08398.gif)![](../graphics/stm_eqn08399.gif)![](../graphics/stm_eqn05299.gif)![](../graphics/stm_eqn05300.gif)![](../graphics/stm_eqn08398.gif)![](../graphics/stm_eqn08399.gif)### 参考

"Abaqus Analysis User's Guide"第35.2.2节"一般多点约束"
