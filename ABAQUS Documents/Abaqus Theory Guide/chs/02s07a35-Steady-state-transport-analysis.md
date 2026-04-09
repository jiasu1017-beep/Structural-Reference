# 2.7.1 稳态传输分析

### 2.7.1 稳态传输分析

![](../graphics/stm_eqn01689.gif)![](../graphics/stm_eqn01690.gif)![](../graphics/stm_eqn01691.gif)![](../graphics/stm_eqn01667.gif)**产品：** Abaqus/Standard

Abaqus/Standard提供了一种专门的分析能力来模拟圆柱形变形体沿平坦刚性表面滚动的稳态行为。该能力使用参考系来消除问题的显式时间依赖性，从而可以执行纯空间依赖分析。对于以恒定地面速度和恒定角滚动速度行驶的轴对称体，在以地面速度移动但不随身体在滚动运动中自旋的参考系中，稳态是可能的。这种参考系的选择允许有限元网格保持静止，因此只有接触区域中的身体部分需要精细网格划分。
### 稳态滚动的运动学

滚动问题的运动学用随身体地面运动一起移动的坐标架来描述。在这个移动参考系中，刚体旋转以空间或欧拉方式描述，变形以材料或拉格朗日方式描述。正是这种运动学描述将稳态移动接触场问题转换为纯空间依赖的模拟。

我们考虑如图2.7.1-1所示的情况，其中身体的地面速度以恒定转向运动描述。

图2.7.1-1 恒定转向运动。

