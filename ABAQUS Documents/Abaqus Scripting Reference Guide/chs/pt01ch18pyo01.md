# 18.1 Assembly 对象









以下命令对 Assembly 对象进行操作。有关 Assembly 对象的更多信息，请参阅"Assembly 对象"第 6.1 节。

**访问**

```
import meshEdit
```

### 18.1.1 collapseMeshEdge(...)

此方法折叠部件实例的四边形或三角形元素的边缘。

**必需参数**

*edge*

一个单一的 [MeshEdge](pt01ch31pyo04.md) 对象，指定要折叠的元素边缘。

*collapseMethod*

一个 SymbolicConstant，指定用于折叠边缘的方法。可能的值为 FORWARD、REVERSE 和 AVERAGE。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 18.1.2 combineElement(...)

此方法组合部件实例的两个三角形元素。

**必需参数**

*elements*

一个三角形 [MeshElement](pt01ch31pyo05.md) 对象序列，指定要组合的元素。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 18.1.3 deleteElement(...)

此方法从部件实例中删除给定元素。元素必须使用自底向上网格技术生成。

**必需参数**

*elements*

一个 [MeshElement](pt01ch31pyo05.md) 对象序列或包含元素的 Set 对象。

**可选参数**

*deleteUnreferencedNodes*

一个 Boolean，指定是否删除在给定元素被删除后变得未被引用的所有关联节点。默认值为 OFF。

**返回值**

无

**异常**

无。

### 18.1.4 projectNode(...)

此方法将给定部件实例的节点投影到网格实体、几何实体或基准对象上。

**必需参数**

*nodes*

要投影的 [MeshNode](pt01ch31pyo09.md) 对象序列。

*projectionReference*

一个对象，指定节点投影操作的目标。*projectionReference* 可以是以下任一对象：[MeshNode](pt01ch31pyo09.md)、[MeshEdge](pt01ch31pyo04.md)、[MeshFace](pt01ch31pyo08.md)、[Vertex](pt01ch07pyo15.md)、[Edge](pt01ch07pyo03.md)、[Face](pt01ch07pyo05.md)、[DatumPoint](pt01ch15pyo05.md)、[DatumAxis](pt01ch15pyo02.md) 或 [DatumPlane](pt01ch15pyo04.md)。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 18.1.5 editNode(...)

此方法更改部件实例上给定节点的坐标。

**必需参数**

*nodes*

包含节点的 MeshNode 对象序列或 Set 对象。

**可选参数**

*coordinate1*

一个 Float，指定第一个坐标的值。如果 *coordinate1* 和 *offset1* 都未指定，则现有值不变。

*coordinate2*

一个 Float，指定第二个坐标的值。如果 *coordinate2* 和 *offset2* 都未指定，则现有值不变。

*coordinate3*

一个 Float，指定第三个坐标的值。如果 *coordinate3* 和 *offset3* 都未指定，则现有值不变。

*coordinates*

一个三维坐标元组序列，指定每个给定节点的坐标。指定时，坐标元组的数量必须与给定节点的数量匹配，并按节点索引升序与给定节点对应排列。此外，不能指定 *coordinate1*、*coordinate2*、*coordinate3*、*offset1*、*offset2* 或 *offset3*。

*offset1*

一个 Float，指定要应用于指定节点第一个坐标值的偏移量。

*offset2*

一个 Float，指定要应用于指定节点第二个坐标值的偏移量。

*offset3*

一个 Float，指定要应用于指定节点第三个坐标值的偏移量。

*localCsys*

一个 DatumCsys 对象，指定局部坐标系。如果未指定，将使用全局坐标系。

*projectToGeometry*

一个 Boolean，指定是否将节点投影回其原始几何。例如，如果节点在一个面上，此方法首先将节点定位到新位置，然后将其投影回原始面。默认值为 ON。

**返回值**

无

**异常**

同一坐标分量不能同时指定坐标和偏移量。

### 18.1.6 mergeNodes(...)

合并部件实例的节点。节点必须使用自底向上网格技术生成。

**必需参数**

*nodes*

一个 [MeshNode](pt01ch31pyo09.md) 对象序列，指定要合并的节点。

**可选参数**

*tolerance*

一个 Float，指定将合并到单个节点的两个节点之间的最大距离。新节点的位置是合并节点的平均位置。默认值为 10⁻⁶。

