# 4.5 矩阵质量检查





**产品：** Abaqus/Standard

**优势：** 现在，您可以在矩阵生成或子结构生成分析中检查生成的刚度矩阵和质量矩阵的质量。

**描述：** 您可以在矩阵生成或子结构生成过程中请求对生成的刚度矩阵和质量矩阵进行“刚体模式”检查。在矩阵生成过程中检查生成的全局组装矩阵的质量。在子结构生成过程中检查生成的凝聚子结构矩阵的质量。矩阵检查生成六个“人工”刚体模式，并将矩阵投影到刚体模式子空间上。预期在不存在边界条件约束的情况下，投影的 6 ![](../graphics/rnb_eqn00002.gif) 6 刚度矩阵（也称为刚体能量矩阵）接近于零。为了执行刚度矩阵质量检查，可以在矩阵生成过程中抑制边界条件和多点约束。从投影的 6 ![](../graphics/rnb_eqn00002.gif) 6 刚体质量矩阵中提取模型的总体惯性统计信息。您可以指定旋转中心以创建人工旋转刚体模式并计算全局惯性张量。如果请求了矩阵质量检查，检查结果将打印在数据（`.dat`）文件中。

**参考：**

**Abaqus Analysis User's Guide**
- [“Defining substructures，” Section 10.1.2](../usb/usb-link.md#usb-anl-asuperelementdef)
- [“Generating matrices，” Section 10.3.1](../usb/usb-link.md#usb-anl-amtxgenerationperturbation)

**Abaqus Keywords Reference Guide**
- [*MATRIX CHECK](../key/key-link.md#usb-kws-hmatrixcheck)
- [*MATRIX GENERATE](../key/key-link.md#usb-kws-hmatrixgenerate)
- [*SUBSTRUCTURE GENERATE](../key/key-link.md#usb-kws-ssubgenerate)




