# 3.9.4 管道支撑单元

### 3.9.4 管道支撑单元

**产品：** Abaqus/Standard

这些单元为建模管道与支撑之间在动态事件期间并非总是接触的相互作用这一特定情况而提供。管道假定具有圆形截面，可以与两种管道支撑几何中的一种相互作用：圆形孔和"蛋架"支撑。提供了两种此类界面单元，每种几何一种，如图3.9.4-1和图3.9.4-2所示。如图3.9.4-2所示，需要一个圆柱几何界面来建模管道与圆形孔的相互作用，而图3.9.4-1显示需要几个单向几何单元来建模与蛋架的相互作用——每个蛋架面对方需要一个垂直的单元。

图3.9.4-1 用于管道/"蛋架"支撑相互作用的ITSUNI单元。

![](../graphics/eits-egg-crate-nls.png)

图3.9.4-2 用于管道/钻孔支撑相互作用的ITSCYL单元。

![](../graphics/eits-drilled-hole-nls.png)

界面单元本身由弹簧和摩擦连杆以及阻尼器组成，如图3.9.4-3所示。弹簧假定表现为如图3.9.4-4所示：当管道与支撑之间没有接触时，弹簧不传递力；当管道与支撑接触时，力随着管道壁的变形而增加。这个力可以建模为管道轴线与支撑孔中心之间相对位移的线性或非线性函数。

图3.9.4-3 管道支撑单元行为。

![](../graphics/eits-elem-behav-nls.png)

图3.9.4-4 ITS单元中建模间隙和管道扁平化的非线性弹簧行为。

![](../graphics/tube-tube-elem-nls.png)

弹簧和摩擦连杆的摩擦部分使用Abaqus中的Coulomb摩擦模型：该模型在"Coulomb摩擦，"第5.2.3节中描述。

提供阻尼器是为了建模管道与支撑板之间环形空间中流体的效应。它的行为可以是线性或非线性的。该模型假设流体产生的剪切力可以忽略不计，因此这些界面单元传递的唯一剪切力是由管道与支撑之间直接接触引起的摩擦力。

这些单元在动态应用中节省大量计算工作的一个主要简化是，假设管道与其支撑板之间的撞击不涉及动量的瞬时传递或能量损失：Abaqus/Standard中与间隙和其他界面单元一起使用的标准撞击算法（并在"间歇接触/撞击，"第2.4.2节中描述）不需要。这个简化来源于这些单元将与管道的梁单元模型结合使用的假设，因此管道截面由其轴线的位置和方向定义，管道截面的局部变形被忽略。实际上，当管道撞击支撑时，最初只有小部分管道壁失去动量，因此——瞬时地——只有小的动能损失。当使用这些单元时，这个瞬时能量损失被忽略。管道壁的后续压扁由单元中的弹簧连杆建模，作用于管道轴线上的节点和代表支撑孔中心的节点之间。因此，将这种局部压扁行为建模为等效弹簧提供了简化，即不需要瞬时撞击计算。在这种方法不合理的情况下，可以使用间隙单元代替这些特殊的界面单元，代价是更多的计算工作。

本节的其余部分讨论这些单元中使用的运动学定义及其对整体平衡方程和Newton求解这些方程所需的Jacobian（刚度）矩阵的贡献。
### 几何和运动学

每个管道支撑单元有两个节点。一个节点代表管道轴线，另一个是支撑板中孔的中心（或者对于"蛋架"，是一对平行边之间的中点）。

设![](../graphics/stm_eqn05349.gif)是沿管道轴线的单位向量，设![](../graphics/stm_eqn05101.gif)是沿界面单元轴线的单位向量（也就是说，对于与蛋架一起使用的"单向"界面，垂直于支撑的平行边，对于与圆形孔一起使用的"圆柱"界面，平行于连接单元两个节点的线）。假定![](../graphics/stm_eqn05101.gif)在管道横截面内，因此垂直于![](../graphics/stm_eqn05349.gif)。我们定义第三个基向量为

![](../graphics/stm_eqn05350.gif)

设![](../graphics/stm_eqn00996.gif)是单元节点*N*在任何时刻的当前位置（这里*N*是1或2）。

单元中的相对位移从管道与支撑板中孔完全对准的位置测量；即，当单元的节点处于相同位置时。它们定义如下：

沿界面单元轴向，

![](../graphics/stm_eqn05351.gif)

沿管道轴向，

![](../graphics/stm_eqn05352.gif)和

切向，在管道横截面平面内，

对于单向情况：

![](../graphics/stm_eqn05353.gif)

对于圆柱情况：

![](../graphics/stm_eqn05354.gif)

基向量——![](../graphics/stm_eqn05349.gif)，沿管道轴线和支撑板中孔的轴线——假定是固定的。在单向单元中，![](../graphics/stm_eqn05355.gif)和![](../graphics/stm_eqn05101.gif)向量也是固定的。在圆柱界面中，![](../graphics/stm_eqn05101.gif)平行于连接单元节点的线，因此

