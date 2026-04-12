# S







### scale factor animation

在 Abaqus/CAE 中从输出数据库（ODB）的单个步骤和帧创建的绘图系列。不同的绘图是通过将变形比例因子乘以一系列动画比例因子而形成的。
更多信息：- [「比例因子动画，」Abaqus/CAE User's Guide 第 49.1.2 节](../usi/usi-link.md#usv-anm-understandscale)

### scratch output database（`.ods`）file

包含 [session step](gl01gls20.md#gls-sessionstep) 的文件（`*job_name*.ods`），当原始输出数据库文件关闭或 Abaqus/CAE 会话结束时自动删除。
更多信息：- [「了解创建和分析模型时生成的文件，」Abaqus/CAE User's Guide 第 9.4 节](../usi/usi-link.md#usi-dbs-conc-filesgenerated)

### script

由一组指令组成的程序类型。在 Abaqus/CAE 中，您在会话期间执行的几乎每个操作都可以通过包含一组 Abaqus/CAE 命令的脚本来复制。您可以在自动写入每个 Abaqus/CAE 会话的重放文件（`abaqus.rpy`）中找到 Abaqus/CAE 命令的示例。
更多信息：- [「了解创建和分析模型时生成的文件，」Abaqus/CAE User's Guide 第 9.4 节](../usi/usi-link.md#usi-dbs-conc-filesgenerated)

### secondary cursor

Abaqus/CAE Sketch 模块中活动光标，看起来像一个加号（+），当 Sketch 模块提示您选择点时出现在主光标附近。默认情况下，如果您将主光标移动到符合条件的点附近，辅助光标会直接跳到该点，而主光标保持固定；因此，您可以轻松地准确看到选择了哪个点，然后再确认选择。另请参阅 [primary cursor](gl01gls17.md#gls-primarycursor)。
更多信息：- [「Sketcher 光标和预选择，」Abaqus/CAE User's Guide 第 20.4.5 节](../usi/usi-link.md#usi-ske-secondarycursor)

### section definition

指定 Abaqus/CAE 装配区域或 Abaqus/Standard、Abaq us/Explicit 或 Abaqus/CFD 模型中元素集合的属性的数据。截面定义可以包含材料名称、泊松比、横向剪切数据等各种参数的信息。
更多信息：- [第 12 章，「The Property module，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-prp)

### section point

积分点。当定义在分析期间集成的壳或梁截面时，必须指定截面厚度方向上的截面积分点数量。一组截面点位于壳元素表面上每个材料积分点处，或沿梁元素长度方向分布。
更多信息：- [第 12 章，「The Property module，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-prp)

### seed

沿未网格化装配边缘放置的标记，用于指示所需网格密度。默认情况下，网格种子仅提供目标网格密度；如有必要，网格生成器会改变原始种子分布以成功生成网格。您可以通过约束种子来防止这种重新分布。
更多信息：- [「了解种子设置，」Abaqus/CAE User's Guide 第 17.4 节](../usi/usi-link.md#usi-mgn-conc-seed)

### session

程序接受输入、处理信息并响应用户命令的时间。Abaqus/CAE 会话从您启动 Abaqus/CAE 时开始，直到您退出。
更多信息：- [「启动和退出 Abaqus/CAE，」Abaqus/CAE User's Guide 第 2.1 节](../usi/usi-link.md#uss-gst-startexit)

### session step

Abaqus/CAE 保存到 [临时输出数据库文件](gl01gls20.md#gls-scratch-odb)（`*job_name*.ods`）中的步骤，其中 Abaqus/CAE 保存您通过操作现有场输出变量或组合多个分析帧的结果创建的场输出。
更多信息：- [「启动和退出 Abaqus/CAE，」Abaqus/CAE User's Guide 第 2.1 节](../usi/usi-link.md#uss-gst-startexit)

### set

命名区域或对象集合，您可以在其上执行各种操作。另请参阅 [node set](gl01gls15.md#gls-nodeset)、[element set](gl01gls06.md#gls-elementset)、[geometry set](gl01gls08.md#gls-geometricset) 和 [discrete set](gl01gls05.md#gls-discreteset)。
更多信息：- [「输入语法规则，」Abaqus Analysis User's Guide 第 1.2.1 节](../usb/usb-link.md#usb-int-iinputsyntax)

- [「了解集合和曲面，」Abaqus/CAE User's Guide 第 73.2 节](../usi/usi-link.md#usi-set-concepts)

### Set toolset

Abaqus/CAE 工具集，允许您在除 Visualization 模块之外的所有 Abaqus/CAE 模块中创建和管理集合。
更多信息：- [第 73 章，「The Set and Surface toolsets，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-set)

### shell

关于元素公式，shell 是捕获弯曲和膜行为，适合于厚度相对于其他尺寸较小的结构的元素公式。
更多信息：- [「壳单元，」Abaqus Analysis User's Guide 第 29.6 节](../usb/usb-link.md#usbeshell)

关于几何类型，shell 是曲面几何。
更多信息：- [「零件和特征之间的关系，」Abaqus/CAE User's Guide 第 11.3.1 节](../usi/usi-link.md#usi-prt-conc-parts-features)

### shell sections

壳区域截面属性。Shell 对结构建模，其中一个维度（厚度）显著小于其他两个维度，且厚度方向的应力可以忽略不计。
更多信息：- [「壳截面行为，」Abaqus Analysis User's Guide 第 29.6.4 节](../usb/usb-link.md#usb-elm-eshellsectionbehavior)

- [「定义截面，」Abaqus/CAE User's Guide 第 12.2.3 节](../usi/usi-link.md#usi-prp-prop-section)

### sizing method

Abaqus/CAE 在自适应重网格过程期间生成新元素尺寸的方法。对于特定变量，sizing method 从重网格规则定义的区域读取并操作基求解值及其相应误差指示器输出变量的场。Abaqus 使用 sizing method 计算新元素尺寸。Abaqus/CAE 提供两种 sizing method：**Uniform error distribution** 和 **Minimum/maximum control**。
更多信息：- [「尺寸方法」中的「基于求解的网格尺寸，」Abaqus Analysis User's Guide 第 12.3.3 节](../usb/usb-link.md#usb-anl-aadpsizing-methods)

- [「选择重网格规则 sizing method，」Abaqus/CAE User's Guide 第 17.21.3 节](../usi/usi-link.md#usi-mgn-adaptivity-rulesizing)

### sketch

用于帮助形成定义 Abaqus/CAE 本机零件的几何的二维轮廓。您使用草图创建平面或轴对称特征；或者您可以拉伸、旋转或扫描草图以形成三维特征。
更多信息：- [第 20 章，「The Sketch module，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-ske)

### sketch coordinates

在 Sketcher 中创建新草图几何时出现在右上角的游标坐标。草图坐标仅在它们与当前网格坐标不同时才出现——即当网格原点或旋转发生变化时。
更多信息：- [「相对于草图重新对齐草图网格，」Abaqus/CAE User's Guide 第 20.4.4 节](../usi/usi-link.md#usi-ske-reorient)

### Sketcher

Abaqus/CAE 工具集，允许您绘制形成特征二维轮廓的线和曲线，添加约束到草图，并在 Abaqus/CAE 中修改草图。
更多信息：- [第 20 章，「The Sketch module，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-ske)

### Sketch module

Abaqus/CAE 模块，用于创建定义平面零件、梁或分割的草图，或创建可被拉伸、扫描或旋转以形成三维零件的草图。
更多信息：- [第 20 章，「The Sketch module，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-ske)

### slider

Abaqus/CAE 对话框中表盘上的指示器，您可以拖动它来设置具有连续可能值范围的选项的值。
更多信息：- [「使用基本对话框组件，」Abaqus/CAE User's Guide 第 3.2.1 节](../usi/usi-link.md#uss-int-dialog-basic)

### SMP（shared memory parallel）

一种并行执行模式，其中多个处理器共享单个地址空间。Abaqus 支持基于线程的 SMP。
更多信息：- [「并行执行，」Abaqus Analysis User's Guide 第 3.5 节](../usb/usb-link.md#usbapar)

### solid sections

定义二维、三维和轴对称实体区域截面属性的信息集合。
更多信息：- [「定义截面，」Abaqus/CAE User's Guide 第 12.2.3 节](../usi/usi-link.md#usi-prp-prop-section)

### solver

用于指代 Abaqus 产品的术语：Abaqus/Standard（隐式）、Abaqus/Explicit（显式）和 Abaqus/CFD（计算流体动力学）。另请参阅 [equation solver](gl01gls06.md#gls-eqnsolver)。

### spline

由数学函数定义的曲线，以高平滑度连接独立点。使用 Abaqus/CAE Sketch 模块中的样条工具绘制连接一系列点的平滑曲线。Abaqus/CAE 使用沿样条所有点之间的三次样条拟合来计算曲线形状；因此，样条的一阶和二阶导数是连续的。
更多信息：- [「绘制样条，」Abaqus/CAE User's Guide 第 20.10.10 节](../usi/usi-link.md#usi-ske-splinebtn)

### stand-alone sketch

独立于任何特定特征的 Abaqus/CAE 草图；您可以将独立草图合并到当前草图中。
更多信息：- [「独立草图，」Abaqus/CAE User's Guide 第 20.3.1 节](../usi/usi-link.md#usi-ske-standalone)

### status（`.sta`）file

在 Abaqus/Standard、Abaqus/Explicit 或 Abaqus/CFD 分析作业期间生成的文件（`*job_name*.sta`），包含分析进度信息。
更多信息：- [「输出，」Abaqus Analysis User's Guide 第 4.1.1 节](../usb/usb-link.md#usb-out-ooutput)

- [「自由度监视器请求，」Abaqus/CAE User's Guide 第 14.5.4 节](../usi/usi-link.md#usi-sim-conc-monitor)

### STEP [STandard for the Exchange of Product model data（STEP ISO 10303-1）]

IGES 的替代标准，试图克服 IGES 的一些缺点。STEP 格式旨在提供产品在整个生命周期中的计算机可解释表示，独立于任何特定系统。您可以导入 STEP 格式零件，也可以导出 STEP 格式零件。此外，您还可以从 STEP 文件导入和导出草图。
更多信息：- [「导入和导出 Abaqus/CAE 文件，」Abaqus/CAE User's Guide 第 10.1 节](../usi/usi-link.md#usi-imp-concepts)

- [「导入零件，」Abaqus/CAE User's Guide 第 10.7.2 节](../usi/usi-link.md#usi-dbs-import-part)

- [「导出几何、模型和网格数据，」Abaqus/CAE User's Guide 第 10.9 节](../usi/usi-link.md#usi-imp-export)

### step

提供便捷方式来捕获模型载荷和边界条件变化、模型各部分相互作用的方 式以及分析过程中可能发生的任何其他变化的序列。此外，步骤允许您更改分析过程、数据输出和各种控件。您还可以使用步骤来定义关于非线性基础状态的线性扰动分析。
更多信息：- [「在 Abaqus 中定义模型，」Abaqus Analysis User's Guide 第 1.3.1 节](../usb/usb-link.md#usb-int-imodel)

- [「什么是步骤？，」Abaqus/CAE User's Guide 第 14.3.1 节](../usi/usi-link.md#usi-sim-conc-unsteps)

### step-dependent manager

Abaqus/CAE 对话框，包含您创建的所有特定类型对象的列表，以及 **Create**、**Edit**、**Copy**、**Rename** 和 **Delete** 按钮，可用于操作现有对象和创建新对象。step-dependent manager 类似于 [basic manager](gl01gls03.md#gls-basicmanager)，但包含有关管理器中列出每个对象历史的附加信息。
更多信息：- [「什么是步骤相关管理器？，」Abaqus/CAE User's Guide 第 3.4.2 节](../usi/usi-link.md#uss-int-step-manager)

### step-dependent object

您可以创建并在分析的特定步骤中进行修改和停用的对象。载荷、边界条件和相互作用都是与步骤相关的对象。
更多信息：- [「什么是步骤相关管理器？，」Abaqus/CAE User's Guide 第 3.4.2 节](../usi/usi-link.md#uss-int-step-manager)

### Step module

Abaqus/CAE 模块，用于创建和定义分析步骤并为每个步骤请求输出。您还可以使用 Step 模块指定自适应网格划分以及接触和通用求解控制。
更多信息：- [第 14 章，「The Step module，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-sim)

### stream

用于可视化流体流动分析数据的流线集合。
更多信息：- [第 74 章，「The Stream toolset，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-str)

### streamline

瞬间与流速矢量相切的曲线。在流体流动分析中，流线显示流体元素在任意时间点沿流体流动的方向。
更多信息：- [第 74 章，「The Stream toolset，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-str)

### structured meshing

Abaqus/CAE 使用简单预定义网格拓扑生成结构化网格的技术。Abaqus/CAE 将规则形状区域（如正方形或立方体）的网格转换到要网格化的区域几何上。
更多信息：- [「结构化网格和映射网格，」Abaqus/CAE User's Guide 第 17.8 节](../usi/usi-link.md#usi-mgn-conc-mapped)

### substructure

消除了内部自由度的元素集合。
更多信息：- [「使用子结构，」Abaqus Analysis User's Guide 第 10.1.1 节](../usb/usb-link.md#usb-anl-asuperelements)

- [「定义子结构，」Abaqus Analysis User's Guide 第 10.1.2 节](../usb/usb-link.md#usb-anl-asuperelementdef)

- [第 39 章，「Substructures，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-adv-substructures)

### substructure database

描述子结构几何的文件集。Abaqus 在分析期间将所有子结构数据写入子结构数据库。
更多信息：- [「定义子结构，」Abaqus Analysis User's Guide 第 10.1.2 节](../usb/usb-link.md#usb-anl-asuperelementdef)

- [第 39 章，「Substructures，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-adv-substructures)

### substructure dynamic modes

在子结构定义中保留的特征模态和残余模态。
更多信息：- [「定义子结构，」Abaqus Analysis User's Guide 第 10.1.2 节](../usb/usb-link.md#usb-anl-asuperelementdef)

- [第 39 章，「Substructures，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-adv-substructures)

### suppress

暂时从 Abaqus/CAE 模型中删除特征以简化零件或装配外观的过程。此外，抑制特征可以提高重新生成速度。另请参阅 [resume](gl01gls19.md#gls-resume)。
更多信息：- [「使用 Feature Manipulation toolset，」Abaqus/CAE User's Guide 第 65.1 节](../usi/usi-link.md#usi-fts-concepts)

### surface

可在几何刚体或离散有限元模型的面、边或节点上定义的命名区域。曲面定义还可包含区分曲面正面和负面的信息。
更多信息：- [「曲面：概述，」Abaqus Analysis User's Guide 第 2.3.1 节](../usb/usb-link.md#usb-int-asurfoverview)

- [第 73 章，「The Set and Surface toolsets，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-set)

### Surface toolset

Abaqus/CAE 工具集，允许您在除 Visualization 模块之外的所有 Abaqus/CAE 模块中创建和管理曲面。
更多信息：- [第 73 章，「The Set and Surface toolsets，」Abaqus/CAE User's Guide](../usi/usi-link.md#usi-set)

### swept meshing

Abaqus/CAE 用于对复杂拉伸或旋转实体区域以及旋转曲面区域进行网格划分的技术。扫掠网格技术涉及两个阶段：
- Abaqus/CAE 在区域一侧（称为源侧）创建网格。
- Abaqus/CAE 逐层复制该网格的节点，直到达到最终侧（称为目标侧）。

更多信息：- [「扫掠网格，」Abaqus/CAE User's Guide 第 17.9 节](../usi/usi-link.md#usi-mgn-conc-sweep)

### symbol plot

Abaqus/CAE 绘图，显示在分析的指定步骤和帧处特定向量或张量变量的大小和方向。Abaqus/CAE 将值表示为符号（箭头），绘制在模型中获得结果的位置。
更多信息：- [第 45 章，「将分析结果绘制为符号，」Abaqus/CAE User's Guide](../usi/usi-link.md#usv-symbol)

### synchronization

Abaqus/CAE 在会话中每个支持动画的 viewport 中同时动画数据的过程，以便在逐帧检查数据、动画模型绘图或动画时间相关 *X–Y* 绘图时，viewports 一起播放、停止和递增。
更多信息：- [「控制多个 viewports 中的动画，」Abaqus/CAE User's Guide 第 49.4.6 节](../usi/usi-link.md#usv-anm-synch)



