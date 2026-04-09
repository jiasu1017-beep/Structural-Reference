# 3.6.6 Abaqus/Explicit中的小应变壳单元

### 3.6.6 Abaqus/Explicit中的小应变壳单元

**产品：** Abaqus/Explicit

Abaqus/Explicit中的小应变壳单元使用Mindlin-Reissner型弯曲理论，该理论包括横向剪切，并基于Belytschko等人（[1984](07s01a01-References.md)，[1992](07s01a01-References.md)）描述的共旋速度-应变公式。共旋有限元公式通过在每个单元的采样点嵌入局部坐标系来降低非线性力学的复杂性。通过在局部坐标系中表达单元运动学，大大减少了计算量。因此，共旋速度-应变公式在显式时间积分软件中提供了显著的速度优势，在该软件中，单元计算在整个求解过程中可能占据主导地位。
### 共旋坐标系

壳的几何形状由其参考表面定义，参考表面由单元的节点坐标确定。嵌入的单元共旋坐标系![](../graphics/stm_eqn04513.gif)与参考表面相切，并随单元旋转。这个嵌入的共旋坐标系作为局部坐标系，其构造如下：

对于四边形单元，局部坐标![](../graphics/stm_eqn04514.gif)与连接边中点的连线重合，![](../graphics/stm_eqn04515.gif)，如图3.6.6-1所示。

图3.6.6-1 小应变四边形和三角形壳单元的局部坐标系。

![](../graphics/stmsmstrain-quadtri-shells.png)![](../graphics/stm_eqn04514.gif)-![](../graphics/stm_eqn04516.gif)平面被定义为通过该线并垂直于叉积![](../graphics/stm_eqn04517.gif)。

对于三角形单元，局部坐标![](../graphics/stm_eqn04514.gif)与连接节点1和节点2的边重合，如图3.6.6-1所示。![](../graphics/stm_eqn04514.gif)-![](../graphics/stm_eqn04516.gif)平面与单元的平面重合。出于符号目的，共旋坐标系由三组基向量![](../graphics/stm_eqn04518.gif)定义，任何以其分量表示的向量或张量都将带有上标"帽子"。

虽然此处描述的共旋坐标系在实际单元计算中使用，但该系统对用户是透明的。所有报告的应力、应变和其他张量量都是相对于"有限应变壳单元公式"第3.6.5节中描述的坐标系定义的。
### 速度应变公式

壳参考表面上任意点的速度由离散节点速度用双线性等参形函数![](../graphics/stm_eqn04211.gif)表示为

![](../graphics/stm_eqn04519.gif)

![](../graphics/stm_eqn04520.gif)其中![](../graphics/stm_eqn04521.gif)和![](../graphics/stm_eqn04522.gif)分别是节点平移速度和节点旋转速度。函数![](../graphics/stm_eqn04211.gif)是![](../graphics/stm_eqn04212.gif)连续的，![](../graphics/stm_eqn01209.gif)是非正交、非距离测量的参数坐标。希腊下标范围为1到2，大写罗马上标表示单元的节点。除非另有说明，否则对重复的上标和下标使用标准求和约定。

在Mindlin-Reissner板壳理论中，壳中任意点的速度由参考表面速度![](../graphics/stm_eqn04523.gif)和角速度向量![](../graphics/stm_eqn02713.gif)定义为

![](../graphics/stm_eqn04524.gif)其中![](../graphics/stm_eqn04525.gif)表示向量叉积，![](../graphics/stm_eqn04526.gif)是沿壳单元厚度方向的距离。速度应变（共旋分量由

![](../graphics/stm_eqn04527.gif)给出，这允许我们将每个速度应变分量用节点平移和旋转速度表示：

![](../graphics/stm_eqn04528.gif)

![](../graphics/stm_eqn04529.gif)

![](../graphics/stm_eqn04530.gif)

![](../graphics/stm_eqn04531.gif)

![](../graphics/stm_eqn04532.gif)
### 小应变单元S4RS

S4RS单元基于[Belytschko等人（1984）](07s01a01-References.md)。通过在单元中心使用单点积分——即在![](../graphics/stm_eqn01209.gif)=0处——我们得到梯度算子

