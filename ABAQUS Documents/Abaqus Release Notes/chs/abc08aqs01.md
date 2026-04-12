# 8.1 损伤起始的初始条件





**产品：** Abaqus/Standard  Abaqus/Explicit

**优势：** 现在可以直接在延性、剪切以及 Mschenborn 和 Sonne 成形极限图损伤起始准则的损伤起始测量上定义初始条件。

**说明：** 此功能在金属成形操作在一个分析中进行，然后是使成形的金属部件进一步变形的单独分析的情况下特别有用。第一个分析结束时的损伤起始测量可以直接指定为第二个分析的初始条件。建模损伤起始初始条件的替代但近似的方法是指定等效塑性应变的初始值。Abaqus 根据指定的初始等效塑性应变计算损伤起始测量值，假设初始（未变形）状态和最终（变形）状态之间的应变路径是线性的。这种近似方法在应变空间中显著偏离线性的变形路径时效果不佳。
**参考文献：**

**Abaqus Analysis User's Guide**
- ["Abaqus/Standard 和 Abaqus/Explicit 中的初始条件，" 第 34.2.1 节](../usb/usb-link.md#usb-prc-pinitialcond)

**Abaqus Keywords Reference Guide**
- [*INITIAL CONDITIONS](../key/key-link.md#usb-kws-minitialcond)

**Abaqus Verification Guide**
- ["延性金属的渐进损伤和失效，" 第 2.2.21 节](../ver/ver-link.md#ver-mat-damage)
