# 76.4 控制曲线细化





Abaqus/CAE 在显示零件或零件实例时，对曲线面或曲线边使用分面表示。当您在 Part 模块中工作时，可以使用"Part Display Options"对话框中的 **Curve refinement** 选项来指定应用于当前零件的此分面程度。您可以在极粗到极细之间的五个分面级别中选择一个。将细化设置为 **Extra Coarse** 以加速大型模型的显示。将细化设置为 **Extra Fine** 如果您想要为打印创建非常精确的显示。Abaqus/CAE 仅将曲线细化设置应用于当前视口中的零件。

此外，Abaqus/CAE 在 Assembly 模块中使用零件实例的分面表示来确定零件实例之间的接触，并确定连接线的位置。您使用 **Curve refinement** 选项来控制接触和位置计算的准确性。

**控制曲线细化的步骤：**

1. 找到 **Curve refinement** 选项。从主菜单栏，选择 ****View**![](../graphics/images/arrow.gif)**Part Display Options****。在出现的对话框中，点击 **General** 选项卡。
2. 选择所需的曲线细化设置。
3. 点击 **OK** 实施您的更改并关闭对话框。Abaqus/CAE 仅将曲线细化设置应用于当前视口中的零件。

![](../graphics/images/black4rule.gif) 有关相关信息，请点击以下项：
- [第76章，"自定义几何和网格显示](pt07ch76.md)"
