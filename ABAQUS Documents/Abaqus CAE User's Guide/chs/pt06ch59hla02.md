# 59.4 通过选择方向和间距创建附件点





您可以通过选择起点和方向并指定点的间距来定位附件点。如果需要，您可以通过将指定的点投影到选定的面上来创建附件点。您可以使用附件点来定义点式紧固件的位置。有关更多信息，请参见["关于紧固件，" 第29.1节](pt04ch29s01.md)。

**通过选择方向和间距创建附件点的步骤：**

1. 从主菜单栏，选择 ****Tools**![](../graphics/images/arrow.gif)**Attachment**![](../graphics/images/arrow.gif)**Points Along Direction****。
   **提示：**您也可以使用 ![](../graphics/ico_attPtByDir.png) 工具通过选择方向和间距来创建附件点，该工具位于 Interaction 模块或 Property 模块工具箱的附件工具中。有关工具箱中附件工具的图表，请参见["了解附件点和线，" 第59.1节](pt06ch59s01.md)。

2. 从当前视口，选择代表起点的点。您也可以在提示区域出现的文本字段中输入点的 *X*、*Y* 和 *Z* 坐标。Abaqus/CAE 显示**沿方向创建附件点**对话框。

3. 在对话框中，使用以下方法之一选择指定创建点方向的方法：
   - 选择 **End point**，然后单击 ![](../graphics/ico_selectBlue.png) 选择指定方向向量终点的点。
   - 选择 **Straight line**，然后单击 ![](../graphics/ico_selectBlue.png) 选择指定方向向量的直线。

4. 执行以下操作之一来指定沿方向向量的点的间距：
   - 选择 **Number of points between start and end points**，然后输入所需的点数。（仅当您选择终点来指定方向向量时，此选项才可用。）
   - 选择 **Spacing**，然后输入每个附件点之间的距离。执行以下操作之一来指定要创建的点数：
      - 选择 **Number of points along direction**，然后输入所需的点数。附件点可以延伸到方向向量的终点之外。单击 ![](../graphics/ico_flipArrow.png) 以反转方向向量。
      - 选择 **Auto-fit points between start and end points**，以允许 Abaqus/CAE 确定可以在起点和终点之间以指定间距创建的点数。

5. 默认情况下，Abaqus/CAE 在方向向量的两端创建额外的附件点。如果需要，请切换关闭 **At start point** 和/或 **At end point** 以防止 Abaqus/CAE 创建额外的点。

6. 要将指定的点投影到选定的面上，请显示 **Projection** 选项卡页面，然后执行以下操作：
   1. 切换打开 **Project onto faces**。
   2. 单击 ![](../graphics/ico_selectBlue.png)，然后选择要将点投影到的面。这些面可以是平面或非平面。
   3. 选择投影点的方法。
      - 选择 **Proximity** 以允许 Abaqus/CAE 从每个点到所选面上最近的点绘制向量。
      - 选择 **Direction** 以定义沿其投影点的向量。单击 ![](../graphics/ico_selectBlue.png) 以选择向量的**起点**和**终点**。
      有关更多信息，请参见["了解投影方法，" 第59.2节](pt06ch59s02.md)。

7. 默认情况下，Abaqus/CAE 创建一个将包含附件点的集合。如果需要，您可以修改集合名称。如果不想创建包含附件点的集合，请切换关闭 **Create set with name**。

8. 单击 **OK** 创建附件点。Abaqus/CAE 显示附件点。有关编辑附件点的信息，请参见["编辑通过选择方向和间距创建的附件点，" 第59.7.1节](pt06ch59s03hlb01.md)。

![](../graphics/images/black4rule.gif) 有关相关信息，请单击以下任一项：
- ["了解附件点和线，" 第59.1节](pt06ch59s01.md)
- ["关于紧固件，" 第29.1节](pt04ch29s01.md)



