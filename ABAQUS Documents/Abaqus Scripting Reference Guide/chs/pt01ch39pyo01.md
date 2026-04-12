# 39.1 Path 对象

Path 对象通过指定一系列节点或点来定义模型中的线。

**访问**

```
import visualization
session.paths[*name*]
```

### 39.1.1 Path(...)

此方法创建 Path 对象。

**Path**

```
session.Path
```

**必需参数**

*name*

字符串，指定存储库键。

*type*

 SymbolicConstant，指定要创建的路径类型。可选值为 NODE_LIST、POINT_LIST、EDGE_LIST、CIRCUMFERENTIAL 和 RADIAL。

*expression*

序列，指定构成路径的节点或点。路径表达式的定义取决于 *type* 参数。
- 如果 *type*=NODE_LIST，则 *expression* 必须是序列的序列。每个内部序列包含两个项目，第一个项目是字符串，指定零件实例的名称，第二个项目可以是 Int 序列或字符串序列，每个指定一个 Int 范围。
- 如果 *type*=POINT_LIST，则 *expression* 必须是三个 Float 的元组序列，指定每个点的坐标。
- 如果 *type*=EDGE_LIST，则 *expression* 必须是序列的序列。每个内部序列包含两个项目，第一个项目是字符串，指定零件实例的名称，第二个项目是四个 Int 的元组序列，唯一标识元素边缘。四个 Int 分别是：1. 元素标签。2. 元素面索引（从 1 开始）。3. 面边缘索引（从 1 开始）。4. 边缘方向。正数指定边缘方向从边缘起点节点到边缘终点节点。负数指定相反方向。
- 当 *type*=CIRCUMFERENTIAL 或 RADIAL 时，*expression* 必须是三个三个 Float 的元组序列，指定用于定义坐标系的点的坐标。

*circleDefinition*

 SymbolicConstant，指定定义圆的方法。此参数仅在 *type*=CIRCUMFERENTIAL 或 RADIAL 时有效。可选值为 ORIGIN_AXIS 和 POINT_ARC。

当值为 ORIGIN_AXIS 时，*expression* 中的前两个点是旋转轴上的点，第三个点位于 X 轴上。当值为 POINT_ARC 时，*expression* 中的三个点位于圆弧上。

*numSegments*

 Int，指定路径中等分段的数目。此参数仅在 *type*=CIRCUMFERENTIAL 或 RADIAL 时有效。

*startAngle*

 Float，指定圆周路径的起始角度。此参数仅在 *type*=CIRCUMFERENTIAL 时有效。

*endAngle*

 Float，指定圆周路径的结束角度。此参数仅在 *type*=CIRCUMFERENTIAL 时有效。

*radius*

 SymbolicConstant CIRCLE_RADIUS 或 Float，指定圆周路径的半径。此参数仅在 *type*=CIRCUMFERENTIAL 时有效。

*radialAngle*

 Float，指定径向路径与指定坐标系 *X* 轴之间的角度。此参数仅在 *type*=RADIAL 时有效。

*startRadius*

 SymbolicConstant CIRCLE_RADIUS 或 Float，指定径向路径的起始半径。此参数仅在 *type*=RADIAL 时有效。

*endRadius*

 SymbolicConstant CIRCLE_RADIUS 或 Float，指定径向路径的结束半径。此参数仅在 *type*=RADIAL 时有效。

**可选参数**

无。

**返回值**

Path 对象。

**异常**

ModelError、ErrorUnsupportedNodeData、ErrorUnsupportedPointData、ErrorIncorrectPathData、KeyError、ErrorEmptyPathName、ErrorPathNotFound 和 ErrorNoOdbPathDisplay。

ValueError：当 *type*=CIRCUMFERENTIAL 或 RADIAL 时，如果 *expression* 中指定的三个点共线。

### 39.1.2 成员

Path 对象的成员与 [Path](pt01ch39pyo01.md#ker-path-path-pyc) 方法的参数具有相同的名称和描述。

