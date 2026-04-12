# 45.3 Region 对象

Region 对象的目的是在属性与应用该属性的几何或离散实体之间提供链接。属性（Load、BC、IC 等）应用于一个或多个 Region 对象；每个 Region 对象又与拾取的 Set 或 Surface 或命名 Set 或 Surface 相关联。Region 对象提供统一接口（或"外观"），访问位于 Set 或 Surface 的数据和功能。

将属性应用于拾取的 Set 或 Surface 的脚本需要显式创建 Region 对象，并将隐式创建匹配的内部 Set 或 Surface。相反，将属性应用于命名 Set 或 Surface 的脚本需要显式创建该 Set 或 Surface（见 39.4），并将隐式创建区域对象。

Region 与 Set/Surface 之间的引用通过名称（用户提供的或内部的）。如果 Set/Surface 被抑制、删除或重命名，Region 对象将无法找到关联的 Set/Surface，并将此情况传达给属性，但不会受到其他影响。如果同名 Set/Surface 变为可用（仅对用户提供的名称可能），Region 对象将重新建立连接。纠正此问题的另一种方法是重新应用属性。

每当特定 Load、BC、IC 等命令接受命名集或命名曲面时，该命令也将接受 Region 对象。例如：

```
myRegion = regionToolset.Region(edges=edges1)
mdb.models['Model-1'].DisplacementBC(name='BC-1',
    createStepName='Initial', region=myRegion, u1=SET,
    u2=SET)
myRegion = regionToolset.Region(elements=e[1:100])
p = mdb.models['mirror'].parts['COLLAR_MIRROR-1']
p.SectionAssignment(region=myRegion, sectionName='Section-1')
```

 Abaqus 不提供 `regions` 存储库；作为替代，您应该为 Region 对象分配变量并通过变量引用它。Region 对象的生命周期与显示组使用的 [Leaf](pt01ch16pyo04.md) 对象的生命周期类似；因此，您应该在创建 Region 对象后立即使用它。Region 对象的内容不打算在再生后保留。如果使用过时的 Region 对象，脚本可能无法正确运行。

查询属性的 Region 将返回 Region 元组。元组的内容是集名称，后跟集的所有者和三个表示为整数的标志。标志指示区域空间、区域类型以及区域是否为内部集。

**访问**

```
import regionToolset
```

### 45.3.1 Region(...)

此命令创建类似集的区域。例如：

```
myRegion = regionToolset.Region(vertices=v[2:4],
    edges=e[4:5]+e[6:9])
```
参数与 `Set` 方法的参数相同，但 *name* 参数除外。

在大多数情况下，构造函数仅使用一个序列参数调用。参数 *xVertices*、*xEdges* 和 *xFaces* 用于排除较低维度的实体，并提供对区域内容的更精细控制。例如，以下语句定义了一个包含方形面但不包括其中两条边缘的区域：

```
region = regionToolset.Region(faces=f[3:4], xEdges=e[1:3])
```

**Path**

```
Region
```

**必需参数**

无。

**可选参数**

*elements*

 Element 对象序列。默认值为 `None`。

*nodes*

 Node 对象序列。默认值为 `None`。

*vertices*

 Vertex 对象序列。默认值为 `None`。

*edges*

 Edge 对象序列。默认值为 `None`。

*faces*

 Face 对象序列。默认值为 `None`。

*cells*

 Cell 对象序列。默认值为 `None`。

*referencePoints*

 ReferencePoint 对象序列。默认值为空序列。

*xVertices*

 Vertex 对象序列，用于从区域中排除特定顶点。默认值为 `None`。

*xEdges*

 Vertex 对象序列，用于从区域中排除特定边缘。默认值为 `None`。

*xFaces*

 Vertex 对象序列，用于从区域中排除特定面。默认值为 `None`。

*skinFaces*

元组元组，指定皮肤名称和与此皮肤关联的面序列。仅对 3D 和 2D 零件的几何区域有效。

*skinEdges*

元组元组，指定皮肤名称和与此皮肤关联的边缘序列。仅对轴对称零件的几何区域有效。

*stringerEdges*

元组元组，指定加强筋名称和与此加强筋关联的边缘序列。仅对 3D 和 2D 零件的几何区域有效。

**返回值**

Region 对象。

**异常**

无。

### 45.3.2 Region(...)

此命令创建类似曲面的区域。例如：

```
myRegion = regionToolset.Region(side1Faces=f[12:14])
```
参数与 `Surface` 方法的参数相同，但 *name* 参数除外。

**Path**

```
Region
```

**必需参数**

无。

**可选参数**

在大多数情况下，您仅需提供一个序列参数。

*side1Faces*

 Face 对象序列（曲面适用于面的 SIDE1）。默认值为 `None`。

*side2Faces*

 Face 对象序列（曲面适用于面的 SIDE2）。默认值为 `None`。

*side12Faces*

 Face 对象序列（曲面同时适用于面的 SIDE1 和 SIDE2）。默认值为 `None`。

*side1Edges*

 Edge 对象序列（曲面适用于边缘的 SIDE1）。默认值为 `None`。

*side2Edges*

 Edge 对象序列（曲面适用于边缘的 SIDE2）。默认值为 `None`。

*end1Edges*

 Edge 对象序列（曲面适用于边缘的 END1）。默认值为 `None`。

*end2Edges*

 Edge 对象序列（曲面适用于边缘的 END2）。默认值为 `None`。

*circumEdges*

 Edge 对象序列（曲面适用于边缘的周向）。默认值为 `None`。

*face1Elements*

 Element 对象序列（曲面适用于元素的 FACE1）。默认值为 `None`。

*face2Elements*

 Element 对象序列（曲面适用于元素的 FACE2）。默认值为 `None`。

*face3Elements*

 Element 对象序列（曲面适用于元素的 FACE3）。默认值为 `None`。

*face4Elements*

 Element 对象序列（曲面适用于元素的 FACE4）。默认值为 `None`。

*face5Elements*

 Element 对象序列（曲面适用于元素的 FACE5）。默认值为 `None`。

*face6Elements*

 Element 对象序列（曲面适用于元素的 FACE6）。默认值为 `None`。

*side1Elements*

 Element 对象序列（曲面适用于元素的 SIDE1）。默认值为 `None`。

*side2Elements*

 Element 对象序列（曲面适用于元素的 SIDE2）。默认值为 `None`。

*side12Elements*

 Element 对象序列（曲面同时适用于元素的 SIDE1 和 SIDE2）。默认值为 `None`。

*end1Elements*

 Element 对象序列（曲面适用于元素的 END1）。默认值为 `None`。

*end2Elements*

 Element 对象序列（曲面适用于元素的 END2）。默认值为 `None`。

*circumElements*

 Element 对象序列（曲面适用于元素的周向）。默认值为 `None`。

**返回值**

Region 对象。

**异常**

无。

### 45.3.3 成员

Region 对象没有成员。