![](../graphics/stm_eqn04533.gif)

速度应变可以表示为

![](../graphics/stm_eqn04534.gif)

![](../graphics/stm_eqn04535.gif)

![](../graphics/stm_eqn04536.gif)

![](../graphics/stm_eqn04537.gif)

![](../graphics/stm_eqn04538.gif)其中

![](../graphics/stm_eqn04539.gif)

局部节点力和力矩通过截面力和力矩分量计算为

![](../graphics/stm_eqn04540.gif)

![](../graphics/stm_eqn04541.gif)

![](../graphics/stm_eqn04542.gif)

![](../graphics/stm_eqn04543.gif)

![](../graphics/stm_eqn04544.gif)

![](../graphics/stm_eqn04545.gif)截面力和力矩分量由

![](../graphics/stm_eqn04546.gif)

![](../graphics/stm_eqn04547.gif)给出，其中*A*是单元面积，*h*是厚度，![](../graphics/stm_eqn04548.gif)是从速度应变和适用本构模型在共旋系统中计算的Cauchy应力。虽然![](../graphics/stm_eqn04549.gif)在经典Mindlin-Reissner板理论中是剪切因子，但在这里作为惩罚参数来强制执行Kirchhoff正交条件，因为壳变薄。
### 小应变单元S4RSW

开发S4RS单元的主要目标是获得具有最少计算量的收敛稳定单元。由于强调速度，在制定S4RS单元的方程时做了一些简化。虽然S4RS单元在大多数实际应用中表现非常好，但它有两个已知的缺点：

它在翘曲时可能表现不佳，特别是，它不能正确解决扭转梁问题。

它在薄板极限下不通过弯曲分片测试。在S4RSW单元中，在应变-位移方程中添加了额外项以消除第一个缺点，并在横向剪切计算中使用剪切投影来解决第二个缺点。S4RSW单元中的速度应变分量在[Belytschko等人（1992）](07s01a01-References.md)中给出为

![](../graphics/stm_eqn04550.gif)

![](../graphics/stm_eqn04551.gif)

![](../graphics/stm_eqn04552.gif)其中![](../graphics/stm_eqn04553.gif)是节点*I*处的伪法线，![](../graphics/stm_eqn04554.gif)由

![](../graphics/stm_eqn04555.gif)给出，其中

![](../graphics/stm_eqn04556.gif)

![](../graphics/stm_eqn04557.gif)

![](../graphics/stm_eqn04558.gif)伪法线![](../graphics/stm_eqn04553.gif)表示局部于特定单元的节点法线，通过取相邻单元边的向量叉积得到。

横向剪切速度应变分量由

![](../graphics/stm_eqn04559.gif)

![](../graphics/stm_eqn04560.gif)给出，其中节点旋转分量![](../graphics/stm_eqn04561.gif)和![](../graphics/stm_eqn04562.gif)基于投影和变换。考虑三个相邻的局部单元节点*K*、*I*和*J*，如图3.6.6-2所示。构造垂直于单元边![](../graphics/stm_eqn04565.gif)和![](../graphics/stm_eqn04566.gif)的外向向量![](../graphics/stm_eqn04563.gif)和![](../graphics/stm_eqn04564.gif)。此外，它们与参考表面在边中点相切。

图3.6.6-2 S4RSW单元中剪切投影的向量和边定义。

![](../graphics/stms4rsw-vertexedge-nls.png)

然后，通过节点投影给出关于外向向量![](../graphics/stm_eqn04564.gif)的角速度![](../graphics/stm_eqn04567.gif)

![](../graphics/stm_eqn04568.gif)其中![](../graphics/stm_eqn04569.gif)是节点*I*关于![](../graphics/stm_eqn04564.gif)的旋转速度，![](../graphics/stm_eqn04570.gif)是节点*J*关于![](../graphics/stm_eqn04564.gif)的旋转速度，![](../graphics/stm_eqn04571.gif)是边*I*的长度。最后，用于横向剪切速度应变的节点旋转分量![](../graphics/stm_eqn04561.gif)和![](../graphics/stm_eqn04562.gif)由变换给出

