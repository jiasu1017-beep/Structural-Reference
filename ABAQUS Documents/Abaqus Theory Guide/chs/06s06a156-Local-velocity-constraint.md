# 6.6.5 局部速度约束

### 6.6.5 局部速度约束

**产品：** Abaqus/Standard

![](../graphics/stm_eqn08412.gif)Abaqus/Standard中的V LOCAL MPC将第一个MPC节点处的速度分量约束为等于第三个节点处沿局部旋转方向的速度分量。这些局部方向根据第二个节点的旋转旋转。在初始配置中，第一个局部方向是从MPC第二个到第三个节点的方向。如果这些节点重合，则使用全局z轴。第一个节点的速度为：

![](../graphics/stm_eqn08413.gif)约束被近似积分以定义

其中

![](../graphics/stm_eqn08414.gif)是约束第二个节点增量旋转一半大小的增量定义的旋转增量，和，是增量开始时的局部方向。

![](../graphics/stm_eqn08415.gif)### 参考

![](../graphics/stm_eqn08416.gif)![](../graphics/stm_eqn08417.gif)![](../graphics/stm_eqn08418.gif)![](../graphics/stm_eqn00982.gif)### 参考

"Abaqus Analysis User's Guide"第35.2.2节"一般多点约束"
