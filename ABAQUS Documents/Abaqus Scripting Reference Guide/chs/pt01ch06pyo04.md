# 6.4 PartInstance 对象





PartInstance 对象是 Part 对象的实例。

**访问**

```
import assembly
mdb.models[*name*].rootAssembly.allinstances
mdb.models[*name*].rootAssembly.instances[*name*]
```

### 6.4.1 Instance(...)

此方法创建 PartInstance 对象并将其放入 instances 仓库。

**路径**

```
mdb.models[*name*].rootAssembly.Instance
```

**必需参数**

*name*

一个 String，指定仓库键。名称必须是有效的 Abaqus 对象名称。

*part*

一个 [Part](pt01ch37pyo01.md) 对象要被实例化。如果零件不存在，则不会创建 PartInstance 对象。

**可选参数**

*autoOffset*

一个 Boolean，指定是否为新实例应用自动偏移，以将其与现有实例偏移开。默认值为 OFF。

*dependent*

一个 Boolean，指定零件实例是依赖的还是独立的。如果 *dependent*=OFF，则零件实例是独立的。默认值为 OFF。

**返回值**

一个 PartInstance 对象。

**异常**

无。

### 6.4.2 InstanceFromBooleanCut(...)

此方法在从基础零件实例减去或切割一组零件实例的几何后，在 `instances` 仓库中创建 PartInstance。

**路径**

```
mdb.models[*name*].rootAssembly.InstanceFromBooleanCut
```

**必需参数**

*name*

一个 String，指定仓库键。名称必须是有效的 Abaqus 对象名称。

*instanceToBeCut*

一个 PartInstance，指定要从中切割其他实例的基础实例。

*cuttingInstances*

一个 PartInstance 对象序列，指定要用作切割基础实例的实例。

**可选参数**

*originalInstances*

一个 SymbolicConstant，指定在合并操作后是否应抑制或删除原始实例。可能的值为 SUPPRESS 或 DELETE。默认值为 SUPPRESS。

**返回值**

一个 PartInstance 对象。

**异常**

无。

### 6.4.3 InstanceFromBooleanMerge(...)

此方法在合并两个或多个零件实例后，在 `instances` 仓库中创建 PartInstance。

**路径**

```
mdb.models[*name*].rootAssembly.InstanceFromBooleanMerge
```

**必需参数**

*name*

一个 String，指定仓库键。名称必须是有效的 Abaqus 对象名称。

*instances*

一个 PartInstance 对象序列，指定要合并的零件实例。

**可选参数**

*keepIntersections*

一个 Boolean，指定在合并操作后是否应保留 Abaqus 本机零件实例的边界交叉点。默认值为 False。

*originalInstances*

一个 SymbolicConstant，指定在合并操作后是否应抑制或删除原始实例。可能的值为 SUPPRESS 或 DELETE。默认值为 SUPPRESS。

*domain*

一个 SymbolicConstant，指定是合并指定零件实例的几何还是网格。可能的值为 GEOMETRY、MESH 或 BOTH。默认值为 GEOMETRY。

*mergeNodes*

一个 SymbolicConstant，指定应考虑合并指定零件实例的哪些节点。此参数仅在 *domain* 为 MESH 时适用。可能的值为 BOUNDARY_ONLY、ALL 或 NONE。默认值为 BOUNDARY_ONLY。

*nodeMergingTolerance*

一个 Float，指定将被合并并替换为新节点（位置为删除节点的平均位置）的指定零件实例节点之间的最大距离。此参数仅在 *domain* 为 MESH 时适用。默认值为 10–6。

*removeDuplicateElements*

一个 Boolean，指定是否将新零件中具有相同连接性的元素合并为单个元素。此参数仅在 *domain* 为 MESH 时适用。默认值为 True。

**返回值**

一个 PartInstance 对象。

**异常**

无。

### 6.4.4 LinearInstancePattern(...)

此方法创建多个 PartInstance 对象，以线性图案放置到 instances 仓库中。

**路径**

```
mdb.models[*name*].rootAssembly.LinearInstancePattern
```

**必需参数**

*instanceList*

一个 String 序列，指定要图案化的实例名称。

*number1*

一个 Int，指定沿图案第一个方向出现的实例总数，包括原始实例。

*spacing1*

一个 Float，指定沿图案第一个方向实例之间的间距。

*number2*

一个 Int，指定沿图案第二个方向出现的实例总数，包括原始实例。

*spacing2*

一个 Float，指定沿图案第二个方向实例之间的间距。

**可选参数**

*direction1*

三个 Float 序列，指定第一个方向的向量。默认值为 (1.0, 0.0, 0.0)。

*direction2*

三个 Float 序列，指定第二个方向的向量。默认值为 (0.0, 1.0, 0.0)。

**返回值**

一个 PartInstance 对象序列。

**异常**

无。

### 6.4.5 RadialInstancePattern(...)

