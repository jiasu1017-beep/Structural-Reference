# 绪论





这是 Abaqus 的示例问题指南。它包含许多已解决的示例，展示了该程序在常见问题类型中的应用。其中一些问题相当困难，需要结合代码中的多种功能。

选择这些问题有两个目的：通过在非平凡案例中运行代码来验证 Abaqus 中的功能，并为必须处理相对不熟悉的问题类别的用户提供指导。在每个工作示例中，指南中的讨论说明了包含该示例的原因，并引导读者完成分析的标准方法：单元和网格选择、材料模型以及结果讨论。许多问题使用不同的单元类型、网格密度和其他变体进行处理。

所有分析的输入数据文件都随 Abaqus 版本一起提供在压缩档案文件中。使用 **abaqus fetch** 实用程序来提取这些输入文件以供使用。例如，要获取输入文件 [boltpipeflange_3d_cyclsym.inp](../eif/boltpipeflange_3d_cyclsym.inp)，请键入

```
abaqus fetch job=boltpipeflange_3d_cyclsym.inp
```

参数化研究脚本（`.psf`）和用户子程序（`.f`）文件可以相同的方式获取。通过省略文件扩展名，可以获取特定问题的所有文件。**abaqus fetch** 实用程序在["获取示例输入文件，"《Abaqus 分析用户指南》第 3.2.16 节](../usb/usb-link.md#usb-int-dfetchproc)中有详细说明。

有时搜索输入文件会很有用。**findkeyword** 实用程序用于定位包含用户指定输入的输入文件。该实用程序在["查询关键字/问题数据库"，《Abaqus 分析用户指南》第 3.2.15 节](../usb/usb-link.md#usb-int-dkeywordproc)中定义。

要重现某些示例中报告的解决方案的图形表示，可能需要提高输入文件中使用的输出频率。例如，在["Indian Point 反应堆给水管线的线性分析，"第 2.2.2 节"](ch02s02aex81.md) 中，只有在每个增量将解决方案写入结果文件时，才能获得指南中出现的图形；也就是说，如果将输入文件更改为读取

```
*NODE FILE, ..., FREQUENCY=1
```

而不是现在显示的 `FREQUENCY=100`。

除了 Abaqus 示例问题指南外，还有其他两个包含工作问题的指南。[Abaqus 基准指南](../bmk/bmk-link.md#bmk) 包含基准问题（包括 NAFEMS 测试问题套件）和用于评估 Abaqus 性能的标准分析。本指南中的测试是简单几何或实际问题简化版本的多单元测试。[Abaqus 验证指南](../ver/ver-link.md#ver) 包含大量示例，旨在作为基本建模功能的初步验证。

新 Abaqus 版本的认证过程包括运行和验证[《Abaqus 示例问题指南》](book01.md)、[《Abaqus 基准指南》](../bmk/bmk-link.md#bmk)和[《Abaqus 验证指南》](../ver/ver-link.md#ver)中所有问题的结果。