![](../graphics/stm_eqn04572.gif)

![](../graphics/stm_eqn04573.gif)

在形心积分点评估横向剪切的最终形式为

![](../graphics/stm_eqn04574.gif)

![](../graphics/stm_eqn04575.gif)其中

![](../graphics/stm_eqn04576.gif)

![](../graphics/stm_eqn04577.gif)和

![](../graphics/stm_eqn04578.gif)

然后，局部节点力和力矩由截面合力矩给出为

![](../graphics/stm_eqn04579.gif)

![](../graphics/stm_eqn04580.gif)

![](../graphics/stm_eqn04581.gif)

![](../graphics/stm_eqn04582.gif)

![](../graphics/stm_eqn04583.gif)

![](../graphics/stm_eqn04545.gif)
### 小应变单元S3RS

三角形壳单元公式类似于S4RS单元，基于[Kennedy等人（1986）](07s01a01-References.md)。该单元不受四边形单元公式中固有的零能模式影响。

速度应变的计算与S4RS单元相同，只是梯度算子由

![](../graphics/stm_eqn04584.gif)

给出。三角形壳的局部节点力和力矩可以表示为

![](../graphics/stm_eqn04585.gif)

![](../graphics/stm_eqn04586.gif)

![](../graphics/stm_eqn04587.gif)

![](../graphics/stm_eqn04588.gif)

![](../graphics/stm_eqn04545.gif)![](../graphics/stm_eqn04526.gif)分量通过依次求解以下方程获得：

![](../graphics/stm_eqn04589.gif)

![](../graphics/stm_eqn04590.gif)

![](../graphics/stm_eqn04591.gif)这些方程分别表示关于![](../graphics/stm_eqn04514.gif)轴的力矩平衡、关于![](../graphics/stm_eqn04516.gif)轴的力矩平衡，以及![](../graphics/stm_eqn04526.gif)方向上的力平衡。
### 沙漏控制

由于使用单点积分，四边形单元可能出现几种伪模式，通常称为沙漏模式。为了抑制沙漏模式，使用了[Belytschko等人（1984）](07s01a01-References.md)描述的一致伪模式控制。沙漏形状向量![](../graphics/stm_eqn04428.gif)定义为

![](../graphics/stm_eqn04592.gif)沙漏应变率由

![](../graphics/stm_eqn04593.gif)

![](../graphics/stm_eqn04594.gif)

![](../graphics/stm_eqn04595.gif)获得，其中上标*B*和*M*分别表示与弯曲和面内（膜）响应相关的沙漏模式。单元S4RS的相应广义沙漏应力由

![](../graphics/stm_eqn04596.gif)

![](../graphics/stm_eqn04597.gif)

![](../graphics/stm_eqn04598.gif)给出，其中*h*是壳厚度，*E*和*G*分别是杨氏模量和剪切模量。默认沙漏控制参数为![](../graphics/stm_eqn04599.gif)=![](../graphics/stm_eqn04600.gif)=0.050和![](../graphics/stm_eqn04601.gif)=0.005。比例因子![](../graphics/stm_eqn04602.gif)、![](../graphics/stm_eqn04602.gif)和![](../graphics/stm_eqn04603.gif)（默认情况下![](../graphics/stm_eqn04602.gif)=![](../graphics/stm_eqn04602.gif)=![](../graphics/stm_eqn04603.gif)=1）用于用户更改相应的默认沙漏控制参数。对于S4RSW单元，广义沙漏应力![](../graphics/stm_eqn04604.gif)和![](../graphics/stm_eqn04605.gif)与S4RS单元中的相同，但广义沙漏应力![](../graphics/stm_eqn04606.gif)被修改为

![](../graphics/stm_eqn04607.gif)

对应于广义沙漏应力的节点沙漏力和力矩为

![](../graphics/stm_eqn04608.gif)

![](../graphics/stm_eqn04609.gif)

![](../graphics/stm_eqn04610.gif)这些沙漏力和力矩直接加到前面描述的局部节点力和力矩上。
### 参考

### 参考

"Choosing a shell element," Section 29.6.2 of the Abaqus Analysis User's Guide
