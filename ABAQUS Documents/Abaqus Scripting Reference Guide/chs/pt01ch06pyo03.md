# 6.3 Feature 对象





以下命令对 Feature 对象进行操作。有关 Feature 对象的更多信息，请参见["Feature 对象"，第 20.1 节](pt01ch20pyo01.md)。

**访问**

```
import assembly
```

### 6.3.1 AttachmentLines(...)

此方法通过在给定源面和目标面集合之间创建附着线来创建 Feature 对象。给定点首先使用指定的投影方法投影到源面上。然后将点沿源面法向投影到目标面上。用户可以指定投影数量或投影向量长度用于投影到目标面上。然后在源面和最近目标面之间创建线。后续线在目标面之间创建。

**路径**

```
mdb.models[*name*].rootAssembly.AttachmentLines
```

**必需参数**

*name*

一个 String，指定唯一的特征名称。

*points*

一个点元组。每个点可以是 Vertex、Datum point、Reference point、Attachment point、孤网格 Node 或 Interesting point 对象。

*sourceFaces*

一个 [Face](pt01ch07pyo05.md) 对象序列，指定要将点投影到的几何面。

*sourceElementFaces*

一个 [MeshFace](pt01ch31pyo08.md) 对象序列，指定要将点投影到的孤网格元素面。

*targetFaces*

一个 [Face](pt01ch07pyo05.md) 对象序列，指定附着线将终止的几何面。

*targetElementFaces*

一个 [MeshFace](pt01ch31pyo08.md) 对象序列，指定附着线将终止的孤网格元素面。

**可选参数**

*projectionMethod*

一个 SymbolicConstant，指定用于投影到源面的方法。可能的值为 PROJECT_BY_PROXIMITY 和 PROJECT_BY_DIRECTION。默认值为 PROJECT_BY_PROXIMITY。

*projectionDirStartPt*

一个点，指定投影方向的起点，用于投影到源面上。点可以是 Vertex、Datum point、Reference point、Attachment point、孤网格 Node、Interesting Point 对象，或表示点坐标的 Float 元组。

*projectionDirEndPt*

一个点，指定投影方向的终点，用于投影到源面上。点可以是 Vertex、Datum point、Reference point、Attachment point、孤网格 Node、Interesting point 对象，或表示点坐标的 Float 元组。

*sourceToTargetProjMethod*

一个 SymbolicConstant，指定用于投影到目标面的方法。可能的值为 PROJECT_BY_NUMBER 和 PROJECT_BY_DISTANCE。默认值为 PROJECT_BY_NUMBER。

*numProjections*

一个整数，指定每个点应投影到的最大层数，当源到目标投影方法为 PROJECT_BY_NUMBER 时。

*projectionDistance*

一个 float，指定当源到目标投影方法为 PROJECT_BY_DISTANCE 时投影向量的最大距离。

*flipSourceToTargetDirection*

一个 Boolean，指定是否应翻转从源面到目标面的计算投影方向。

*setName*

一个 String，指定唯一的集合名称。

**返回值**

一个 Feature 对象。

**异常**

无。

### 6.3.2 Coaxial(...)

此方法移动实例，使其选定的面与固定实例的选定面同轴。

**路径**

```
mdb.models[*name*].rootAssembly.Coaxial
```

**必需参数**

*movableAxis*

圆柱或圆锥 Face on the part instance to be moved.

*fixedAxis*

圆柱或圆锥 Face on the part instance that remains fixed.

*flip*

一个 Boolean，指定轴是前向对齐（OFF）还是反向对齐（ON）。

**可选参数**

无。

**返回值**

一个 Feature 对象。

**异常**

AbaqusException。

### 6.3.3 CoincidentPoint(...)

此方法移动实例，使指定点与固定实例的指定点重合。

**路径**

```
mdb.models[*name*].rootAssembly.CoincidentPoint
```

**必需参数**

*movablePoint*

位于要移动的零件实例上的 Vertex、Datum point、ReferencePoint 或孤网格上的网格节点。

*fixedPoint*

位于保持固定的零件实例上的 Vertex、Datum point、ReferencePoint 或孤网格上的网格节点。

**可选参数**

无。

**返回值**

一个 Feature 对象。

**异常**

无。

### 6.3.4 EdgeToEdge(...)

此方法移动实例，使其边缘与固定实例的边缘平行。

**路径**

```
mdb.models[*name*].rootAssembly.EdgeToEdge
```

**必需参数**

*movableAxis*

要移动的零件实例上的直 Edge、Datum axis 或孤网格上的元素边缘。

*fixedAxis*

保持固定的零件实例上的直 Edge、Datum axis 或孤网格上的元素边缘。

*flip*

一个 Boolean，指定边缘是前向对齐（OFF）还是反向对齐（ON）。

*clearance*

一个 Float，指定两个边缘之间的距离（仅适用于二维和轴对称实例）。

**可选参数**

无。

**返回值**

一个 Feature 对象。

**异常**

AbaqusException。

### 6.3.5 FaceToFace(...)

此方法移动实例，使其面与固定实例的面重合。

**路径**

```
mdb.models[*name*].rootAssembly.FaceToFace
```

**必需参数**

*movablePlane*

要移动的零件实例上的平面 face、Datum plane 或孤网格上的面。

*fixedPlane*

保持固定的零件实例上的平面 face、Datum plane 或孤网格上的面。

*flip*

一个 Boolean，指定面的法线是前向对齐（OFF）还是反向对齐（ON）。

*clearance*

一个 Float，指定两个面之间的距离。

**可选参数**

无。

**返回值**

一个 Feature 对象。

**异常**

AbaqusException。

### 6.3.6 ParallelCsys(...)

此方法移动实例，使其 Datum 坐标系与固定实例的 Datum 坐标系平行。

**路径**

```
mdb.models[*name*].rootAssembly.ParallelCsys
```

**必需参数**

*movableCsys*

要移动的零件实例上的 Datum 坐标系。

*fixedCsys*

保持固定的零件实例上的 Datum 坐标系。

**可选参数**

无。

**返回值**

一个 Feature 对象。

**异常**

AbaqusException。

### 6.3.7 ParallelEdge(...)

此方法移动实例，使其边缘与固定实例的边缘平行。

**路径**

```
mdb.models[*name*].rootAssembly.ParallelEdge
```

**必需参数**

*movableAxis*

要移动的零件实例上的直 Edge、Datum axis 或孤网格上的元素边缘。

*fixedAxis*

保持固定的零件实例上的直 Edge、Datum axis 或孤网格上的元素边缘。

*flip*

一个 Boolean，指定边缘是前向对齐（OFF）还是反向对齐（ON）。

**可选参数**

无。

**返回值**

一个 Feature 对象。

**异常**

AbaqusException。

### 6.3.8 ParallelFace(...)

此方法移动实例，使其面与固定实例的面平行。

**路径**

```
mdb.models[*name*].rootAssembly.ParallelFace
```

**必需参数**

*movablePlane*

要移动的零件实例上的平面 face、Datum plane 或孤网格上的面。

*fixedPlane*

保持固定的零件实例上的平面 face、Datum plane 或孤网格上的面。

*flip*

一个 Boolean，指定面的法线是前向对齐（OFF）还是反向对齐（ON）。

**可选参数**

无。

**返回值**

一个 Feature 对象。

**异常**

AbaqusException。




