# 33.3 定义点质量和旋转惯性





您可以为部件或装配上的点定义集中质量和旋转惯性。您还可以定义与质量和惯性成比例的阻尼。在Abaqus/Standard分析中，您可以定义复合阻尼。更多信息，请参见["点质量"，Abaqus Analysis User's Guide第30.1.1节](../usb/usb-link.md#usb-elm-emasses)和["旋转惯性"，Abaqus Analysis User's Guide第30.2.1节](../usb/usb-link.md#usb-elm-erotinertia)。

**要定义点质量和旋转惯性：**

1. 从Property模块或Interaction模块的主菜单栏中，选择****Special**![](../graphics/images/arrow.gif)**Inertia**![](../graphics/images/arrow.gif)**Create****。
2. 在出现的**Create Inertia**对话框中，命名惯性，选择**Point mass/inertia**，然后单击**Continue**。
3. 使用以下方法之一选择要定义质量和旋转惯性的点：
   - 在视口中选择点。完成选择后，单击鼠标按钮2。如果模型包含几何体和网格组件的组合，请从提示区域选择以下之一：
     - 选择**Geometry**以为部件或装配的几何部分或参考点定义点质量和旋转惯性。
     - 选择**Mesh**以为孤立网格组件定义点质量和旋转惯性。您可以使用角度方法从孤立网格中选择一组节点。更多信息，请参见["使用角度和特征边缘方法选择多个对象"，第6.2.3节](pt01ch06s02hlb03.md)。
   - 要从现有集列表中选择，请执行以下操作：
     1. 在提示区域右侧单击**Sets**以显示包含可用集列表的**Region Selection**对话框。
     2. 选择感兴趣的集，然后单击**Continue**。
   **注意：**默认选择方法基于您最近使用的选择方法。要切换到另一种方法，请在提示区域右侧单击**Select in Viewport**或**Sets**。
   出现**Edit Inertia**对话框。视口中突出显示了您要应用点质量和旋转惯性的区域。
4. 在**Magnitude**标签页的**Mass**部分，执行以下操作：
   - 对于各向同性质量，切换**Isotropic**并指定质量大小。
   - 对于各向异性质量，切换**Anisotropic**并指定质量分量<img src="../graphics/usi_eqn00712.gif">、<img src="../graphics/usi_eqn00713.gif">和<img src="../graphics/usi_eqn00714.gif">。
5. 在页面的**Rotary Inertia**部分，指定转动惯量（单位[ML2](../popups/usb-int-iconventions-unitsym.md)）。
   1. 如果要指定惯性积，请切换**Specify off-diagonal terms**。
   2. 输入转动惯量的值。
   **I11** 局部1轴的转动惯量，<img src="../graphics/usi_eqn00695.gif">。
   **I22** 局部2轴的转动惯量，<img src="../graphics/usi_eqn00696.gif">。
   **I33** 局部3轴的转动惯量，<img src="../graphics/usi_eqn00697.gif">。
   3. 如果适用，输入惯性积的值。
   **I12** 惯性积，<img src="../graphics/usi_eqn00698.gif">。
   **I13** 惯性积，<img src="../graphics/usi_eqn00699.gif">。
   **I23** 惯性积，<img src="../graphics/usi_eqn00700.gif">。
6. 如果要更改转动惯量的坐标系（**CSYS**），请单击![](../graphics/ico_selectBlue.png)并使用以下方法之一：
   - 在视口中选择现有的基准坐标系。
   - 按名称选择现有的基准坐标系。
     1. 在提示区域中单击**Datum CSYS List**以显示基准坐标系列表。
     2. 从列表中选择一个名称，然后单击**OK**。
   - 单击提示区域中的**Use Global CSYS**以返回全局坐标系。默认情况下，使用全局坐标系来定义转动惯性。
7. 使用**Damping**标签页定义质量或惯性比例阻尼。对于Abaqus/Standard分析，您还可以定义复合阻尼。您可以为质量和复合阻尼或惯性和复合阻尼指定值；但是，Abaqus仅使用与特定动态分析过程相关的阻尼。如果质量和转动惯性需要不同的阻尼值，则必须创建单独的惯性定义。
   - 在**Alpha**字段中，输入<img src="../graphics/usi_eqn00272.gif">因子以为直接积分动态或显式动态分析创建质量或惯性比例阻尼。此值在模态动态分析中被忽略。默认值为0.0。
   - 在**Composite**字段中，输入临界阻尼分数<img src="../graphics/usi_eqn00715.gif>，用于在模态动态分析中计算复合阻尼因子。此值在直接积分动态分析中被忽略。默认值为0.0。
8. 单击**OK**保存数据并关闭对话框。符号出现在视口中，代表您刚创建的点质量和旋转惯性。

![](../graphics/images/black4rule.gif)有关相关主题的信息，请单击以下任一项：
- ["控制属性的显示"，第76.15节](pt07ch76hla14.md)
- ["表示特殊工程特征的符号"，第C.3节](ap03s03.md)




