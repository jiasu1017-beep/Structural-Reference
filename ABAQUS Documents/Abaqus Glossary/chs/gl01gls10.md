# P







### parameter

限制或赋予其所表征事物特定形式的变量数量。在 Abaqus/CAE 中，parameter 是定义特征的参数（如拉伸长度）。它也用于术语 [edge parameter](gl01gls06.md#gls-edgeparameter) 中，描述沿边的位置，表示为长度的一部分。另请参阅 [keyword parameter](gl01gls12.md#gls-keywordparam)，了解参数在 Abaqus 输入文件中的使用方法，以及 [input parameter](gl01gls10.md#gls-inputparam)，了解它们在 Abaqus/Design 中的使用方法。
更多信息：- [「输入语法规则，」Abaqus Analysis User's Guide 第 1.2.1 节](../usb/usb-link.md#usb-int-iinputsyntax)

- [第 65 章，「The Feature Manipulation toolset，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-fts)

### Parasolid

由 Unigraphics 开发的实体建模系统。您可以导入由 Parasolid Version 7 到 Version 13 生成的 Parasolid 格式零件。您不能以 Parasolid 格式导出零件。
更多信息：- [「可以从 Abaqus/CAE 导入和导出哪些类型的文件？，」Abaqus/CAE User's Guide 第 10.1.1 节](../usi/usi-link.md#usi-imp-concepts-whatkind)

- [「导入零件，」Abaqus/CAE User's Guide 第 10.7.2 节](../usi/usi-link.md#usi-dbs-import-part)

### parent feature

请参阅 [child feature](gl01gls04.md#gls-childfeature)。

### part

Abaqus/CAE 模型的几何构建块。您可以将零件实例组装起来创建装配，然后对其进行网格划分和分析。
更多信息：- [「定义装配，」Abaqus Analysis User's Guide 第 2.10.1 节](../usb/usb-link.md#usb-int-ipartassy)

- [「了解 Part 模块的作用，」Abaqus/CAE User's Guide 第 11.1 节](../usi/usi-link.md#usi-prt-intro)

### part instance

原始 Abaqus/CAE 零件的可重用副本，只是实例还保持与原始零件的关联；如果您修改零件，零件实例也会同时被修改。组装模型时，您使用零件实例，而不是原始零件。
更多信息：- [「定义装配，」Abaqus Analysis User's Guide 第 2.10.1 节](../usb/usb-link.md#usb-int-ipartassy)

- [「使用零件实例，」Abaqus/CAE User's Guide 第 13.3 节](../usi/usi-link.md#usi-asm-concepts)

### partition

用于将 Abaqus/CAE 零件或装配划分区域的特征。这种区域有许多用途；例如，应用载荷或分配网格属性。
更多信息：- [第 70 章，「The Partition toolset，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-par)

### Partition toolset

Abaqus/CAE 工具集，允许您将零件或装配划分为区域。
更多信息：- [第 70 章，「The Partition toolset，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-par)

### Part module

Abaqus/CAE 模块，用于创建、编辑和管理当前模型中的零件。
更多信息：- [第 11 章，「The Part module，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-prt)

### part-related modules

在 viewport 中显示零件的 Abaqus/CAE 模块。Part 和 Property 模块被视为与零件相关的模块。
更多信息：- [「什么是模块？，」Abaqus/CAE User's Guide 第 2.3 节](../usi/usi-link.md#uss-top-whatis-module)

### part set

由零件区域组成的 Abaqus/CAE 集。零件集仅在您位于 Part 或 Property 模块时可用。
更多信息：- [「零件集和装配集有何不同？，」Abaqus/CAE User's Guide 第 73.2.2 节](../usi/usi-link.md#usi-set-conc-difference)

### path

通过在模型中指定一系列点来定义的线。您可以沿路径以 *X–Y* 绘图的形式查看结果。
更多信息：- [第 48 章，「沿路径查看结果，」Abaqus/CAE User's Guide](../usi/usi-link.md#usv-path)

### plot state

生成 viewport 中绘图的所有活动自定义选项的组合。您通过生成相应类型的绘图进入特定的绘图状态。例如，如果您生成未变形绘图，则当前 viewport 将处于未变形绘图状态。viewport 的绘图状态会持续存在，Abaqus/CAE 会使用您对自定义选项所做的任何更改对其进行更新，直到您在同一 viewport 中生成其他状态的绘图。
更多信息：- [「什么是绘图状态？，」Abaqus/CAE User's Guide 第 40.3.1 节](../usi/usi-link.md#usv-concept-plotstates-whatis)

### plug-in

安装到另一个应用程序中以扩展该应用程序功能的软件片段。
更多信息：- [「什么是 plug-in？，」Abaqus/CAE User's Guide 第 81.1 节](../usi/usi-link.md#usi-plg-whatis)

- [第 82 章，「Abaqus plug-ins，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-plg-examples)

### PNG（Portable Network Graphics）

用于存储位图图像的行业标准。PNG 文件由颜色信息和图像的压缩位图表示组成。Abaqus/CAE 允许您将选定 viewport 的图像保存为 PNG 格式文件。
更多信息：- [「打印图像格式，」Abaqus/CAE User's Guide 第 8.1.1 节](../usi/usi-link.md#uss-pri-conc-gif)

### position constraint

在 Abaqus/CAE 中组装期间用于预设零件实例相对位置的约束。
更多信息：- [「位置约束方法有何不同，」Abaqus/CAE User's Guide 第 13.5.2 节](../usi/usi-link.md#usi-asm-concept-alignmate)

### positioning point

定位于网格无关紧固件第一个 [fastening point](gl01gls07.md#gls-fasteningpoint) 的点。定位点可以位于要被紧固的第一个表面上，也可以位于第一个表面附近并沿法线或用户指定方向投影。
更多信息：- [「指定定位点、投影方法和紧固点」中的「网格无关紧固件，」Abaqus Analysis User's Guide 第 35.3.4 节](../usb/usb-link.md#usb-cni-afastener-points)

### PostScript

由 Adobe Systems 开发的页面描述语言，提供灵活的字体功能和高质量图形。PostScript 使用类似英语的命令来控制页面布局以及加载和缩放轮廓字体。Abaqus/CAE 允许您直接将选定 viewport 的图像打印到 PostScript 打印机，或将相同图像保存为 PostScript 格式文件。
更多信息：- [「打印图像格式，」Abaqus/CAE User's Guide 第 8.1.1 节](../usi/usi-link.md#uss-pri-conc-gif)

### predefined field

存在于模型空间域上的时间相关、非求解相关条件。
更多信息：- [「预定义场，」Abaqus Analysis User's Guide 第 34.6.1 节](../usb/usb-link.md#usb-prc-pfields)

- [「创建和修改预设条件，」Abaqus/CAE User's Guide 第 16.4 节](../usi/usi-link.md#usi-lbi-edit-editors)

### prescribed condition

应用于模型的外部条件，如载荷、初始条件或边界条件。
更多信息：- [「预设条件：概述，」Abaqus Analysis User's Guide 第 34.1.1 节](../usb/usb-link.md#usb-prc-pprescribedover)

- [第 16 章，「The Load module，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-lbi)

### preselection

屏幕上对象外观的变化，帮助您为特定 Abaqus/CAE 过程进行所需的选择。两种类型的预选择可用：
- 预选择高亮显示：当您停止移动光标时出现在 Abaqus/CAE viewport 中。在当前光标位置将被选择的所有对象以橙色高亮显示。
- 预选择符号：当您在选择点的过程中围绕 Abaqus/CAE 草图移动光标时出现，如圆心或线端点。预选择符号帮助您定位光标，并指示草图上可选择的点，如顶点或中点。

如果您在预选择高亮显示或预选择符号可见时单击，Abaqus/CAE 将选择指示的对象。更多信息：- [「选择和取消选择单个对象，」Abaqus/CAE User's Guide 第 6.2.1 节](../usi/usi-link.md#uss-pic-select1)

- [「Sketcher 光标和预选择，」Abaqus/CAE User's Guide 第 20.4.5 节](../usi/usi-link.md#usi-ske-secondarycursor)

### primary axis

[离散方向](gl01gls05.md#gls-discreteorient) 的近似材料方向。Abaqus/CAE 使用 primary axis 和 [normal axis](gl01gls15.md#gls-normalaxis) 构建右手笛卡尔坐标系。您选择要在结果方向中表示 primary axis 的坐标系轴，并选择拓扑或基准或输入向量值来定义所需的轴。
更多信息：- [「将离散方向用于材料方向和复合铺层方向，」Abaqus/CAE User's Guide 第 12.16 节](../usi/usi-link.md#usi-prp-discrete-orient)

### primary cursor

与计算机上大多数应用程序一起使用的活动光标。主光标通常显示为箭头指针；您通过移动鼠标来定位此光标。另请参阅 [secondary cursor](gl01gls20.md#gls-secondcursor)。
更多信息：- [「Sketcher 光标和预选择，」Abaqus/CAE User's Guide 第 20.4.5 节](../usi/usi-link.md#usi-ske-secondarycursor)

### printed output（`.dat`）file

包含 Abaqus 分析输入文件预处理器生成的信息的文件（`*job_name*.dat`），包括模型定义以及处理输入数据时检测到的任何错误或警告消息。此外，打印输出文件还包含分析期间写入的任何打印输出数据。
更多信息：- [「输出，」Abaqus Analysis User's Guide 第 4.1.1 节](../usb/usb-link.md#usb-out-ooutput)

- [「输出到数据和结果文件，」Abaqus Analysis User's Guide 第 4.1.2 节](../usb/usb-link.md#usb-out-oprintfile)

- [「了解输出请求，」Abaqus/CAE User's Guide 第 14.4 节](../usi/usi-link.md#usi-sim-concepts-output)

### privileged plane

[3D compass](gl01gls01.md#gls-3dcompass) 的底座。默认情况下，Abaqus/CAE 绘制 [3D compass](gl01gls01.md#gls-3dcompass)，使 *X*–*Z* 平面成为 privileged plane。您可以自定义 [3D compass](gl01gls01.md#gls-3dcompass) 的外观，将 privileged plane 更改为三个主要指南针平面中的任何一个（*X*–*Y*、*Y*–*Z* 或 *X*–*Z*）。
更多信息：- [「自定义 3D 指南针，」Abaqus/CAE User's Guide 第 5.3.4 节](../usi/usi-link.md#uss-viw-3dcompass-customize)

### probe

Abaqus/CAE 在您围绕当前 viewport 移动光标时显示信息的模式。探测模型绘图显示模型数据和分 析结果；探测 *X–Y* 绘图显示 *X–Y* 曲线数据。
更多信息：- [第 51 章，「探测模型，」Abaqus/CAE User's Guide](../usi/usi-link.md#usv-probe)

### procedure

分析步骤中要执行的的分析类型。静态应力、动态应力、特征值屈曲和瞬态热传递是分析过程的示例。

在 Abaqus/CAE 中，您执行的许多任务被分解为分步过程。当您执行这些过程之一时，Abaqus/CAE 在主窗口底部附近的提示区域适时显示每个步骤的说明。
更多信息：- [「求解分析问题：概述，」Abaqus Analysis User's Guide 第 6.1.1 节](../usb/usb-link.md#usb-anl-asolving)

- [「在过程期间使用提示区域，」Abaqus/CAE User's Guide 第 3.1 节](../usi/usi-link.md#uss-int-proc)

### profile

与横截面形状和尺寸相关的梁截面工程属性的定义（如横截面积和惯性矩）。定义梁截面时，必须在截面定义中包含对 profile 的引用。
更多信息：- [「定义 profile，」Abaqus/CAE User's Guide 第 12.2.2 节](../usi/usi-link.md#usi-prp-prop-profile)

曲面 profile 是定义解析刚体表面横截面的线段集合。
更多信息：- [「解析刚体表面定义，」Abaqus Analysis User's Guide 第 2.3.4 节](../usb/usb-link.md#usb-int-arigidsurf)

Profile 还指变量在空间或时间上的分布，如温度 profile 或风速 profile。
更多信息：- [「非耦合热传递分析，」Abaqus Analysis User's Guide 第 6.5.2 节](../usb/usb-link.md#usb-anl-aheattransfer)

- [「Abaqus/Aqua 分析，」Abaqus Analysis User's Guide 第 6.11.1 节](../usb/usb-link.md#usb-anl-aaqua)

### prompt area

位于 Abaqus/CAE 主窗口底部的区域，显示过程期间您要遵循的说明。
更多信息：- [「在过程期间使用提示区域，」Abaqus/CAE User's Guide 第 3.1 节](../usi/usi-link.md#uss-int-proc)

### Property module

Abaqus/CAE 模块，允许您通过创建截面定义并将其分配给零件或零件区域来定义模型的材料和截面属性。大多数截面定义引用您也使用 Property 模块创建的材料定义。
更多信息：- [第 12 章，「The Property module，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-prp)



