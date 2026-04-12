# I







### IGES（Initial Graphics Exchange Specification）file

为计算机辅助设计（CAD）系统之间的图形交换而设计的中立数据格式。使用 Abaqus/CAE，您可以导入 IGES 格式的零件，也可以导出 IGES 格式的零件。此外，您还可以从 IGES 文件导入和导出草图。
更多信息：- [第 10 章，「导入和导出几何数据及模型，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-imp)

### increment

分析步骤的时间间隔。
更多信息：- [「定义分析，」Abaqus Analysis User's Guide 第 6.1.2 节](../usb/usb-link.md#usb-anl-aover)

- [「指定模型属性，」Abaqus/CAE User's Guide 第 9.8.4 节](../usi/usi-link.md#usi-dbs-editmodel)

### initial condition

您预设的条件，用于定义求解、状态或场变量（如应力或温度）的初始值。您可以通过在 Load 模块中创建预定义场来定义初始条件。
更多信息：- [「Abaqus/Standard 和 Abaqus/Explicit 中的初始条件，」Abaqus Analysis User's Guide 第 34.2.1 节](../usb/usb-link.md#usb-prc-pinitialcond)

- [「Abaqus/CFD 中的初始条件，」Abaqus Analysis User's Guide 第 34.2.2 节](../usb/usb-link.md#usb-prc-pinitialcondcfd)

- [「创建和修改预设条件，」Abaqus/CAE User's Guide 第 16.4 节](../usi/usi-link.md#usi-lbi-edit-editors)

### input file

由 Abaqus/Standard、Abaqus/Explicit 或 Abaqus/CFD 读取和处理的 ASCII 文件，包含定义模型的关键字和数据。当您使用 Abaqus/CAE 提交分析作业时，它会根据您定义的模型生成输入文件。如有必要，您可以使用 Keywords Editor 修改 Abaqus/CAE 生成的输入文件。此外，您可以将 Abaqus/Standard 或 Abaqus/Explicit 输入文件导入 Abaqus/CAE；Abaqus/CAE 将导入输入文件中的选项和数据行转换为新的 Abaqus/CAE 模型。
更多信息：- [「在 Abaqus 中定义模型，」Abaqus Analysis User's Guide 第 1.3.1 节](../usb/usb-link.md#usb-int-imodel)

- [「了解创建和分析模型时生成的文件，」Abaqus/CAE User's Guide 第 9.4 节](../usi/usi-link.md#usi-dbs-conc-filesgenerated)

- [「从 Abaqus 输入文件导入模型，」Abaqus/CAE User's Guide 第 10.5.2 节](../usi/usi-link.md#usi-imp-inputfiles)

### input parameter

Abaqus/Design 中的一项功能，允许您创建使用参数代替输入量的输入文件。参数根据其定义进行评估，并在 Abaqus/Standard 或 Abaqus/Explicit 执行分析之前替换参数化量。另请参阅 [keyword parameter](gl01gls12.md#gls-keywordparam)，了解关键字参数在 Abaqus 输入文件中的使用方法。
更多信息：- [「编写参数研究脚本，」Abaqus Analysis User's Guide 第 20.1.1 节](../usb/usb-link.md#usb-scr-pscriptparstudies)

### instance

请参阅 [part instance](gl01gls17.md#gls-partinstance)。

### interaction

定义模型中物体或区域如何彼此相互作用或与其周围环境相互作用的与步骤相关的对象；示例包括接触、与机械连接器关联的运动关系以及热约束（如对流或辐射边界条件）。相互作用还建立场之间的依赖关系，如耦合热-机械、耦合孔隙流体-机械和耦合热-电效应。在 Abaqus/CAE 中，弹性基础也被视为一种相互作用形式。
更多信息：- [第九部分，「Interactions，」Abaqus Analysis User's Guide](../usb/usb-link.md#usbcontactchapter)

- [第 15 章，「The Interaction module，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-itn)

### Interaction module

Abaqus/CAE 模块，用于定义模型区域之间或模型区域与其周围环境之间的 [interactions](gl01gls10.md#gls-interaction)。
更多信息：- [第 15 章，「The Interaction module，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-itn)

### interaction property

完全定义某些类型相互作用所必需的数据集合。
更多信息：- [「接触相互作用分析：概述，」Abaqus Analysis User's Guide 第 36.1.1 节](../usb/usb-link.md#usb-cni-acontactoverview)

- [第 15 章，「The Interaction module，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-itn)



