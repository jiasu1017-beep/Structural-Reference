# 8.3 在Abaqus分析中考虑非线性

**摘要：** 本节讨论如何在Abaqus分析中考虑非线性。主要关注几何非线性。

## 8.3.1 几何非线性

在分析中考虑几何非线性的影响只需对Abaqus/Standard模型进行少量修改。您需要确保在<a rel="xbook" href="../key/key-link.htm#usb-kws-hstep"><span class="abqkeywordnostar">\*STEP</span></a>选项上将<span class="abqparameter">NLGEOM</span>参数设置为<span class="abqparamvalue">YES</span>，以使步骤定义考虑几何非线性。在Abaqus/Explicit中，这是默认设置。您还需要按照8.2.3节"Abaqus/Standard中的自动增量控制"中的讨论设置时间增量参数。

以下输入描述了一个静态分析，其中载荷施加在5个时间单位内，初始时间增量为1个时间单位；最小和最大时间增量分别设置为0.0001和1.5：

![静力学分析输入]( ../graphics/gss-c7-delta-t-input.png )

Abaqus将在第一个增量中施加总载荷的20%（1.0/5.0），如果遇到收敛问题且需要的增量小于0.0001，Abaqus将终止分析。如果由于求解容易收敛而使时间增量增大，Abaqus可使用的最大时间增量为1.5。

**局部方向**

在几何非线性分析中，局部材料方向可能随每个单元的变形而旋转。对于壳单元、梁单元和桁架单元，局部材料方向始终随变形而旋转。对于实体单元，只有当单元引用了<a rel="xbook" href="../key/key-link.htm#usb-kws-morientation"><span class="abqkeywordnostar">\*ORIENTATION</span></a>选项时，局部材料方向才随变形旋转；否则，默认的局部材料方向在整个分析过程中保持不变。

通过使用<a rel="xbook" href="../key/key-link.htm#usb-kws-mtransform"><span class="abqkeywordnostar">\*TRANSFORM</span></a>选项在节点上定义的局部方向在整个分析过程中保持固定；它们不会随变形而旋转。有关更多详细信息，请参阅《Abaqus分析用户手册》第2.1.5节"变换坐标系"。

**对后续步骤的影响**

一旦您在某个步骤中包含了几何非线性，该非线性将被考虑在所有后续步骤中。如果在后续步骤中未请求非线性几何效应，Abaqus将发出警告，指出它们仍将在该步骤中被考虑。

**其他几何非线性效应**

当激活几何非线性时，模型中的大变形并不是唯一需要考虑的重要效应。Abaqus/Standard还在单元刚度计算中包含由施加的载荷引起的项，即所谓的载荷刚度。这些项改善了收敛行为。此外，壳中的膜载荷以及电缆和梁中的轴向载荷在响应横向载荷时贡献了这些结构的大部分刚度。通过包含几何非线性，响应横向载荷时的膜刚度也将被考虑。

## 8.3.2 材料非线性

向Abaqus模型添加材料非线性将在第10章"材料"中讨论。

## 8.3.3 边界非线性

边界非线性的介绍将在第12章"接触"中讨论。
