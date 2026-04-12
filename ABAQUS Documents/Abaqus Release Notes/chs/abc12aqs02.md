# 12.2 混合模式分层过程中的模式混合比输出







**产品：**Abaqus/Standard  

**优点：**对于用内聚单元建模的分层行为，您现在可以输出损伤起始时和损伤演化过程中的模式混合比。

**说明：**分层是层压复合材料的常见失效模式，分层所需的能量通常是分层区域模式混合比的强函数。模式混合比指的是拉伸与剪切变形的相对比例。在大多数实际情况下，分层过程本质上是强混合模式的，模式混合比在分层过程中通常会发生显著变化。新的输出变量 MMIXDMI 和 MMIXDME 分别在损伤起始和损伤演化过程中测量内聚单元积分点处的模式混合比。这些变量在混合模式分层期间提供了失效模式（拉伸与剪切）的准确度量。
**参考：**

**Abaqus Analysis User's Guide**
- ["Defining the constitutive response of cohesive elements using a traction-separation description," Section 32.5.6](../usb/usb-link.md#usb-elm-ecohesivebehavior)

**Abaqus Keywords Reference Guide**
- [*OUTPUT](../key/key-link.md#usb-kws-houtput)

**Abaqus Verification Guide**
- ["Transferring results from one Abaqus/Standard analysis to another Abaqus/Standard analysis," Section 3.14.2](../ver/ver-link.md#ver-prc-import-stdtostd)

