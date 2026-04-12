# 6.1 并联流变框架增强





**产品：** Abaqus/Standard  Abaqus/Explicit

**优势：** 现在可以使用幂律蠕变模型或包含压力和总变形依赖性的用户定义蠕变模型来定义粘弹性网络中的粘性响应。在平衡网络中，现在可以定义包含组合各向同性硬化和运动硬化的塑性响应。非线性运动硬化的实现将最有利于包含循环加载的应用。此外，现在支持在各种 Abaqus 分析之间传输使用并联流变框架定义的模型的结果。

**说明：** 粘弹性网络中的粘性响应可以使用包含压力依赖性的新型幂律蠕变模型来定义。此外，用户定义的蠕变模型可以通过适当的不变量包含对压力和总变形的依赖性。在 Abaqus/Standard 中，平衡网络响应已增强，可以包含具有组合各向同性非线性运动硬化的塑性。非线性运动硬化的实现基于 Armstrong-Frederick 模型，允许指定多个背应力。最后，现在完全支持导入使用并联流变框架定义的材料模型的能力。
**参考文献：**

**Abaqus Analysis User's Guide**
- ["在 Abaqus 分析之间传输结果：概述，" 第 9.2.1 节](../usb/usb-link.md#usb-anl-atransferoverview)
- ["并联流变框架，" 第 22.8.2 节](../usb/usb-link.md#usb-mat-cnonlinvisco)

**Abaqus Keywords Reference Guide**
- [*VISCOELASTIC](../key/key-link.md#usb-kws-mviscoelast)

**Abaqus User Subroutines Reference Guide**
- ["UCREEPNETWORK," 第 1.1.23 节](../sub/sub-link.md#sub-rtn-uucreepnetwork)

**Abaqus Verification Guide**
- ["使用并联流变框架传输结果，" 第 3.14.20 节](../ver/ver-link.md#ver-prc-import-prf)
