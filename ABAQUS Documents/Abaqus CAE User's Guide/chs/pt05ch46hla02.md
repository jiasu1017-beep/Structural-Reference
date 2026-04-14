# 46.3 生成材料取向图

材料取向图在指定步骤和帧以及指定截面点显示模型中单元的材料方向。Abaqus/CAE将材料取向表示为单元积分点处的三轴。有关选择结果步骤的更多信息，请参见["选择特定结果步骤和帧，" 第42.3.1节](pt05ch42s01hlb01.md)。有关选择截面点位置的信息，请参见["选择截面点数据"中的"按类别选择截面点数据，" 第42.5.9节](pt05ch42s03s01.md#usv-res-visvariableshelldb)。

**要生成材料取向图：**

1. [打开包含分析结果的输出数据库](pt02ch09s06hlb02.md)。
2. 选择要显示的结果[步骤和帧](pt05ch42s01hlb01.md)。
3. 选择要显示的[截面点](pt05ch54s03hlb03.md)。
4. 选择您想要的绘图状态独立和材料取向图[自定义](pt05ch40s03s03.md)选项。
5. 从主菜单栏中，选择****Plot**![](../graphics/images/arrow.gif)**Material Orientations****，然后选择是在未变形形状、变形形状还是两者上绘制材料取向。**提示：**您还可以使用工具箱中的变形![](../graphics/ico_plotMatOrientDeformed.png)、未变形![](../graphics/ico_plotMatOrientUndeformed.png)或叠加![](../graphics/ico_plotMatOrientDefUndef.png)材料取向工具生成材料取向图。当前视口更改为显示自定义材料取向图。每次您在步骤和帧选择器、截面点选择器、绘图状态独立选项、叠加绘图选项（如果适用）或材料取向图选项对话框中单击**Apply**时，Abaqus会自动刷新您的材料取向图。

![](../graphics/images/black4rule.gif)有关相关信息，请单击以下项目：- ["材料取向图选项概述，" 第46.2节](pt05ch46hla01.md)

