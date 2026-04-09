# 6.5.3 肘单元上的压力载荷

### 6.5.3 肘单元上的压力载荷

**产品：** Abaqus/Standard

肘单元通常用于管道建模，其中在承受均匀或静水压力时管道曲率可以发生显著变化。因此，为这些单元开发了包括大几何变化的压力载荷，如本节所述。

压力在肘部侧表面上的虚功贡献为

![](../graphics/stm_eqn08261.gif)其中

*p*

是压力幅度，

![](../graphics/stm_eqn04502.gif)

是肘部侧壁中面一点处的虚位移，

![](../graphics/stm_eqn00483.gif)

是侧壁中面法线，且

*A*

是侧壁在当前构型中占据的空间面积。

表面法线和微分面积的乘积可以用沿管道的材料坐标![](../graphics/stm_eqn08262.gif)和围绕管道截面的![](../graphics/stm_eqn00155.gif)重写：

![](../graphics/stm_eqn08263.gif)其中![](../graphics/stm_eqn08264.gif)是初始管道半径，因此

![](../graphics/stm_eqn08265.gif)其中![](../graphics/stm_eqn08266.gif)是侧壁在参考构型中占据的空间面积。

对于静水压力，压力幅度是位置的函数：

![](../graphics/stm_eqn08267.gif)其中

![](../graphics/stm_eqn08268.gif)

是参考压力幅度，

![](../graphics/stm_eqn08269.gif)

是零压力高度，

![](../graphics/stm_eqn08270.gif)

是参考高度，且

![](../graphics/stm_eqn02234.gif)

是![](../graphics/stm_eqn08271.gif)，垂直方向的单位向量。

在肘单元上，侧表面上的位置![](../graphics/stm_eqn00117.gif)插值为

![](../graphics/stm_eqn08272.gif)其中

![](../graphics/stm_eqn08273.gif)

是管道轴线上一点的位置，

![](../graphics/stm_eqn08274.gif)

是径向位移，

![](../graphics/stm_eqn08275.gif)

是切向位移，

![](../graphics/stm_eqn03949.gif)

是![](../graphics/stm_eqn08276.gif)，且

![](../graphics/stm_eqn00479.gif)

是![](../graphics/stm_eqn08277.gif)，其中![](../graphics/stm_eqn08278.gif)和![](../graphics/stm_eqn08279.gif)是横截面基向量。

位置的一阶变分现在可以表示为

![](../graphics/stm_eqn08280.gif)位置对参数化的导数为

![](../graphics/stm_eqn08281.gif)和

![](../graphics/stm_eqn08282.gif)假设（1）由于管道中扭转可以忽略，![](../graphics/stm_eqn08283.gif)和![](../graphics/stm_eqn08284.gif)项可以忽略；（2）由于管道中翘曲可以忽略，![](../graphics/stm_eqn08285.gif)及其导数项可以忽略；（3）![](../graphics/stm_eqn08286.gif)；（4）拉伸![](../graphics/stm_eqn08287.gif)是统一的；和（5）![](../graphics/stm_eqn08288.gif)和![](../graphics/stm_eqn08289.gif)相对于![](../graphics/stm_eqn08290.gif)很小，我们得到以下表达式用于![](../graphics/stm_eqn08291.gif)的被积函数：

![](../graphics/stm_eqn08292.gif)对于闭端载荷，肘部端盖上的压力虚功贡献为

![](../graphics/stm_eqn08293.gif)其中*r*和![](../graphics/stm_eqn00155.gif)是端盖上二维圆柱坐标系统中的材料坐标，![](../graphics/stm_eqn01642.gif)表示端盖上的位置，![](../graphics/stm_eqn08294.gif)是肘单元端盖在当前构型中占据的空间面积。我们假定端盖的以下变形：

![](../graphics/stm_eqn08295.gif)其中![](../graphics/stm_eqn08296.gif)是标识所考虑端盖的参数。如果端盖的变形中，参考端盖构型的径向射线在变形下保持直线，则这个假定的变形自然出现。可以容易地表明，只要端盖的圆周曲线的变形是可微的，假定的端盖变形将是可微的。对于应用中出现的端盖边界形状（主要是椭圆化模式），假定的变形将是局部可逆的，因此对变形表面上的函数进行积分可能没有问题。

忽略由于翘曲的项在侧表面位置表达式中，端盖上位置的一阶变分为

![](../graphics/stm_eqn08297.gif)![](../graphics/stm_eqn01642.gif)相对于*r*和![](../graphics/stm_eqn00155.gif)的导数为

![](../graphics/stm_eqn08298.gif)和

![](../graphics/stm_eqn08299.gif)端盖压力虚功的被积函数现在可以表示为

![](../graphics/stm_eqn08300.gif)其中![](../graphics/stm_eqn02561.gif)是![](../graphics/stm_eqn08301.gif)（如果端盖的中心是元素的节点1），![](../graphics/stm_eqn08302.gif)（如果中心是元素节点2或3）。

压力载荷的载荷刚度定义为虚功的一阶变分，由![](../graphics/stm_eqn08303.gif)给出。以下表达式是其计算所需的：

![](../graphics/stm_eqn08304.gif)

![](../graphics/stm_eqn08305.gif)和

![](../graphics/stm_eqn08306.gif)在上述中，![](../graphics/stm_eqn08307.gif)仅在静水压力情况下非零，在第一种情况下由

![](../graphics/stm_eqn08308.gif)给出，在第二种情况下由

![](../graphics/stm_eqn08309.gif)给出。

### 参考

### 参考

"Pipes and pipebends with deforming cross-sections: elbow elements," Abaqus Analysis User's Guide 第29.5.1节
