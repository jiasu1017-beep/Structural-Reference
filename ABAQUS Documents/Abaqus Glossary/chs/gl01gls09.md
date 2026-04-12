# M







### main window

您与 Abaqus/CAE 交互的 GUI。主窗口包含菜单栏、提示区域、工具栏以及多种其他组件，允许您执行创建和分析模型以及查看分析结果所需的任务。主窗口的某些方面（如菜单栏和工具栏）可能会随着您完成建模过程而变化。
更多信息：- [「主窗口概述，」Abaqus/CAE User's Guide 第 2.2 节](../usi/usi-link.md#uss-top-mainwindow)

### maintenance delivery

通用发布后的软件更新，解决状态报告中识别的问题，但不包括增强功能或新功能。维护交付由产品名称和版本号后跟 2、3 等指定，例如 Abaqus 6.14-2 和 Abaqus 6.14-3。另请参阅 [general release](gl01gls08.md#gls-generalrelease)。

### manager

请参阅 [basic manager](gl01gls03.md#gls-basicmanager) 和 [step-dependent manager](gl01gls20.md#gls-stepmanager)。

### material orientation triad

Abaqus/CAE viewport 注释，指示 Visualization 模块中模型元素在元素积分点处的材料方向。
更多信息：- [「自定义材料方向绘图 triad，」Abaqus/CAE User's Guide 第 46.4.1 节](../usi/usi-link.md#usv-matorient-triadcolor)

### membrane sections

空间中在表面平面内提供强度但没有弯曲刚度的薄表面。
更多信息：- [「膜单元，」Abaqus Analysis User's Guide 第 29.1 节](../usb/usb-link.md#usbmembrane)

- [「定义截面，」Abaqus/CAE User's Guide 第 12.2.3 节](../usi/usi-link.md#usi-prp-prop-section)

### mesh

在 FEA 模型上定义的有限元素的排列。您可以在零件上或装配上定义网格。
网格划分是将几何离散化为有限元表示的活动。
更多信息：- [「元素定义，」Abaqus Analysis User's Guide 第 2.2.1 节](../usb/usb-link.md#usb-int-ielement)

- [第 17 章，「The Mesh module，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-mgn)

### mesh-geometry association

Abaqus/CAE 技术，用于将网格与几何体关联，以正确传递来自几何实体的载荷和边界条件。自上而下网格划分技术自动将网格与用于创建它的几何体关联。如果您使用自底向上网格划分技术或编辑自上而下网格的关联，可能需要检查关联。
更多信息：- [「网格-几何关联，」Abaqus/CAE User's Guide 第 17.12 节](../usi/usi-link.md#usi-mgn-conc-associate)

### Mesh module

Abaqus/CAE 模块，包含用于在创建或导入 Abaqus/CAE 的零件和装配上生成网格的工具。此外，Mesh 模块还提供有关现有网格的信息查询功能。
更多信息：- [第 17 章，「The Mesh module，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-mgn)

### mesh surface

从装配中的本机或孤立网格中选择元素面或边的命名集合，可用于请求特定模型区域的输出或向其添加载荷。
更多信息：- [第 73 章，「The Set and Surface toolsets，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-set)

### message area

Abaqus/CAE 主窗口中用于显示信息和警告的部分。
更多信息：- [「主窗口概述，」Abaqus/CAE User's Guide 第 2.2 节](../usi/usi-link.md#uss-top-mainwindow)

### message（`.msg`）file

包含 Abaqus/Standard 或 Abaqus/Explicit 分析进度诊断或信息消息的文件（`*job_name*.msg`）。
更多信息：- [「输出，」Abaqus Analysis User's Guide 第 4.1.1 节](../usb/usb-link.md#usb-out-ooutput)

- [「了解创建和分析模型时生成的文件，」Abaqus/CAE User's Guide 第 9.4 节](../usi/usi-link.md#usi-dbs-conc-filesgenerated)

- [「诊断打印，」Abaqus/CAE User's Guide 第 14.5.3 节](../usi/usi-link.md#usi-sim-conc-diag-print)

### midsurface model

具有厚度和偏移定义的外壳模型，代替实体模型用于分析。中面模型旨在提供简化的模型，在不影响结果的情况下降低分析成本。
更多信息：- [第 35 章，「中面建模，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-adv-midsurface)

### mixed-interface substructure dynamic modes

子结构动态模式，其中仅部分保留的自由度受到约束，而其他自由度未受到约束。
更多信息：- [「定义子结构，」Abaqus Analysis User's Guide 第 10.1.2 节](../usb/usb-link.md#usb-anl-asuperelementdef)

### model

进行分析所需的数据集合；也指被分析的物理对象。
更多信息：- [「在 Abaqus 中定义模型，」Abaqus Analysis User's Guide 第 1.3.1 节](../usb/usb-link.md#usb-int-imodel)

- [「什么是 Abaqus/CAE 模型？，」Abaqus/CAE User's Guide 第 9.2 节](../usi/usi-link.md#usi-dbs-conc-whatismodel)

### model data

Abaqus/Standard、Abaqus/Explicit 或 Abaqus/CFD 输入文件的一部分，定义有限元模型：元素、节点、元素属性、材料定义等——任何指定模型本身的数据。模型数据包括 Abaqus 输入文件中出现在 [*STEP](../key/key-link.md#usb-kws-hstep) 选项之前的所有数据。
更多信息：- [「在 Abaqus 中定义模型，」Abaqus Analysis User's Guide 第 1.3.1 节](../usb/usb-link.md#usb-int-imodel)

### model database

Abaqus/CAE 用于存储模型和分析作业的数据库。虽然您可能在计算机或网络上存储了多个模型数据库，但 Abaqus/CAE 一次只能在一个上工作。正在使用的模型数据库称为当前模型数据库，Abaqus/CAE 在主窗口顶部显示其名称。
更多信息：- [「什么是 Abaqus/CAE 模型数据库？，」Abaqus/CAE User's Guide 第 9.1 节](../usi/usi-link.md#usi-dbs-concepts)

### model definition

模型的内部 Abaqus 表示。
更多信息：- [「在 Abaqus 中定义模型，」Abaqus Analysis User's Guide 第 1.3.1 节](../usb/usb-link.md#usb-int-imodel)

- [「控制 Abaqus/CAE 生成的输入文件，」Abaqus/CAE User's Guide 第 9.10 节](../usi/usi-link.md#usi-dbs-controlinput)

### modeling space

零件所在的空间。零件可以存在于三维、二维或轴对称建模空间。
更多信息：- [「零件建模空间，」Abaqus/CAE User's Guide 第 11.4.1 节](../usi/usi-link.md#usi-prt-conc-dimensionality)

### module

Abaqus/CAE 的功能单元。每个模块定义建模过程的一个逻辑方面，如定义几何、定义材料属性和生成网格，并且仅包含与建模任务特定部分相关的工具。
更多信息：- [「什么是模块？，」Abaqus/CAE User's Guide 第 2.3 节](../usi/usi-link.md#uss-top-whatis-module)

### monitor

请参阅 [job monitor](gl01gls11.md#gls-job-monitor)。

### movable part instance

在 Abaqus/CAE 中应用装配约束期间其位置可以改变的零件实例。
更多信息：- [「位置约束方法有何不同，」Abaqus/CAE User's Guide 第 13.5.2 节](../usi/usi-link.md#usi-asm-concept-alignmate)

### MPI（message passing interface）

由 MPI 标准定义的软件库，用于并行化软件。MPI 通常用于在计算集群或工作站网络上实现执行，但在 SMP（共享内存并行）机器上也能提供有效的并行化。另请参阅 [MPI-based parallel](gl01gls14.md#gls-mpi-based-parallel) 和 [SMP](gl01gls20.md#gls-smp)。
更多信息：- [MPI Forum](http://www.mpi-forum.org)

### MPI-based parallel

Abaqus 在多处理器工作站或计算集群上使用 MPI 库支持的 DMP 处理。
更多信息：- [「并行执行，」Abaqus Analysis User's Guide 第 3.5 节](../usb/usb-link.md#usbapar)

### multiphysics

数值求解多个相互作用物理域的耦合方法。Abaqus 提供内置完全耦合过程、顺序耦合和协同模拟作为多物理场模拟的求解技术。请参阅 www.3ds.com/simulia 上的 [Co-simulation 页面](http://www.3ds.com/support/certified-hardware/simulia-system-information/compatibility/co-simulation/)。
更多信息：- [「多物理场分析」中的「求解分析问题：概述，」Abaqus Analysis User's Guide 第 6.1.1 节](../usb/usb-link.md#usb-anl-asolving-multiphysics)

### multi-point constraint

允许您将区域从节点的自由度约束到单个点或多个点的约束。
更多信息：- [「通用多点约束，」Abaqus Analysis User's Guide 第 35.2.2 节](../usb/usb-link.md#usb-cni-pmpc)