![](../graphics/corneringrolling.png)身体以恒定角滚动速度![](../graphics/stm_eqn01091.gif)绕刚性车轴![](../graphics/stm_eqn00553.gif)旋转，![](../graphics/stm_eqn01638.gif)，而车轴又以恒定角速度![](../graphics/stm_eqn01258.gif)绕固定转向轴![](../graphics/stm_eqn00483.gif)（通过点![](../graphics/stm_eqn01639.gif）旋转。因此，时间*t*时粒子![](../graphics/stm_eqn00141.gif)的运动由刚体滚动旋转到位置![](../graphics/stm_eqn01640.gif)组成，描述为

![](../graphics/stm_eqn01641.gif)然后变形到点![](../graphics/stm_eqn00117.gif)，随后绕![](../graphics/stm_eqn00483.gif)进行转向旋转（或进动）到位置![](../graphics/stm_eqn01642.gif)，使得

![](../graphics/stm_eqn01643.gif)其中![](../graphics/stm_eqn01644.gif是由![](../graphics/stm_eqn01645.gif给出的转向旋转，![](../graphics/stm_eqn01646.gif)是与旋转向量![](../graphics/stm_eqn01647.gif)相关的斜对称矩阵。类似地，![](../graphics/stm_eqn01648.gif)是自旋旋转矩阵，定义为![](../graphics/stm_eqn01649.gif)，![](../graphics/stm_eqn01650.gif)是与旋转向量![](../graphics/stm_eqn01651.gif)相关的斜对称矩阵。粒子的速度变为

![](../graphics/stm_eqn01652.gif)为了描述身体的变形，我们定义映射![](../graphics/stm_eqn01653.gif)，它给出时间*t*时点![](../graphics/stm_eqn00141.gif)作为其时间*t*时位置![](../graphics/stm_eqn01640.gif)函数的位置，所以![](../graphics/stm_eqn01654.gif)因此

![](../graphics/stm_eqn01655.gif)其中

![](../graphics/stm_eqn01656.gif)注意到![](../graphics/stm_eqn01657.gif)，并引入周向方向![](../graphics/stm_eqn01658.gif)，其中![](../graphics/stm_eqn01659.gif)是参考体上一点的半径，参考体的速度可以写为![](../graphics/stm_eqn01660.gif)，所以

![](../graphics/stm_eqn01661.gif)其中*S*是沿流线的距离测量坐标。使用此结果，连同![](../graphics/stm_eqn01662.gif)，粒子的速度可以写为

![](../graphics/stm_eqn01663.gif)加速度通过二次微分和一些操作获得：

![](../graphics/stm_eqn01664.gif)

为了获得在身体相关参考系中的速度和加速度表达式，我们使用变换

![](../graphics/stm_eqn01665.gif)从而得到

![](../graphics/stm_eqn01666.gif)和

![](../graphics/stm_eqn01667.gif)对于稳态条件，这些表达式简化为

![](../graphics/stm_eqn01668.gif)和

![](../graphics/stm_eqn01669.gif)

最后一个表达式中的第一项可以被识别为由于绕![](../graphics/stm_eqn00483.gif)旋转而产生的离心力的加速度。注意到![](../graphics/stm_eqn01670.gif)是速度的度量，第二项可以被识别为产生科里奥利力的加速度。最后一项结合了由于绕![](../graphics/stm_eqn00553.gif)旋转而产生的科里奥利和离心力。当变形沿周向均匀时，这种科里奥利效应消失，因此加速度仅产生离心力。

身体中心![](../graphics/stm_eqn01638.gif)（必须位于轴线![](../graphics/stm_eqn00553.gif上）的速度为

![](../graphics/stm_eqn01671.gif)因为滚动和变形引起的运动在轴线上消失。

为了获得直线运动（如图2.7.1-2所示）的表达式，我们将![](../graphics/stm_eqn01639.gif)移动到远离身体中心![](../graphics/stm_eqn01672.gif)的位置，但保持![](../graphics/stm_eqn01673.gif)相同。在这种情况下![](../graphics/stm_eqn01674.gif)，因此在极限情况下

![](../graphics/stm_eqn01675.gif)

![](../graphics/stm_eqn01676.gif)这对应于直线滚动。

图2.7.1-2 直线滚动。

![](../graphics/stm_eqn00553.gif)![](../graphics/stm_eqn01638.gif)![](../graphics/stm_eqn01676.gif)![](../graphics/straightlinerolling.png)
### 惯性

来自达朗贝尔力的虚功贡献为

![](../graphics/stm_eqn01677.gif)使用散度定理，虚功贡献变为

![](../graphics/stm_eqn01678.gif)虚功率变为

![](../graphics/stm_eqn01679.gif)对于纯直线滚动，每个表达式中只需考虑最后一项。
### 关于非线性基态进行谐波分析

为了对滚动轮胎进行稳态动力学或频率分析，有必要将虚功表达式关于基态线性化。假设形式的谐波解![](../graphics/stm_eqn01680.gif)，可以表明，对于直线滚动的情况，线性化虚功率为

![](../graphics/stm_eqn01681.gif)第一项是由于绕车轴自转引起的荷载刚度贡献。第二项是虚部反对称陀螺算子。第三项是标准质量算子。
### 接触条件

为了获得接触条件，我们从上一节推导的速度表达式开始。对于变形体表面上的点

![](../graphics/stm_eqn01682.gif)其中![](../graphics/stm_eqn00483.gif)是转向轴（必须垂直于刚性表面），![](../graphics/stm_eqn01258.gif)是绕![](../graphics/stm_eqn00483.gif)的转向角速度。假设基础（或刚性表面）上一点的速度为![](../graphics/stm_eqn01683.gif)，相对运动变为

![](../graphics/stm_eqn01684.gif)其中![](../graphics/stm_eqn01685.gif)。这个方程可以分解为法向和切向分量。渗透率为

![](../graphics/stm_eqn01686.gif)对于任何接触点![](../graphics/stm_eqn01687.gif)；因此，

![](../graphics/stm_eqn01688.gif)其增量形式简化为标准接触条件

![](../graphics/stm_eqn01689.gif)对于稳态条件，![](../graphics/stm_eqn01690.gif)和![](../graphics/stm_eqn01691.gif)。

类似地，滑移率为

![](../graphics/stm_eqn01692.gif)其中![](../graphics/stm_eqn01693.gif)是接触表面上两个正交的单位切向量，所以![](../graphics/stm_eqn01694.gif)。对于稳态条件，![](../graphics/stm_eqn01695.gif)，所以

![](../graphics/stm_eqn01696.gif)![](../graphics/stm_eqn01697.gif)的变化给出

![](../graphics/stm_eqn01698.gif)对于直线滚动，我们可以用![](../graphics/stm_eqn01699.gif)替换![](../graphics/stm_eqn01673.gif)，从而得到

![](../graphics/stm_eqn01700.gif)和

![](../graphics/stm_eqn01701.gif)

为了完成公式，必须建立摩擦应力与滑移速度之间的关系。Abaqus为稳态滚动提供了库仑摩擦定律。该定律假设如果摩擦应力

![](../graphics/stm_eqn01702.gif)等于临界应力![](../graphics/stm_eqn01703.gif)，则发生滑移，其中![](../graphics/stm_eqn01704.gif)和![](../graphics/stm_eqn01705.gif)是沿![](../graphics/stm_eqn01706.gif)的剪切应力，![](../graphics/stm_eqn01087.gif)是摩擦系数，*p*是接触压力。另一方面，当![](../graphics/stm_eqn01707.gif)时，不发生相对运动。在Abaqus中，无相对运动条件通过刚性黏性行为近似

![](../graphics/stm_eqn01708.gif)其中![](../graphics/stm_eqn01697.gif)是切向滑移速度，![](../graphics/stm_eqn01709.gif)是"黏附黏度"，由关系式得出

![](../graphics/stm_eqn01710.gif)允许的黏性滑移速度定义为周向速度的一个分数

![](../graphics/stm_eqn01711.gif)其中![](../graphics/stm_eqn01712.gif)是用户定义的滑移容差。

这些表达式对滑移的标准虚功贡献，

![](../graphics/stm_eqn01713.gif)和滑移的虚功率，

![](../graphics/stm_eqn01714.gif)
### 参考

### 参考

![](../graphics/stm_eqn01697.gif)![](../graphics/stm_eqn01696.gif)"Abaqus Analysis User's Guide"第6.4.1节"稳态传输分析"
