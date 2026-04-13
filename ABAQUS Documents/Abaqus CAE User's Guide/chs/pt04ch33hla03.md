# 33.5 定义热容





您可以为部件或装配上的点定义集中热容。更多信息，请参见["点电容"，Abaqus Analysis User's Guide第30.4.1节](../usb/usb-link.md#usb-elm-ecapacitance)。

**要定义热容：**

1. 从Property模块或Interaction模块的主菜单栏中，选择****Special**![](../graphics/images/arrow.gif)**Inertia**![](../graphics/images/arrow.gif)**Create****。
2. 在出现的**Create Inertia**对话框中，命名惯性，选择**Heat capacitance**，然后单击**Continue**。
3. 使用以下方法之一选择要定义热容的点：
   - 在视口中选择点。完成选择后，单击鼠标按钮2。如果模型包含几何体和网格组件的组合，请从提示区域选择以下之一：
     - 选择**Geometry**以为部件或装配的几何部分或参考点定义热容。
     - 选择**Mesh**以为孤立网格组件定义热容。您可以使用角度方法从孤立网格中选择一组节点。更多信息，请参见["使用角度和特征边缘方法选择多个对象"，第6.2.3节](pt01ch06s02hlb03.md)。
   - 要从现有集列表中选择，请执行以下操作：
     1. 在提示区域右侧单击**Sets**以显示包含可用集列表的**Region Selection**对话框。
     2. 选择感兴趣的集，然后单击**Continue**。
   **注意：**默认选择方法基于您最近使用的选择方法。要切换到另一种方法，请在提示区域右侧单击**Select in Viewport**或**Sets**。
   出现**Edit Inertia**对话框。视口中突出显示了您要应用热容的区域。
4. 如果需要，切换**Use temperature-dependent data**并输入温度。
5. 如果需要，指定**Number of field variables**并输入第一个字段变量的值、第二个字段变量的值等。
6. 在**Data**表中，输入以下内容：
   **Capacitance** 输入电容大小，<img src="../graphics/usi_eqn00716.gif">（密度比热体积）。
7. 单击**OK**保存数据并关闭对话框。符号出现在视口中，代表您刚创建的热容。

![](../graphics/images/black4rule.gif)有关相关主题的信息，请单击以下任一项：
- ["控制属性的显示"，第76.15节](pt07ch76hla14.md)
- ["表示特殊工程特征的符号"，第C.3节](ap03s03.md)




