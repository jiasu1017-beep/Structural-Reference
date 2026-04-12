# 34.23 OdbSet 对象

集合对象用于标识模型的区域。

**访问**

```
import odbAccess
session.odbs[*name*].parts[*name*].elementSets[*name*]
session.odbs[*name*].parts[*name*].nodeSets[*name*]
session.odbs[*name*].parts[*name*].surfaces[*name*]
session.odbs[*name*].rootAssembly.elementSets[*name*]
session.odbs[*name*].rootAssembly.instances[*name*].elementSets[*name*]
session.odbs[*name*].rootAssembly.instances[*name*].nodeSets[*name*]
session.odbs[*name*].rootAssembly.instances[*name*].surfaces[*name*]
session.odbs[*name*].rootAssembly.nodeSets[*name*]
session.odbs[*name*].rootAssembly.surfaces[*name*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.elementSets[*name*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.nodeSets[*name*]
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]\
.instance.surfaces[*name*]
```

### 34.23.1 NodeSet(...)

此方法从 [OdbMeshNode](pt01ch34pyo18.md) 对象数组（用于部件实例级集合）或 [OdbMeshNode](pt01ch34pyo18.md) 对象数组序列（用于装配级集合）创建节点集。

**路径**

```
session.odbs[*name*].parts[*name*].NodeSet                   
```

```
session.odbs[*name*].rootAssembly.instances[*name*].NodeSet                   
```

```
session.odbs[*name*].rootAssembly.NodeSet                   
```

**必要参数**

*name*

一个字符串，指定集合的名称和仓库键。

*nodes*

[OdbMeshNode](pt01ch34pyo18.md) 对象序列。例如，对于部件：

```
nodes=part1.nodes[1:5]
```
对于装配：
```
nodes=(instance1.nodes[6:7], instance2.nodes[1:5])
```

**可选参数**

无。

**返回值**

OdbSet 对象。

**异常**

InvalidNameError。

### 34.23.2 NodeSetFromNodeLabels(...)

此方法从节点标签序列创建节点集。

**路径**

```
session.odbs[*name*].parts[*name*].NodeSetFromNodeLabels                   
```

```
session.odbs[*name*].rootAssembly.instances[*name*].NodeSetFromNodeLabels                   
```

```
session.odbs[*name*].rootAssembly.NodeSetFromNodeLabels                   
```

**必要参数**

*name*

一个字符串，指定集合的名称和仓库键。

*nodeLabels*

节点标签序列。节点标签是 Int 节点标识符序列。例如，对于部件：

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

OdbSet 对象。

**异常**

InvalidNameError。

### 34.23.3 ElementSet(...)

此方法从 [OdbMeshElement](pt01ch34pyo17.md) 对象数组（用于部件实例级集合）或 [OdbMeshElement](pt01ch34pyo17.md) 对象数组序列（用于装配级集合）创建元素集。

**路径**

```
session.odbs[*name*].parts[*name*].ElementSet                   
```

```
session.odbs[*name*].rootAssembly.instances[*name*].ElementSet                   
```

**必要参数**

*name*

一个字符串，指定集合的名称和仓库键。

*elements*

[OdbMeshElement](pt01ch34pyo17.md) 对象序列。例如，对于部件：

```
elements=instance1.elements[1:5]
```
对于装配：
```
elements=(instance1.elements[1:5], instance2.elements[1:5])
```

**可选参数**

无。

**返回值**

OdbSet 对象。

**异常**

InvalidNameError。

### 34.23.4 ElementSetFromElementLabels(...)

此方法从元素标签序列创建元素集。

**路径**

```
session.odbs[*name*].parts[*name*].ElementSetFromElementLabels                   
```

```
session.odbs[*name*].rootAssembly.instances[*name*].ElementSetFromElementLabels                   
```

```
session.odbs[*name*].rootAssembly.ElementSetFromElementLabels                   
```

**必要参数**

*name*

一个字符串，指定集合的名称和仓库键。

*elementLabels*

元素标签序列。元素标签是 Int 元素标识符序列。例如，对于部件：

