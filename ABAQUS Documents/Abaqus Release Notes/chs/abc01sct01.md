# 1.2 Abaqus 产品





Abaqus 套件的各个组件在本节中描述。

### 分析

**Abaqus/Standard**：这个通用分析产品可以求解涉及构件静态、动态、热、电和电磁响应的大量线性和非线性问题。Abaqus/Standard 包括除 Abaqus/Explicit 和 Abaqus/CFD 程序以及以下所述的附加分析功能之外的所有分析功能。

**Abaqus/Explicit**：该产品使用显式时间积分法提供固态和结构的非线性、瞬态、动态分析。其强大的接触能力、可靠性和在大模型上的计算效率也使其非常适用于涉及不连续非线性行为的准静态应用。

**Abaqus/CFD**：该产品是一个计算流体动力学程序，支持在 Abaqus/CAE 中进行前处理、模拟和后处理。Abaqus/CFD 提供可扩展的并行 CFD 模拟能力，以解决非线性耦合流体-热和流体-结构问题。

### 前处理和后处理

**Abaqus/CAE**：该产品是一个完整的 Abaqus 环境，提供一个简单、一致的界面，用于创建、提交、监控和评估 Abaqus 模拟的结果。Abaqus/CAE 分为多个模块，每个模块定义建模过程的一个逻辑方面；例如，定义几何体、定义材料属性、生成网格、提交分析作业和解释结果。

**Abaqus/Viewer**：Abaqus/CAE 的这个子集仅包含 Visualization 模块的后处理功能。它使用输出数据库（`.odb`）从分析产品获取结果。输出数据库是一个中性二进制文件。因此，在任何平台上运行的 Abaqus 分析结果都可以在任何其他支持 Abaqus/Viewer 的平台上查看。它提供变形构型、云图、矢量图和 *X–Y* 图，以及结果动画。

### 附加分析功能

**Abaqus/Aqua**：这是 Abaqus/Standard 和 Abaqus/Explicit 的附加分析功能，提供基于稳态流、波和风效应计算拖曳力和浮力的能力，用于模拟海上管道和浮动平台结构。Abaqus/Aqua 适用于可以用线元素（包括梁、管道和桁架元素）理想化的结构。

**Abaqus/Design**：这是 Abaqus/Standard 的附加分析功能，允许用户执行设计灵敏度分析（DSA）。计算输出变量相对于指定设计参数的导数。

**Optimization Module**：Abaqus/CAE 中提供了执行形状和拓扑优化的功能。此功能需要额外的许可证才能提交分析优化过程。

**Abaqus/Foundation**：此分析选项提供了更高效地访问 Abaqus/Standard 中的线性静态和动态分析功能。

**CZone for Abaqus**：这是 Abaqus/Explicit 的附加功能，提供访问基于 Engenuity, Ltd. 的 CZone 技术的先进压溃模拟方法。针对复合材料部件和组件的设计，CZone for Abaqus 可在承受冲击的复合材料结构模拟中包含材料压溃行为。

### 可选分析功能

**Abaqus/AMS**：这是 Abaqus/Standard 的附加分析功能，允许用户在执行自然频率提取时选择自动多级子结构（AMS）特征值求解器。

**与 MpCCI 的协同仿真**：这是 Abaqus 的附加分析功能，可用于通过将 Abaqus 与支持 MpCCI 接口的任何第三方分析程序耦合来求解多物理场问题。

### 关联接口和几何转换器

**SIMULIA Associative Interface for Abaqus/CAE**：这是 Abaqus/CAE 的附加功能，在 CATIA V6 会话和 Abaqus/CAE 会话之间建立连接。该连接可用于将模型信息从 CATIA V6 传输到 Abaqus/CAE。随后对 CATIA V6 中模型的修改可以传播到 Abaqus/CAE 模型，同时保留在 Abaqus/CAE 中模型上定义的任何分析功能（如载荷或边界条件）。CATIA V6 装配文件（`.eaf`）格式的 CATIA V6 模型也可以直接导入到 Abaqus/CAE。

