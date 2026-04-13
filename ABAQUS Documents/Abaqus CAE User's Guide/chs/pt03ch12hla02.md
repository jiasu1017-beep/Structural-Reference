# 11.28 镜像部件





从主菜单栏选择****Shape**![](../graphics/images/arrow.gif)**Transform**![](../graphics/images/arrow.gif)**Mirror****可以将当前视口中的部件转换为其镜像。此操作类似于复制部件并使用镜像选项（["复制部件，"第11.5节](pt03ch11s05.md)）。但是，变换原始部件会保留完整特征创建历史和编辑这些特征的能力。您可以选择保留原始几何和镜像几何，并且可以选择任何平面或基准平面作为镜像平面。

镜像工具仅在当前视口包含三维实体或壳部件时可用。镜像特征，像所有特征一样，可以被删除、抑制和恢复；但是，镜像特征不包含可修改参数，因此在创建后无法编辑。

**镜像部件：**

1. 从主菜单栏，选择****Shape**![](../graphics/images/arrow.gif)**Transform**![](../graphics/images/arrow.gif)**Mirror****。
   **提示：**您也可以使用位于Part模块工具箱中的![](../graphics/ico_partMirror.png)工具来镜像部件。有关Part模块工具箱中工具的图表，请参见["使用Part模块工具箱，"第11.17节](pt03ch11s17.md)。
2. 从提示区域，切换**Keep original geometry**以在部件被镜像时保留原始几何。
3. 从提示区域，切换**Keep internal boundaries**以在部件被镜像时保留原始几何和新几何之间的任何相交边界。此选项与**Keep original geometry**一起使用才有效。
4. 从视口中选择一个基准平面或平面。Abaqus/CAE使用您选择的选项创建镜像几何。

![](../graphics/images/black4rule.gif)有关相关主题的信息，请点击以下项目：
- ["什么是基于特征建模？，"第11.3节](pt03ch11s03.md)




