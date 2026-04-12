# 5.5 Abaqus/CAE 中基于 XFEM 的裂纹扩展功能增强





**产品：** Abaqus/CAE

**优势：** 在 Abaqus/CAE 中，您可以指定是使用单元质心处的应力/应变值、裂纹尖端处的应力/应变值，还是两者组合的位置来测量裂纹扩展准则，这提高了 Abaqus 产品功能的覆盖范围。

**说明：** Abaqus/CAE 现在支持裂纹尖端前方应力和应变场的局部计算选项。您可以指定使用单元质心处的应力/应变值、裂纹尖端处的应力/应变值，还是两者组合的位置来确定损伤起始准则是否满足，并确定裂纹扩展方向（如需要）。

**Abaqus/CAE 使用方法：**
```
Property 模块：
    材料编辑器：****Mechanical**![](../graphics/images/arrow.gif)**Damage for Traction Separation Laws****:
    **Quade Damage**, **Maxe Damage**, **Quads Damage**, **Maxs Damage**, **Maxpe Damage**,
    或 **Maxps Damage**：****Position**![](../graphics/images/arrow.gif)**Centroid****、**Crack tip** 或 **Combined**
```

**参考文献：**

**Abaqus/CAE User's Guide**
- ["定义损伤，" 第 12.9.3 节](../usi/usi-link.md#usi-prp-mechanical-damage)
