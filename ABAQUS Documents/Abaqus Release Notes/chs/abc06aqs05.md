# 6.5 用户定义材料行为的新型混合公式





**产品：** Abaqus/Standard

**优势：** 现在可以通过用户子程序 [`UMAT`](../sub/sub-link.md#sub-xsl-umat) 使用混合单元定义几乎不可压缩和完全不可压缩的非线性弹性材料行为。

**说明：** 当用户材料用于定义混合单元响应时，Abaqus 使用的默认公式适用于使用增量公式的材料模型（例如金属塑性），但与通常用于超弹性材料的总公式不一致。在后一种情况下，默认公式可能导致收敛问题。当几乎不可压缩的非线性弹性用户材料受到大变形时，可以观察到这种收敛问题。Abaqus/Standard 现在为这种情况提供了替代总公式。该公式与 Abaqus 用于超弹性材料的原生几乎不可压缩公式一致，在这些情况下比默认公式效果更好。Abaqus/Standard 还首次提供了通过用户子程序 [`UMAT`](../sub/sub-link.md#sub-xsl-umat) 定义完全不可压缩响应的能力。总混合公式可以通过最小的更改来实现现有 [`UMAT`](../sub/sub-link.md#sub-xsl-umat)。对于完全不可压缩材料，用户子程序 [`UMAT`](../sub/sub-link.md#sub-xsl-umat) 只需要定义材料响应的偏应力部分。
**参考文献：**

**Abaqus Analysis User's Guide**
- ["用户定义的机械材料行为，" 第 26.7.1 节](../usb/usb-link.md#usb-mat-cusermat)

**Abaqus Keywords Reference Guide**
- [*USER MATERIAL](../key/key-link.md#usb-kws-musermaterial)

**Abaqus User Subroutines Reference Guide**
- ["UMAT," 第 1.1.41 节](../sub/sub-link.md#sub-rtn-uumat)

**Abaqus Verification Guide**
- ["`UMAT` 和 `UHYPER`," 第 4.1.21 节](../ver/ver-link.md#ver-sub-umatuhyper)
