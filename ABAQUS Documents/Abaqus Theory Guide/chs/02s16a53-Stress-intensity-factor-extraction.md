# 2.16.2 应力强度因子提取

### 2.16.2 应力强度因子提取

**产品：** Abaqus/Standard

![](../graphics/stm_eqn02639.gif)![](../graphics/stm_eqn02640.gif)![](../graphics/stm_eqn02641.gif)应力强度因子![](../graphics/stm_eqn02639.gif)![](../graphics/stm_eqn02640.gif)![](../graphics/stm_eqn02642.gif)![](../graphics/stm_eqn02643.gif)![](../graphics/stm_eqn02644.gif)![](../graphics/stm_eqn02644.gif)![](../graphics/stm_eqn02642.gif)线性弹性材料的能量释放率（*J*积分）相关，其中![](../graphics/stm_eqn02643.gif)![](../graphics/stm_eqn02644被称为对数前能量因子矩阵（[Shih and Asaro, 1988](07s01a01-References.md); [Barnett and Asaro, 1972](07s01a01-References.md); [Gao, Abbudi, and Barnett, 1991](07s01a01-References.md); [Suo, 1990](07s01a01-References.md)）。对于均匀、各向同性材料，![](../graphics/stm_eqn02645.gif)![](../graphics/stm_eqn02646.gif)![](../graphics/stm_eqn02647.gif)![](../graphics/stm_eqn02648.gif)![](../graphics/stm_eqn02649.gif)![](../graphics/stm_eqn02650.gif)![](../graphics/stm_eqn02651.gif)![](../graphics/stm_eqn02652.gif)![](../graphics/stm_eqn02653.gif)![](../graphics/stm_eqn02645.gif)中平面应力为![](../graphics/stm_eqn02654.gif)![](../graphics/stm_eqn02654.gif)中

![](../graphics/stm_eqn02655.gif)![](../graphics/stm_eqn02655)

![](../graphics/stm_eqn02656.gif)![](../graphics/stm_eqn02657.gif)![](../graphics/stm_eqn02658.gif)![](../graphics/stm_eqn02639.gif)![](../graphics/stm_eqn02640.gif)![](../graphics/stm_eqn02656.gif)于平面应变、轴对称和三维；![](../graphics/stm_eqn02659.gif)![](../graphics/stm_eqn01111.gif)![](../graphics/stm_eqn00377.gif)![](../graphics/stm_eqn02659.gif)中*r*和![](../graphics/stm_eqn02660.gif)![](../graphics/stm_eqn02660)

在本节中，我们描述了一种交互积分方法（[Shih and Asaro, 1988](07s01a01-References.md)）来提取混合模式加载下裂纹的各个应力强度因子。该方法适用于各向同性和各向异性线性材料中的裂纹。
### 交互积分方法

通常，给定问题的*J*积分可以写为

![](../graphics/stm_eqn02661.gif)![](../graphics/stm_eqn02662.gif)![](../graphics/stm_eqn02663.gif)![](../graphics/stm_eqn02664.gif)![](../graphics/stm_eqn02661.gif)中当指示*B*的分量时，![](../graphics/stm_eqn02665.gif)![](../graphics/stm_eqn02665.gif)辅助场叠加到实际场上得到

![](../graphics/stm_eqn02666.gif)![](../graphics/stm_eqn02666)

![](../graphics/stm_eqn02639.gif)![](../graphics/stm_eqn02667.gif)![](../graphics/stm_eqn02668.gif)由于在![](../graphics/stm_eqn02669.gif)![](../graphics/stm_eqn02669)

![](../graphics/stm_eqn02670.gif)![](../graphics/stm_eqn02671.gif)如果对模式![](../graphics/stm_eqn02670.gif)模式![](../graphics/stm_eqn02672.gif)![](../graphics/stm_eqn02673.gif)![](../graphics/stm_eqn02672.gif)果为![](../graphics/stm_eqn02674.gif)![](../graphics/stm_eqn02675.gif)![](../graphics/stm_eqn02674.gif)中![](../graphics/stm_eqn02675.gif)积分的计算接下来讨论。

![](../graphics/stm_eqn02676.gif)基于*J*积分的定义，交互积分![](../graphics/stm_eqn02677.gif)![](../graphics/stm_eqn02678.gif)![](../graphics/stm_eqn02677.gif)中![](../graphics/stm_eqn02679.gif)![](../graphics/stm_eqn02680.gif)![](../graphics/stm_eqn02681.gif)![](../graphics/stm_eqn02597.gif)![](../graphics/stm_eqn02598.gif)![](../graphics/stm_eqn02597.gif)![](../graphics/stm_eqn02679.gif)标![](../graphics/stm_eqn01412.gif)![](../graphics/stm_eqn02618.gif)图2.16.2-1 在裂纹前缘点*s*处局部正交笛卡尔坐标的定义；裂纹位于![](../graphics/stm_eqn01412)![](../graphics/stm_eqn02618.gif)面。

![](../graphics/stmcinter-crack-front-nls.png)

![](../graphics/stm_eqn02621.gif)following Abaqus/Standard中用于计算*J*积分的域积分程序，我们为虚拟裂纹前进定义一个交互积分![](../graphics/stm_eqn02682.gif)![](../graphics/stm_eqn02623.gif)![](../graphics/stm_eqn02624.gif)![](../graphics/stm_eqn00483.gif)![](../graphics/stm_eqn02623.gif)![](../graphics/stm_eqn00178.gif)![](../graphics/stm_eqn02683.gif)![](../graphics/stm_eqn02682.gif)中*L*表示所考虑的裂纹前缘；![](../graphics/stm_eqn02623.gif)包围裂纹尖端的无穷小管状表面上的面积元素（即，![](../graphics/stm_eqn02624.gif)；![](../graphics/stm_eqn02676.gif)![](../graphics/stm_eqn00280.gif)为了获得裂纹前缘线上每个节点集*P*处的![](../graphics/stm_eqn02676.gif)![](../graphics/stm_eqn00280.gif)用与裂纹前缘沿线有限元中使用的相同插值函数进行离散化：

![](../graphics/stm_eqn02635.gif)![](../graphics/stm_eqn02636.gif)![](../graphics/stm_eqn02637.gif)![](../graphics/stm_eqn02684.gif)![](../graphics/stm_eqn02635.gif)中在节点集*P*处![](../graphics/stm_eqn02685.gif)![](../graphics/stm_eqn02685)
### 参考

### 参考

"Abaqus Analysis User's Guide"第11.4.2节"轮廓积分评估"
