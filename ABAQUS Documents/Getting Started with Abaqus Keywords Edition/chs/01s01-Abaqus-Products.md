# 1.1 Abaqus产品

Abaqus由三个主要分析产品组成——Abaqus/Standard、Abaqus/Explicit和Abaqus/CFD。多种附加分析选项可用于进一步扩展Abaqus/Standard和Abaqus/Explicit的功能。Abaqus/Aqua选项可与Abaqus/Standard和Abaqus/Explicit配合使用。Abaqus/Design和Abaqus/AMS选项适用于Abaqus/Standard。Abaqus/Foundation是Abaqus/Standard的可选子集。Abaqus/CAE是完整的Abaqus环境，包括创建Abaqus模型、交互式提交和监控Abaqus作业以及评估结果的功能。Abaqus/Viewer是Abaqus/CAE的子集，仅包含后处理功能。Abaqus还提供转换器，可将几何信息从第三方CAD系统转换为Abaqus/CAE模型，将实体从第三方前处理器转换为Abaqus分析输入，并将Abaqus分析输出转换为第三方后处理器实体。这些产品之间的关系如图1-1所示。

**图1-1** Abaqus产品。

![../graphics/gss-abaqus-mod-v-nls.png](../graphics/gss-abaqus-mod-v-nls.png)

**Abaqus/Standard**

Abaqus/Standard是一种通用分析产品，可解决涉及组件静态、动态、热、电和电磁响应的各种线性和非线性问题。本指南详细讨论了此产品。Abaqus/Standard在每个求解"增量"时隐式求解方程组。相比之下，Abaqus/Explicit通过小的时间增量将解向前推进，而无需在每个增量处求解耦合方程组（甚至不形成全局刚度矩阵）。

**Abaqus/Explicit**

Abaqus/Explicit是一种专用分析产品，使用显式动态有限元公式。它适用于模拟短暂瞬态动力学事件，如碰撞和爆炸问题，同时在处理接触条件高度非线性的问题（如成形模拟）时也非常高效。本指南详细讨论了Abaqus/Explicit。

**Abaqus/CFD**

Abaqus/CFD是一种计算流体动力学分析产品。它可以解决各类不可压缩流动问题，包括层流和湍流、热对流流动以及变形网格问题。本指南讨论了Abaqus/CFD。

**Abaqus/CAE**

Abaqus/CAE（完整Abaqus环境）是Abaqus的交互式图形环境。它允许通过生成或导入待分析结构的几何体并将几何体分解为可网格化的区域来快速轻松地创建模型。可以为几何体分配物理和材料属性，以及载荷和边界条件。Abaqus/CAE包含非常强大的网格划分选项，用于网格化几何体并验证生成的有限元分析模型。模型完成后，Abaqus/CAE可以提交、监控和控制分析作业。然后可以使用可视化模块来解释结果。

Abaqus/Viewer是Abaqus/CAE的子集，仅包含可视化模块的后处理功能，本指南对此进行了讨论。本指南不讨论其他Abaqus/CAE模块。

**Abaqus/Aqua**

Abaqus/Aqua是可添加到Abaqus/Standard和Abaqus/Explicit的一系列可选功能。它用于模拟海洋结构物（如石油平台）。一些可选功能包括波载荷和风载荷效应以及浮力。本指南不讨论Abaqus/Aqua。

**Abaqus/Design**

Abaqus/Design是可添加到Abaqus/Standard以执行设计灵敏度计算的一系列可选功能。本指南不讨论Abaqus/Design。

**Abaqus/AMS**

Abaqus/AMS是可添加到Abaqus/Standard的可选功能。它在自然频率提取过程中使用自动多级子结构（AMS）特征值求解器。本指南不讨论Abaqus/AMS。

**Abaqus/Foundation**

Abaqus/Foundation提供了更高效地访问Abaqus/Standard中线性静态和动态分析功能的方法。本指南不讨论Abaqus/Foundation。

**几何转换器**

Abaqus提供以下转换器，用于将几何信息从第三方CAD系统转换为Abaqus/CAE的零件和装配体：

- SIMULIA Associative Interface for Abaqus/CAE在CATIA V6和Abaqus/CAE之间建立链接，允许您传输模型数据并将设计变更从CATIA V6传播到Abaqus/CAE。
- CATIA V5 Associative Interface在CATIA V5和Abaqus/CAE之间建立链接，允许您传输模型数据并将设计变更从CATIA V5传播到Abaqus/CAE。
- SolidWorks Associative Interface在SolidWorks和Abaqus/CAE之间建立链接，允许您传输模型数据并将设计变更从SolidWorks传播到Abaqus/CAE。
- Pro/ENGINEER Associative Interface在Pro/ENGINEER和Abaqus/CAE之间建立链接，允许您传输模型数据并在Pro/ENGINEER和Abaqus/CAE之间传播设计变更。
- Geometry Translator for CATIA V4允许您将CATIA V4格式零件和装配体的几何体直接导入Abaqus/CAE。
- Geometry Translator for Parasolid允许您将Parasolid格式零件和装配体的几何体直接导入Abaqus/CAE。

此外，Abaqus/CAE Associative Interface for NX在NX和Abaqus/CAE之间建立链接，允许您在NX和Abaqus/CAE之间传输模型数据并传播设计变更。Abaqus/CAE Associative Interface for NX可以从Elysium Inc.（www.elysiuminc.com）购买和下载。

本指南不讨论几何转换器。

**转换器工具**

Abaqus提供以下转换器，用于将实体从第三方前处理器转换为Abaqus分析输入，或将Abaqus分析输出转换为第三方后处理器实体：

- **`abaqus fromansys`** 将ANSYS输入文件转换为Abaqus输入文件。
- **`abaqus fromdyna`** 将LS-DYNA关键字文件转换为Abaqus输入文件。
- **`abaqus fromnastran`** 将Nastran bulk data文件转换为Abaqus输入文件。
- **`abaqus frompamcrash`** 将PAM-CRASH输入文件转换为Abaqus输入文件。
- **`abaqus fromradioss`** 将RADIOSS输入文件转换为Abaqus输入文件。
- **`abaqus adams`** 将Abaqus SIM数据库文件中的结果转换为MSC.ADAMS modal neutral（`.mnf`）文件，这是ADAMS/Flex所需的格式。
- **`abaqus moldflow`** 将Moldflow分析的有限元模型信息转换为部分Abaqus输入文件。
- **`abaqus tonastran`** 将Abaqus输入文件转换为Nastran bulk data文件格式。
- **`abaqus toOutput2`** 将Abaqus输出数据库文件转换为Nastran Output2文件格式。
- **`abaqus tozaero`** 实现Abaqus和ZAERO之间的气动弹性数据交换。

本指南不讨论转换器工具。