**CATIA V5 Associative Interface**：这是 Abaqus/CAE 的附加功能，在 CATIA V5 会话和 Abaqus/CAE 会话之间建立连接。该连接可用于将模型信息从 CATIA V5 传输到 Abaqus/CAE。随后对 CATIA V5 中模型的修改可以传播到 Abaqus/CAE 模型，同时保留在 Abaqus/CAE 中模型上定义的任何分析功能（如载荷或边界条件）。CATIA V5 格式的零件（`.CATPart`）和产品（`.CATProduct`）几何体也可以直接导入到 Abaqus/CAE。

**SolidWorks Associative Interface**：这是 Abaqus/CAE 的附加功能，在 SolidWorks 会话和 Abaqus/CAE 会话之间建立连接。该连接可用于将模型信息从 SolidWorks 传输到 Abaqus/CAE。随后对 SolidWorks 中模型的修改可以传播到 Abaqus/CAE 模型，同时保留在 Abaqus/CAE 中模型上定义的任何分析功能（如载荷或边界条件）。

**Pro/ENGINEER Associative Interface**：这是 Abaqus/CAE 的附加功能，在 Pro/ENGINEER 会话和 Abaqus/CAE 会话之间建立连接。该连接可用于在 Pro/ENGINEER 和 Abaqus/CAE 之间传输模型信息。对 Pro/ENGINEER 中模型的修改可以传播到 Abaqus/CAE 模型，而不影响在 Abaqus/CAE 中模型上定义的任何分析功能（如载荷或边界条件），某些几何修改可以在 Abaqus/CAE 中进行并传播到 Pro/ENGINEER 中的模型。