```
elementLabels=(2,3,5,7)
```
对于装配：
```
elementLabels=(('Instance-1', (2,3,5,7)), ('Instance-2', (1,2,3)))
```

**可选参数**

无。

**返回值**

OdbSet 对象。

**异常**

InvalidNameError。

### 34.23.5 MeshSurface(...)

此方法从元素和侧面标识符为装配创建曲面。

**路径**

```
session.odbs[*name*].parts[*name*].MeshSurface                   
```

```
session.odbs[*name*].rootAssembly.instances[*name*].MeshSurface                   
```

```
session.odbs[*name*].rootAssembly.MeshSurface                   
```

**必要参数**

*name*

一个字符串，指定集合的名称和仓库键。

*meshSurfaces*

序列的序列。每个序列由元素序列和侧面标识符组成。可能的侧面标识符取决于元素类型，如下表所述：

| 元素序列 | 侧面标识符 |
| --- | --- |
| 实体单元 | FACE1, FACE2, FACE3, FACE4, FACE5, FACE6 |
| 三维壳单元 | SIDE1, SIDE2 |
| 二维单元 | FACE1, FACE2, FACE3, FACE4 |
| 线单元 | END, END2 |

例如：

```
side1Elements=instance1.elements[217:218]
side2Elements=instance2.elements[100:105]
assembly.MeshSurface(name='Surf-1',
meshSurfaces=((side1Elems,SIDE1),
(side2Elems,SIDE2)))
```

**可选参数**

无。

**返回值**

OdbSet 对象。

**异常**

InvalidNameError。

### 34.23.6 MeshSurfaceFromElsets(...)

此方法从元素集序列创建网格曲面。

**路径**

```
session.odbs[*name*].parts[*name*].MeshSurfaceFromElsets                   
```

```
session.odbs[*name*].rootAssembly.instances[*name*].MeshSurfaceFromElsets                   
```

```
session.odbs[*name*].rootAssembly.MeshSurfaceFromElsets                   
```

**必要参数**

*name*

一个字符串，指定集合的名称和仓库键。

*elementSetSeq*

元素集序列。例如，

```
elementSetSeq=((elset1,SIDE1),(elset2,SIDE2))
```
其中 `elset1=session.odbs[*name*].rootAssembly.elementSets['Clutch']` 并且 `SIDE1` 和 `SIDE2` 指示元素集的侧面。

**可选参数**

无。

**返回值**

OdbSet 对象。

**异常**

InvalidNameError。

### 34.23.7 MeshSurfaceFromLabels(...)

此方法从曲面标签序列创建网格曲面。

**路径**

```
session.odbs[*name*].parts[*name*].MeshSurfaceFromLabels                   
```

```
session.odbs[*name*].rootAssembly.instances[*name*].MeshSurfaceFromLabels                   
```

```
session.odbs[*name*].rootAssembly.MeshSurfaceFromLabels                   
```

**必要参数**

*name*

一个字符串，指定集合的名称和仓库键。

*surfaceLabels*

曲面标签序列。例如，

```
surfaceLabels=(('Instance-1', ((10, FACE1), (11, FACE2))), 
('Instance-2', ((10, FACE3), (12, FACE4))))
```
其中 `10` 是元素编号，`FACE1` 指示元素的侧面。

**可选参数**

无。

**返回值**

OdbSet 对象。

**异常**

InvalidNameError。

### 34.23.8 成员

OdbSet 对象可以具有以下成员：

*name*

一个字符串，指定集合的名称和仓库键。

*instanceNames*

字符串元组，指定节点、元素和面的命名空间；如果集合在 Part 或 [OdbInstance](pt01ch34pyo15.md) 对象上，则为 `None`。

*nodes*

一个 [OdbMeshNodeArray](pt01ch34pyo18.md) 对象，如果集合跨越多个部件实例，则此成员是每个部件实例的序列序列。

*elements*

一个 [OdbMeshElementArray](pt01ch34pyo17.md) 对象，如果集合跨越多个部件实例，则此成员是每个部件实例的序列序列。

*faces*

SymbolicConstant 元组，指定元素面。如果集合跨越多个部件实例，则此成员是每个部件实例的序列序列。
