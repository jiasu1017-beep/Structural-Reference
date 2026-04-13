# 37.5 创建将点连接到地的弹簧和阻尼器





在Abaqus/Standard分析中，您可以定义将点连接到地并表现出与场变量无关的相同线性行为的弹簧和阻阻器。更多信息，请参见["弹簧"，Abaqus Analysis User's Guide第32.1.1节](../usb/usb-link.md#usb-elm-espring)和["阻尼器"，Abaqus Analysis User's Guide第32.2.1节](../usb/usb-link.md#usb-elm-edashpot)。

您可以通过使用Step模块中的历史输出请求编辑器从弹簧/阻阻器获取应力和应变的历史数据。在编辑器的**Domain**部分，选择**Springs/Dashpots**并从出现的菜单中选择所需的弹簧/阻阻器。更多信息，请参见["创建输出请求"，第14.12.1节](pt03ch14s12hlb01.md)。

**要创建将点连接到地的弹簧和阻阻器：**

1. 从Property模块或Interaction模块的主菜单栏中，选择****Special**![](../graphics/images/arrow.gif)**Springs/Dashpots**![](../graphics/images/arrow.gif)**Create****。
2. 在出现的**Create Springs/Dashpots**对话框中，命名弹簧/阻阻器，选择**Connect points to ground**，然后单击**Continue**。
3. 使用以下方法之一选择要连接到地的点：
   - 在视口中选择点。（更多信息，请参见[第6章，"在视口中选择对象"](pt01ch06.md)。）
   **提示：**默认情况下，**Selection**工具栏中的![](../graphics/ico_filterVisible.png)**选择屏幕最近处的实体**工具处于关闭状态。如果进行模糊选择，Abaqus/CAE会高亮显示该点并在视口左下角显示该点的描述。使用**Next**和**Previous**按钮循环浏览可能的选择，然后单击**OK**确认您的选择。
   如果模型包含几何体和网格组件的组合，请从提示区域选择以下之一：
   - 选择**Geometry**以为几何体或参考点定义弹簧/阻阻器。
   - 选择**Mesh**以为网格定义弹簧/阻阻器。
   - 要从现有集列表中选择，请执行以下操作：
     1. 在提示区域右侧单击**Sets**以显示包含可用集列表的**Region Selection**对话框。
     2. 选择感兴趣的集，然后单击**Continue**。
   **注意：**默认选择方法基于您最近使用的选择方法。要切换到另一种方法，请在提示区域右侧单击**Select in Viewport**或**Sets**。
   出现**Edit Springs/Dashpots**对话框。
4. 在对话框的**Direction**部分，执行以下操作：
   - 单击**Degree of freedom**字段旁边的箭头，并选择弹簧/阻阻器关联的自由度。
   - 全局坐标系确定默认的弹簧/阻阻器方向。要为弹簧/阻阻器指定方向，单击![](../graphics/ico_selectBlue.png)。使用以下方法之一指定弹簧/阻阻器的方向：
   - 单击提示区域中的**Datum CSYS List**以从基准坐标系列表中选择名称。
   - 在视口中选择一个基准坐标系。
   - 单击提示区域中的**Use Global CSYS**以使用全局坐标系。Abaqus/CAE在视口中显示为弹簧/阻阻器指定的局部坐标系。
5. 在对话框的**Property**部分，选中适当的框以包含：
   - **Spring stiffness**。输入弹簧每相对位移的力。
   - **Dashpot coefficient**。输入阻阻器每相对速度的力。如果您同时定义弹簧和阻阻器行为，它们将并行作用。
6. 单击**OK**创建弹簧/阻阻器并关闭**Edit Springs/Dashpots**对话框。符号出现在视口中，代表您刚创建的弹簧/阻阻器。

![](../graphics/images/black4rule.gif)有关相关主题的信息，请单击以下任一项：
- ["编辑将点连接到地的弹簧和阻尼器所应用区域的"，第37.6节](pt04ch37hla04.md)
- ["控制属性的显示"，第76.15节](pt07ch76hla14.md)
- ["表示特殊工程特征的符号"，第C.3节](ap03s03.md)