此方法创建多个 PartInstance 对象，以径向图案放置到 instances 仓库中。

**路径**

```
mdb.models[*name*].rootAssembly.RadialInstancePattern
```

**必需参数**

*instanceList*

一个 String 序列，指定要图案化的实例名称。

*number*

一个 Int，指定径向图案中出现的实例总数，包括原始实例。

*totalAngle*

一个 Float，指定图案中第一个和最后一个实例之间的总角度（以度为单位）。正角度对应逆时针方向。值 360 和 360 表示一个特殊情况，即图案完整一圈。在这种情况下，由于副本将覆盖原始位置，因此不会将副本放置在最后一个位置。可能的值为 360.0 ![](../graphics/ker_eqn00013.gif) *totalAngle* ![](../graphics/ker_eqn00013.gif) 360.0。

**可选参数**

*point*

三个 Float 序列，指定径向图案的中心。默认值为 (0.0, 0.0, 0.0)。

*axis*

三个 Float 序列，指定径向图案的中心轴。默认值为 (0.0, 0.0, 1.0)。

**返回值**

一个 PartInstance 对象序列。

**异常**

无。

### 6.4.6 checkGeometry(...)

此方法检查零件实例几何的有效性，并打印零件实例上所有拓扑实体（面、边缘、顶点等）的计数。

**必需参数**

无。

**可选参数**

*detailed*

一个 Boolean，指定是否将详细输出打印到重放文件。默认值为 OFF。

*level*

一个 Int，指定执行的检查级别。值可以从 20 到 70，值越高报告的错误越不重要。默认值为 20，报告所有关键错误。使用默认值时，存储的有效性状态将更新以与此检查结果一致。

**返回值**

无

**异常**

如果这是依赖零件实例且 *level* 未指定或设置为 20，则抛出异常，因为无法更新依赖零件实例的有效性状态。在这种情况下，应在 [Part](pt01ch37pyo01.md) 上调用此命令。

```
The geometry of dependent part instances cannot be changed.
```

无。

### 6.4.7 Contact(...)

此方法将实例沿指定方向平移，直到与固定实例接触。

**必需参数**

*movableList*

要移动的零件实例上的 [Face](pt01ch07pyo05.md) 或 [Edge](pt01ch07pyo03.md) 对象序列。

*fixedList*

保持固定的零件实例上的 [Face](pt01ch07pyo05.md) 或 [Edge](pt01ch07pyo03.md) 对象序列。

*direction*

三个 Float 序列，指定接触方向。

*clearance*

一个 Float，指定沿接触方向两个面之间的距离。

**可选参数**

*isFaceEdges*

一个 Boolean，指定 Abaqus 如何计算接触。如果 *isFaceEdges* 为 OFF，则从可动面到固定面计算接触。如果 *isFaceEdges* 为 ON，则仅使用可动面的边缘而不是其内部来计算接触。默认值为 OFF。

**返回值**

一个 [Feature](pt01ch20pyo01.md) 对象。

**异常**

无。

### 6.4.8 ConvertConstraints()

此方法将实例的定位约束转换为绝对位置。该方法删除实例上的约束特征，但保留空间中的位置。

**参数**

无。

**返回值**

无

**异常**

无。

### 6.4.9 getPosition()

此方法打印应用于 PartInstance 对象的平移和旋转的总和。

**参数**

无。

**返回值**

无

**异常**

无。

### 6.4.10 getRotation()

此方法返回一个元组，包括旋转点、旋转轴和旋转角度（以度为单位）。

**参数**

无。

**返回值**

一个元组，包括旋转点、旋转轴和旋转角度（以度为单位）。

**异常**

无。

### 6.4.11 getTranslation()

此方法返回一个表示 *X*-、*Y*- 和 *Z*- 方向平移的三个 Float 元组。

**参数**

无。

**返回值**

一个表示平移的三个 Float 元组。

**异常**

无。

### 6.4.12 replace(...)

此方法用另一个零件的实例替换一个实例。

**必需参数**

*instanceOf*

一个 [Part](pt01ch37pyo01.md) 对象，指定将替换原始 [Part](pt01ch37pyo01.md) 的零件。

**可选参数**

*applyConstraints*

一个 Boolean，指定是在新实例上应用现有约束，还是将新实例定位在与原始实例相同的位置。默认值为 True。值为 False 表示约束将应用于实例，将从特征列表中删除。

**返回值**

无

**异常**

无。

### 6.4.13 rotateAboutAxis(...)

此方法将实例平移指定量。

**必需参数**

*axisPoint*

三个 Float 序列，指定轴上一点的 *X*-、*Y*- 和 *Z*- 坐标。

*axisDirection*

三个 Float 序列，指定轴的方向向量。

*angle*

一个 Float，指定旋转角度（以度为单位）。使用右手定则确定方向。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 6.4.14 translate(...)

此方法将实例平移指定量。

**必需参数**

