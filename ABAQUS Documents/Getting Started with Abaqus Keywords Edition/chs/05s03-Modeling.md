# 5.3 壳体材料方向

壳单元与连续体单元不同，它使用每个单元局部的材料方向。各向异性材料数据（如纤维增强复合材料的数据）以及单元输出变量（如应力和应变）均基于这些局部材料方向来定义。在大位移分析中，壳体表面的局部材料轴随每个积分点处材料的平均运动而旋转。

## 5.3.1 默认局部材料方向

局部材料1方向和2方向位于壳体平面内。默认的局部1方向是全局1轴在壳体表面上的投影。如果全局1轴垂直于壳体表面，则局部1方向是全局3轴在壳体表面上的投影。局部2方向垂直于壳体表面内的局部1方向，使得局部1方向、局部2方向与表面正法向形成右手系（见图5-6）。

**图5-6** 默认局部壳体材料方向。

![../graphics/gss-localshell-nls.png](../graphics/gss-localshell-nls.png)

默认局部材料方向有时会产生问题；一个典型的例子是图5-7所示的圆柱体。

**图5-7** 圆柱体中默认局部材料1方向。

![../graphics/gss-one-direct.png](../graphics/gss-one-direct.png)

在图中大多数单元中，局部1方向是周向的。然而，有一排单元与全局1轴垂直。对于这些单元，局部1方向是全局3轴在壳体上的投影，使得局部1方向变成轴向而非周向。直接应力在局部1方向上的等值线图![../graphics/gsk_eqn00032.gif](../graphics/gsk_eqn00032.gif)看起来非常奇怪，因为对于大多数单元，![../graphics/gsk_eqn00032.gif](../graphics/gsk_eqn00032.gif)是周向应力，而对于某些单元，它是轴向应力。在这种情况下，有必要为模型定义更合适的局部方向，这将在下一节讨论。

## 5.3.2 创建替代材料方向

`*ORIENTATION`选项允许您直接控制局部材料方向。使用它可以用局部直角坐标系、柱坐标系或球坐标系来替代全局笛卡尔坐标系。通过指定两点*a*和*b*的位置来定义局部坐标系（![../graphics/gsk_eqn00042.gif](../graphics/gsk_eqn00042.gif)、![../graphics/gsk_eqn00043.gif](../graphics/gsk_eqn00043.gif)、![../graphics/gsk_eqn00044.gif](../graphics/gsk_eqn00044.gif)）的方向，如图5-8所示。例如，使用以下选项定义局部直角坐标系：

`*ORIENTATION`, SYSTEM=RECTANGULAR, NAME=LOCALR

44 `![../graphics/gsk_eqn00045.gif](../graphics/gsk_eqn00045.gif)`, `![../graphics/gsk_eqn00046.gif](../graphics/gsk_eqn00046.gif)`, `![../graphics/gsk_eqn00047.gif](../graphics/gsk_eqn00047.gif)`, `![../graphics/gsk_eqn00048.gif](../graphics/gsk_eqn00048.gif)`, `![../graphics/gsk_eqn00049.gif](../graphics/gsk_eqn00049.gif)`, `![../graphics/gsk_eqn00050.gif](../graphics/gsk_eqn00050.gif)`

**图5-8** 局部坐标系的定义。

![../graphics/gss-coord-system-nls.png](../graphics/gss-coord-system-nls.png)

`NAME`参数为此方向指定一个标签，点*a*（![../graphics/gsk_eqn00045.gif](../graphics/gsk_eqn00045.gif)、![../graphics/gsk_eqn00046.gif](../graphics/gsk_eqn00046.gif)、![../graphics/gsk_eqn00047.gif](../graphics/gsk_eqn00047.gif)）和点*b*（![../graphics/gsk_eqn00048.gif](../graphics/gsk_eqn00048.gif)、![../graphics/gsk_eqn00049.gif](../graphics/gsk_eqn00049.gif)、![../graphics/gsk_eqn00050.gif](../graphics/gsk_eqn00050.gif)）的坐标在全局笛卡尔坐标系中给出。然后通过`*SHELL SECTION`或`*SHELL GENERAL SECTION`选项上的`ORIENTATION`参数来引用局部坐标系。

