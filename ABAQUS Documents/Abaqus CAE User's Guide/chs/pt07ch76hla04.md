# 76.5 定义网格特征边





您可以指定仅显示网格零件的特征边，如 ["控制边可见性，" 第76.3节](pt07ch76hla02.md) 中所述。您使用特征边来遮蔽网格提供的细节；特征边通常是正在网格化的零件的物理边缘，不包括所有附加的单元边缘。[图76-5](pt07ch76hla04.md#usi-featangle-partassembly) 显示了以三个不同特征角度（0、5和20）显示的网格零件。

**图76-5** 显示特征角度为0、5和20的图。

![](../graphics/usi-featangle-partassembly.png)

特征边被定义为法线相差超过"特征角度"的相邻边。当您选择 **Feature** 网格边可见性时，您可以自定义特征角度。较大的角度将减少特征边的数量；相反，较小的角度将导致更多边可见。默认网格特征角度为20。

**设置网格特征角度的步骤：**

1. 找到特征角度选项。从主菜单栏，选择 ****View**![](../graphics/images/arrow.gif)**Part Display Options**** 或 ****View**![](../graphics/images/arrow.gif)**Assembly Display Options****。在出现的对话框中，点击 **General** 选项卡。
2. 从对话框底部，从要显示的网格边列表中选择 **Feature edges**。Abaqus/CAE 在 **Feature** 右侧显示一个 **Angle** 数据字段。
3. 点击 **Angle** 数据输入字段，并输入所需的特征角度。
4. 点击 **OK** 实施您的更改并关闭对话框。您的更改会在会话期间保存。

![](../graphics/images/black4rule.gif) 有关相关信息，请点击以下任一项：
- ["控制边可见性，" 第76.3节](pt07ch76hla02.md)
- [第76章，"自定义几何和网格显示](pt07ch76.md)"
