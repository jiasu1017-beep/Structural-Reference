# 2.16.3 T应力提取

### 2.16.3 T应力提取

**产品：** Abaqus/Standard

在线弹性体中尖锐裂纹附近应力场相对于*r*（距裂纹尖端的距离）的渐近展开为

![](../graphics/stm_eqn02686)（[Williams, 1957](07s01a01-References.md)），其中*r*和![](../graphics/stm_eqn01111是以裂纹尖端为中心的平面极坐标。局部轴定义使得1轴位于裂纹前缘感兴趣点处的裂纹平面内，并垂直于该点的裂纹前缘；2轴垂直于裂纹平面（因此垂直于裂纹前缘）；3轴沿裂纹前缘切线。![](../graphics/stm_eqn02687)是裂纹尖端处裂纹表面上的表面牵引力，![](../graphics/stm_eqn02688)是![](../graphics/stm_eqn02689的常数应力项。![](../graphics/stm_eqn02690是裂纹前缘的延伸应变。平面应变中![](../graphics/stm_eqn02691；平面应力中项![](../graphics/stm_eqn02692消失。

*T*应力表示平行于裂纹表面的应力。它是一个有用的量，不仅在线弹性裂纹分析中，而且在弹塑性断裂研究中也是如此。

*T*应力通常出现在线弹性材料的裂纹稳定性和 kink 讨论中。对于I型加载下的小量裂纹扩展，当![](../graphics/stm_eqn02693时，直裂纹路径已被证明是稳定的，而当![](../graphics/stm_eqn02694时，路径将不稳定，因此将偏离直线（[Cotterell and Rice, 1980](07s01a01-References.md)）。[Xu, Bower, and Ortiz (1994)](07s01a01-References.md) 在三维裂纹扩展研究中也发现了类似趋势。[Hutchinson and Suo (1992)](07s01a01-References.md) 还表明，一旦裂纹在混合模式加载下开始扩展，扩展裂纹路径如何受*T*应力影响。（裂纹起始方向可以另外使用"裂纹扩展方向预测"第2.16.4节中讨论的标准预测。）

*T*应力在弹塑性断裂分析中也起重要作用，即使*T*应力是根据包含裂纹的相同固体的线弹性材料特性计算的。[Larsson and Carlsson (1973)](07s01a01-References.md) 的早期研究表明，*T*应力可以对塑性区大小和形状产生显著影响，并且通过将*T*应力作为第二个裂纹尖端参数，可以充分预测实际试样中的小塑性区。一些最近的研究（[Bilby et al., 1986](07s01a01-References.md); [Al-Ani and Hancock, 1991](07s01a01-References.md); [Betegn and Hancock, 1991](07s01a01-References.md); [Du and Hancock, 1991](07s01a01-References.md); [Parks, 1992](07s01a01-References.md); 和 [Wang, 1991](07s01a01-References.md)）进一步表明，*T*应力可以很好地与弹塑性裂纹尖端场的拉伸应力三轴度相关。这些工作中观察到的的重要特征是，负*T*应力可以降低裂纹尖端前方的拉伸应力三轴度（也称为静水拉伸应力）；*T*应力越负，拉伸应力三轴度的降低越大。相比之下，正*T*应力只会导致应力三轴度的适度升高。研究发现，当拉伸应力三轴度高时（由正*T*应力表示），裂纹尖端场可以充分由HRR解（[Hutchinson, 1968](07s01a01-References.md); [Rice and Rosengren, 1968](07s01a01-References.md)）描述，由单个参数缩放：*J*积分；即，将存在*J*主导。当拉伸应力三轴度降低时（由*T*应力变得更负表示），裂纹尖端场将很快偏离HRR解，并且将失去*J*主导（裂纹尖端周围的渐近场不能很好地由HRR场表征）。因此，使用*T*应力（基于荷载水平和线弹性材料特性计算）来表征裂纹尖端应力状态的三轴度，使用*J*积分（基于实际弹塑性变形场计算）来测量裂纹尖端变形的尺度，提供了一种双参数断裂力学理论，在广泛范围的裂纹配置和加载下准确描述平面应变或三维中的I型弹塑性裂纹尖端应力和变形。

为了提取*T*应力，我们使用辅助线载荷解，幅值为*f*，施加在裂纹扩展平面内并沿裂纹线：

![](../graphics/stm_eqn02695)

![](../graphics/stm_eqn02696)对于平面应力的项![](../graphics/stm_eqn02697。

使用的交互积分与提取应力强度因子的交互积分完全相同：

![](../graphics/stm_eqn02698)其中![](../graphics/stm_eqn01031为

![](../graphics/stm_eqn02699)

在极限![](../graphics/stm_eqn02619，使用局部渐近场，

![](../graphics/stm_eqn02700)其中平面应力为![](../graphics/stm_eqn02646和![](../graphics/stm_eqn02701；平面应变、轴对称和三维为![](../graphics/stm_eqn02647和![](../graphics/stm_eqn02702；平面应变和平面应力为零；![](../graphics/stm_eqn02703是热膨胀系数；![](../graphics/stm_eqn02705是温度差。

如果只建模结构的一半，则![](../graphics/stm_eqn02706翻倍。![](../graphics/stm_eqn02706可以通过与*J*积分计算和应力强度因子提取相同的域积分方法计算，这在"J积分评估"第2.16.1节和"应力强度因子提取"第2.16.2节中描述。
### 参考

### 参考

"Abaqus Analysis User's Guide"第11.4.2节"轮廓积分评估"