*removeDuplicateElements*

一个 Boolean，指定是否将具有相同连接性的元素在合并后合并为单个元素。默认值为 True。

**返回值**

无

**异常**

无。

### 18.1.7 mergeNodes(...)

合并部件实例的两个节点。至少有一个节点必须使用自底向上网格技术生成。

**必需参数**

*node1*

一个 [MeshNode](pt01ch31pyo09.md) 对象，指定要合并的第一个节点。

*node2*

一个 [MeshNode](pt01ch31pyo09.md) 对象，指定要合并的第二个节点。

**可选参数**

*removeDuplicateElements*

一个 Boolean，指定是否将具有相同连接性的元素在合并后合并为单个元素。默认值为 True。

**返回值**

无

**异常**

无。

### 18.1.8 splitElement(...)

此方法将四边形元素拆分为三角形元素。

**必需参数**

*elements*

一个四边形 [MeshElement](pt01ch31pyo05.md) 对象序列，指定要拆分的元素。每个四边形元素通过较短的的对角线拆分为两个三角形元素。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 18.1.9 splitMeshEdge(...)

此方法拆分部件实例的四边形或三角形元素的边缘。

**必需参数**

*edge*

一个单一的 [MeshEdge](pt01ch31pyo04.md) 对象，指定要拆分的元素边缘。

**可选参数**

*parameter*

一个 Float，指定沿 *edge* 拆分的标准化距离。可能的值为 0.0 ≤ *parameter* ≤ 1.0。默认值为 0.5。

**返回值**

无

**异常**

无。

### 18.1.10 swapMeshEdge(...)

此方法交换部件实例的两个相邻三角形元素的的对角线。

**必需参数**

*edge*

一个单一的 [MeshEdge](pt01ch31pyo04.md) 对象，指定要交换的元素边缘。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 18.1.11 generateMeshByOffset(...)

此方法通过从表面边界向外法向生成元素层，从孤立网格表面生成实体或壳网格。

**必需参数**

*region*

一个 Region 对象，指定要偏移的区域。

*meshType*

一个 Symbolic Constant，指定要生成的网格类型。可能的值为 SOLID 或 SHELL。

*totalThickness*

一个 Float，指定实体层的总厚度。此参数仅在 *meshType*=SOLID 时适用。

*distanceBetweenLayers*

一个 Float，指定壳层之间的距离。此参数仅在 *meshType*=SHELL 时适用。

*numLayers*

一个 Int，指定要生成的元素层数。

**可选参数**

*offsetDirection*

一个 Symbolic Constant，指定偏移方向。此参数仅在给定区域涉及壳网格时是必需的。可能的值为 OUTWARD、INWARD 和 BOTH。默认值为 OUTWARD。

*initialOffset*

一个 Float，指定初始偏移的大小。默认值为零。

*shareNodes*

Boolean，指定第一层节点是否应与底面上的节点共享。默认值为 False。

*deleteBaseElements*

一个 Boolean，指定在生成偏移层后是否删除壳元素。默认值为 False。此参数仅在 *meshType*=SHELL 时适用。

*constantThicknessCorners*

一个 Boolean，指定是使用基于元素的厚度还是基于节点的厚度。默认值为 False。

*extendElementSets*

一个 Boolean，指定是否将包含底元素的现有元素集扩展到包括相应的偏移元素。默认值为 False。

**返回值**

无

**异常**

无。

### 18.1.12 redoMeshEdit()

此方法执行最近一次被 `undoMeshEdit` 方法撤消的网格编辑或自底向上网格操作。装配上必须当前可用的重做操作。这意味着用户必须在装配上执行了 `undoMeshEdit` 方法，并且用户之后没有在装配上执行任何进一步的网格编辑命令。这也意味着用户提供了足够的缓存大小来存储撤消操作。

**参数**

无。

**返回值**

无

**异常**

无。

### 18.1.13 undoMeshEdit()

此方法撤消装配上最近的网格编辑或自底向上网格操作，并将受影响部件实例上的网格恢复到其先前状态。装配上必须可用的网格编辑撤消操作。这意味着在执行网格编辑命令之前，用户已启用网格编辑撤消并提供了足够的缓存大小来存储网格编辑操作。

**参数**

无。

**返回值**

无

**异常**

无。





