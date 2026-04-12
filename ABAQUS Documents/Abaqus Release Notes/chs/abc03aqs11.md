# 3.11 使用 CATIA V6 Associative Interface 进行参数的双向导入





**产品：** Abaqus/CAE

**优势：** 使用 CATIA V6 Associative Interface 导入模型后，您可以修改模型中的几何参数。Abaqus/CAE 模型和原始 CATIA V6 模型都会根据修改后的参数进行更新，这允许您在迭代设计时保持 Abaqus/CAE 和 CATIA V6 模型同步。

**描述：** CATIA V6 Associative Interface 的参数更新功能允许您在从 CATIA V6 导入模型后专门在 Abaqus/CAE 中工作，同时保持原始 CATIA V6 模型与任何几何变更同步。某些几何参数可以在 Abaqus/CAE 中修改，然后这些修改会传播到原始 CATIA V6 模型（此功能以前仅适用于 CATIA V5 和 Pro/ENGINEER 模型）。

要使用双向导入，您必须首先在 CATIA V6 模型中指定将导入到 Abaqus/CAE 的参数及其值。这些参数用于定义 CATIA V6 模型中的尺寸；例如，参数可用于指定孔特征的半径。当您使用 CATIA V6 Associative Interface 将模型导入 Abaqus/CAE 时，指定的参数列表也会导入。您使用 Abaqus/CAE 中的 **CAD Parameters** 对话框修改每个参数的值。当您单击 **Update** 时，与修改后的尺寸关联的特征会重新生成，并且模型的几何体会在 Abaqus/CAE 和 CATIA V6 模型中更新。

有关使用双向导入的详细说明，请从 Dassault Systèmes 知识库（[www.3ds.com/support/knowledge-base](http://www.3ds.com/support/knowledge-base)）下载 CATIA V6 Associative Interface User's Guide。

**Abaqus/CAE 使用：**
```
零件模块：
    ****Tools**![](../graphics/images/arrow.gif)**CAD Parameters****。
装配模块：
    ****Tools**![](../graphics/images/arrow.gif)**CAD Interfaces**![](../graphics/images/arrow.gif)**CAD Parameters****。
```

**参考：**

**Abaqus/CAE User's Guide**
- [“Updating geometry parameters in an imported model，” Section 60.2](../usi/usi-link.md#usi-cad-bidirectional)




