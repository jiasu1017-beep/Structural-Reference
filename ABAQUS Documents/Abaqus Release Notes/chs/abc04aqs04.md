# 4.4 Abaqus/CFD 中的 k-epsilon 可实现湍流模型





### 4.4 Abaqus/CFD 中的 k-epsilon 可实现湍流模型

**产品：** Abaqus/CFD

**优势：** 现在，您可以将 *k*–![](../graphics/rnb_eqn00001.gif) 可实现湍流模型应用于流体流动问题。

**描述：** *k*–![](../graphics/rnb_eqn00001.gif) 可实现模型是一个双方程湍流模型，它演化湍动能 *k* 和能量耗散率 ![](../graphics/rnb_eqn00001.gif) 的方程。模型方程由基本物理原理和量纲分析推导；*k* 方程使用第一性原理推导，![](../graphics/rnb_eqn00001.gif) 方程使用物理洞察假设。这个特定版本使用可实现性约束，这通过修改模型系数和 epsilon 方程来强制雷诺兹应力中的数学一致性（例如，强制正应力的正性和柯西-施warz 不等式）。这些修改保证了预测雷诺兹应力的物理一致性。为了提高 *k*–![](../graphics/rnb_eqn00001.gif) 可实现模型在网格不够细以解析壁面有界流动中粘性子层的情况下的准确性，实现了一种称为双层模型的近壁模型。

**参考：**

**Abaqus Analysis User's Guide**
- [“Incompressible fluid dynamic analysis，” Section 6.6.2](../usb/usb-link.md#usb-anl-aifluiddyn)

**Abaqus Keywords Reference Guide**
- [*TURBULENCE MODEL](../key/key-link.md#usb-kws-hturbulence)




