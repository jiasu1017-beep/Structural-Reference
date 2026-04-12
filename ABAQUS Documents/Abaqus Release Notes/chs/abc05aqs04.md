# 5.4 自适应网格细化增强





**产品：** Abaqus/Explicit

**优势：** 现在可以将自适应网格细化功能应用于欧拉截面中的元素子集。

**说明：** 此功能适用于细化区域占欧拉域的一小部分且在分析过程中变化不大的模型。当使用多个域运行作业时，此子集中的元素可以独立分解并分配给不同的处理器。使用这种方法可以大大改善处理器之间的负载平衡。对于细化区域在分析过程中变化的模型，可以通过动态负载平衡方案减少负载不平衡。
**参考文献：**

**Abaqus Analysis User's Guide**
- ["Abaqus/Explicit 中的并行执行，" 第 3.5.3 节](../usb/usb-link.md#usb-int-aparallelexecution)
- ["在欧拉域中定义自适应网格细化，" 第 14.1.4 节](../usb/usb-link.md#usb-anl-aeulerianadaptivemeshrefinement)

**Abaqus Keywords Reference Guide**
- [*ADAPTIVE MESH REFINEMENT](../key/key-link.md#usb-kws-hadaptivemeshrefinement)
- [*DOMAIN DECOMPOSITION](../key/key-link.md#usb-kws-mdomaindecomp)
