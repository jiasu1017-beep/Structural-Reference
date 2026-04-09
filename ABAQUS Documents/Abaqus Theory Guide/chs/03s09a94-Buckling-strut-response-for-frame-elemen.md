# 3.9.3 框架单元的屈曲支撑响应

### 3.9.3 框架单元的屈曲支撑响应

**产品：** Abaqus/Standard

框架单元支持可选的力响应，其中仅由单元支持轴向力。此外，轴向力沿单元恒定；所有横向力和所有弯矩为零。单元中的轴向力可以是线弹性，或者可以接受屈曲支撑响应，其中力对轴向应变由具有滞后的屈曲包络线表征，如下所述。关于标准框架单元响应详见"带集中塑性的框架单元，"第3.9.2节。

在压缩中，屈曲支撑响应以简单方式模拟细长构件在单调或循环加载时的高度非线性屈曲和后屈曲损伤。在拉伸中，响应由各向同性硬化塑性模拟。屈曲支撑包络线是唯象的，来源于类似管道构件的实验。由于屈曲包络线的描述包括外管直径和管壁厚度，只有管道截面类型允许与屈曲支撑响应一起使用。

屈曲支撑响应在压缩载荷超过屈曲临界载荷![](../graphics/stm_eqn05273.gif)之前是线弹性的。![](../graphics/stm_eqn05273.gif)的值用ISO（国际标准化组织）方程确定，如下所述。
### 屈曲预测和ISO方程

ISO方程用于预测具有类管道截面的细长构件屈曲的发生。所有有量纲的量都有应力维度。我们定义*I*，它是轴向压应力![](../graphics/stm_eqn05274.gif)和关于局部1和2轴的最大弯曲应力![](../graphics/stm_eqn05275.gif)和![](../graphics/stm_eqn05276.gif)的函数，由表达式

![](../graphics/stm_eqn05277.gif)给出。这里，![](../graphics/stm_eqn05278.gif)是特征轴向压应力，![](../graphics/stm_eqn05279.gif)是特征弯曲应力，![](../graphics/stm_eqn05280.gif)和![](../graphics/stm_eqn05281.gif)是对应于截面方向1和2的折减因子，![](../graphics/stm_eqn05282.gif)和![](../graphics/stm_eqn05283.gif)是对应于1和2方向的Euler屈曲应力。ISO方程指出，只要

![](../graphics/stm_eqn05284.gif)屈曲就不会发生。定义*I*中的项，我们使用以下符号：

![](../graphics/stm_eqn05285.gif)

是屈服应力，

*E*

是杨氏弹性模量，

*A*

是横截面积，

![](../graphics/stm_eqn05286.gif)

是1和2方向的有效长度因子（用户定义的），

![](../graphics/stm_eqn05287.gif)

是1和2方向的无支撑长度（用户定义的），

![](../graphics/stm_eqn05288.gif)

是关于局部横截面方向的惯性矩，

![](../graphics/stm_eqn05289.gif)

是弹性截面模量，

![](../graphics/stm_eqn05290.gif)

是塑性截面模量，

*r*

是回转半径。对于管道截面，如果*D*是外径，*t*是管壁厚度，

![](../graphics/stm_eqn03733.gif)

![](../graphics/stm_eqn05291.gif)，

![](../graphics/stm_eqn05289.gif)

![](../graphics/stm_eqn05292.gif)，

![](../graphics/stm_eqn05290.gif)

![](../graphics/stm_eqn05293.gif)，

*r*

![](../graphics/stm_eqn05294.gif)。ISO方程中的项计算如下：

![](../graphics/stm_eqn05274.gif)

是轴向压应力，![](../graphics/stm_eqn05295.gif)，其中*P*是单元中的轴向力。

![](../graphics/stm_eqn05296.gif)

是关于1或2横截面轴的最大弯曲应力，

![](../graphics/stm_eqn05297.gif)、![](../graphics/stm_eqn05298.gif)，其中![](../graphics/stm_eqn05299.gif)和![](../graphics/stm_eqn05300.gif)

是关于1和2方向的弯矩。

![](../graphics/stm_eqn05301.gif)

是特征局部屈曲应力，

![](../graphics/stm_eqn05302.gif)，对于![](../graphics/stm_eqn05303.gif)，

![](../graphics/stm_eqn05304.gif)，对于![](../graphics/stm_eqn05305.gif)，其中![](../graphics/stm_eqn05306.gif)和

![](../graphics/stm_eqn05307.gif)，

