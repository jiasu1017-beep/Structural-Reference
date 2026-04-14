# 76.7 控制梁截面显示





如果您使用线框零件对梁进行建模，则必须创建引用梁截面的梁截面，并必须将梁截面分配给线框零件。此外，您必须为线框零件分配梁方向。然后，您可以使用 ****View**![](../graphics/images/arrow.gif)**Part Display Options**** 和 ****View**![](../graphics/images/arrow.gif)**Assembly Display Options**** 菜单项在当前视口中查看零件和装配中梁截面的真实显示。

当显示梁截面时，Abaqus/CAE 同时禁用视图切割和模型的缩放和收缩。显示梁截面有助于检查正确的截面是否已分配给特定区域，以及分配的梁方向是否导致预期的截面方向。例如，[图76-6](pt07ch76hla06.md#cargo-crane-example-usi2) 显示了 ["示例：货物起重机，" 入门教程第6.4节](../gsa/gsa-link.md#gsa-bms-exacargocrane) 中描述的轻便起重机上显示的箱型梁截面。

**图76-6** 显示梁截面的货物起重机示例。

![](../graphics/usi-prp-cargocrane.png)

如果您将通用梁截面分配给线框，Abaqus/CAE 将梁截面显示为椭圆，其横截面积和惯性矩（![](../graphics/usi_eqn00695.gif) 和 ![](../graphics/usi_eqn00696.gif)）与您指定的值匹配。如果您将桁架截面分配给线框，Abaqus/CAE 将桁架截面显示为圆，其横截面积与您指定的值匹配。

Abaqus/CAE 不会沿梁的长度渲染梁截面的渐变。如果您的模型包含渐变梁截面，Abaqus/CAE 使用梁的起始截面沿整个长度渲染这些梁。有关渐变梁的更多信息，请参见 ["创建梁截面，" 第12.13.11节](pt03ch12s13s04.md)。

Abaqus/CAE 根据当前的颜色编码和透明度设置渲染梁截面。当这些设置更改时，梁截面的颜色和透明度也会更改。

**控制梁截面显示的步骤：**

1. 找到 **Render beam profiles** 选项。从主菜单栏，选择 ****View**![](../graphics/images/arrow.gif)**Part Display Options**** 或 ****View**![](../graphics/images/arrow.gif)**Assembly Display Options****。在出现的对话框中，点击 **General** 选项卡。
2. 从对话框底部，切换打开 **Render beam profiles** 以显示梁截面。
3. 如果需要，应用 **Scale factor** 到梁截面以增加或减小其大小。默认值为1。
4. 点击 **OK** 实施您的更改并关闭对话框。Abaqus/CAE 以适当的尺寸和正确的方向显示梁截面的截面。您的更改会在会话期间保存。

![](../graphics/images/black4rule.gif) 有关相关信息，请点击以下任一项：
- ["定义截面，" 第12.2.2节](pt03ch12s02s02.md)
- [第76章，"自定义几何和网格显示](pt07ch76.md)"
- ["控制梁截面显示，" 第55.12.5节](pt05ch55s12hlb05.md)
