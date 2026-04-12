# 3.1 尺寸优化





**产品：** Abaqus/CAE

**优势：** 现在，您可以创建通过修改壳单元厚度来优化壳模型的尺寸优化。

**描述：** 除了拓扑优化和形状优化之外，现在您还可以创建尺寸优化。尺寸优化应用于壳零件，优化设计区域中壳单元的厚度。当您配置尺寸优化时，可以指定所选区域应包含相同厚度的壳单元“簇”。您可以使用聚类在正在优化的金属板结构中生成加强肋或环，或定义等厚度区域之间的边界。聚类区域可以通过恒定厚度的板材在制造中再现；例如，通过焊接和冲压单个金属板结构形成的汽车“白车身”。

当您查看尺寸优化的结果时，默认情况下，Visualization 模块显示壳单元的厚度。

**Abaqus/CAE 使用：**
```
优化模块：
    ****Task**![](../graphics/images/arrow.gif)**Create****，**Name：** *优化任务名称*，**Type：** **Sizing optimization**
```

**参考：**

**Abaqus/CAE User's Guide**
- [“Creating an optimization task，” Section 18.6.1](../usi/usi-link.md#usi-opz-topo-taskeditor)
- [“Configuring a sizing optimization task，” Section 18.6.4](../usi/usi-link.md#usi-opz-sizing-taskconfigure)

**Abaqus Example Problems Guide**
- [“Sizing optimization of a gear shift control holder，” Section 11.3.1](../exa/exa-link.md#exa-opt-gearshift)
- [“Sizing optimization of a car door，” Section 11.3.2](../exa/exa-link.md#exa-opt-cardoorsizing)




