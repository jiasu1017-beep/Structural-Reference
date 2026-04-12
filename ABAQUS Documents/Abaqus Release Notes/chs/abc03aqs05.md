# 3.5 创建软单元的其他标准





**产品：** Abaqus/CAE

**优势：** 在拓扑优化期间，Abaqus 会创建软单元，这些单元对最终结构的刚度影响可以忽略不计，但对结构的自由度数量仍有影响。当您优化非线性模型时，建议选择删除软单元，因为这些单元否则会退化或坍塌，并阻止 Abaqus 收敛到解决方案。新增了定义单元何时被视为软单元的其他标准。

**描述：** 当您创建拓扑优化任务时，可以指定创建软单元的标准。其他标准包括：
- 最大剪切应变
- 最小主应变
- 最大弹塑性应变
- 体积压缩

此外，如果您选择标准或激进标准，可以通过选择仅删除有相邻软单元的软单元来防止孤立软单元被删除。

**Abaqus/CAE 使用：**
```
优化模块：
    ****Task**![](../graphics/images/arrow.gif)**Create****，**Name：** *任务名称*，**Type：** **Topology optimization**，**Advanced**
```

**参考：**

**Abaqus/CAE User's Guide**
- [“Configuring advanced options” in “Configuring a topology optimization task，” Section 18.6.2](../usi/usi-link.md#usi-opz-topo-taskconfigure-general-advanced)




