# 45.4 Set 对象

如果集跨越多个零件实例，则成员 *vertices*、*edges*、*faces*、*cells*、*elements* 或 *nodes* 返回给定查询的所有顶点/边缘/面/细胞/元素/节点的序列，分别用于包含在集中的每个零件实例。例如：

```
assembly=mdb.models['Transmission'].rootAssembly
    clutchElements=assembly.instances['Clutch'].elements
    clutchSet=clutchElements[16:18]+clutchElements[78:80]
    housingElements=assembly.instances['Housing'].elements
    housingSet=housingElements[45:48]
    transmissionSet=assembly.Set(name='TransmissionSet', \
                                 elements=(clutchSet, housingSet))
    len(transmissionSet.elements)=7
    transmissionSet.elements[0]=mdb.models['Transmission'].rootAssembly.instances['Clutch-1'].elements[16]
    transmissionSet.elements[6]=mdb.models['Transmission'].rootAssembly.instances['housing-1'].elements[47]
```

**访问**

```
import part
mdb.models[*name*].parts[*name*].allInternalSets[*name*]
mdb.models[*name*].parts[*name*].allSets[*name*]
mdb.models[*name*].parts[*name*].sets[*name*]
import assembly
mdb.models[*name*].rootAssembly.allinstances.sets[*name*]
mdb.models[*name*].rootAssembly.allInternalSets[*name*]
mdb.models[*name*].rootAssembly.allSets[*name*]
mdb.models[*name*].rootAssembly.instances[*name*].sets[*name*]
mdb.models[*name*].rootAssembly.modelInstances[*i*].sets[*name*]
mdb.models[*name*].rootAssembly.sets[*name*]
```

### 45.4.1 Set(...)

此方法从模型数据库中的对象序列创建集。

**Path**

```
mdb.models[*name*].parts[*name*].Set
```

```
mdb.models[*name*].rootAssembly.Set
```

**必需参数**

*name*

 String，指定存储库键。

**可选参数**

必须提供至少一个序列参数 — *elements*、*nodes*、*vertices*、*edges*、*faces*、*cells* 或 *referencePoints*。参数 *xVertices*、*xEdges* 和 *xFaces* 用于排除较低维度的实体，并提供对集内容的更精细控制。例如，以下语句定义了一个包含方形面但不包括其中两条边缘的区域：

```
set = mdb.models['Model-1'].rootAssembly.Set(name='mySet', \
                                             faces=f[3:4], \
                                             xEdges=e[1:3])
```

*nodes*

 [MeshNode](pt01ch31pyo09.md) 对象序列。默认值为 `None`。

*elements*

 [MeshElement](pt01ch31pyo05.md) 对象序列。默认值为 `None`。

*region*

 Region 对象，指定要包含在集中的其他对象。默认值为 `None`。

*vertices*

 Vertex 对象序列。默认值为 `None`。

*edges*

 Edge 对象序列。默认值为 `None`。

*faces*

 Face 对象序列。默认值为 `None`。

*cells*

 Cell 对象序列。默认值为 `None`。

*xVertices*

 Vertex 对象序列，用于从集中排除特定顶点。默认值为 `None`。

*xEdges*

 Edge 对象序列，用于从集中排除特定边缘。默认值为 `None`。

*xFaces*

 Face 对象序列，用于从集中排除特定面。默认值为 `None`。

*referencePoints*

 ReferencePoint 对象序列。默认值为空序列。

*skinFaces*

元组元组，指定皮肤名称和与此皮肤关联的面序列。仅对 3D 和 2D 零件的几何区域有效。

*skinEdges*

元组元组，指定皮肤名称和与此皮肤关联的边缘序列。仅对轴对称零件的几何区域有效。

*stringerEdges*

元组元组，指定加强筋名称和与此加强筋关联的边缘序列。仅对 3D 和 2D 零件的几何区域有效。

**返回值**

Set 对象。

**异常**

InvalidNameError。

### 45.4.2 SetByBoolean(...)

此方法通过对两个或多个输入集执行布尔运算来创建集。

**Path**

```
mdb.models[*name*].parts[*name*].SetByBoolean
```