*vector*

三个 Float 序列，指定平移向量。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 6.4.15 translateTo(...)

此方法将实例沿指定方向平移，直到与固定实例接触。

**必需参数**

*movableList*

要移动的零件实例上的 [Face](pt01ch07pyo05.md) 或 [Edge](pt01ch07pyo03.md) 对象序列。

*fixedList*

保持固定的零件实例上的 [Face](pt01ch07pyo05.md) 或 [Edge](pt01ch07pyo03.md) 对象序列。

*direction*

三个 Float 序列，指定接触方向。

*clearance*

一个 Float，指定沿接触方向两个面之间的距离。

**可选参数**

*vector*

三个 Float 序列，指定平移向量。如果指定了此参数，则可动实例将按指定量平移，而不求解实际接触。

**返回值**

一个 [Feature](pt01ch20pyo01.md) 对象。

**异常**

无。

### 6.4.16 成员

PartInstance 对象可以具有以下成员：

*name*

一个 String，指定仓库键。名称必须是有效的 Abaqus 对象名称。

*dependent*

一个 Boolean，指定零件实例是依赖的还是独立的。如果 *dependent*=OFF，则零件实例是独立的。默认值为 OFF。

*excludedFromSimulation*

一个 Boolean，指定零件实例是否从模拟中排除。如果 *excludedFromSimulation*=ON，则零件实例被排除在模拟之外。默认值为 OFF。

*geometryValidity*

一个 Boolean，指定实例几何的有效性。该值是计算的，但可以设置为 ON 以对无效实例执行特征和网格操作。如果实例最初无效，则无法保证此类操作会成功。

*analysisType*

一个 SymbolicConstant，指定零件类型。可能的值为 DEFORMABLE_BODY、EULERIAN、DISCRETE_RIGID_SURFACE 和 ANALYTIC_RIGID_SURFACE。

*referenceNode*

一个 Int，指定参考节点编号。此成员仅在 *analysisType*=DISCRETE_RIGID_SURFACE 或 ANALYTIC_RIGID_SURFACE 时有效。

*part*

一个 [Part](pt01ch37pyo01.md) 对象，指定被实例化的零件。

*sets*

一个 [Set](pt01ch45pyo04.md) 对象仓库，指定在零件上创建的集合。更多信息，请参见[第 45 章，"区域命令"](pt01ch45.md)。

*surfaces*

一个 [Surface](pt01ch45pyo05.md) 对象仓库，指定在零件上创建的表面。更多信息，请参见[第 45 章，"区域命令"](pt01ch45.md)。

*skins*

一个 [Skin](pt01ch45pyo06.md) 对象仓库，指定在零件上创建的蒙皮。更多信息，请参见[第 45 章，"区域命令"](pt01ch45.md)。

*stringers*

一个 [Stringer](pt01ch45pyo07.md) 对象仓库，指定在零件上创建的纵梁。更多信息，请参见[第 45 章，"区域命令"](pt01ch45.md)。

*vertices*

一个 [VertexArray](pt01ch07pyo15.md) 对象。

*ignoredVertices*

一个 [IgnoredVertexArray](pt01ch07pyo09.md) 对象。

*edges*

一个 [EdgeArray](pt01ch07pyo03.md) 对象。

*ignoredEdges*

一个 [IgnoredEdgeArray](pt01ch07pyo07.md) 对象。

*faces*

一个 [FaceArray](pt01ch07pyo05.md) 对象。

*cells*

一个 [CellArray](pt01ch07pyo01.md) 对象。

*datums*

一个 [Datum](pt01ch15pyo01.md) 对象仓库。

*elements*

一个 [MeshElementArray](pt01ch31pyo05.md) 对象。

*nodes*

一个 [MeshNodeArray](pt01ch31pyo09.md) 对象。

*elemFaces*

一个 [MeshFace](pt01ch31pyo08.md) 对象仓库，指定零件实例中的所有元素面。对于给定元素和该元素内给定的面索引，可以使用键 (i*8 + j) 从仓库中检索相应的 [MeshFace](pt01ch31pyo08.md) 对象，其中 i 和 j 分别是零基元素和面索引。

*elementFaces*

一个 [MeshFaceArray](pt01ch31pyo08.md) 对象。

*elemEdges*

一个 [MeshEdge](pt01ch31pyo04.md) 对象仓库，指定零件实例中的所有元素边缘。对于给定元素和该元素内给定面上的给定边缘索引，可以使用键 (i*32 + j*4 + k) 从仓库中检索相应的 [MeshEdge](pt01ch31pyo04.md) 对象，其中 i、j 和 k 分别是零基元素、面和边缘索引。

*elementEdges*

一个 [MeshEdgeArray](pt01ch31pyo04.md) 对象。

*referencePoints*

一个 [ReferencePoint](pt01ch07pyo13.md) 对象仓库。

*partName*

一个 String，指定创建实例的零件名称。