![](../graphics/stm_eqn05308.gif)，对于![](../graphics/stm_eqn05309.gif)，

![](../graphics/stm_eqn05310.gif)，

![](../graphics/stm_eqn05311.gif)是一个临界屈曲系数。

![](../graphics/stm_eqn05278.gif)

是特征轴向压应力，

![](../graphics/stm_eqn05312.gif)，对于![](../graphics/stm_eqn05313.gif)，

![](../graphics/stm_eqn05314.gif)，对于![](../graphics/stm_eqn05315.gif)，其中![](../graphics/stm_eqn05316.gif)，

且![](../graphics/stm_eqn05317.gif)，

![](../graphics/stm_eqn05318.gif)。

![](../graphics/stm_eqn05279.gif)

是特征弯曲应力（对于管道截面![](../graphics/stm_eqn05319.gif)），

![](../graphics/stm_eqn05320.gif)，对于![](../graphics/stm_eqn05321.gif)，

![](../graphics/stm_eqn05322.gif)，对于![](../graphics/stm_eqn05323.gif)，

![](../graphics/stm_eqn05324.gif)，对于![](../graphics/stm_eqn05325.gif)，

其中![](../graphics/stm_eqn05326.gif)和![](../graphics/stm_eqn05327.gif)。

![](../graphics/stm_eqn05328.gif)

是对应于1或2方向的Euler屈曲应力，

![](../graphics/stm_eqn05329.gif)和![](../graphics/stm_eqn05330.gif)。

![](../graphics/stm_eqn05331.gif)

是对应于横截面方向1和2的折减因子。这些因子作为端弯矩、压应力和Euler屈曲函数的函数由用户定义。每个因子的默认值是![](../graphics/stm_eqn05332.gif)。

如果允许在标准框架单元响应和屈曲支撑响应之间切换，则当![](../graphics/stm_eqn05333.gif)时一次性切换到屈曲支撑响应。ISO方程提供临界载荷值![](../graphics/stm_eqn05273.gif)，定义为当ISO方程满足时单元中轴向力![](../graphics/stm_eqn05334.gif)的值。为防止在存在大弯矩但可忽略轴向力的情况下切换，使用了额外的不等式。这个额外的检查，称为强度方程，取以下形式：

![](../graphics/stm_eqn05335.gif)对于要切换到屈曲支撑行为的框架单元，ISO方程和强度方程都必须满足，![](../graphics/stm_eqn05336.gif)和![](../graphics/stm_eqn05337.gif)。如果从分析开始就请求单元的屈曲支撑响应，则单元不能支持弯矩。在这种情况下，ISO方程变为简化陈述：对于

![](../graphics/stm_eqn05338.gif)不会发生屈曲。
### Marshall支撑包络线

Marshall支撑包络线定义了后屈曲受损弹性模型和滞后回路响应。为定义Marshall支撑包络线，需要![](../graphics/stm_eqn05339.gif)的值和以下七个常数：

![](../graphics/stm_eqn01040.gif)

是定义![](../graphics/stm_eqn05340.gif)的系数（![](../graphics/stm_eqn05341.gif)），

![](../graphics/stm_eqn01256.gif)

是各向同性硬化斜率系数（0.02），

![](../graphics/stm_eqn05342.gif)

是定义![](../graphics/stm_eqn05343.gif)的系数（![](../graphics/stm_eqn05344.gif)），

![](../graphics/stm_eqn05345.gif)

是定义![](../graphics/stm_eqn05343.gif)的系数（![](../graphics/stm_eqn05346.gif)），

![](../graphics/stm_eqn04549.gif)

是力系数（0.28），

![](../graphics/stm_eqn01219.gif)

是斜率系数（0.02），

![](../graphics/stm_eqn05347.gif)

是力系数（min(1.0, ![](../graphics/stm_eqn05348.gif))）。

括号中的值是Abaqus提供的默认值，![](../graphics/stm_eqn05339.gif)的值如上所述从ISO方程得出。

Marshall包络线控制支撑的压缩和拉伸响应，如图3.9.3-1所示。包络线内部的虚线表示定义加载-卸载力对应变路径的受损弹性模量。

图3.9.3-1 Marshall支撑理论屈曲包络线。

![](../graphics/eusingframe-envelope-nls.png)
### 参考

### 参考

"Frame elements," Section 29.4.1 of the Abaqus Analysis User's Guide

"Frame section behavior," Section 29.4.2 of the Abaqus Analysis User's Guide
