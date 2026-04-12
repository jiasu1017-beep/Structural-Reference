# 5.2 基于 XFEM 的裂纹扩展功能增强





**产品：** Abaqus/Standard

**优势：** 扩展有限元法（XFEM）允许您在分析过程中沿任意的、依赖于解的路径建模不连续性（如裂纹）。该方法现在可以扩展到包含孔隙压力自由度，以考虑孔隙压力的不连续性以及裂纹单元表面内的流体流动。该功能对于准确评估油气行业的水力压裂过程以及生命科学和消费品行业的流体流动非常有用。为了提高精度，现在可以使用非局部平均应力场和应变场来确定损伤起始准则是否满足，并确定裂纹扩展方向。此外，还支持在裂纹单元表面输出某些量的结果。

**说明：** XFEM 允许您在不重新网格化裂纹表面的情况下建模裂纹增长，因为它不要求网格与裂纹的几何形状相匹配。基于 XFEM 的内聚段方法已扩展用于建模水力驱动断裂。在这种情况下，引入具有孔隙压力自由度的额外虚节点来模拟裂纹单元表面内的流体流动，并表示裂纹单元中位移和流体压力的不连续性。流体流动连续性包括裂纹单元表面内部和跨表面的切向和法向流动以及裂纹单元表面的张开速率。裂纹单元表面上的流体压力有助于内聚段在富集单元中的牵引-分离行为，从而实现水力驱动断裂的建模。

在之前的版本中，您可以使用裂纹尖端前方单元的局部应力和应变场来确定裂纹扩展以及断裂准则是否满足。对于粗网格和/或非结构化网格的情况，裂纹尖端前方应力和应变场的非局部平均可以对这些场进行更准确的评估，从而可以提高计算扩展方向的精度。

现在您可以在裂纹单元表面上输出和可视化某些表面变量。
**参考文献：**

**Abaqus Analysis User's Guide**
- ["使用扩展有限元方法将不连续性建模为富集特征，" 第 10.7.1 节](../usb/usb-link.md#usb-anl-aenrichment)
- ["Abaqus/Standard 和 Abaqus/Explicit 中的边界条件，" 第 34.3.1 节](../usb/usb-link.md#usb-prc-pboundary)
- ["孔隙流体流动，" 第 34.4.7 节](../usb/usb-link.md#usb-prc-pporousflow)

**Abaqus Keywords Reference Guide**
- [*BOUNDARY](../key/key-link.md#usb-kws-hboundary)
- [*CFLOW](../key/key-link.md#usb-kws-hcflow)
- [*CONTACT OUTPUT](../key/key-link.md#usb-kws-hcontactoutput)
- [*DAMAGE INITIATION](../key/key-link.md#usb-kws-mdamageinitiation)
- [*ENRICHMENT](../key/key-link.md#usb-kws-menrichment)

**Abaqus Benchmarks Guide**
- ["使用 XFEM 进行水力驱动断裂的扩展，" 第 1.19.5 节](../bmk/bmk-link.md#bmk-anl-xfemhydrfract)