您还必须指定另一条信息。还需要告诉Abaqus局部轴对应哪个材料方向。在`*ORIENTATION`之后的第二个数据行上，指定最接近垂直于壳体表面的局部轴（1、2或3）。Abaqus遵循轴的循环排列（1、2、3），并将您所选轴之后的轴投影到壳体区域上，形成材料1方向。例如，如果您选择![../graphics/gsk_eqn00042.gif](../graphics/gsk_eqn00042.gif)轴，Abaqus将![../graphics/gsk_eqn00043.gif](../graphics/gsk_eqn00043.gif)轴投影到壳体上形成材料1方向。材料2方向由壳体法向与材料1方向的叉乘定义。通常，最终的材料2方向与其他局部轴（在本例中为![../graphics/gsk_eqn00044.gif](../graphics/gsk_eqn00044.gif)轴）的投影在弯曲壳体上不会重合。

如果这些局部轴无法创建所需的材料方向，您可以指定绕所选轴的旋转。在投影到壳体表面以获得最终材料方向之前，其他两个局部轴会按此角度旋转。下面的选项块将创建如图5-9所示的局部坐标系：

`*ORIENTATION`, SYSTEM=RECTANGULAR, NAME=LOCALR

45 `![../graphics/gsk_eqn00045.gif](../graphics/gsk_eqn00045.gif)`, `![../graphics/gsk_eqn00046.gif](../graphics/gsk_eqn00046.gif)`, `![../graphics/gsk_eqn00047.gif](../graphics/gsk_eqn00047.gif)`, `![../graphics/gsk_eqn00048.gif](../graphics/gsk_eqn00048.gif)`, `![../graphics/gsk_eqn00049.gif](../graphics/gsk_eqn00049.gif)`, `![../graphics/gsk_eqn00050.gif](../graphics/gsk_eqn00050.gif)`

1, ![../graphics/gsk_eqn00051.gif](../graphics/gsk_eqn00051.gif)

同样，经过旋转的![../graphics/gsk_eqn00043.gif](../graphics/gsk_eqn00043.gif)和![../graphics/gsk_eqn00044.gif](../graphics/gsk_eqn00044.gif)轴被Abaqus投影到壳体单元的表面上。为了便于解释投影，所选轴应尽可能接近壳体法向。

**图5-9** 壳体单元局部坐标系的旋转。

![../graphics/gss-rotation-nls.png](../graphics/gss-rotation-nls.png)

如果图5-7所示圆柱体的中心线与全局3轴重合，则可以使用以下选项块来定义一致的材料方向：

`*ORIENTATION`, SYSTEM=CYLINDRICAL, NAME=CYLIND1

47 0., 0., 0., 0., 0., 1.

1, 0.

点*a*和*b*位于圆柱体的中心线上。由于圆柱体的方向与新定义的柱坐标系的方向一致，![../graphics/gsk_eqn00042.gif](../graphics/gsk_eqn00042.gif)轴是径向的，![../graphics/gsk_eqn00043.gif](../graphics/gsk_eqn00043.gif)轴是周向的，![../graphics/gsk_eqn00044.gif](../graphics/gsk_eqn00044.gif)轴是轴向的。![../graphics/gsk_eqn00042.gif](../graphics/gsk_eqn00042.gif)轴近似对应于壳体法向方向，并指定了零旋转；因此，![../graphics/gsk_eqn00043.gif](../graphics/gsk_eqn00043.gif)轴在壳体表面上的投影就是材料1方向。因此，材料1方向始终是周向的，相应的材料2方向始终是轴向的。
