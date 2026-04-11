# Abaqus验证指南






这是Abaqus的验证指南。它包含大量作为这些程序基本验证的测试案例。每个测试案例验证代码中一个或多个明确定义的功能。这些测试案例足够小，在大多数情况下，可以手工计算正确的结果。

本指南根据所测试的功能类型分为章节。元素验证章节中的问题广泛测试了元素库。其他章节记录了材料、过程、用户子程序、杂项选项以及将结果从Abaqus/Explicit导入Abaqus/Standard的测试。

除了[Abaqus验证指南](book01.md)之外，还有其他两本包含算例的指南。[Abaqus基准指南](../bmk/bmk-link.md#bmk)包含基准问题（包括NAFEMS测试问题套件）和用于评估Abaqus性能的的标准分析。本指南中的测试是简单几何或实际问题简化版本的多元素测试。[Abaqus算例指南](../exa/exa-link.md#exa)包含许多已解算的示例，用于测试用户可能解决的类型的问题。这些问题中的许多都相当困难，并测试了代码中功能的组合。

新的Abaqus版本的认证过程包括运行和验证[Abaqus算例指南](../exa/exa-link.md#exa)、[Abaqus基准指南](../bmk/bmk-link.md#bmk)和Abaqus验证指南中所有问题的结果。

用户在进行分析之前，熟悉[Abaqus基准指南](../bmk/bmk-link.md#bmk)、[Abaqus算例指南](../exa/exa-link.md#exa)和Abaqus验证指南是非常重要的，以确定对其将使用的功能进行的验证级别。然后用户应该决定在开始分析之前是否需要进行任何额外的验证。

指南中提到的所有输入文件都随Abaqus版本包含在压缩档案文件中。使用**abaqus fetch**实用程序来提取这些输入文件以供使用。例如，要获取["单个无约束元素的特征值提取，"第1.2.1节](ch01s02abv01.md)的输入文件[ec12afe1.inp](../eif/ec12afe1.inp)，请键入

```
abaqus fetch job=ec12afe1.inp
```

参数化研究脚本（`.psf`）和用户子程序（`.f`）文件可以以相同的方式获取。通过省略文件扩展名可以获得特定问题的所有文件。**abaqus fetch**实用程序在["获取样本输入文件，"Abaqus分析用户指南第3.2.16节](../usb/usb-link.md#usb-int-dfetchproc)中有详细说明。

有时搜索输入文件是有用的。**findkeyword**实用程序用于定位包含用户指定输入的输入文件。该实用程序在["查询关键字/问题数据库，"Abaqus分析用户指南第3.2.15节](../usb/usb-link.md#usb-int-dkeywordproc)中定义。

