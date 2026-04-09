# 1.1.1 引言：概述

### 1.1.1 引言：概述

Abaqus有限元系统包括：

Abaqus/Standard，一个通用有限元程序；

Abaqus/Explicit，一个显式动力学有限元程序；

Abaqus/CAE，一个交互式环境，用于创建有限元模型、提交Abaqus分析、监控和诊断作业以及评估结果；以及

Abaqus/Viewer，Abaqus/CAE的一个子集，仅包含可视化模块的后处理功能。如果您的许可证包含某些附加选项，则可以使用它们进一步扩展Abaqus/Standard和Abaqus/Explicit的功能。

Abaqus/Aqua选项与Abaqus/Standard和Abaqus/Explicit配合使用。Abaqus/Aqua包含专门为分析水下安装的梁状结构而设计的可选功能，这些结构承受水流和波浪荷载作用。

Abaqus/Design选项使您能够执行设计灵敏度分析（DSA）。Abaqus/Design选项与Abaqus/Standard配合使用。

Abaqus/AMS是一个可选的特征值求解器，在Abaqus/Standard内运行，可快速求解大型对称特征值问题。

Abaqus协同仿真技术提供两个应用，作为独立的附加功能可用于Abaqus与第三方分析程序之间的耦合。

Abaqus/Foundation是Abaqus/Standard的一个可选子集，以更高的成本效益提供Abaqus/Standard中的线性静力和动力分析功能。

本指南描述了Abaqus中使用的理论。本指南中的许多章节适用于Abaqus/Standard和Abaqus/Explicit。某些章节显然仅适用于Abaqus/Standard或Abaqus/Explicit；例如，过程章节中的所有章节都适用于Abaqus/Standard，只有讨论显式动力学积分过程的章节适用于Abaqus/Explicit。如果某个章节适用于哪个程序不明显，则会清楚标明。

本指南的目的是定义Abaqus中使用的理论，这些理论通常在力学、结构和有限元的标准教科书中没有，但使用Abaqus的工程师却非常熟悉。本指南旨在作为定义代码中可用内容的参考文档。不过，它的编写方式也可以作为教程文档使用，需要在陌生领域获得一些背景知识的读者可以使用。材料的呈现方式应该使任何具有工程背景的用户都能理解。其中一些理论可能对这样的用户相对陌生；例如，很少有工程课程提供关于塑性、壳理论、固体大变形或多孔介质分析的广泛背景。然而，Abaqus包含所有这些模型和许多其他模型的功能。本指南在这些主题的覆盖面上远非全面：从这个意义上说，它只是一本参考卷。强烈建议用户通过文本和论文深入研究感兴趣的主题。本指南末尾的第7章"参考文献"列出了应提供获取此类信息起点的参考文献。（Abaqus不提供除Abaqus出版物以外的其他出版物上发表的论文副本。EPRI报告可从Research Reports Center (RRC)，Box 50490，Palo Alto，CA 94303获取。）

第1章"引言与基本方程"讨论了本指南中使用的符号表示，以及运动学和力学的一些基本概念——如旋转、应力和平衡——以及非线性有限元分析的基本方程。第2章"过程"描述了Abaqus中可用的各种分析过程（非线性静力应力分析、动力学、特征值提取等）。第3章"单元"描述了单元公式。第4章"机械本构理论"描述了机械本构理论。

第5章"界面建模"讨论了Abaqus/Standard中接触/相互作用公式的最重要方面。第6章"荷载与约束"描述了一些更复杂荷载类型和多点约束的公式。