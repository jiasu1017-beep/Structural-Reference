# Abaqus Example Problems Guide





[Trademarks and Legal Notices](../popups/usb-lgl.md)

[Conversion Tables, Constants, and Material Properties](../popups/usb-tbl.md)

[Preface](../popups/usb-pre.md)





1 # Introduction






这是 Abaqus 的例题指南。它包含许多示例，展示了程序在常见问题类型中的使用。其中一些问题相当困难，需要结合代码中的多种功能。

这些问题有两个目的：通过在非平凡案例中运行代码来验证 Abaqus 的功能，并为需要处理相对不熟悉的问题类型的用户提供指导。在每个示例中，指南的讨论说明了为什么包含该示例，并引导读者了解分析的标准方法：单元和网格选择、材料模型以及结果讨论。许多问题使用不同的单元类型、网格密度和其他变体进行分析。

所有分析的输入数据文件都随 Abaqus 版本一起提供在压缩存档文件中。使用 **abaqus fetch** 实用程序来提取这些输入文件以供使用。例如，要获取输入文件 [boltpipeflange_3d_cyclsym.inp](../eif/boltpipeflange_3d_cyclsym.inp)，请键入

```
abaqus fetch job=boltpipeflange_3d_cyclsym.inp
```

参数化研究脚本（`.psf`）和用户子程序（`.f`）文件可以以相同的方式获取。通过省略文件扩展名可以获取特定问题的所有文件。**abaqus fetch** 实用程序的详细说明见 ["Fetching sample input files," Section 3.2.16 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-dfetchproc)。

有时搜索输入文件很有用。**findkeyword** 实用程序用于定位包含用户指定输入的输入文件。该实用程序在 ["Querying the keyword/problem database," Section 3.2.15 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-dkeywordproc) 中定义。

要重现某些示例中报告的解决方案图形表示，可能需要增加输入文件中使用的输出频率。例如，在 ["Linear analysis of the Indian Point reactor feedwater line," Section 2.2.2](ch02s02aex81.md) 中，只有当解每个增量都写入结果文件时，才能获得指南中出现的图形；也就是说，需要将输入文件更改为读取

```
*NODE FILE, ..., FREQUENCY=1
```

而不是现在的 `FREQUENCY=100`。

