# 76.8 控制壳厚度显示





如果您使用壳单元对分析中的相对较薄的组件进行建模，您可以使用 ****View**![](../graphics/images/arrow.gif)**Part Display Options**** 和 ****View**![](../graphics/images/arrow.gif)**Assembly Display Options**** 菜单选项来查看模型中这些壳单元的实际厚度。显示壳厚度使您能够检查壳几何相对于模型其余部分的厚度。您可以应用比例因子来减少或增加会话的壳厚度显示。[图76-7](pt07ch76hla07.md#usv-gen-shellthickness-example) 显示了在 ["示例：加筋板上的爆炸载荷，" 入门教程第10.5节](../gsa/gsa-link.md#gsa-mat-exablastload) 中描述的加筋板模型上显示的比例因子更改效果。

**图76-7** 从上到下：壳厚度比例因子设置为1（默认）、2和4。

![](../graphics/uss-dsp-shellthickness-graphic.png)

Abaqus/CAE 仅对三维壳单元渲染壳厚度；轴对称壳单元（如 SAX1 单元）不显示厚度。显示壳厚度时，Abaqus/CAE 也会渲染壳几何的边缘，除非视口中显示了视图切割。Abaqus/CAE 根据当前的颜色编码和透明度设置渲染壳厚度。当这些设置更改时，壳厚度的颜色和透明度也会更改。

如果使用离散场定义了壳厚度或壳偏移，**Render shell thickness** 选项无效。壳始终以零厚度和无偏移显示。

**控制壳厚度显示的步骤：**

1. 找到 **Render shell thickness** 选项。从主菜单栏，选择 ****View**![](../graphics/images/arrow.gif)**Part Display Options**** 或 ****View**![](../graphics/images/arrow.gif)**Assembly Display Options****。在出现的对话框中，点击 **General** 选项卡。
2. 从对话框底部，切换打开 **Render shell thickness** 以显示模型中壳截面的壳厚度。
3. 如果需要，应用 **Scale factor** 到壳厚度以增加或减小其厚度。默认值为1，它产生壳厚度设置的逼真渲染。
4. 点击 **OK** 实施您的更改并关闭对话框。Abaqus/CAE 以适当的厚度显示所选零件或装配中的壳截面。您的更改会在会话期间保存。

![](../graphics/images/black4rule.gif) 有关相关信息，请点击以下任一项：
- ["定义截面，" 第12.2.3节](pt03ch12s02s03.md)
- [第76章，"自定义几何和网格显示](pt07ch76.md)"
- ["控制壳厚度显示，" 第55.12.6节](pt05ch55s12hlb06.md)
