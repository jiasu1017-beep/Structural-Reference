# 12.1 将 Abaqus 分析结果写入 SIM 数据库







**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**优点：**您现在可以将结果写入 SIM 数据库（`.sim`）文件，这允许您将 Abaqus 分析的结果导入到 3DEXPERIENCE 平台上的 Physics Results Explorer 应用程序中进行高性能后处理。

**说明：**新的 SIM 数据库（`*job-name*.sim`）是用于在 3DEXPERIENCE 平台应用程序和隐式及显式求解器等计算密集型组件之间交换大型 FEA 数据的文件格式。例如，Physics Results Explorer 应用程序使用 SIM 数据库进行分析结果的高性能后处理。

Abaqus 输出数据库现在有两种格式：ODB 和 SIM。默认情况下，结果输出以 ODB 格式创建。只有 SIM 格式的结果才能导入到 3DEXPERIENCE 平台进行高性能后处理。对于 Abaqus/Standard 和 Abaqus/Explicit 分析，新的 **resultsformat** 命令行选项提供对 Abaqus 结果输出格式的控制，包括以两种格式写入结果。对于 Abaqus/CFD 分析，您使用 **field** 和 **history** 命令行选项以 SIM 格式写入结果。

输出格式的选择取决于您对高性能可视化、Physics Results Explorer 应用程序和后处理需求的体验程度。
- 如果您仍在学习使用高性能可视化并想将结果与 Abaqus/Viewer 进行比较，请以两种格式写入结果。
- 如果模型很大，您需要 Physics Results Explorer 应用程序的改进性能以及 Abaqus/Viewer 的功能，请以两种格式写入结果。
- 如果您确信 Physics Results Explorer 应用程序中的高性能可视化功能提供了您需要的所有功能，请以 SIM 格式写入结果。

Abaqus/Standard 和 Abaqus/Explicit 中的选项子集不支持生成 SIM 格式结果的分析；Abaqus/CFD 对 SIM 格式的输出没有限制。如果您在分析中包含这些选项或参数中的一个或多个，并以 SIM 格式或两种格式写入结果，分析将终止并出错或产生有限的结果。有关更多信息，请参阅《Abaqus Analysis User's Guide》中["Output," Section 4.1.1](../usb/usb-link.md#usb-out-ooutput-sim-limitations) 中的 ["Limitations when writing results in SIM format"](../usb/usb-link.md#usb)。

**Abaqus/CAE 使用方法：**
```
Job 模块:
    ****Job**![](../graphics/images/arrow.gif)**Edit****: **General** 选项卡页面: **Results Format**: **ODB**、**SIM** 或 **Both**（仅适用于 Abaqus/Standard 和 Abaqus/Explicit）
```

**参考：**

**Abaqus Analysis User's Guide**
- ["Abaqus/Standard, Abaqus/Explicit, and Abaqus/CFD execution," Section 3.2.2](../usb/usb-link.md#usb-int-danalysisproc)
- ["Output," Section 4.1.1](../usb/usb-link.md#usb-out-ooutput)

**Abaqus/CAE User's Guide**
- ["The job editor," Section 19.2.4](../usi/usi-link.md#usi-ana-conc-unjobset)

