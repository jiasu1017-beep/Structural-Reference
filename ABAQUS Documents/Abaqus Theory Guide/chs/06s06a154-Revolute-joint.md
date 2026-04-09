# 6.6.3 旋转关节

### 6.6.3 旋转关节

**产品：** Abaqus/Standard  Abaqus/Explicit

旋转关节是两个节点之间的关节，其中节点的旋转不同，绕一个在关节中固定并随其旋转的轴的相对旋转。一个简单的例子是铰链。

![](../graphics/stm_eqn08381.gif)![](../graphics/stm_eqn08382.gif)![](../graphics/stm_eqn08383.gif)![](../graphics/stm_eqn00001.gif)旋转关节在Abaqus/Standard中实现为多点约束，将约束节点（MPC的第一个节点）的总旋转定义为"主节点"（MPC的第二个节点）的总旋转，然后是绕关节轴的相对旋转：

![](../graphics/stm_eqn08384.gif)![](../graphics/stm_eqn00001.gif)关节轴也随主节点的旋转而旋转：

![](../graphics/stm_eqn08385.gif)从节点的角速度为

旋转的虚变分为

![](../graphics/stm_eqn08386.gif)因此，关节施加了三个约束（从节点角速度的每个分量都受到约束），但引入了相对旋转形式的额外自由度。这意味着如果未规定，关节总共提供两个约束；如果规定了，则提供三个约束。

![](../graphics/stm_eqn08387.gif)![](../graphics/stm_eqn08383.gif)![](../graphics/stm_eqn08383.gif)关节三个节点的虚功贡献为

其中是节点S处的总力矩，是节点M处的总力矩，是关节处的力矩。施加约束（方程），得

![](../graphics/stm_eqn08388.gif)![](../graphics/stm_eqn08389.gif)![](../graphics/stm_eqn08390.gif)![](../graphics/stm_eqn08391.gif)如果没有与关节节点相关的进一步约束，和是独立变分，因此约束虚功方程意味着

![](../graphics/stm_eqn08392.gif)![](../graphics/stm_eqn08393.gif)![](../graphics/stm_eqn08394.gif)和

![](../graphics/stm_eqn08395.gif)由于旋转关节以这种方式实现，关节中的相对旋转作为模型中的自由度出现（MPC第三个节点处的自由度6）。因此，可以通过将值指定为集中载荷来在关节处施加力矩；可以通过指定边界条件来给出随时间的规定变化；或者可以通过将弹簧和/或阻尼器连接到地面与此自由度关联来将刚度和/或阻尼与关节的相对旋转关联（使用连接到地面的弹簧或阻尼器，因为变量是相对旋转）。

![](../graphics/stm_eqn08396.gif)### 参考

![](../graphics/stm_eqn08383.gif)![](../graphics/stm_eqn08391.gif)![](../graphics/stm_eqn08383.gif)### 参考

"Abaqus Analysis User's Guide"第35.2.2节"一般多点约束"