**Abaqus/CAE Associative Interface for NX**：这是 Abaqus/CAE 的附加功能，在 NX 会话和 Abaqus/CAE 会话之间建立连接。该连接可用于在 NX 和 Abaqus/CAE 之间传输模型数据和传播设计变更。Abaqus/CAE Associative Interface for NX 可以从 Elysium Inc.（[www.elysiuminc.com](http://www.elysiuminc.com)）购买和下载。

**Geometry Translator for CATIA V4**：此附加功能允许用户将 CATIA V4 格式零件和 CATIA V4 装配（`.model`、`.catdata` 和 `.exp` 文件）的几何体直接导入到 Abaqus/CAE。

**Geometry Translator for Parasolid**：此附加功能允许用户将 Parasolid 格式零件和 Parasolid 装配（`.x_t`、`.x_b` 和 `.xmt` 文件）的几何体直接导入到 Abaqus/CAE。

### 转换器实用程序

- Abaqus 转换器随版本一起提供。它们通过 Abaqus 执行程序（"驱动程序"）调用。转换器及其调用命令如下所述：
  - **abaqus fromansys** 将 ANSYS 输入文件转换为 Abaqus 输入文件。
  - **abaqus fromdyna** 将 LS-DYNA 关键字文件转换为 Abaqus 输入文件。
  - **abaqus fromnastran** 将 Nastran 批量数据文件转换为 Abaqus 输入文件。
  - **abaqus frompamcrash** 将 PAM-CRASH 输入文件转换为部分 Abaqus 输入文件。
  - **abaqus fromradioss** 将 RADIOSS 输入文件转换为部分 Abaqus 输入文件。
  - **abaqus adams** 将 Abaqus SIM 数据库文件中的结果转换为 MSC.ADAMS 模态中性（`.mnf`）文件，这是 ADAMS/Flex 所需的格式。
  - **abaqus moldflow** 将 Moldflow 分析的有限元模型信息转换为部分 Abaqus 输入文件。
  - **abaqus tonastran** 将 Abaqus 输入文件转换为 Nastran 批量数据文件格式。
  - **abaqus toOutput2** 将 Abaqus 输出数据库文件转换为 Nastran Output2 文件格式。
  - **abaqus tozaero** 使 Abaqus 和 ZAERO 分析产品之间的气动弹性数据交换成为可能。

### 其他实用程序

- 版本中包含其他程序。它们都通过 Abaqus 执行程序（"驱动程序"）调用。这些实用程序及其调用命令如下所述：
  - **abaqus append** 将单独的结果文件合并为单个文件。
  - **abaqus ascfil** 在 ASCII 和二进制格式之间转换 Abaqus 结果文件，这对于在不同计算机类型之间移动结果文件很有用。
  - **abaqus cosimulation** 使用单个命令运行协同仿真，其中分析作业选项指定两个 Abaqus 作业。
  - **abaqus cse** 运行 SIMULIA Co-Simulation Engine（CSE）Director 进程，该进程管理 Abaqus 与第三方求解器之间的协同仿真。通常，当仅在 Abaqus求解器之间执行协同仿真时，不需要调用 CSE Director 进程；当使用 **abaqus cosimulation** 运行 Abaqus 协同仿真过程时，它会自动调用。
  - **abaqus doc** 使用 Web 浏览器访问 Abaqus 文档集合。
  - **abaqus dymola** 在 Abaqus/Standard 或 Abaqus/Explicit 模型与从 Dymola 导出的模型之间运行协同仿真。
  - **abaqus emloads** 将电磁分析的结果输出转换为用于后续分析的载荷。
  - **abaqus encrypt** 创建一个编码的、密码保护的 Abaqus 输入文件版本，而 **abaqus decrypt** 将加密文件转换回其原始未编码格式。
  - **abaqus fetch** 从随版本提供的示例输入文件库中提取示例输入文件。
  - **abaqus findkeyword** 提供使用指定 Abaqus 选项的示例问题列表。此实用程序将帮助用户找到他们可能首次使用的功能的示例。
  - **abaqus free** 将输入文件中的所有固定格式数据转换为自由格式。
  - **abaqus licensing** 提供 FLEXnet 和 Dassault Systèmes（DS）许可的管理和监控工具。
  - **abaqus make** 编译和链接用户编写的 Abaqus 后处理程序，并创建 Abaqus/Standard 和 Abaqus/Explicit 用户子例程的用户定义库。
  - **abaqus mtxasm** 组装 SIM 文档中包含的单元矩阵，并可选地将组装后的矩阵写入文本文件。
  - **abaqus networkDBConnector** 创建到网络 ODB 服务器的连接，该服务器可用于访问远程输出数据库。
  - **abaqus restartjoin** 将由模型的重启分析生成的输出数据库文件追加到由原始分析生成的输出数据库。
  - **abaqus odbcombine** 将两个或多个 Abaqus 输出数据库文件中的结果数据合并为单个输出数据库文件。
  - **abaqus odbreport** 以文本、HTML 或 CSV 文件格式创建输出数据库信息的组织报告。
  - **abaqus python** 访问 Python 解释器。
  - **abaqus resume** 恢复 Abaqus 分析作业。
  - **abaqus script** 启动 Python 脚本会话。
  - **abaqus sim_version** 将 SIM 数据库文件从一个版本转换到另一个版本，查询 SIM 数据库文件的 SIM 发布级别，或确定您正在使用的代码的 SIM 发布级别。
  - **abaqus substructurecombine** 将由模型的两个子结构生成的模型和结果数据组合为单个输出数据库文件。
  - **abaqus suspend** 暂停 Abaqus 分析作业。
  - **abaqus terminate** 终止 Abaqus 分析作业。
  - **abaqus upgrade** 将以前版本的 Abaqus 输入文件或输出数据库文件升级到当前版本。

### 平台支持

分析产品（Abaqus/Standard、Abaqus/Explicit 和 Abaqus/CFD）和交互产品（Abaqus/CAE 和 Abaqus/Viewer）在以下平台上受支持：
- Windows/x86-64
- Linux/x86-64

### 文档变更

由于 Abaqus Interface for Moldflow 中的翻译功能已集成到 Abaqus/Standard 中作为 **abaqus moldflow** 执行过程，Abaqus Interface for Moldflow User's Guide 已从 Abaqus 文档集合中移除。有关运行 **abaqus moldflow** 执行过程的信息，请参阅《Abaqus Analysis User's Guide》（[Abaqus 分析用户指南](../usb/usb-link.md#usb)）中的["Translating Moldflow data to Abaqus input files," Section 3.2.37](../usb/usb-link.md#usb-int-dmflabaproc)。有关翻译示例，请参阅《Abaqus Example Problems Guide》（[Abaqus 例题指南](../exa/exa-link.md#exa)）中的["Moldflow translation examples," Section 1.3.19](../exa/exa-link.md#exa-sta-moldflow)。




