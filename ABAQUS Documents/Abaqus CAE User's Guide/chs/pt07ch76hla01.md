# 76.2 选择渲染样式





渲染样式是 Abaqus/CAE 显示模型的方式。您可以使用 ****View**![](../graphics/images/arrow.gif)**Part Display Options**** 和 ****View**![](../graphics/images/arrow.gif)**Assembly Display Options**** 菜单项以三种渲染样式之一显示模型：线框、隐藏或着色；这些样式如图 [图76-1](pt07ch76hla01.md#cae-render) 所示。以下是这些选择的说明。

**图76-1** 显示渲染样式选项的模型。从左到右：线框、隐藏和光源着色渲染样式。

![](../graphics/cae-render.png)

**线框**

显示模型边；内部边和外部边都可能可见。线框图产生一种框架式的视觉效果，面不在其中显示。线框是绘制最快的渲染样式。

**隐藏**

显示线框图，其中被模型遮挡的边要么不显示，要么以虚线显示，具体取决于您选择哪个选项。（有关此选项的更多信息，请参见 ["控制边可见性，" 第76.3节](pt07ch76hla02.md)。）隐藏图产生实心而非框架式的外观。

**着色**

显示填充图，其中光源似乎照射在模型上。着色图产生高度三维的视觉效果。着色图中附着在面上的边始终以黑色绘制。

**控制渲染样式的步骤：**

1. 找到 **Render Style** 选项。从主菜单栏，选择 ****View**![](../graphics/images/arrow.gif)**Part Display Options**** 或 ****View**![](../graphics/images/arrow.gif)**Assembly Display Options****。在出现的对话框中，点击 **General** 选项卡。
2. 从对话框顶部，点击 **Wireframe**、**Hidden** 或 **Shaded** 来选择您想要的样式。**提示：**您也可以使用位于 **Render Style** 工具栏中的线框 ![](../graphics/ico_displayWire.png)、隐藏 ![](../graphics/ico_displayHidden.png) 和着色 ![](../graphics/ico_displayShaded.png) 图标来选择渲染样式。
3. 点击 **OK** 实施您的更改并关闭对话框。Abaqus/CAE 以选定的样式渲染显示，您的更改会在会话期间保存。

![](../graphics/images/black4rule.gif) 有关相关信息，请点击以下任一项：
- [第76章，"自定义几何和网格显示](pt07ch76.md)"
- ["选择渲染样式，" 第55.2.1节](pt05ch55s02hlb01.md)
