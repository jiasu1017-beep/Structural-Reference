# 4.6 柔性体生成





**产品：** Abaqus/Standard

**优势：** 现在，您可以从子结构生成柔性体。在柔性体动态模拟中，此功能可以消除存储完整子结构恢复矩阵的需要，该矩阵通常非常大，从而提高性能并减小子结构 `.sim` 文件的大小。

**描述：** Abaqus/Standard 可以从子结构生成柔性体。生成的柔性体可用于使用外部求解器的柔性体动态模拟。Abaqus/Standard 支持生成多种可由外部柔性体动力学求解器使用的柔性体类型。生成的柔性体实体存储在子结构 `.sim` 文件中，可由后处理程序转换为 conventional 柔性体表示。

**参考：**

**Abaqus Analysis User's Guide**
- [“Defining substructures，” Section 10.1.2](../usb/usb-link.md#usb-anl-asuperelementdef)

**Abaqus Keywords Reference Guide**
- [*FLEXIBLE BODY](../key/key-link.md#usb-kws-hflexiblebody)
- [*SUBSTRUCTURE GENERATE](../key/key-link.md#usb-kws-ssubgenerate)