```
mdb.models[*name*].rootAssembly.SetByBoolean
```

**必需参数**

*name*

 String，指定存储库键。

*sets*

 Set 对象序列。

**可选参数**

*operation*

 SymbolicConstant，指定要执行的布尔运算。可选值为 UNION、INTERSECTION 和 DIFFERENCE。默认值为 UNION。请注意，如果指定了 DIFFERENCE，则给定输入集的顺序很重要；指定在第一个之后的所有集将从第一个中减去。

**返回值**

Set 对象。

**异常**

InvalidNameError。

### 45.4.3 SetFromColor(...)

此方法创建包含标记有指定颜色属性的面的集。第三方应用程序可以为面分配颜色属性，并且颜色属性可以从 ACIS 文件导入 Abaqus。您可以使用此方法仅在零件上创建集；但是，您可以从装配中的零件实例访问这些集。

**Path**

```
mdb.models[*name*].parts[*name*].SetFromColor
```

**必需参数**

*name*

 String，指定存储库键。

*color*

三个 Int 的序列，指定 RGB 颜色。值可以范围为 0 到 255。第一个整数为红色，第二个为绿色，第三个为蓝色。例如，黄色面的颜色为：

```
color=(255,255,0)
```

**可选参数**

无。

**返回值**

Set 对象。

**异常**

InvalidNameError。

### 45.4.4 SetFromElementLabels(...)

此方法从模型数据库中的元素标签序列创建集。

**Path**

```
mdb.models[*name*].parts[*name*].SetFromElementLabels
```

```
mdb.models[*name*].rootAssembly.SetFromElementLabels
```

**必需参数**

*name*

 String，指定存储库键。

*elementLabels*

元素标签序列。元素标签是 Int 元素标识符的序列。例如，对于零件：

```
elementLabels=(2,3,5,7)
```
 对于装配：
```
elementLabels=(('Instance-1', (2,3,5,7)),
      ('Instance-2', (1,2,3)))
```

**可选参数**

无。

**返回值**

Set 对象。

**异常**

InvalidNameError。

### 45.4.5 SetFromNodeLabels(...)

此方法从模型数据库中的节点标签序列创建集。

**Path**

```
mdb.models[*name*].parts[*name*].SetFromNodeLabels
```

```
mdb.models[*name*].rootAssembly.SetFromNodeLabels
```

**必需参数**

*name*

 String，指定存储库键。

*nodeLabels*

节点标签序列。节点标签是 Int 节点标识符的序列。例如，对于零件：

```
nodeLabels=(2,3,5,7)
```
对于装配：
```
nodeLabels=(('Instance-1', (2,3,5,7)), ('Instance-2', (1,2,3)))
```

**可选参数**

无。

**返回值**

Set 对象。

**异常**

InvalidNameError。

### 45.4.6 MapSetsFromOdb(...)

此方法基于从 Odb 中元素质心位置的映射集创建集。

**Path**

```
mdb.models[*name*].parts[*name*].MapSetsFromOdb
```

**必需参数**

*odbPath*

 String，指定包含源集的 ODB 路径。

*odbSets*

 ODB 上要映射的集名称列表。

**可选参数**

*partSets*

对应于 ODB 集的要构建或使用的集名称列表。

*method*

枚举，指定 OVERWRITE、APPEND、INTERSECT 或 REMOVE。默认为 OVERWRITE。

**返回值**

Set 对象或 Set 对象元组。

**异常**

无。

### 45.4.7 成员

Set 对象具有以下成员：

*elements*

 [MeshElementArray](pt01ch31pyo05.md) 对象。

*nodes*

 [MeshNodeArray](pt01ch31pyo09.md) 对象。

*vertices*

 [VertexArray](pt01ch07pyo15.md) 对象。

*edges*

 [EdgeArray](pt01ch07pyo03.md) 对象。

*faces*

 [FaceArray](pt01ch07pyo05.md) 对象。

*cells*

 [CellArray](pt01ch07pyo01.md) 对象。

*referencePoints*

 [ReferencePointArray](pt01ch07pyo13.md) 对象。

