# 简介










这是 Abaqus 的验证指南。它包含大量测试用例，作为这些程序的基本验证。每个测试用例验证代码中的一个或多个明确定义的选项。这些测试用例足够小，在大多数情况下，可以手工计算正确结果。

本指南按被测试的功能类型分章节。单元验证章节中的问题广泛测试了单元库。其他章节记录了材料、过程、用户子程序、杂项选项以及从 Abaqus/Explicit 导入结果到 Abaqus/Standard 的测试。

除了 [Abaqus 验证指南](book01.md) 之外，还有另外两本包含工程问题的指南。[Abaqus 基准指南](../bmk/bmk-link.md#bmk) 包含基准问题（包括 NAFEMS 测试问题套件）和用于评估 Abaqus 性能的标准分析。本指南中的测试是简单几何或简化实际问题的多单元测试。[Abaqus 例题指南](../exa/exa-link.md#exa) 包含许多已解算的示例，这些示例用用户可能解决的问题类型测试代码。许多这些问题相当困难，测试了代码中功能的组合。

新 Abaqus 版本的认证过程包括运行和验证 [Abaqus 例题指南](../exa/exa-link.md#exa)、[Abaqus 基准指南](../bmk/bmk-link.md#bmk) 和 Abaqus 验证指南中所有问题的结果。

用户在进行任何分析之前，熟悉 [Abaqus 基准指南](../bmk/bmk-link.md#bmk)、[Abaqus 例题指南](../exa/exa-link.md#exa) 和 Abaqus 验证指南是非常重要的。以确定已完成的针对将使用的功能的验证级别。然后用户应该决定在开始分析之前是否需要任何额外的验证。

指南中引用的所有输入文件都随 Abaqus 版本一起提供在压缩档案文件中。**abaqus fetch** 实用程序用于提取这些输入文件以供使用。例如，要获取 ["单无约束单元的特征值提取，" 1.2.1 节](ch01s02abv01.md) 的输入文件 [ec12afe1.inp](../eif/ec12afe1.inp)，请键入

```
abaqus fetch job=ec12afe1.inp
```

参数化研究脚本（`.psf`）和用户子程序（`.f`）文件可以以相同的方式获取。可以通过省略文件扩展名来获取特定问题的所有文件。**abaqus fetch** 实用程序在 ["获取样本输入文件，" Abaqus 分析用户指南 3.2.16 节](../usb/usb-link.md#usb-int-dfetchproc) 中有详细说明。

有时搜索输入文件很有用。**findkeyword** 实用程序用于定位包含用户指定输入的输入文件。该实用程序在 ["查询关键字/问题数据库，" Abaqus 分析用户指南 3.2.15 节](../usb/usb-link.md#usb-int-dkeywordproc) 中定义。