![](../graphics/stm_eqn05356.gif)其中

![](../graphics/stm_eqn05357.gif)因此，

![](../graphics/stm_eqn05358.gif)

因此，对于这个单元

![](../graphics/stm_eqn05359.gif)和

![](../graphics/stm_eqn05360.gif)

为简单起见，我们用后向差分近似替换积分

![](../graphics/stm_eqn05361.gif)
### 单元中的力

单元产生一个轴向力——![](../graphics/stm_eqn05362.gif)，平行于![](../graphics/stm_eqn05101.gif)——和两个剪切力——![](../graphics/stm_eqn05363.gif)，平行于![](../graphics/stm_eqn05364.gif)，![](../graphics/stm_eqn05365.gif)，平行于![](../graphics/stm_eqn05349.gif)。此外，由于单元的节点在管道中心和支撑板中孔的中心，而管道与其支撑之间的相互作用力在管道与支撑的接触点传递，这些力也在单元节点处引起弯矩。假定由![](../graphics/stm_eqn05362.gif)和由![](../graphics/stm_eqn05365.gif)引起的弯矩不显著，可以忽略。唯一考虑的弯矩是节点1（管道中心）处的![](../graphics/stm_eqn05366.gif)和节点2（孔中心）处的![](../graphics/stm_eqn05367.gif)。这里![](../graphics/stm_eqn05368.gif)是管道的外径，![](../graphics/stm_eqn05369.gif)是圆柱界面的孔直径，或者是单向界面的平行支撑板之间的距离（见图3.9.4-5）。

图3.9.4-5 横截面中的接触力。

![](../graphics/stmtube-contact.png)

单元的虚功贡献为

![](../graphics/stm_eqn05370.gif)其中![](../graphics/stm_eqn05371.gif)是节点*N*绕![](../graphics/stm_eqn05349.gif)轴的虚旋转速率。

从这个表达式，单元对方程平衡的Jacobian（刚度）矩阵的贡献立即可得为

![](../graphics/stm_eqn05372.gif)

"初始应力"项，

![](../graphics/stm_eqn05373.gif)仅对圆柱界面非零，对于圆柱界面

![](../graphics/stm_eqn05374.gif)所以

![](../graphics/stm_eqn05375.gif)因此

![](../graphics/stm_eqn05376.gif)而且，对于这个单元，

![](../graphics/stm_eqn05377.gif)所以

![](../graphics/stm_eqn05378.gif)这项不是对称的。

因此，圆柱界面的"初始应力"项为

![](../graphics/stm_eqn05379.gif)

刚度矩阵的其他项与单元中力的变化相关，![](../graphics/stm_eqn05380.gif)、![](../graphics/stm_eqn05381.gif)和![](../graphics/stm_eqn05382.gif)。我们假定![](../graphics/stm_eqn05362.gif)由弹簧力和阻尼器力组成，它们分别是![](../graphics/stm_eqn03453.gif)和![](../graphics/stm_eqn05383.gif)的函数：

![](../graphics/stm_eqn05384.gif)

![](../graphics/stm_eqn05385.gif)所以

![](../graphics/stm_eqn05386.gif)

对于Abaqus/Standard中用于非线性动态分析的隐式积分算子，

![](../graphics/stm_eqn05387.gif)其中

![](../graphics/stm_eqn05388.gif)这里![](../graphics/stm_eqn00883.gif)是时间增量，![](../graphics/stm_eqn01256.gif)和![](../graphics/stm_eqn01219.gif)是积分算子的参数。

因此，

![](../graphics/stm_eqn05389.gif)

![](../graphics/stm_eqn05381.gif)和![](../graphics/stm_eqn05382.gif)的值来自摩擦理论，并由该理论从![](../graphics/stm_eqn05390.gif)、![](../graphics/stm_eqn05391.gif)和![](../graphics/stm_eqn05392.gif)定义（见"Coulomb摩擦，"第5.2.3节）。

总之，

![](../graphics/stm_eqn05393.gif)和

![](../graphics/stm_eqn05394.gif)所以单元的刚度贡献为

![](../graphics/stm_eqn05395.gif)

如果![](../graphics/stm_eqn05363.gif)、![](../graphics/stm_eqn05381.gif)或![](../graphics/stm_eqn05382.gif)非零，这个矩阵不是对称的。没有摩擦时它们为零，![](../graphics/stm_eqn05396.gif)和![](../graphics/stm_eqn05362.gif)中的项是唯一的非零项。在动态应用中摩擦系数相对较小的情况下，项![](../graphics/stm_eqn05397.gif)和——如果管道直径不是非常大——![](../graphics/stm_eqn05398.gif)、![](../graphics/stm_eqn05399.gif)、![](../graphics/stm_eqn05400.gif)和![](../graphics/stm_eqn05401.gif)可以忽略，因此，使用对称近似Jacobian矩阵不会严重降低平衡方程Newton求解的收敛率。
### 参考

### 参考

"Tube support elements," Section 32.8.1 of the Abaqus Analysis User's Guide