除了 Abaqus Example Problems Guide，还有其他两本包含示例问题的指南。[Abaqus Benchmarks Guide](../bmk/bmk-link.md#bmk) 包含基准问题（包括 NAFEMS 测试问题套件）和用于评估 Abaqus 性能的标准分析。本指南中的测试是简单几何或实际问题简化版本的多单元测试。[Abaqus Verification Guide](../ver/ver-link.md#ver) 包含大量示例，旨在对基本建模功能进行初步验证。

新 Abaqus 版本的认证过程包括运行和验证 [Abaqus Example Problems Guide](book01.md)、[Abaqus Benchmarks Guide](../bmk/bmk-link.md#bmk) 和 [Abaqus Verification Guide](../ver/ver-link.md#ver) 中所有问题的结果。





1 # 1.1 Static and quasi-static stress analyses






- ["Axisymmetric analysis of bolted pipe flange connections," Section 1.1.1](ch01s01aex01.md)
- ["Elastic-plastic collapse of a thin-walled elbow under in-plane bending and internal pressure," Section 1.1.2](ch01s01aex02.md)
- ["Parametric study of a linear elastic pipeline under in-plane bending," Section 1.1.3](ch01s01aex03.md)
- ["Indentation of an elastomeric foam specimen with a hemispherical punch," Section 1.1.4](ch01s01aex04.md)
- ["Collapse of a concrete slab," Section 1.1.5](ch01s01aex05.md)
- ["Jointed rock slope stability," Section 1.1.6](ch01s01aex06.md)
- ["Notched beam under cyclic loading," Section 1.1.7](ch01s01aex07.md)
- ["Uniaxial ratchetting under tension and compression," Section 1.1.8](ch01s01aex08.md)
- ["Hydrostatic fluid elements: modeling an airspring," Section 1.1.9](ch01s01aex09.md)
- ["Shell-to-solid submodeling and shell-to-solid coupling of a pipe joint," Section 1.1.10](ch01s01aex10.md)
- ["Stress-free element reactivation," Section 1.1.11](ch01s01aex11.md)
- ["Transient loading of a viscoelastic bushing," Section 1.1.12](ch01s01aex12.md)
- ["Indentation of a thick plate," Section 1.1.13](ch01s01aex13.md)
- ["Damage and failure of a laminated composite plate," Section 1.1.14](ch01s01aex14.md)
- ["Analysis of an automotive boot seal," Section 1.1.15](ch01s01aex15.md)
- ["Pressure penetration analysis of an air duct kiss seal," Section 1.1.16](ch01s01aex16.md)
- ["Self-contact in rubber/foam components: jounce bumper," Section 1.1.17](ch01s01aex17.md)
- ["Self-contact in rubber/foam components: rubber gasket," Section 1.1.18](ch01s01aex18.md)
- ["Submodeling of a stacked sheet metal assembly," Section 1.1.19](ch01s01aex19.md)
- ["Axisymmetric analysis of a threaded connection," Section 1.1.20](ch01s01aex20.md)
- ["Direct cyclic analysis of a cylinder head under cyclic thermal-mechanical loadings," Section 1.1.21](ch01s01aex21.md)
- ["Erosion of material (sand production) in an oil wellbore," Section 1.1.22](ch01s01aex22.md)
- ["Submodel stress analysis of pressure vessel closure hardware," Section 1.1.23](ch01s01aex23.md)
- ["Using a composite layup to model a yacht hull," Section 1.1.24](ch01s01aex24.md)
- ["Energy computations in a contact analysis," Section 1.1.25](ch01s01aex25.md)





1 # 1 Static Stress/Displacement Analyses






- ["Static and quasi-static stress analyses," Section 1.1](ch01s01.md)
- ["Buckling and collapse analyses," Section 1.2](ch01s02.md)
- ["Forming analyses," Section 1.3](ch01s03.md)
- ["Fracture and damage," Section 1.4](ch01s04.md)
- ["Import analyses," Section 1.5](ch01s05.md)





1 # 1.1.1 Axisymmetric analysis of bolted pipe flange connections






**产品：** Abaqus/Standard   

螺栓管道法兰连接是许多管道系统中的常见且重要的部件。这种连接通常由管道轮毂、带螺栓孔的管道法兰、螺栓和螺母组以及垫圈组成。这些部件在紧固过程中以及施加内压和温度等操作载荷时相互作用的。经常有关于这些部件之间不同相互作用类型的实验和数值研究。这些研究包括：产生均匀螺栓应力的螺栓预紧程序分析（S브리얼和 Ezell，1992）、螺纹接触分析（Fukuoka，1992；Chaaban 和 Muzzo，1991）以及整个管道接头组件的完整应力分析（Sawa 等，1991）。为了建立最佳设计，完整应力分析确定了以下因素：控制密封性能的接触应力、螺栓力与内压之间的关系、有效垫圈密封宽度以及螺栓中产生的弯矩。本示例展示瞭如何使用经济的轴对称模型进行这种设计分析，以及如何通过与使用三维段模型的模拟结果进行比较来评估轴对称解的准确性。此外，还分析了使用多级子结构的几个三维模型，以演示具有大量保留自由度、子结构的使用。最后，分析了包含刚度矩阵的三维模型，以演示矩阵输入功能的使用。

### 几何和模型

[图 1.1.1-1](ch01s01aex01.md#sxmpipeflange-schematic) 中描述了正在分析的螺栓接头组件。各个部件的几何和尺寸来自 Sawa 等（1991），稍作修改以简化建模。轮毂和垫圈的内壁半径均为 25 mm。管道法兰和垫圈的外壁半径分别为 82.5 mm 和 52.5 mm。垫圈厚度为 2.5 mm。管道法兰有八个螺栓孔，均匀分布在半径为 65 mm 的节圆上。在本分析中，螺栓孔半径被修改为与螺栓相同：8 mm。螺栓头（支承面）假定为圆形，其半径为 12 mm。

螺栓和管道轮毂/法兰的杨氏模量为 206 GPa，泊松比为 0.3。垫圈使用实体连续体或垫圈单元建模。当使用连续体单元时，垫圈的杨氏模量 *E* 等于 68.7 GPa，其泊松比 ![](../graphics/exa_eqn00001.gif) 等于 0.3。

当使用垫圈单元时，使用线性垫圈压力/闭合关系，有效"法向刚度"![](../graphics/exa_eqn00002.gif) 等于材料杨氏模量除以厚度，因此 ![](../graphics/exa_eqn00003.gif) 27.48 GPa/mm。类似地，使用线性剪切应力/剪切运动关系，有效剪切刚度 ![](../graphics/exa_eqn00004.gif) 等于材料剪切模量除以厚度，因此 ![](../graphics/exa_eqn00005.gif) 10.57 GPa/mm。膜行为使用 68.7 GPa 的杨氏模量和 0.3 的泊松比指定。所有接触区域（支承面与法兰之间以及垫圈与轮毂之间）假定为粘接触条件。忽略螺栓杆与螺栓孔之间的接触。

管道接头对称半部的有限元理想化模型如[图 1.1.1-2](ch01s01aex01.md#sxmpipeflange-axisym) 和[图 1.1.1-3](ch01s01aex01.md#sxmpipeflange-3dmodel)所示，分别对应于轴对称和三维分析。轴对称分析使用的网格包括管道轮毂/法兰和垫圈的网格以及螺栓的单独网格。在[图 1.1.1-2](ch01s01aex01.md#sxmpipeflange-axisym)中，顶图显示了管道轮毂和法兰的网格，螺栓孔区域以较浅的颜色显示；底图显示了垫圈和螺栓到位的整体网格。

对于轴对称模型，在管道轮毂/法兰的整个网格中使用二阶减缩积分单元 CAX8R。垫圈使用 CAX8R 实体连续体单元或 GKAX6 垫圈单元建模。垫圈与管道轮毂/法兰之间的接触使用接触对建模，接触对介于在接触区域中定义的单元面或此类基于单元的表面与基于节点的表面之间。在轴对称分析中，必须正确建模螺栓和穿孔法兰。由于螺栓不承受环向应力，因此将螺栓建模为平面应力单元。为此目的使用了二阶减缩积分平面应力单元 CPS8R。与单元面关联的接触表面定义自动解释了平面应力条件。为了考虑接头中使用的所有八个螺栓，必须计算螺栓杆和螺栓头组合横截面积，并使用实体单元的面积属性将面积适当重新分配到螺栓网格。接触面积自动调整。

[图 1.1.1-4](ch01s01aex01.md#sxmpipeflange-xsects) 说明了螺栓头和杆的横截面视图。每个平面应力单元代表延伸到 *x*–*y* 平面之外的体积。例如，单元 *A* 代表的体积计算为 (![](../graphics/exa_eqn00006.gif)) (![](../graphics/exa_eqn00007.gif))。同样，单元 *B* 代表的体积计算为 (![](../graphics/exa_eqn00008.gif)) (![](../graphics/exa_eqn00009.gif))。特定单元在 *x*–*z* 平面中的横截面积可以计算为

![](../graphics/exa_eqn00010.gif)

其中 *R* 是螺栓头半径 ![](../graphics/exa_eqn00011.gif) 或杆半径 ![](../graphics/exa_eqn00012.gif)（取决于单元位置），而 ![](../graphics/exa_eqn00013.gif) 和 ![](../graphics/exa_eqn00014.gif) 分别是给定单元左侧和右侧的 *x* 坐标。

如果横截面积除以相应的单元宽度 ![](../graphics/exa_eqn00015.gif) 和 ![](../graphics/exa_eqn00016.gif)，我们得到代表性单元厚度。将每个单元厚度乘以八（模型中的螺栓数量）会产生在实体截面定义中找到的厚度值。

与模型接触表面上的螺栓头单元关联的横截面积用于计算用于定义模型基于节点的表面的节点表面积。再次参考[图 1.1.1-4](ch01s01aex01.md#sxmpipeflange-xsects)，单个螺栓的节点接触面积计算如下：

![](../graphics/exa_eqn00017.gif)

![](../graphics/exa_eqn00018.gif)

![](../graphics/exa_eqn00019.gif)

其中 ![](../graphics/exa_eqn00020.gif) 到 ![](../graphics/exa_eqn00021.gif) 是与接触节点 1-9 关联的接触面积，![](../graphics/exa_eqn00022.gif) 到 ![](../graphics/exa_eqn00023.gif) 是与螺栓头单元 *C*–*F* 关联的横截面积。将上述面积乘以八（模型中的螺栓数量）可提供在接触属性定义中找到的节点接触面积。

在轴对称分析中处理管道法兰中螺栓孔存在的一种常见方法是，对螺栓孔区域网格中使用的材料属性进行均质化，并使用对应该区域中较弱材料的不均匀材料属性。确定穿孔平板有效材料属性的一般指南见 ASME Section VIII Div 2 Article 4-9。对于正在研究的结构类型（不是平板），确定有效材料属性的常用方法是计算弹性模量折减系数，即节圆中韧带面积与节圆环形面积的比率。在本模型中，节圆的环形面积由 ![](../graphics/exa_eqn00024.gif) 6534.51 mm2 给出，螺栓孔的总面积由 ![](../graphics/exa_eqn00025.gif) 1608.5 mm2 给出。因此，折减系数简单为 ![](../graphics/exa_eqn00026.gif) 0.754。有效的平面内弹性模量 ![](../graphics/exa_eqn00027.gif) 和 ![](../graphics/exa_eqn00028.gif) 通过将这些模量 ![](../graphics/exa_eqn00029.gif) 和 ![](../graphics/exa_eqn00030.gif) 乘以此系数获得。我们假定 *r*–*z* 平面中的材料各向同性；因此，![](../graphics/exa_eqn00031.gif) 环向方向的模量 ![](../graphics/exa_eqn00032.gif) 应该非常小，选择为 ![](../graphics/exa_eqn00033.gif) 106。然后根据有效弹性模量计算平面内剪切模量：![](../graphics/exa_eqn00034.gif) 环向方向的剪切模量也以类似方式计算，但将 ![](../graphics/exa_eqn00001.gif) 设置为零（它们未在轴对称模型中使用）。因此，我们有 ![](../graphics/exa_eqn00035.gif) 155292 MPa、![](../graphics/exa_eqn00036.gif) 0.155292 MPa、![](../graphics/exa_eqn00037.gif) 59728 MPa 和 ![](../graphics/exa_eqn00038.gif) 0.07765 MPa。这些正交弹性模量使用工程常数为网格的螺栓孔部分指定。

无子结构的三维分析网格（如[图 1.1.1-3](ch01s01aex01.md#sxmpipeflange-3dmodel)所示）代表管道接头的 22.5 段，使用二阶减缩积分砖单元 C3D20R 用于管道轮毂/法兰和螺栓。垫圈使用 C3D20R 单元或 GK3D18 单元建模。顶图显示了管道轮毂和法兰的网格，底图显示了垫圈和螺栓（颜色较浅）。接触通过在接触区域中对元素特定面进行分组而定义的接触表面的相互作用来建模。对于主表面和从表面都是可变形的三维接触，必须使用小滑移接触对公式来表明接触表面之间发生小的相对滑动。不需要对三维模型中使用的材料属性进行特殊调整，因为所有部件都进行了适当建模。

测试了四种使用子结构建模法兰的不同网格。为[图 1.1.1-3](ch01s01aex01.md#sxmpipeflange-3dmodel)所示的整个 22.5 段法兰创建了第一级子结构，而垫圈和螺栓的网格与之前相同。与螺栓帽接触的法兰上的节点形成基于节点的表面，与垫圈接触的法兰上的节点形成另一个基于节点的表面。这些基于节点的表面将与螺栓帽和垫圈上的主表面形成接触对，主表面使用表面定义选项定义。子结构上保留的自由度包括这些基于节点的表面中节点的所有三个自由度，以及法兰 0 和 22.5 面上节点的所有三个自由度。适当的边界条件在子结构使用级别指定。

通过相对于 22.5 平面反射第一级子结构来创建 45 的第二级子结构。从属于反射子结构的 22.5 面上的节点在所有三个自由度上约束到原始第一级子结构的 22.5 面对应的节点。反射子结构对应的半螺栓和垫圈扇区也通过反射构建。保留的自由度包括所有接触节点集的所有三个自由度以及法兰 0 和 45 面上节点的所有三个自由度。MPC 类型 CYCLSYM 用于在这些两个面上施加循环对称边界条件。

通过相对于 45 平面反射原始 45 二级子结构并将其连接到原始 45 子结构来创建 90 的第三级子结构。模型 45-90 扇区对应的垫圈和螺栓的剩余部分通过反射和适当的约束创建。在这种情况下，不必在法兰的 0 和 90 面上保留任何自由度，因为这个 90 子结构不会连接到其他子结构，可以在校结构创建级别指定适当的边界条件。

最终的子结构模型是通过相对于垫圈垂直于 *y* 轴的对称平面镜像 90 网格来设置的。因此，当不使用子结构时，原本大型分析（![](../graphics/exa_eqn00039.gif) 750,000 个未知数）可以通过使用第三级子结构两次来方便地求解（![](../graphics/exa_eqn00039.gif) 80,000 个未知数）。使用稀疏求解器，因为它显著减少了此模型的运行时间。

最后，通过将[图 1.1.1-3](ch01s01aex01.md#sxmpipeflange-3dmodel)所示的整个 22.5 段法兰的单元替换为刚度矩阵来创建基于矩阵的三维模型，而垫圈和螺栓的网格与之前相同。法兰与垫圈之间以及法兰与螺栓帽之间的接触使用与子结构模型相同的基于节点的从属表面进行建模。适当的边界条件与应用在与子结构的三维模型相同的方式应用。

### 载荷和边界条件

唯一的边界条件是对称边界条件。在轴对称模型中，![](../graphics/exa_eqn00040.gif) 0 应用于垫圈的对称平面和螺栓底部。在三维模型中，![](../graphics/exa_eqn00041.gif) 0 应用于垫圈的对称平面以及螺栓底部。![](../graphics/exa_eqn00042.gif)0 和 ![](../graphics/exa_eqn00042.gif)22.5 平面也是对称平面。在 ![](../graphics/exa_eqn00042.gif)22.5 平面上，通过调用适当的节点变换并在对此对称平面中的局部方向施加边界条件来强制执行对称边界条件。这些变换使用局部坐标系定义实现。在两个对称平面上，![](../graphics/exa_eqn00040.gif) 0 的对称边界条件在除与 C BIQUAD MPC 关联的从属节点和接触表面一侧上的节点之外的的所有地方施加。第二个例外是为了避免过度约束问题，如果边界条件与与粗糙摩擦规范关联的拉格朗日乘数约束方向相同，则会出现此类问题。

在使用子结构的模型中，边界条件根据所使用的子结构指定。对于第一级 22.5 子结构，边界条件和约束方程与[图 1.1.1-3](ch01s01aex01.md#sxmpipeflange-3dmodel)所示的三维模型相同。对于 45 二级子结构，对称边界条件在 ![](../graphics/exa_eqn00043.gif)45 平面上用约束方程 ![](../graphics/exa_eqn00044.gif) 0 强制执行。也可以使用变换。对于 90 三级子结构，面 ![](../graphics/exa_eqn00045.gif)90 用边界条件 ![](../graphics/exa_eqn00046.gif) 0 约束。

对于包含矩阵的三维模型，对称边界条件应用节点变换。这些节点的刚度矩阵条目也在局部坐标中。

通过将预紧节点与预紧截面关联，向每个螺栓施加 15 kN 的夹紧力。预紧截面通过表面定义识别。然后通过向预紧节点施加集中载荷来规定预紧。在轴对称分析中，由于有八个螺栓，施加的实际载荷为 120 kN。在没有子结构的三维模型中，由于只建模了半个螺栓，施加的实际载荷为 7.5 kN。在使用子结构的模型中，所有半螺栓都加载了 7.5 kN 的力。对于所有模型，预紧截面规定在螺栓杆中间左右。

在所有分析的所有表面相互作用中假定为粘接触条件，并用粗糙摩擦和无分离接触模拟。

### 结果和讨论

所有分析均作为小位移分析进行。

[图 1.1.1-5](ch01s01aex01.md#sxmpipeflange-normsol) 显示了当使用实体连续体单元建模垫圈时，轴对称（底部）和三维（顶部）分析预测的垫圈在垫圈与管道轮毂/法兰界面处的法向应力分布的俯视图。该图显示，压缩法向应力在垫圈外边缘最高，向内径向减小，在约 35 mm 半径处从压缩变为拉伸，这与 Sawa 等（1991）报告的发现一致。轴对称和三维分析在整体解方面的良好一致性非常明显，表明对于此类问题，轴对称分析为三维分析提供了一种简单但相当准确的替代方案。

[图 1.1.1-6](ch01s01aex01.md#sxmpipeflange-normgas) 显示了当使用垫圈单元建模垫圈时，轴对称（底部）和三维（顶部）分析预测的垫圈在垫圈与管道轮毂/法兰界面处的法向应力分布的俯视图。轴对称和三维分析在整体解方面也显示出良好的一致性。垫圈在约 40 mm 半径处开始承受压缩载荷，与之前结果相差 5 mm。这种差异是因为垫圈单元无法在其厚度方向承受拉伸载荷。这个解在物理上更真实，因为在大多数情况下，垫圈在受到拉伸载荷时会与相邻部件分离。从使用连续体单元对垫圈建模的输入文件中移除垫圈/法兰接触表面定义中的无分离接触，与[图 1.1.1-6](ch01s01aex01.md#sxmpipeflange-normgas) 中获得的结果非常一致（因为在那种情况下，垫圈中的实体连续体单元无法在垫圈厚度方向承受拉伸载荷）。

可以修改本示例中的模型以研究其他因素，例如垫圈的有效密封宽度或垫圈在操作载荷下的密封性能。垫圈单元具有允许在垫圈厚度方向定义非常复杂行为的优势。垫圈单元还可以使用 Abaqus 提供的任何小应变材料模型，包括用户定义的材料模型。[图 1.1.1-7](ch01s01aex01.md#sxmpipeflange-isogas) 显示了当为垫圈单元规定各向同性材料属性时，轴对称（底部）和三维（顶部）分析预测的垫圈在垫圈与管道轮毂/法兰界面处的法向应力分布的比较。[图 1.1.1-7](ch01s01aex01.md#sxmpipeflange-isogas) 中的结果与使用实体和轴对称单元模拟垫圈的分析中获得的结果（图 1.1.1-5](ch01s01aex01.md#sxmpipeflange-normsol)）比较良好。

[图 1.1.1-8](ch01s01aex01.md#sxmpipeflange-zlinestress) 显示了在平面 ![](../graphics/exa_eqn00047.gif) 0 中垫圈在界面处的法向应力分布。结果绘制用于：仅包含实体连续体单元且无子结构的三维模型、包含矩阵的三维模型，以及上述描述的包含子结构的四个模型。

有一种执行过程可以将两个子结构输出数据库中的模型和结果数据组合到单个输出数据库中。有关更多信息，请参阅 ["Combining output from substructures," Section 3.2.22 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-dsubstructurecombineproc)。

本示例还可用于演示准牛顿非线性求解器的有效性。该求解器在几个连续平衡迭代中使用廉价的近似刚度矩阵更新，而不是像默认的完整牛顿方法那样在每次迭代中进行完整的刚度矩阵分解。准牛顿方法导致更多但较便宜的迭代次数，以及计算成本的净节省。

### 输入文件

[boltpipeflange_axi_solidgask.inp](../eif/boltpipeflange_axi_solidgask.inp)

使用实体连续体单元建模垫圈的轴对称分析。

[boltpipeflange_axi_node.inp](../eif/boltpipeflange_axi_node.inp)

boltpipeflange_axi_solidgask.inp 和 boltpipeflange_axi_gkax6.inp 的节点定义。

[boltpipeflange_axi_element.inp](../eif/boltpipeflange_axi_element.inp)

boltpipeflange_axi_solidgask.inp 的单元定义。

[boltpipeflange_3d_solidgask.inp](../eif/boltpipeflange_3d_solidgask.inp)

使用实体连续体单元建模垫圈的三维分析。

[boltpipeflange_axi_gkax6.inp](../eif/boltpipeflange_axi_gkax6.inp)

使用垫圈单元建模垫圈的轴对称分析。

[boltpipeflange_3d_gk3d18.inp](../eif/boltpipeflange_3d_gk3d18.inp)

使用垫圈单元建模垫圈的三维分析。

[boltpipeflange_3d_substr1.inp](../eif/boltpipeflange_3d_substr1.inp)

使用第一级子结构（22.5 模型）的三维分析。

[boltpipeflange_3d_substr2.inp](../eif/boltpipeflange_3d_substr2.inp)

使用第二级子结构（45 模型）的三维分析。

[boltpipeflange_3d_substr3_1.inp](../eif/boltpipeflange_3d_substr3_1.inp)

一次使用第三级子结构（90 模型）的三维分析。

[boltpipeflange_3d_substr3_2.inp](../eif/boltpipeflange_3d_substr3_2.inp)

两次使用第三级子结构（90 镜像模型）的三维分析。

[boltpipeflange_3d_gen1.inp](../eif/boltpipeflange_3d_gen1.inp)

被 boltpipeflange_3d_substr1.inp 和 boltpipeflange_3d_gen2.inp 引用的第一级子结构生成数据。

[boltpipeflange_3d_gen2.inp](../eif/boltpipeflange_3d_gen2.inp)

被 boltpipeflange_3d_substr2.inp 和 boltpipeflange_3d_gen3.inp 引用的第二级子结构生成数据。

[boltpipeflange_3d_gen3.inp](../eif/boltpipeflange_3d_gen3.inp)

被 boltpipeflange_3d_substr3_1.inp 和 boltpipeflange_3d_substr3_2.inp 引用的第三级子结构生成数据。

[boltpipeflange_3d_node.inp](../eif/boltpipeflange_3d_node.inp)

用于 boltpipeflange_3d_substr1.inp、boltpipeflange_3d_substr2.inp、boltpipeflange_3d_substr3_1.inp、boltpipeflange_3d_substr3_2.inp、boltpipeflange_3d_cyclsym.inp、boltpipeflange_3d_gen1.inp、boltpipeflange_3d_gen2.inp 和 boltpipeflange_3d_gen3.inp 的节点坐标。

[boltpipeflange_3d_cyclsym.inp](../eif/boltpipeflange_3d_cyclsym.inp)

与文件 boltpipeflange_3d_substr2.inp 相同，只是使用了 CYCLSYM 类型 MPC。

[boltpipeflange_3d_missnode.inp](../eif/boltpipeflange_3d_missnode.inp)

与文件 boltpipeflange_3d_gk3d18.inp 相同，只是为垫圈单元使用了生成缺失节点的选项。

[boltpipeflange_3d_isomat.inp](../eif/boltpipeflange_3d_isomat.inp)

与文件 boltpipeflange_3d_gk3d18.inp 相同，只是垫圈单元使用 [*MATERIAL](../key/key-link.md#usb-kws-mmaterial) 选项建模为各向同性。

[boltpipeflange_3d_ortho.inp](../eif/boltpipeflange_3d_ortho.inp)

与文件 boltpipeflange_3d_gk3d18.inp 相同，只是垫圈单元使用 [*ORIENTATION](../key/key-link.md#usb-kws-morientation) 选项建模为正交各向异性。

[boltpipeflange_axi_isomat.inp](../eif/boltpipeflange_axi_isomat.inp)

与文件 boltpipeflange_axi_gkax6.inp 相同，只是垫圈单元使用 [*MATERIAL](../key/key-link.md#usb-kws-mmaterial) 选项建模为各向同性。

[boltpipeflange_3d_usr_umat.inp](../eif/boltpipeflange_3d_usr_umat.inp)

与文件 boltpipeflange_3d_gk3d18.inp 相同，只是垫圈单元使用用户子程序 [`UMAT`](../sub/sub-link.md#sub-xsl-umat) 建模为各向同性。

[boltpipeflange_3d_usr_umat.f](../eif/boltpipeflange_3d_usr_umat.f)

用于 boltpipeflange_3d_usr_umat.inp 的用户子程序 [`UMAT`](../sub/sub-link.md#sub-xsl-umat)。

[boltpipeflange_3d_solidnum.inp](../eif/boltpipeflange_3d_solidnum.inp)

与文件 boltpipeflange_3d_gk3d18.inp 相同，只是垫圈单元使用实体单元编号。

[boltpipeflange_3d_matrix.inp](../eif/boltpipeflange_3d_matrix.inp)

包含矩阵和使用实体连续体单元建模垫圈的三维分析。

[boltpipeflange_3d_stiffPID4.inp](../eif/boltpipeflange_3d_stiffPID4.inp)

表示包含矩阵的三维分析中法兰段部分刚度的矩阵。

[boltpipeflange_3d_stiffPID5.inp](../eif/boltpipeflange_3d_stiffPID5.inp)

表示包含矩阵的三维分析中法兰段剩余部分刚度的矩阵。

[boltpipeflange_3d_qn.inp](../eif/boltpipeflange_3d_qn.inp)

与文件 boltpipeflange_3d_gk3d18.inp 相同，只是使用了准牛顿非线性求解器。

### 参考文献

Bibel, G. D., and R. M. Ezell, "An Improved Flange Bolt-Up Procedure Using Experimentally Determined Elastic Interaction Coefficients," Journal of Pressure Vessel Technology, vol. 114, pp. 439-443, 1992.

Chaaban, A., and U. Muzzo, "Finite Element Analysis of Residual Stresses in Threaded End Closures," Transactions of ASME, vol. 113, pp. 398-401, 1991.

Fukuoka, T., "Finite Element Simulation of Tightening Process of Bolted Joint with a Tensioner," Journal of Pressure Vessel Technology, vol. 114, pp. 433-438, 1992.

Sawa, T., N. Higurashi, and H. Akagawa, "A Stress Analysis of Pipe Flange Connections," Journal of Pressure Vessel Technology, vol. 113, pp. 497-503, 1991.

### 图

**图 1.1.1-1** 螺栓接头示意图。所有尺寸单位为 mm。

![](../graphics/sxmpipeflange-schematic-nls.png)

**图 1.1.1-2** 螺栓接头的轴对称模型。

![](../graphics/sxmpipeflange-axisym.png)

**图 1.1.1-3** 螺栓接头的 22.5 段三维模型。

![](../graphics/sxmpipeflange-3dmodel.png)

**图 1.1.1-4** 螺栓头和杆的横截面视图。

![](../graphics/sxmpipeflange-xsects-nls.png)

**图 1.1.1-5** 当使用实体单元建模垫圈时，垫圈接触表面的法向应力分布：三维与轴对称结果比较。

![](../graphics/sxmpipeflange-normsol.png)

**图 1.1.1-6** 当使用垫圈单元并直接规定垫圈行为时，垫圈接触表面的法向应力分布：三维与轴对称结果比较。

![](../graphics/sxmpipeflange-normgas.png)

**图 1.1.1-7** 当使用垫圈单元并使用各向同性材料属性时，垫圈接触表面的法向应力分布：三维与轴对称结果比较。

![](../graphics/sxmpipeflange-isogas.png)

**图 1.1.1-8** 沿直线 ![](../graphics/exa_eqn00047.gif) 0 的垫圈接触表面的法向应力分布，用于有和没有子结构的模型。

![](../graphics/sxmpipeflange-zlinestress.png)





