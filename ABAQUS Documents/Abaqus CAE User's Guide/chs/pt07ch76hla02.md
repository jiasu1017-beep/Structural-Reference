# 76.3 控制边可见性





使用 ****View**![](../graphics/images/arrow.gif)**Part Display Options**** 或 ****View**![](../graphics/images/arrow.gif)**Assembly Display Options**** 菜单项，您可以控制以下内容的可见性：

**几何边**

如果零件或零件实例以隐藏渲染样式显示，Abaqus/CAE 默认抑制被遮挡的几何边。或者，如果您切换打开 **Show dotted lines in hidden render style** 选项，Abaqus/CAE 使用虚线样式显示被遮挡的边。

如果零件或零件实例以着色渲染样式显示，Abaqus/CAE 默认显示边。非线框边（附着在面上的边）以黑色显示。或者，如果您切换关闭 **Show edges in shaded render style** 选项，Abaqus/CAE 抑制边显示。

如果三维零件或零件实例包含具有曲线边的面，默认情况下，Abaqus/CAE 显示从面产生的灰色"轮廓"边，如[图76-2](pt07ch76hla02.md#viw-silhouette) 的隐藏线图所示。

**图76-2** 显示轮廓边的隐藏线图。

![](../graphics/viw-silhouette-nls.png)

与真边不同，轮廓边仅作为视觉辅助；例如，您不能选择或分割轮廓边。或者，如果您切换关闭 **Show silhouette edges** 选项，Abaqus/CAE 仅显示真边。

Abaqus/CAE 使用零件的分面表示来显示弯曲零件，您使用 **Curve refinement** 选项来指定分面程度。有关更多信息，请参见 ["控制曲线细化，" 第76.4节](pt07ch76hla03.md)。

**参考表示**

如果您正在创建中面模型并将中面区域分配给实体模型中的单元，则所选单元的几何包含在参考表示中。默认情况下，Abaqus/CAE 在 Part 模块中显示参考表示。但是，您可以使用 **Show reference representation** 选项在显示零件或装配的所有模块中切换参考表示的显示。切换关闭 **Apply translucency** 以不透明方式显示参考表示，而不是默认的半透明外观。有关参考表示的更多信息，请参见 ["理解参考表示，" 第35.2节](pt04ch35s02.md)。

**高亮面**

您可以控制 Abaqus/CAE 显示零件和装配的高亮几何面的样式。[图76-3](pt07ch76hla02.md#uss-dsp-highlighting) 显示了选中前面部的样本零件的三种视图：左图使用点刻法作为选择方法，中间图显示了等值线的示例，右图显示面片选择。

**图76-3** 使用 **Stippling**、**Isolines** 和 **Facets** 高亮面。

![](../graphics/uss-dsp-highlighting.png)

点刻法提供了性能优势，特别是对于大型复杂零件和装配。使用等值线可以让您比点刻法更容易地以线框模式查看零件或装配。最后，显示零件或装配的所有面片可以帮助您更有效地调试网格，因为网格划分取决于零件或装配中面片的方向。

**网格边**

对于网格零件或从输出数据库导入的零件中的网格边，可见性选项为：

**所有边**

显示所有单元边。要查看模型内部的单元边，您还必须将[渲染样式](pt07ch76hla01.md)设置为线框。

**外部边**

仅显示模型外部的边。

**特征边**

仅显示模型外部的边中计算为特征边的边。特征边位于法线相差超过"特征角度"的单元之间。有关控制特征角度的更多信息，请参见 ["定义网格特征边，" 第76.5节](pt07ch76hla04.md)。

**自由边**

仅显示属于单个单元的边。自由边显示对于定位网格中可能的孔洞或裂缝特别有用。

这些选项如图 [图76-4](pt07ch76hla02.md#viw-edgedisplay) 所示。

**图76-4** 显示网格边显示选项的模型。

![](../graphics/viw-edgeviz-nls.png)

如果以着色渲染样式显示网格，Abaqus/CAE 默认显示边。或者，如果您切换关闭 **Show edges in shaded render style** 选项，Abaqus/CAE 抑制边显示。

除了将隐藏几何边显示为虚线外，您无法控制边的线型、颜色或粗细。

**控制边可见性的步骤：**

1. 找到边可见性选项。从主菜单栏，选择 ****View**![](../graphics/images/arrow.gif)**Part Display Options**** 或 ****View**![](../graphics/images/arrow.gif)**Assembly Display Options****。在出现的对话框中，点击 **General** 选项卡。
2. 选择所需的 **Geometry** 边设置。
3. 选择所需的 **Mesh Edges** 设置。
4. 点击 **OK** 实施您的更改并关闭对话框。您的更改会在会话期间保存。

![](../graphics/images/black4rule.gif) 有关相关信息，请点击以下任一项：
- ["定义网格特征边，" 第76.5节](pt07ch76hla04.md)
- ["选择渲染样式，" 第76.2节](pt07ch76hla01.md)
- [第76章，"自定义几何和网格显示](pt07ch76.md)"
