# 6.6.1 滑动约束

### 6.6.1 滑动约束

![](../graphics/stm_eqn08339.gif)![](../graphics/stm_eqn08338.gif)![](../graphics/stm_eqn00483.gif)**产品：** Abaqus/Standard  Abaqus/Explicit

滑动约束有多种用途。例如，此MPC与其他MPC类型结合使用，用于将壳单元网格约束到实体单元网格。MPC通过强制初始穿过厚度的直线保持直线（尽管有旋转和位移）来保持与标准壳理论的的一致性。当应用于壳-实体界面上的实体单元节点时，此MPC强制执行与壳模型运动学近似的兼容性。

该约束的理论如下：

![](../graphics/stm_eqn08310.gif)![](../graphics/stm_eqn08311.gif)![](../graphics/stm_eqn08312.gif)设是要定义线的点；设是必须位于此线上的节点。线的方向给定为

![](../graphics/stm_eqn08313.gif)其中

![](../graphics/stm_eqn08314.gif)![](../graphics/stm_eqn08315.gif)设是在全局坐标系中x-、y-、z-方向上的基向量。然后，定义一个垂直于线的单位向量为

![](../graphics/stm_eqn08316.gif)![](../graphics/stm_eqn08317.gif)除非在这种情况下我们使用

![](../graphics/stm_eqn08318.gif)现在我们可以定义一个正交法线为

![](../graphics/stm_eqn08319.gif)![](../graphics/stm_eqn08320.gif)![](../graphics/stm_eqn00483.gif)![](../graphics/stm_eqn04159.gif)![](../graphics/stm_eqn04161.gif)![](../graphics/stm_eqn08310.gif)![](../graphics/stm_eqn08311.gif)![](../graphics/stm_eqn04159.gif)![](../graphics/stm_eqn04161.gif)、、现在形成一个正交基向量集，和垂直于连接和的线。约束可以通过以下条件施加：连接节点m到节点1的线垂直于和；即，

![](../graphics/stm_eqn08321.gif)和

![](../graphics/stm_eqn08322.gif)![](../graphics/stm_eqn04159.gif)我们现在选择一个局部坐标编号系统，使得i是具有最大投影的全局方向：

![](../graphics/stm_eqn08323.gif)![](../graphics/stm_eqn08324.gif)类似地，我们选择全局方向j使得且

![](../graphics/stm_eqn08325.gif)![](../graphics/stm_eqn08326.gif)使用这个定义，约束条件可以相对于节点m的坐标分量明确写成

![](../graphics/stm_eqn08327.gif)和

![](../graphics/stm_eqn08328.gif)![](../graphics/stm_eqn08329.gif)![](../graphics/stm_eqn08330.gif)这些方程可用于消除（注意的编号避免了在这个消除中除以零）：

![](../graphics/stm_eqn08331.gif)和

![](../graphics/stm_eqn08332.gif)上述方程将强制执行所需的约束。我们还需要这些约束的导数。这些是

和

![](../graphics/stm_eqn08333.gif)其中

![](../graphics/stm_eqn08334.gif)和

![](../graphics/stm_eqn08335.gif)这些方程简化为

![](../graphics/stm_eqn08336.gif)和

可以从的定义中获得，因此，

![](../graphics/stm_eqn08337.gif)因此，

![](../graphics/stm_eqn08338.gif)![](../graphics/stm_eqn08339.gif)![](../graphics/stm_eqn00483.gif)和

![](../graphics/stm_eqn08340.gif)增量约束方程变为

![](../graphics/stm_eqn08341.gif)和

![](../graphics/stm_eqn08342.gif)设。然后，当使用上述相同的排序写出时，这些方程为

![](../graphics/stm_eqn08343.gif)和

![](../graphics/stm_eqn08344.gif)![](../graphics/stm_eqn08345.gif)![](../graphics/stm_eqn08346.gif)求解得

![](../graphics/stm_eqn08347.gif)和

![](../graphics/stm_eqn08348.gif)![](../graphics/stm_eqn08349.gif)在二维情况下，位于x-y或r-z平面中。这意味第二个约束方程自动满足。剩余的约束方程为

![](../graphics/stm_eqn08350.gif)及其导数为

![](../graphics/stm_eqn08351.gif)### 参考

![](../graphics/stm_eqn00483.gif)![](../graphics/stm_eqn08352.gif)### 参考

![](../graphics/stm_eqn08316.gif)![](../graphics/stm_eqn08317.gif)![](../graphics/stm_eqn08353.gif)"Abaqus Analysis User's Guide"第35.2.2节"一般多点约束"
