# 6.7 由状态变量控制的单元删除





**产品：** Abaqus/Standard

**优势：** 在 Abaqus/Standard 中，现在可以使用状态变量控制实体、壳、膜和梁单元的删除。删除的单元没有承载应力的能力，也不会对模型刚度做出贡献。它们也不接受单元质量检查，因此分析不会因这些单元的过度变形而终止。

**说明：** 在 Abaqus/Standard 中，现在可以类似于以前在 Abaqus/Explicit 中可用的功能，使用状态变量控制单元的删除。必须指定控制删除的状态变量的编号，并且对于每个材料可以不同。该状态变量存储单元删除标志，可以为零或一的值。值为一表示材料点是活跃的，而值为零表示材料点处于非活跃状态，该点的应力设置为零。一旦材料点被删除，它就不能被重新激活。删除标志可以通过在材料点调用的任何使用状态变量的 Abaqus/Standard 用户子程序进行修改。如果单元的所有材料点都变为非活跃的，则该单元被删除。可以通过请求输出变量 STATUS 来监控单元的状态。
**参考文献：**

**Abaqus Analysis User's Guide**
- ["用户子程序：概述，" 第 18.1.1 节](../usb/usb-link.md#usb-anl-asubroutineover)
- ["用户定义的机械材料行为，" 第 26.7.1 节](../usb/usb-link.md#usb-mat-cusermat)

**Abaqus Keywords Reference Guide**
- [*DEPVAR](../key/key-link.md#usb-kws-mdepvar)
