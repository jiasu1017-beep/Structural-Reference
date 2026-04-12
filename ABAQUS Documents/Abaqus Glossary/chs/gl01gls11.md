# R







### radio button

Abaqus/CAE 对话框中某些选项的选项按钮，允许您在互斥选项之间进行选择。当某个特定选项由单选按钮控制时，您一次只能选择其中一个按钮。
更多信息：- [「使用基本对话框组件，」Abaqus/CAE User's Guide 第 3.2.1 节](../usi/usi-link.md#uss-int-dialog-basic)

### rake

沿其长度指定一系列点的线段，用于控制 Abaqus/CAE 显示流体流动分析流线的位置。
更多信息：- [「创建流，」Abaqus/CAE User's Guide 第 74.2 节](../usi/usi-link.md#usi-str-hlp-create)

### recovery（`.rec`）file

包含命令的文件（`*model_database_name*.rec`），如果由于 Abaqus/CAE 会话（如电源中断）的灾难性中断而丢失内存中的当前模型数据库，Abaqus/CAE 可使用这些命令重新创建模型数据库。恢复文件仅包含自上次保存模型数据库以来执行的命令；所有剩余命令都保存在 [日志文件](gl01gls11.md#gls-journalfile) 中。
更多信息：- [「重新创建未保存的模型数据库，」Abaqus/CAE User's Guide 第 9.5.3 节](../usi/usi-link.md#usi-dbs-files-recover)

### reference dimension

Abaqus/CAE 中的一种约束类型，注释已在草图其他位置控制的尺寸或无法在当前草图中控制的尺寸（如投影参考几何）。参考尺寸表示草图中几何的大小，同时允许大小更改，这与将几何固定在标注尺寸的尺寸的常规尺寸不同。您可以使用参考尺寸来指示参考几何的大小，或提供替代尺寸，而不会过度约束草图。
更多信息：- [「约束、标注尺寸和参数化草图，」Abaqus/CAE User's Guide 第 20.12 节](../usi/usi-link.md#usi-ske-controlling)

### reference geometry

在 Abaqus/CAE 中，与草图平面相同的平面中现有零件或装配的边和顶点。当您进入 Sketch 模块时，Abaqus/CAE 将参考几何投影到草图纸上；您可以选择参考几何来帮助定位对象并将草图约束到底层几何。
更多信息：- [「参考几何，」Abaqus/CAE User's Guide 第 20.5.1 节](../usi/usi-link.md#usi-ske-refgeo)

### reference representation

零件或零件子集（一个或多个 cell）的替代表示，不用于 Abaqus/CAE 分析。参考表示替换选定的零件或零件部分。被替换的几何从零件的活动表示中移除——即将被网格化并用于分析的几何——留下参考表示来显示相同几何的半透明视图。参考表示通常用作创建新活动表示的工具，如中面模型。
更多信息：- [「了解参考表示，」Abaqus/CAE User's Guide 第 35.2 节](../usi/usi-link.md#usi-adv-midsurface-underrefrep)

### reference surface

由传统壳单元的节点和法线方向定义的空间几何。参考表面通常位于壳厚度的中心，但也可以从中间表面偏移。
更多信息：- [「壳单元：概述，」Abaqus Analysis User's Guide 第 29.6.1 节](../usb/usb-link.md#usb-elm-eshelloverview)

- [「定义传统壳单元的初始几何，」Abaqus Analysis User's Guide 第 29.6.3 节](../usb/usb-link.md#usb-elm-eshellgeometry)

- [「定义温度场，」Abaqus/CAE User's Guide 第 16.11.9 节](../usi/usi-link.md#usi-lbi-helptopics-temp)

### refinement rate limit

Abaqus/CAE 中由重网格算法计算的元素总数上限，用于调节尺寸方法的攻击性并控制较小元素的引入。当 Abaqus/CAE 自适应重划分模型网格时，您在重划分规则中指定的粗化速率限制调节较小元素引入网格的速率。细化因子对自适应网格划分过程的收敛性有显著影响，可能帮助您实现更快、更有效的网格收敛。
更多信息：- [「细化和粗化速率因子」中的「基于求解的网格尺寸，」Abaqus Analysis User's Guide 第 12.3.3 节](../usb/usb-link.md#usb-anl-aadpsizing-ratefactors)

### regenerate

修改 Abaqus/CAE 模型的特征后重新计算模型几何的过程；默认情况下，如果您修改特征，Abaqus/CAE 会自动重新生成所有从属特征。例如，如果您修改零件的特征，Abaqus/CAE 会重新生成该零件、装配中该零件的任何实例以及最终网格。
更多信息：- [「使用 Feature Manipulation toolset，」Abaqus/CAE User's Guide 第 65.1 节](../usi/usi-link.md#usi-fts-concepts)

### region

Abaqus/CAE 模型的任何特定部分。区域可以是顶点、边、面、体、节点、元素或这些实体的集合。您可以通过创建包含这些区域的集合和曲面来指定和命名零件或装配的特定区域。您可以通过分割来将零件或装配划分为更多区域。
更多信息：- [第 73 章，「The Set and Surface toolsets，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-set)

### remeshing rule

Abaqus/CAE 用于使网格迭代适应指定误差目标的规则。重网格规则描述您的自适应网格划分规范的所有方面：
- 将应用规则的区域
- 将应用规则的步骤
- 误差指示器输出变量
- 尺寸方法
- 尺寸约束

更多信息：- [「什么是重网格规则？，」Abaqus/CAE User's Guide 第 17.13.1 节](../usi/usi-link.md#usi-mgn-conc-adaptivity-rulerole)

### render style

在 Abaqus/CAE viewport 中显示对象的方式。render style 的示例包括 **Wireframe**、**Hidden** 和 **Shaded**。
更多信息：- [「选择渲染样式，」Abaqus/CAE User's Guide 第 76.2 节](../usi/usi-link.md#uss-dsp-dynamic-render)

### replay

指定要从中重放 Abaqus/CAE 命令的文件名的选项。您在 Abaqus/CAE 中执行的几乎每个操作都会以 Abaqus 命令的形式自动记录在重放文件（`abaqus.rpy`）中。执行重放文件等同于重放原始操作序列。
更多信息：- [「重新创建未保存的模型数据库，」Abaqus/CAE User's Guide 第 9.5.3 节](../usi/usi-link.md#usi-dbs-files-recover)

### restart（`.res`）file

用于继续分析作业的文件（`*job_name*.res`）。

此外，一种允许您分阶段运行复杂多步模拟而非在单个作业中运行的能力，这样您可以检查结果并确认分析是否按预期执行，然后再继续下一阶段。Abaqus 重启分析功能使用先前求解的重启数据来确定模型对额外负载历史的响应。
更多信息：- [「重启分析，」Abaqus Analysis User's Guide 第 9.1.1 节](../usb/usb-link.md#usb-anl-arestart)

- [「重启输出请求，」Abaqus/CAE User's Guide 第 14.5.2 节](../usi/usi-link.md#usi-sim-conc-restart)

### Results Tree

Abaqus/CAE GUI 的组件，提供会话中可用输出数据的可视描述，包括所有打开的输出数据库以及会话特定数据（如 *X–Y* 数据和 *X–Y* 绘图）。此工具与 Model Tree 共享 Abaqus/CAE 界面的左侧。
更多信息：- [「Results Tree 概述，」Abaqus/CAE User's Guide 第 3.5.2 节](../usi/usi-link.md#uss-top-resultstree-overview)

### resume

将暂时从 Abaqus/CAE 模型中删除的特征恢复到模型的过程，以简化零件或装配的外观。另请参阅 [suppress](gl01gls20.md#gls-suppress)。
更多信息：- [「使用 Feature Manipulation toolset，」Abaqus/CAE User's Guide 第 65.1 节](../usi/usi-link.md#usi-fts-concepts)

### rigid body

节点、元素和/或曲面的集合，其刚度比模型其余部分大得多，以至于其变形可以忽略不计。在 Abaqus/Standard 和 Abaqus/Explicit 中，刚体是刚性元素的集合。另请参阅 [analytical rigid surface](gl01gls02.md#gls-analyticalrigidsurface) 或 [discrete rigid part](gl01gls05.md#gls-discreterigid)，了解 Abaqus/CAE 中刚体的信息。
更多信息：- [「解析刚体表面定义，」Abaqus Analysis User's Guide 第 2.3.4 节](../usb/usb-link.md#usb-int-arigidsurf)

- [「对刚体和显示体进行建模，」Abaqus/CAE User's Guide 第 11.7 节](../usi/usi-link.md#usi-prt-rigid)

### rigid body reference node

位于刚体参考点处的节点。约束刚体时，您应用约束到刚体参考节点的自由度。
更多信息：- [「解析刚体表面定义，」Abaqus Analysis User's Guide 第 2.3.4 节](../usb/usb-link.md#usb-int-arigidsurf)

- [「参考点，」Abaqus/CAE User's Guide 第 11.8.1 节](../usi/usi-link.md#usi-prt-conc-refpoint)

### rigid body reference point

用于定义刚体（Abaqus/CAE 中的刚性零件）运动或对刚体施加约束的选定点。
更多信息：- [「解析刚体表面定义，」Abaqus Analysis User's Guide 第 2.3.4 节](../usb/usb-link.md#usb-int-arigidsurf)

- [「参考点，」Abaqus/CAE User's Guide 第 11.8.1 节](../usi/usi-link.md#usi-prt-conc-refpoint)

### round

用于减少应力集中的零件内部角落的凹形过渡；也称为 fillet。您可以使用 Part 模块中的混合工具将当前 viewport 中选定边缘倒圆到所需半径。
更多信息：- [「混合特征，」Abaqus/CAE User's Guide 第 11.9.5 节](../usi/usi-link.md#usi-prt-conc-round)



