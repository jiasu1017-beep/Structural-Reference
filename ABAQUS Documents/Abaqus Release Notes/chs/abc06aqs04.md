# 6.4 用户定义的频域粘弹性行为





**产品：** Abaqus/Standard

**优势：** 现在可以通过用户子程序 [`UMAT`](../sub/sub-link.md#sub-xsl-umat) 定义频域粘弹性行为。

**说明：** 频域中的粘弹性行为需要指定储能模量（材料刚度）和损耗模量（材料阻尼）。[`UMAT`](../sub/sub-link.md#sub-xsl-umat) 接口和实现已增强，以支持材料刚度和材料阻尼的指定。此功能允许您定义具有复频依赖性的粘弹性响应，这是 Abaqus/Standard 中内置模型不支持的。
**参考文献：**

**Abaqus Analysis User's Guide**
- ["用户定义的机械材料行为，" 第 26.7.1 节](../usb/usb-link.md#usb-mat-cusermat)

**Abaqus Keywords Reference Guide**
- [*USER MATERIAL](../key/key-link.md#usb-kws-musermaterial)

**Abaqus User Subroutines Reference Guide**
- ["UMAT," 第 1.1.41 节](../sub/sub-link.md#sub-rtn-uumat)

**Abaqus Verification Guide**
- ["`UMAT` 和 `UHYPER`," 第 4.1.21 节](../ver/ver-link.md#ver-sub-umatuhyper)
