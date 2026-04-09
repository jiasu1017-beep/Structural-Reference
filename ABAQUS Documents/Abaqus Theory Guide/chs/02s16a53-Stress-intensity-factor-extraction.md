# 2.16.2 应力强度因子提取

### 2.16.2 应力强度因子提取

**产品：** Abaqus/Standard

![](../graphics/stm_eqn02639.gif)![](../graphics/stm_eqn02640.gif)![](../graphics/stm_eqn02641.gif)应力强度因子![](../graphics/stm_eqn02639)、![](../graphics/stm_eqn02640)和![](../graphics/stm_eqn02641在线弹性断裂力学中起重要作用。它们表征了荷载或变形对裂纹尖端应力和应变场大小的影响，并衡量裂纹扩展或裂纹驱动力的倾向。此外，应力强度可以通过

![](../graphics/stm_eqn02642.gif)![](../graphics/stm_eqn02643.gif)![](../graphics/stm_eqn02644.gif)![](../graphics/stm_eqn02644.gif)![](../graphics/stm_eqn02642)与线性弹性材料的能量释放率（*J*积分）相关，其中![](../graphics/stm_eqn02643)和![](../graphics/stm_eqn02644被称为对数前能量因子矩阵（[Shih and Asaro, 1988](07s01a01-References.md); [Barnett and Asaro, 1972](07s01a01-References.md); [Gao, Abbudi, and Barnett, 1991](07s01a01-References.md); [Suo, 1990](07s01a01-References.md)）。对于均匀、各向同性材料，![](../graphics/stm_eqn02644是对角的，上方程简化为

![](../graphics/stm_eqn02645.gif)![](../graphics/stm_eqn02646.gif)![](../graphics/stm_eqn02647.gif)![](../graphics/stm_eqn02648.gif)![](../graphics/stm_eqn02649.gif)![](../graphics/stm_eqn02650.gif)![](../graphics/stm_eqn02651.gif)![](../graphics/stm_eqn02652.gif)![](../graphics/stm_eqn02653.gif)![](../graphics/stm_eqn02645)其中平面应力为![](../graphics/stm_eqn02646，平面应变、轴对称和三维为![](../graphics/stm_eqn02647。对于具有弹性模量![](../graphics/stm_eqn02648和![](../graphics/stm_eqn02649、泊松比![](../graphics/stm_eqn02650和![](../graphics/stm_eqn02651以及剪切模量![](../graphics/stm_eqn02652和![](../graphics/stm_eqn02653的两个不同各向同性材料之间的界面裂纹，

![](../graphics/stm_eqn02654.gif)![](../graphics/stm_eqn02654)其中

![](../graphics/stm_eqn02655.gif)![](../graphics/stm_eqn02655)

![](../graphics/stm_eqn02656.gif)![](../graphics/stm_eqn02657.gif)![](../graphics/stm_eqn02658.gif)![](../graphics/stm_eqn02639.gif)![](../graphics/stm_eqn02640.gif)![](../graphics/stm_eqn02656)对于平面应变、轴对称和三维；![](../graphics/stm_eqn02657对于平面应力。与均匀材料中的类似物不同，![](../graphics/stm_eqn02639和![](../graphics/stm_eqn02640不再是界面裂纹的纯I型和II型应力强度因子。它们只是一个复应力强度因子的实部和虚部，其物理意义可以从界面牵引力表达式理解：

![](../graphics/stm_eqn02659.gif)![](../graphics/stm_eqn01111.gif)![](../graphics/stm_eqn00377.gif)![](../graphics/stm_eqn02659)其中*r*和![](../graphics/stm_eqn01111是以裂纹尖端为中心的极坐标。双材料常数![](../graphics/stm_eqn00377定义为

![](../graphics/stm_eqn02660.gif)![](../graphics/stm_eqn02660)

在本节中，我们描述了一种交互积分方法（[Shih and Asaro, 1988](07s01a01-References.md)）来提取混合模式加载下裂纹的各个应力强度因子。该方法适用于各向同性和各向异性线性材料中的裂纹。
### 交互积分方法

通常，给定问题的*J*积分可以写为

![](../graphics/stm_eqn02661.gif)![](../graphics/stm_eqn02662.gif)![](../graphics/stm_eqn02663.gif)![](../graphics/stm_eqn02664.gif)![](../graphics/stm_eqn02661)其中当指示*B*的分量时，![](../graphics/stm_eqn02662对应于![](../graphics/stm_eqn02663。我们将具有应力强度因子的辅助、纯I型裂纹尖端场的*J*积分定义为

![](../graphics/stm_eqn02665.gif)![](../graphics/stm_eqn02665)将辅助场叠加到实际场上得到

![](../graphics/stm_eqn02666.gif)![](../graphics/stm_eqn02666)

![](../graphics/stm_eqn02639.gif)![](../graphics/stm_eqn02667.gif)![](../graphics/stm_eqn02668.gif)由于在![](../graphics/stm_eqn02668和*J*中不涉及![](../graphics/stm_eqn02639或![](../graphics/stm_eqn02667的项相等，交互积分可以定义为

![](../graphics/stm_eqn02669.gif)![](../graphics/stm_eqn02669)

![](../graphics/stm_eqn02670.gif)![](../graphics/stm_eqn02671.gif)如果对模式![](../graphics/stm_eqn02670)和模式![](../graphics/stm_eqn02671重复计算，则会产生线性方程组：

![](../graphics/stm_eqn02672.gif)![](../graphics/stm_eqn02673.gif)![](../graphics/stm_eqn02672)如果为![](../graphics/stm_eqn02673分配单位值，上述方程的解导致

![](../graphics/stm_eqn02674.gif)![](../graphics/stm_eqn02675.gif)![](../graphics/stm_eqn02674)其中![](../graphics/stm_eqn02675)该积分的计算接下来讨论。

![](../graphics/stm_eqn02676.gif)基于*J*积分的定义，交互积分![](../graphics/stm_eqn02676可以表示为

![](../graphics/stm_eqn02677.gif)![](../graphics/stm_eqn02678.gif)![](../graphics/stm_eqn02677)其中![](../graphics/stm_eqn02678给定为

![](../graphics/stm_eqn02679.gif)![](../graphics/stm_eqn02680.gif)![](../graphics/stm_eqn02681.gif)![](../graphics/stm_eqn02597.gif)![](../graphics/stm_eqn02598.gif)![](../graphics/stm_eqn02597.gif)![](../graphics/stm_eqn02679)下标![](../graphics/stm_eqn02680表示对于![](../graphics/stm_eqn02681的三个辅助纯I型、II型和III型裂纹尖端场。![](../graphics/stm_eqn02597是一个轮廓，位于裂纹前缘位置*s*处的法平面上，开始于裂纹底面，结束于顶面（见图2.16.2-1）。极限![](../graphics/stm_eqn02598表示![](../graphics/stm_eqn02597收缩到裂纹尖端。

![](../graphics/stm_eqn01412.gif)![](../graphics/stm_eqn02618.gif)图2.16.2-1 在裂纹前缘点*s*处局部正交笛卡尔坐标的定义；裂纹位于![](../graphics/stm_eqn01412)![](../graphics/stm_eqn02618)平面。

![](../graphics/stmcinter-crack-front-nls.png)

![](../graphics/stm_eqn02621.gif)following Abaqus/Standard中用于计算*J*积分的域积分程序，我们为虚拟裂纹前进定义一个交互积分![](../graphics/stm_eqn02621：

![](../graphics/stm_eqn02682.gif)![](../graphics/stm_eqn02623.gif)![](../graphics/stm_eqn02624.gif)![](../graphics/stm_eqn00483.gif)![](../graphics/stm_eqn02623.gif)![](../graphics/stm_eqn00178.gif)![](../graphics/stm_eqn02683.gif)![](../graphics/stm_eqn02682)其中*L*表示所考虑的裂纹前缘；![](../graphics/stm_eqn02623)是包围裂纹尖端的无穷小管状表面上的面积元素（即，![](../graphics/stm_eqn02624)）；![](../graphics/stm_eqn00483是![](../graphics/stm_eqn02623的外法线；![](../graphics/stm_eqn00178是虚拟裂纹扩展的局部方向。积分![](../graphics/stm_eqn02683可以通过与用于计算*J*积分相同的域积分方法计算。

![](../graphics/stm_eqn02676.gif)![](../graphics/stm_eqn00280.gif)为了获得裂纹前缘线上每个节点集*P*处的![](../graphics/stm_eqn02676)，![](../graphics/stm_eqn00280)使用与裂纹前缘沿线有限元中使用的相同插值函数进行离散化：

![](../graphics/stm_eqn02635.gif)![](../graphics/stm_eqn02636.gif)![](../graphics/stm_eqn02637.gif)![](../graphics/stm_eqn02684.gif)![](../graphics/stm_eqn02635)其中在节点集*P*处![](../graphics/stm_eqn02636，所有其他![](../graphics/stm_eqn02637为零。结果被代入![](../graphics/stm_eqn02684的表达式。最后，裂纹前缘线上每个节点集*P*处的交互积分值可以计算为

![](../graphics/stm_eqn02685.gif)![](../graphics/stm_eqn02685)
### 参考

### 参考

"Abaqus Analysis User's Guide"第11.4.2节"轮廓积分评估"
