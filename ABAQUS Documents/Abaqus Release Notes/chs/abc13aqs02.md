# 13.2 VUCHARLENGTH：在材料点定义特征单元长度的用户子程序





### 13.2 [`VUCHARLENGTH`](../sub/sub-link.md#sub-xsl-vucharlength)：在材料点定义特征单元长度的用户子程序

**产品：** Abaqus/Explicit

**优点：** 您现在可以使用用户子程序[`VUCHARLENGTH`](../sub/sub-link.md#sub-xsl-vucharlength)将特征单元长度定义为单元拓扑、节点和材料点坐标以及材料方向的函数。

**描述：** 在用户子程序[`VUCHARLENGTH`](../sub/sub-link.md#sub-xsl-vucharlength)中定义的特征单元长度被Abaqus用于正则化方案，以减轻包含应变软化的本构模型中的网格依赖性。它可以与内置Abaqus材料模型以及基于用户子程序的材料模型一起使用。
**参考：**

**Abaqus关键词参考指南**
- [*CHARACTERISTIC LENGTH](../key/key-link.md#usb-kws-mcharacteristiclength)

**Abaqus用户子程序参考指南**
- ["VUCHARLENGTH，" 第1.2.11节](../sub/sub-link.md#sub-rtn-uexpucharlength)

**Abaqus验证指南**
- ["`VUCHARLENGTH`，" 第4.1.32节](../ver/ver-link.md#ver-sub-vucharlength)




