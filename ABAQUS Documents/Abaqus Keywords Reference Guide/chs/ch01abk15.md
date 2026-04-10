# *ASYMMETRIC-AXISYMMETRIC





### *ASYMMETRIC-AXISYMMETRIC定义与CAXA*n*或SAXA*n*元素一起使用的接触元素的积分区域。

此选项用于允许Abaqus/Standard为与CAXA*n*或SAXA*n*元素结合使用的ISL型和IRS型接触元素计算适当的积分区域。[*ASYMMETRIC-AXISYMMETRIC](ch01abk15.md)选项必须与[*INTERFACE](ch09abk22.md)选项结合使用。

**产品：**Abaqus/Standard  

**类型：**模型数据

**级别：**Part、Part instance、Assembly

##### **参考：**

- ["接触相互作用分析概述，" Abaqus Analysis User's Guide第36.1.1节](../usb/usb-link.md#usb-cni-acontactoverview)
- ["存在非对称-轴对称元素时的接触建模，" Abaqus Analysis User's Guide第36.3.10节](../usb/usb-link.md#usb-cni-acontactasymmaxisymm)
- [*INTERFACE](ch09abk22.md)

### **必需参数：**

ANGLE

将此参数设置为接触元素所在的圆周平面的角位置（以度为单位）。有效值为：对于*n*=1，![](../graphics/key_eqn00075.gif)=0、180；对于*n*=2，![](../graphics/key_eqn00075.gif)=0、90、180；对于*n*=3，![](../graphics/key_eqn00075.gif)=0、60、120、180；对于*n*=4，![](../graphics/key_eqn00075.gif)=0、45、90、135、180。Abaqus/Standard在其他圆周平面上不能正确建模接触。

MODE

将此参数设置为与接触元素共享节点的CAXA*n*或SAXA*n*元素使用的Fourier模式数量。

**此选项没有关联的数据行。**