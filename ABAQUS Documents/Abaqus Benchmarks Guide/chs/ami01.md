# 简介

这是 Abaqus 的基准测试指南。它包含了用于评估 Abaqus 性能的基准问题（包括 NAFEMS 测试问题套件）和标准分析。本指南中的测试是对简单几何形状或实际问题简化版本的多单元测试。

除基准测试指南外，还有另外两本包含已解问题的指南。[Abaqus 例题指南](../exa/exa-link.md#exa) 包含许多已解示例，用于测试用户可能解决的各种问题。其中许多问题相当困难，测试了代码的多种功能组合。[Abaqus 验证指南](../ver/ver-link.md#ver) 包含大量示例，旨在对 Abaqus 中的基本建模功能进行初步验证。

新 Abaqus 版本的认证过程包括运行并验证 [Abaqus 例题指南](../exa/exa-link.md#exa)、[Abaqus 基准测试指南](book01.md) 和 [Abaqus 验证指南](../ver/ver-link.md#ver) 中所有问题的结果。

指南中引用的所有输入文件都随 Abaqus 版本一起提供在压缩归档文件中。使用 **abaqus fetch** 工具来提取这些输入文件以供使用。例如，要获取输入文件 [barrelvault_s8r5_reg22.inp](../eif/barrelvault_s8r5_reg22.inp)，请键入

```
abaqus fetch job=barrelvault_s8r5_reg22.inp
```

参数化研究脚本（`.psf`）和用户子程序（`.f`）文件可以采用相同的方式获取。通过省略文件扩展名可以获取特定问题的所有文件。**abaqus fetch** 工具的详细说明见《Abaqus 分析用户指南》第 3.2.16 节 ["获取样本输入文件"](../usb/usb-link.md#usb-int-dfetchproc)。

有时搜索输入文件会很有用。**findkeyword** 工具用于定位包含用户指定输入的输入文件。该工具的定义见《Abaqus 分析用户指南》第 3.2.15 节 ["查询关键字/问题数据库"](../usb/usb-link.md#usb-int-dkeywordproc)。
